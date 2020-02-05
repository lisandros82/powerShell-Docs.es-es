---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Uso de JEA
ms.openlocfilehash: 912e7a3c46be40ff5b5dfa37fe92b67bab5f98dc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995417"
---
# <a name="using-jea"></a>Uso de JEA

En este artículo se describen las distintas formas de poder conectarse a un punto de conexión de JEA y usarlo.

## <a name="using-jea-interactively"></a>Usar JEA de forma interactiva

Si va a probar la configuración de JEA o tiene tareas sencillas para los usuarios, puede usar JEA como haría con una sesión normal de comunicación remota de PowerShell. Para las tareas complejas de comunicación remota, se recomienda usar la [comunicación remota implícita](#using-jea-with-implicit-remoting). La comunicación remota implícita permite a los usuarios trabajar con los objetos de datos de forma local.

Para usar JEA de forma interactiva, necesita lo siguiente:

- El nombre del equipo al que se va a conectar (puede ser el equipo local)
- El nombre del punto de conexión de JEA registrado en ese equipo
- Credenciales que tienen acceso al punto de conexión de JEA en ese equipo

Con esa información, puede iniciar una sesión de JEA con los cmdlets [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) o [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Si la cuenta de usuario actual tiene acceso al punto de conexión de JEA, puede omitir el parámetro **Credential**.

Cuando el mensaje de PowerShell cambie a `[localhost]: PS>`, sabe que ahora va a interactuar con la sesión remota de JEA. Puede ejecutar `Get-Command` para comprobar qué comandos están disponibles. Consulte con el administrador para saber si hay alguna restricción en los parámetros disponibles o los valores de parámetro permitidos.

Recuerde que las sesiones de JEA funcionan en modo NoLanguage. Es posible que algunas de las formas en las que suele usar PowerShell no estén disponibles. Por ejemplo, no puede usar variables para almacenar datos ni inspeccionar las propiedades en los objetos que devuelven los cmdlets. En el ejemplo siguiente se muestran dos enfoques para lograr que los mismos comandos funcionen en modo NoLanguage.

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

Para invocaciones de comandos más complejos que dificultan este enfoque, le recomendamos usar la [comunicación remota implícita](#using-jea-with-implicit-remoting) o la [creación de funciones personalizadas](role-capabilities.md#creating-custom-functions) que encapsulen la funcionalidad que necesita.

## <a name="using-jea-with-implicit-remoting"></a>Uso de JEA con comunicación remota implícita

PowerShell dispone de un modelo de comunicación remota implícita que permite importar cmdlets de proxy desde un equipo remoto e interactuar con ellos como si fueran comandos locales. La comunicación remota implícita se explica en esta **entrada de blog** de [Hey, Scripting Guy!](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/)
La comunicación remota implícita es útil cuando se trabaja con JEA porque permite trabajar con los cmdlets de JEA en un modo de lenguaje completo. Puede usar finalización con tabulación, variables, manipular objetos e incluso usar scripts locales para automatizar las tareas para un punto de conexión de JEA. Siempre que se invoca un comando de proxy, los datos se envían al punto de conexión de JEA en el equipo remoto y se ejecutan allí.

La comunicación remota implícita funciona mediante la importación de cmdlets de una sesión de PowerShell existente. Puede optar por agregar la cadena que elija como prefijo en los nombres de cada cmdlet de proxy. El prefijo permite distinguir qué comandos son para el sistema remoto. Se crea un módulo de script temporal que contiene todos los comandos de proxy y se importa durante la sesión local de PowerShell.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Es posible que algunos sistemas no puedan importar toda la sesión de JEA debido a restricciones en los cmdlets de JEA predeterminados. Para solucionar esto, importe solo los comandos que necesita de la sesión de JEA al proporcionar sus nombres de forma explícita en el parámetro `-CommandName`. Una actualización futura abordará el problema de importación de sesiones de JEA completas en los sistemas afectados.

Si no puede importar una sesión de JEA debido a las restricciones de JEA sobre los parámetros predeterminados, siga los pasos siguientes para filtrar los comandos predeterminados del conjunto importado. Todavía puede usar comandos como `Select-Object`, pero solo la versión local instalada en el equipo en lugar de la que se ha importado desde la sesión remota de JEA.

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

También puede conservar los cmdlets de proxy de comunicación remota implícita mediante [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).
Para obtener más información sobre la comunicación remota implícita, vea la documentación de [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) e [Import-Module](/powershell/microsoft.powershell.core/import-module).

## <a name="using-jea-programmatically"></a>Usar JEA mediante programación

JEA también se puede usar en sistemas de automatización y en aplicaciones de usuario, como sitios web y aplicaciones de soporte técnico internos. El enfoque es el mismo que para crear aplicaciones que se comunican con puntos de conexión de PowerShell sin restricciones. Asegúrese de que el programa está diseñado para funcionar con la limitación impuesta por JEA.

Para tareas simples y de uso único, puede usar [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) para ejecutar comandos en una sesión de JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Para comprobar qué comandos están disponibles para su uso cuando se conecta a una sesión de JEA, ejecute `Get-Command` e itere los resultados para comprobar los parámetros permitidos.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Si va a compilar una aplicación de C#, puede crear un espacio de ejecución de PowerShell que se conecte a una sesión de JEA si especifica el nombre de la configuración de un objeto [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo).

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "https://schemas.microsoft.com/powershell/{0}", configName),
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

Hyper-V en Windows 10 y Windows Server 2016 ofrece [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), una característica que permite a los administradores de Hyper-V administrar máquinas virtuales con PowerShell, con independencia de la configuración de red o de administración remota de la máquina virtual.

Puede usar PowerShell Direct con JEA para proporcionar a un administrador de Hyper-V acceso limitado a la máquina virtual.
Esto puede ser útil si pierde la conectividad de red a la máquina virtual y necesita un administrador de centro de datos para corregir la configuración de red.

No se requiere ninguna configuración adicional para usar JEA en PowerShell Direct. Pero el sistema operativo invitado que se ejecuta dentro de la máquina virtual debe ser Windows 10, Windows Server 2016 o una versión posterior. El administrador de Hyper-V puede conectarse al punto de conexión de JEA mediante los parámetros `-VMName` o `-VMId` en los cmdlets de PSRemoting:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Se recomienda crear una cuenta de usuario dedicada con los derechos mínimos necesarios para administrar el sistema para uso por parte de un administrador de Hyper-V. Recuerde que incluso un usuario sin privilegios puede iniciar sesión en una máquina de Windows de manera predeterminada, incluido con PowerShell sin restricciones. Eso le permite examinar el sistema de archivos y obtener más información sobre el entorno del sistema operativo. Para bloquear a un administrador de Hyper-V y limitar su acceso a una máquina virtual solo mediante PowerShell Direct con JEA, tendrá que denegar los derechos de inicio de sesión local a la cuenta de JEA del administrador de Hyper-V.
