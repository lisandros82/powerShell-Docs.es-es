---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,security
title: Uso de JEA
ms.openlocfilehash: 8a6fb2682cf82de8dd20a8699178d4abde4954c2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="using-jea"></a>Uso de JEA

> Se aplica a: Windows PowerShell 5.0

En este tema, se describen las distintas formas en que puede conectarse a un punto de conexión de JEA y usarlo.

## <a name="using-jea-interactively"></a>Usar JEA de forma interactiva

Si está probando la configuración de JEA o tiene tareas sencillas para que realicen los usuarios, puede usar JEA del mismo modo que lo haría con una sesión normal de comunicación remota de PowerShell.
Para las tareas complejas de comunicación remota, se recomienda usar la [comunicación remota implícita](#using-jea-with-implicit-remoting) en su lugar para facilitar a los usuarios al permitirles trabajar con los objetos de datos de forma local.

Para usar JEA de forma interactiva, necesitará:
- El nombre del equipo al que se conecta (puede ser el equipo local)
- El nombre del punto de conexión de JEA registrado en ese equipo
- Credenciales del equipo que tienen acceso al punto de conexión de JEA

Con esa información a mano, puede iniciar una sesión de JEA mediante [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) o [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Si la cuenta en la que está registrado actualmente tiene acceso al punto de conexión de JEA, puede omitir el parámetro `-Credential`.

Cuando el aviso de PowerShell cambie a `[localhost]: PS>`, sabrá que ya está interactuando con la sesión remota de JEA.
Puede ejecutar `Get-Command` para comprobar qué comandos están disponibles.
Deberá preguntarle a su administrador si hay alguna restricción en los parámetros disponibles o valores de parámetros permitidos.

Como recordatorio, las sesiones de JEA funcionan en modo NoLanguage, por lo que es posible que algunas de las formas en que suele usar PowerShell no estén disponibles.
Por ejemplo, no puede usar variables para almacenar datos o inspeccionar las propiedades en los objetos que devuelven los cmdlets.
En el siguiente ejemplo, se muestra un ejemplo de cómo puede estar usando PowerShell hoy y dos enfoques para lograr que funcione el mismo comando en modo NoLanguage.

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

Para invocaciones de comandos más complejas que dificultan este enfoque, considere el uso de la [comunicación remota implícita](#using-jea-with-implicit-remoting) o la [creación de funciones personalizadas](role-capabilities.md#creating-custom-functions) que encapsulen la funcionalidad que quiere.

## <a name="using-jea-with-implicit-remoting"></a>Uso de JEA con comunicación remota implícita

PowerShell admite un modelo de comunicación remota alternativo en que puede importar los cmdlets del proxy desde un equipo remoto en el equipo local e interactuar con ellos como si fueran comandos locales.
Se denomina comunicación remota implícita y se explica bien en [esta entrada del blog *Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).
La comunicación remota implícita es especialmente útil cuando se trabaja con JEA porque le permite trabajar con los cmdlets de JEA en un modo de lenguaje completo.
Esto significa que puede usar finalización con tabulación, variables, manipular objetos e incluso usar scripts locales para automatizar más fácilmente en un punto de conexión de JEA.
Cada vez que se invoca un comando de proxy, los datos se envían al punto de conexión de JEA en el equipo remoto y se ejecutan allí.

La comunicación remota implícita funciona mediante la importación de cmdlets de una sesión de PowerShell existente.
Puede optar por poner un prefijo en los nombres de cada cmdlet del proxy con una cadena de su elección para distinguir qué comandos son para el sistema remoto.
Se creará un módulo de script temporal que contiene todos los comandos de proxy y se podrá usar durante la sesión local de PowerShell.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Es posible que algunos sistemas no puedan importar toda la sesión de JEA debido a restricciones en los cmdlets de JEA predeterminados.
> Para solucionar esto, importe solo los comandos que necesita de la sesión de JEA al proporcionar sus nombres de forma explícita en el parámetro `-CommandName`.
> Una actualización futura abordará el problema de importación de sesiones de JEA completas en los sistemas afectados.

Si no puede importar una sesión de JEA debido a restricciones de los parámetros de JEA predeterminados, puede seguir los pasos siguientes para filtrar los comandos predeterminados del conjunto importado.
Aún podrá usar comandos como `Select-Object`, solo usará la versión local instalada en el equipo en lugar de la versión remota en la sesión de JEA.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands
```

También puede conservar los cmdlets de proxy de comunicación remota implícita mediante [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).
Para obtener más información sobre la comunicación remota implícita, consulte la documentación de ayuda de [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) e [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programatically"></a>Usar JEA mediante programación

JEA también se puede usar en sistemas de automatización y en aplicaciones de usuario, como sitios web y aplicaciones de soporte técnico internos.
El enfoque es el mismo que el del desarrollo de aplicaciones para comunicarse con puntos de conexión de PowerShell sin restricciones, con la salvedad de que el programa debe tener en cuenta que JEA limita los comandos que se pueden ejecutar en la sesión remota.

Para tareas simples y de uso único, puede usar [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) para ejecutar un conjunto de comandos con JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Para comprobar qué comandos están disponibles para su uso cuando se conecta a una sesión de JEA, ejecute `Get-Command` e itere los resultados para comprobar los parámetros permitidos.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Si está creando una aplicación de C#, puede crear un espacio de ejecución de PowerShell que se conecte a una sesión de JEA al especificar el nombre de la configuración de un objeto [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx).

```csharp

// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/en-us/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
                    creds);                // Credentials
// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a>Usar JEA con PowerShell Direct

Hyper-V en Windows 10 y Windows Server 2016 ofrece [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), una característica que permite a los administradores de Hyper-V administrar máquinas virtuales con PowerShell, con independencia de la configuración de red o de administración remota de la máquina virtual.

Puede usar PowerShell Direct con JEA para proporcionar acceso limitado a un administrador de Hyper-V a la máquina virtual, lo que puede ser útil si pierde la conectividad de red a la máquina virtual y necesita que un administrador de centro de datos corrija la configuración de red.

No se necesita ninguna configuración adicional para usar JEA en PowerShell Direct, pero el sistema operativo que se ejecuta en la máquina virtual debe ser Windows 10 o Windows Server 2016.
El administrador de Hyper-V puede conectarse al punto de conexión de JEA mediante los parámetros `-VMName` o `-VMId` en los cmdlets de PSRemoting:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Se recomienda encarecidamente que cree un usuario local dedicado con el único derecho de administrar el sistema para que lo usen los administradores de Hyper-V.
Recuerde que incluso un usuario sin privilegios puede iniciar sesión en una máquina de Windows de manera predeterminada, incluido al usar PowerShell sin restricciones.
Eso le permitirá examinar el sistema de archivos (o una parte) y obtener más información sobre el entorno del sistema operativo.
Para bloquear a un administrador de Hyper-V de manera que solo tenga acceso a una máquina virtual mediante PowerShell Direct con JEA, tendrá que denegar los derechos de inicio de sesión local a la cuenta de JEA del administrador de Hyper-V.