---
ms.date: 11/13/2018
keywords: powershell, cmdlet
title: Descodificación de un comando de PowerShell desde un proceso en ejecución
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086245"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>Descodificación de un comando de PowerShell desde un proceso en ejecución

En ocasiones, puede tener un proceso en ejecución que ocupa una gran cantidad de recursos de PowerShell.
Este proceso podría ejecutarse en el contexto de un trabajo del [Programador de tareas][] o el [Agente SQL Server][]. Cuando hay varios procesos de PowerShell en ejecución, puede ser difícil saber qué proceso representa el problema. En este artículo se muestra cómo descodificar un bloque de script que se está ejecutando un proceso de PowerShell.

## <a name="create-a-long-running-process"></a>Creación de un proceso de larga duración

Para demostrar este escenario, abra una nueva ventana de PowerShell y ejecute el siguiente código. Ejecuta un comando de PowerShell que da como resultado un número cada minuto durante 10 minutos.

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a>Visualización del proceso

El cuerpo del comando que PowerShell está ejecutando se almacena en la propiedad **CommandLine** de la clase [Win32_Process][]. Si el comando es un [comando codificado][], la propiedad **CommandLine** contiene la cadena "EncodedCommand". Con esta información, el comando codificado puede ser desofuscado mediante el siguiente proceso.

Inicie PowerShell como administrador. Es vital que PowerShell se esté ejecutando como administrador; de lo contrario, no se obtienen resultados al consultar los procesos en ejecución.

Ejecute el siguiente comando para obtener todos los procesos de PowerShell que tienen un comando codificado:

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

El siguiente comando crea un objeto de PowerShell personalizado que contiene el identificador de proceso y el comando codificado.

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

Ahora se puede descodificar el comando codificado. El fragmento de código siguiente recorre en iteración el objeto de detalles del comando, descodifica el comando codificado y agrega de nuevo el comando descodificado al objeto para seguir investigándolo.

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

Ahora se puede revisar el comando descodificado seleccionando la propiedad del comando descodificado.

```output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[Programador de tareas]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Agente SQL Server]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[comando codificado]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
