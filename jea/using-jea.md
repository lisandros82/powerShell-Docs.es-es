---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Uso de JEA
ms.openlocfilehash: fa3d3a3c8bc0090ec9ad788585ec5df933134173
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084052"
---
# <a name="using-jea"></a><span data-ttu-id="761dc-103">Uso de JEA</span><span class="sxs-lookup"><span data-stu-id="761dc-103">Using JEA</span></span>

> <span data-ttu-id="761dc-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="761dc-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="761dc-105">En este tema, se describen las distintas formas en que puede conectarse a un punto de conexión de JEA y usarlo.</span><span class="sxs-lookup"><span data-stu-id="761dc-105">This topic describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="761dc-106">Usar JEA de forma interactiva</span><span class="sxs-lookup"><span data-stu-id="761dc-106">Using JEA interactively</span></span>

<span data-ttu-id="761dc-107">Si está probando la configuración de JEA o tiene tareas sencillas para que realicen los usuarios, puede usar JEA del mismo modo que lo haría con una sesión normal de comunicación remota de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="761dc-107">If you are testing your JEA configuration or have simple tasks for users to perform, you can use JEA the same way you would a regular PowerShell remoting session.</span></span>
<span data-ttu-id="761dc-108">Para las tareas complejas de comunicación remota, se recomienda usar la [comunicación remota implícita](#using-jea-with-implicit-remoting) en su lugar para facilitar a los usuarios al permitirles trabajar con los objetos de datos de forma local.</span><span class="sxs-lookup"><span data-stu-id="761dc-108">For complex remoting tasks, it is recommended to use [implicit remoting](#using-jea-with-implicit-remoting) instead to make it easier for your users by allowing users to operate with the data objects locally.</span></span>

<span data-ttu-id="761dc-109">Para usar JEA de forma interactiva, necesitará:</span><span class="sxs-lookup"><span data-stu-id="761dc-109">To use JEA interactively, you will need:</span></span>
- <span data-ttu-id="761dc-110">El nombre del equipo al que se conecta (puede ser el equipo local)</span><span class="sxs-lookup"><span data-stu-id="761dc-110">The name of the computer you are connecting to (can be the local machine)</span></span>
- <span data-ttu-id="761dc-111">El nombre del punto de conexión de JEA registrado en ese equipo</span><span class="sxs-lookup"><span data-stu-id="761dc-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="761dc-112">Credenciales del equipo que tienen acceso al punto de conexión de JEA</span><span class="sxs-lookup"><span data-stu-id="761dc-112">Credentials for the computer that have access to the JEA endpoint</span></span>

<span data-ttu-id="761dc-113">Con esa información a mano, puede iniciar una sesión de JEA mediante [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) o [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="761dc-113">With that information in hand, you can start a JEA session using [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="761dc-114">Si la cuenta en la que está registrado actualmente tiene acceso al punto de conexión de JEA, puede omitir el parámetro `-Credential`.</span><span class="sxs-lookup"><span data-stu-id="761dc-114">If the account you're currently logged in as has access to the JEA endpoint, you can omit the `-Credential` parameter.</span></span>

<span data-ttu-id="761dc-115">Cuando el aviso de PowerShell cambie a `[localhost]: PS>`, sabrá que ya está interactuando con la sesión remota de JEA.</span><span class="sxs-lookup"><span data-stu-id="761dc-115">When the PowerShell prompt changes to `[localhost]: PS>` you will know that you are now interacting with the remote JEA session.</span></span>
<span data-ttu-id="761dc-116">Puede ejecutar `Get-Command` para comprobar qué comandos están disponibles.</span><span class="sxs-lookup"><span data-stu-id="761dc-116">You can run `Get-Command` to check which commands are available.</span></span>
<span data-ttu-id="761dc-117">Deberá preguntarle a su administrador si hay alguna restricción en los parámetros disponibles o valores de parámetros permitidos.</span><span class="sxs-lookup"><span data-stu-id="761dc-117">You will need to consult with your administrator to learn if there are any restrictions on the available parameters or allowable parameter values.</span></span>

<span data-ttu-id="761dc-118">Como recordatorio, las sesiones de JEA funcionan en modo NoLanguage, por lo que es posible que algunas de las formas en que suele usar PowerShell no estén disponibles.</span><span class="sxs-lookup"><span data-stu-id="761dc-118">As a reminder, JEA sessions operate in NoLanguage mode, so some of the ways you typically use PowerShell may not be available.</span></span>
<span data-ttu-id="761dc-119">Por ejemplo, no puede usar variables para almacenar datos o inspeccionar las propiedades en los objetos que devuelven los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="761dc-119">For instance, you cannot use variables to store data or inspect the properties on objects returned from cmdlets.</span></span>
<span data-ttu-id="761dc-120">En el siguiente ejemplo, se muestra un ejemplo de cómo puede estar usando PowerShell hoy y dos enfoques para lograr que funcione el mismo comando en modo NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="761dc-120">The below example shows an example of how you may be using PowerShell today, and two approaches to get the same command working in NoLanguage mode.</span></span>

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

<span data-ttu-id="761dc-121">Para invocaciones de comandos más complejas que dificultan este enfoque, considere el uso de la [comunicación remota implícita](#using-jea-with-implicit-remoting) o la [creación de funciones personalizadas](role-capabilities.md#creating-custom-functions) que encapsulen la funcionalidad que quiere.</span><span class="sxs-lookup"><span data-stu-id="761dc-121">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you desire.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="761dc-122">Uso de JEA con comunicación remota implícita</span><span class="sxs-lookup"><span data-stu-id="761dc-122">Using JEA with implicit remoting</span></span>

<span data-ttu-id="761dc-123">PowerShell admite un modelo de comunicación remota alternativo en que puede importar los cmdlets del proxy desde un equipo remoto en el equipo local e interactuar con ellos como si fueran comandos locales.</span><span class="sxs-lookup"><span data-stu-id="761dc-123">PowerShell supports an alternative remoting model where you can import proxy cmdlets from a remote machine on your local computer and interact with them as if they were local commands.</span></span>
<span data-ttu-id="761dc-124">Se denomina comunicación remota implícita y se explica bien en [esta entrada del blog *Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="761dc-124">This is called implicit remoting, and is explained well in [this *Hey, Scripting Guy!* blog post](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="761dc-125">La comunicación remota implícita es especialmente útil cuando se trabaja con JEA porque le permite trabajar con los cmdlets de JEA en un modo de lenguaje completo.</span><span class="sxs-lookup"><span data-stu-id="761dc-125">Implicit remoting is particularly useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span>
<span data-ttu-id="761dc-126">Esto significa que puede usar finalización con tabulación, variables, manipular objetos e incluso usar scripts locales para automatizar más fácilmente en un punto de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="761dc-126">This means you can use tab completion, variables, manipulate objects, and even use local scripts to more easily automate against a JEA endpoint.</span></span>
<span data-ttu-id="761dc-127">Cada vez que se invoca un comando de proxy, los datos se envían al punto de conexión de JEA en el equipo remoto y se ejecutan allí.</span><span class="sxs-lookup"><span data-stu-id="761dc-127">Anytime you invoke a proxy command, the data will be sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="761dc-128">La comunicación remota implícita funciona mediante la importación de cmdlets de una sesión de PowerShell existente.</span><span class="sxs-lookup"><span data-stu-id="761dc-128">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span>
<span data-ttu-id="761dc-129">Puede optar por poner un prefijo en los nombres de cada cmdlet del proxy con una cadena de su elección para distinguir qué comandos son para el sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="761dc-129">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing to distinguish which commands are for the remote system.</span></span>
<span data-ttu-id="761dc-130">Se creará un módulo de script temporal que contiene todos los comandos de proxy y se podrá usar durante la sesión local de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="761dc-130">A temporary script module containing all of the proxy commands will be created and can be used for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="761dc-131">Es posible que algunos sistemas no puedan importar toda la sesión de JEA debido a restricciones en los cmdlets de JEA predeterminados.</span><span class="sxs-lookup"><span data-stu-id="761dc-131">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span>
> <span data-ttu-id="761dc-132">Para solucionar esto, importe solo los comandos que necesita de la sesión de JEA al proporcionar sus nombres de forma explícita en el parámetro `-CommandName`.</span><span class="sxs-lookup"><span data-stu-id="761dc-132">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span>
> <span data-ttu-id="761dc-133">Una actualización futura abordará el problema de importación de sesiones de JEA completas en los sistemas afectados.</span><span class="sxs-lookup"><span data-stu-id="761dc-133">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="761dc-134">Si no puede importar una sesión de JEA debido a restricciones de los parámetros de JEA predeterminados, puede seguir los pasos siguientes para filtrar los comandos predeterminados del conjunto importado.</span><span class="sxs-lookup"><span data-stu-id="761dc-134">If you are unable to import a JEA session due to constraints on the default JEA parameters, you can follow the steps below to filter out the default commands from the imported set.</span></span>
<span data-ttu-id="761dc-135">Aún podrá usar comandos como `Select-Object`, solo usará la versión local instalada en el equipo en lugar de la versión remota en la sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="761dc-135">You will still be able to use commands like `Select-Object` -- you'll just use the local version installed on your computer instead of the remote one in the JEA session.</span></span>

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

<span data-ttu-id="761dc-136">También puede conservar los cmdlets de proxy de comunicación remota implícita mediante [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="761dc-136">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="761dc-137">Para obtener más información sobre la comunicación remota implícita, consulte la documentación de ayuda de [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) e [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="761dc-137">For more information about implicit remoting, check out the help documentation for [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) and [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="761dc-138">Usar JEA mediante programación</span><span class="sxs-lookup"><span data-stu-id="761dc-138">Using JEA programmatically</span></span>

<span data-ttu-id="761dc-139">JEA también se puede usar en sistemas de automatización y en aplicaciones de usuario, como sitios web y aplicaciones de soporte técnico internos.</span><span class="sxs-lookup"><span data-stu-id="761dc-139">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and web sites.</span></span>
<span data-ttu-id="761dc-140">El enfoque es el mismo que el del desarrollo de aplicaciones para comunicarse con puntos de conexión de PowerShell sin restricciones, con la salvedad de que el programa debe tener en cuenta que JEA limita los comandos que se pueden ejecutar en la sesión remota.</span><span class="sxs-lookup"><span data-stu-id="761dc-140">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints, with the caveat that the program should be aware that JEA is limiting the commands that can be run in the remote session.</span></span>

<span data-ttu-id="761dc-141">Para tareas simples y de uso único, puede usar [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) para ejecutar un conjunto de comandos con JEA.</span><span class="sxs-lookup"><span data-stu-id="761dc-141">For simple, one-off tasks, you can use [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) to run a set of commands using JEA.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="761dc-142">Para comprobar qué comandos están disponibles para su uso cuando se conecta a una sesión de JEA, ejecute `Get-Command` e itere los resultados para comprobar los parámetros permitidos.</span><span class="sxs-lookup"><span data-stu-id="761dc-142">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="761dc-143">Si está creando una aplicación de C#, puede crear un espacio de ejecución de PowerShell que se conecte a una sesión de JEA al especificar el nombre de la configuración de un objeto [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="761dc-143">If you are building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/library/system.management.automation.pscredential(v=vs.85).aspx)

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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="761dc-144">Usar JEA con PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="761dc-144">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="761dc-145">Hyper-V en Windows 10 y Windows Server 2016 ofrece [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), una característica que permite a los administradores de Hyper-V administrar máquinas virtuales con PowerShell, con independencia de la configuración de red o de administración remota de la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="761dc-145">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), a feature which allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="761dc-146">Puede usar PowerShell Direct con JEA para proporcionar acceso limitado a un administrador de Hyper-V a la máquina virtual, lo que puede ser útil si pierde la conectividad de red a la máquina virtual y necesita que un administrador de centro de datos corrija la configuración de red.</span><span class="sxs-lookup"><span data-stu-id="761dc-146">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM, which can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="761dc-147">No se necesita ninguna configuración adicional para usar JEA en PowerShell Direct, pero el sistema operativo que se ejecuta en la máquina virtual debe ser Windows 10 o Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="761dc-147">No additional configuration is required to use JEA over PowerShell Direct, however the operating system running inside the virtual machine must be Windows 10 or Windows Server 2016.</span></span>
<span data-ttu-id="761dc-148">El administrador de Hyper-V puede conectarse al punto de conexión de JEA mediante los parámetros `-VMName` o `-VMId` en los cmdlets de PSRemoting:</span><span class="sxs-lookup"><span data-stu-id="761dc-148">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="761dc-149">Se recomienda encarecidamente que cree un usuario local dedicado con el único derecho de administrar el sistema para que lo usen los administradores de Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="761dc-149">It is strongly recommended that you create a dedicated local user with no other rights to manage the system for your Hyper-V administrators to use.</span></span>
<span data-ttu-id="761dc-150">Recuerde que incluso un usuario sin privilegios puede iniciar sesión en una máquina de Windows de manera predeterminada, incluido al usar PowerShell sin restricciones.</span><span class="sxs-lookup"><span data-stu-id="761dc-150">Remember that even an unprivileged user can still log into a Windows machine by default, including using unconstrained PowerShell.</span></span>
<span data-ttu-id="761dc-151">Eso le permitirá examinar el sistema de archivos (o una parte) y obtener más información sobre el entorno del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="761dc-151">That will allow them to browse (some of) the file system and learn more about your OS environment.</span></span>
<span data-ttu-id="761dc-152">Para bloquear a un administrador de Hyper-V de manera que solo tenga acceso a una máquina virtual mediante PowerShell Direct con JEA, tendrá que denegar los derechos de inicio de sesión local a la cuenta de JEA del administrador de Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="761dc-152">To lock down a Hyper-V administrator to only access a VM using PowerShell Direct with JEA, you will need to deny local logon rights to the Hyper-V admin's JEA account.</span></span>
