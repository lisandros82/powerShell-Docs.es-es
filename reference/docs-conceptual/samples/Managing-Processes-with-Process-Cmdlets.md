---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Administración de procesos con cmdlets de proceso
ms.openlocfilehash: 8de0cbae508958bf7970ce69e03257ea0a8dca6f
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870751"
---
# <a name="managing-processes-with-process-cmdlets"></a>Administración de procesos con cmdlets de proceso

Puede usar los cmdlets Process en Windows PowerShell para administrar procesos locales y remotos en Windows PowerShell.

## <a name="getting-processes-get-process"></a>Obtener procesos (Get-Process)

Para obtener los procesos que se están ejecutando en el equipo local, ejecute **Get-Process** sin parámetros.

Puede obtener determinados procesos especificando sus nombres de proceso o identificadores de proceso. El siguiente comando obtiene el proceso inactivo:

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

Aunque es normal que los cmdlets no devuelvan datos en algunas situaciones, cuando se especifica un proceso por su id. de proceso **Get-Process**, genera un error si no encuentra ninguna coincidencia, porque la intención habitual consiste en recuperar un proceso en ejecución conocido. Si no hay ningún proceso con ese identificador, es probable que el identificador sea incorrecto o que el proceso de interés haya terminado:

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

Puede usar el parámetro Name del cmdlet Get-Process para especificar un subconjunto de procesos basado en el nombre del proceso. El parámetro Name puede tomar varios nombres de una lista de nombres separados por comas y admite el uso de caracteres comodín, para que pueda escribir patrones de nombre.

Por ejemplo, el siguiente comando obtiene el proceso cuyos nombres comienzan por "ex".

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

Dado que la clase System.Diagnostics.Process de .NET es la base de los procesos de Windows PowerShell, sigue algunas de las convenciones usadas por System.Diagnostics.Process. Una de estas convenciones es que el nombre de proceso de un archivo ejecutable nunca incluya ".exe" al final del nombre del ejecutable.

**Get-Process** también acepta varios valores para el parámetro Name.

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

Puede usar el parámetro ComputerName de Get-Process para obtener procesos en equipos remotos. Por ejemplo, el comando siguiente obtiene los procesos de PowerShell en el equipo local (representado por "localhost") y en dos equipos remotos.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

Los nombres de equipo no son evidentes en esta presentación, pero se almacenan en la propiedad MachineName de los objetos de proceso que devuelve Get-Process. El siguiente comando usa el cmdlet Format-Table para mostrar el identificador de proceso y las propiedades ProcessName y MachineName (ComputerName) de los objetos de proceso.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 |
  Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

Este comando más complejo agrega la propiedad MachineName a la presentación estándar de Get-Process.

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $()){$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a>Detener procesos (Stop-Process)

Windows PowerShell ofrece flexibilidad para enumerar procesos, pero ¿qué hay de detenerlos?

El cmdlet **Stop-Process** toma un nombre o un identificador para especificar un proceso que quiere detener. Su capacidad para detener procesos dependerá de sus permisos. Algunos procesos no se pueden detener. Por ejemplo, si intenta detener el proceso inactivo, obtendrá un error:

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

También puede forzar la solicitud con el parámetro **Confirm**. Este parámetro es especialmente útil si se usa un carácter comodín al especificar el nombre del proceso, ya que accidentalmente podría coincidir con algunos procesos que no quiere detener:

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

La manipulación de procesos complejos es posible si se usan algunos cmdlets de filtrado de objetos. Dado que un objeto Process tiene una propiedad Responding que es true cuando ya no responde, puede detener todas las aplicaciones que no respondan con el comando siguiente:

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

Puede usar el mismo enfoque en otras situaciones. Por ejemplo, supongamos que una aplicación de área de notificaciones secundaria se ejecuta automáticamente cuando los usuarios inician otra aplicación. Es posible que esto no funcione correctamente en las sesiones de Terminal Services, pero lo quiera seguir manteniendo en las sesiones que se ejecutan en la consola del equipo físico. Las sesiones conectadas en el escritorio del equipo físico siempre tienen un identificador de la sesión 0, por lo que puede detener todas las instancias del proceso que están en otras sesiones mediante **Where-Object** y el proceso, **SessionId**:

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

El cmdlet Stop-Process no tiene un parámetro ComputerName. Por lo tanto, para ejecutar un comando para detener un proceso en un equipo remoto, debe usar el cmdlet Invoke-Command. Por ejemplo, para detener el proceso de PowerShell en el equipo remoto Server01, escriba:

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>Detener todas las demás sesiones de Windows PowerShell

En ocasiones puede ser útil poder detener todas las sesiones de Windows PowerShell que se están ejecutando, excepto la sesión actual. Si una sesión usa demasiados recursos o es inaccesible (quizás se esté ejecutando de forma remota o en otra sesión de escritorio), es posible que no pueda detenerla directamente. Si intenta detener todas las sesiones que se están ejecutando, la sesión actual podría finalizar en su lugar.

Cada sesión de Windows PowerShell tiene un PID de variable de entorno que contiene el identificador del proceso de Windows PowerShell. Puede comprobar el $PID con el identificador de cada sesión y finalizar solo las sesiones de Windows PowerShell que tengan un identificador diferente. El siguiente comando de canalización realiza esta acción y devuelve la lista de las sesiones finalizadas (debido al uso del parámetro **PassThru**):

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a>Iniciar, depurar y esperar procesos

Windows PowerShell también incluye cmdlets para iniciar (o reiniciar) y depurar un proceso, así como para esperar a que un proceso se complete antes de ejecutar un comando. Para obtener información acerca de estos cmdlets, vea el tema de ayuda de cada cmdlet.

## <a name="see-also"></a>Consulte también

- [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)
- [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process)
- [Start-Process](/powershell/module/Microsoft.PowerShell.Management/Start-Process)
- [Wait-Process](/powershell/module/Microsoft.PowerShell.Management/Wait-Process)
- [Debug-Process](/powershell/module/Microsoft.PowerShell.Management/Debug-Process)
- [Invoke-Command](/powershell/module/Microsoft.PowerShell.Core/Invoke-Command)
