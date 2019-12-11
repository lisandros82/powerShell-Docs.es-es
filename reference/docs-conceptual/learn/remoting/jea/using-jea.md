---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Uso de JEA
ms.openlocfilehash: 8f3cc9186c61a2ae5b64eb3dc4f72ca83f1a58c5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "70017756"
---
# <a name="using-jea"></a><span data-ttu-id="694d9-103">Uso de JEA</span><span class="sxs-lookup"><span data-stu-id="694d9-103">Using JEA</span></span>

<span data-ttu-id="694d9-104">En este artículo se describen las distintas formas de poder conectarse a un punto de conexión de JEA y usarlo.</span><span class="sxs-lookup"><span data-stu-id="694d9-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="694d9-105">Usar JEA de forma interactiva</span><span class="sxs-lookup"><span data-stu-id="694d9-105">Using JEA interactively</span></span>

<span data-ttu-id="694d9-106">Si va a probar la configuración de JEA o tiene tareas sencillas para los usuarios, puede usar JEA como haría con una sesión normal de comunicación remota de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="694d9-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="694d9-107">Para las tareas complejas de comunicación remota, se recomienda usar la [comunicación remota implícita](#using-jea-with-implicit-remoting).</span><span class="sxs-lookup"><span data-stu-id="694d9-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="694d9-108">La comunicación remota implícita permite a los usuarios trabajar con los objetos de datos de forma local.</span><span class="sxs-lookup"><span data-stu-id="694d9-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="694d9-109">Para usar JEA de forma interactiva, necesita lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="694d9-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="694d9-110">El nombre del equipo al que se va a conectar (puede ser el equipo local)</span><span class="sxs-lookup"><span data-stu-id="694d9-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="694d9-111">El nombre del punto de conexión de JEA registrado en ese equipo</span><span class="sxs-lookup"><span data-stu-id="694d9-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="694d9-112">Credenciales que tienen acceso al punto de conexión de JEA en ese equipo</span><span class="sxs-lookup"><span data-stu-id="694d9-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="694d9-113">Con esa información, puede iniciar una sesión de JEA con los cmdlets [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) o [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="694d9-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="694d9-114">Si la cuenta de usuario actual tiene acceso al punto de conexión de JEA, puede omitir el parámetro **Credential**.</span><span class="sxs-lookup"><span data-stu-id="694d9-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="694d9-115">Cuando el mensaje de PowerShell cambie a `[localhost]: PS>`, sabe que ahora va a interactuar con la sesión remota de JEA.</span><span class="sxs-lookup"><span data-stu-id="694d9-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="694d9-116">Puede ejecutar `Get-Command` para comprobar qué comandos están disponibles.</span><span class="sxs-lookup"><span data-stu-id="694d9-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="694d9-117">Consulte con el administrador para saber si hay alguna restricción en los parámetros disponibles o los valores de parámetro permitidos.</span><span class="sxs-lookup"><span data-stu-id="694d9-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="694d9-118">Recuerde que las sesiones de JEA funcionan en modo NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="694d9-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="694d9-119">Es posible que algunas de las formas en las que suele usar PowerShell no estén disponibles.</span><span class="sxs-lookup"><span data-stu-id="694d9-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="694d9-120">Por ejemplo, no puede usar variables para almacenar datos ni inspeccionar las propiedades en los objetos que devuelven los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="694d9-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="694d9-121">En el ejemplo siguiente se muestran dos enfoques para lograr que los mismos comandos funcionen en modo NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="694d9-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

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

<span data-ttu-id="694d9-122">Para invocaciones de comandos más complejos que dificultan este enfoque, le recomendamos usar la [comunicación remota implícita](#using-jea-with-implicit-remoting) o la [creación de funciones personalizadas](role-capabilities.md#creating-custom-functions) que encapsulen la funcionalidad que necesita.</span><span class="sxs-lookup"><span data-stu-id="694d9-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="694d9-123">Uso de JEA con comunicación remota implícita</span><span class="sxs-lookup"><span data-stu-id="694d9-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="694d9-124">PowerShell dispone de un modelo de comunicación remota implícita que permite importar cmdlets de proxy desde un equipo remoto e interactuar con ellos como si fueran comandos locales.</span><span class="sxs-lookup"><span data-stu-id="694d9-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="694d9-125">La comunicación remota implícita se explica en esta **entrada de blog**</span><span class="sxs-lookup"><span data-stu-id="694d9-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="694d9-126">de [Hey, Scripting Guy!](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/)</span><span class="sxs-lookup"><span data-stu-id="694d9-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="694d9-127">La comunicación remota implícita es útil cuando se trabaja con JEA porque permite trabajar con los cmdlets de JEA en un modo de lenguaje completo.</span><span class="sxs-lookup"><span data-stu-id="694d9-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="694d9-128">Puede usar finalización con tabulación, variables, manipular objetos e incluso usar scripts locales para automatizar las tareas para un punto de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="694d9-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="694d9-129">Siempre que se invoca un comando de proxy, los datos se envían al punto de conexión de JEA en el equipo remoto y se ejecutan allí.</span><span class="sxs-lookup"><span data-stu-id="694d9-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="694d9-130">La comunicación remota implícita funciona mediante la importación de cmdlets de una sesión de PowerShell existente.</span><span class="sxs-lookup"><span data-stu-id="694d9-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="694d9-131">Puede optar por agregar la cadena que elija como prefijo en los nombres de cada cmdlet de proxy.</span><span class="sxs-lookup"><span data-stu-id="694d9-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="694d9-132">El prefijo permite distinguir qué comandos son para el sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="694d9-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="694d9-133">Se crea un módulo de script temporal que contiene todos los comandos de proxy y se importa durante la sesión local de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="694d9-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="694d9-134">Es posible que algunos sistemas no puedan importar toda la sesión de JEA debido a restricciones en los cmdlets de JEA predeterminados.</span><span class="sxs-lookup"><span data-stu-id="694d9-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="694d9-135">Para solucionar esto, importe solo los comandos que necesita de la sesión de JEA al proporcionar sus nombres de forma explícita en el parámetro `-CommandName`.</span><span class="sxs-lookup"><span data-stu-id="694d9-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="694d9-136">Una actualización futura abordará el problema de importación de sesiones de JEA completas en los sistemas afectados.</span><span class="sxs-lookup"><span data-stu-id="694d9-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="694d9-137">Si no puede importar una sesión de JEA debido a las restricciones de JEA sobre los parámetros predeterminados, siga los pasos siguientes para filtrar los comandos predeterminados del conjunto importado.</span><span class="sxs-lookup"><span data-stu-id="694d9-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="694d9-138">Todavía puede usar comandos como `Select-Object`, pero solo la versión local instalada en el equipo en lugar de la que se ha importado desde la sesión remota de JEA.</span><span class="sxs-lookup"><span data-stu-id="694d9-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

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

<span data-ttu-id="694d9-139">También puede conservar los cmdlets de proxy de comunicación remota implícita mediante [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="694d9-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="694d9-140">Para obtener más información sobre la comunicación remota implícita, vea la documentación de [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) e [Import-Module](/powershell/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="694d9-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="694d9-141">Usar JEA mediante programación</span><span class="sxs-lookup"><span data-stu-id="694d9-141">Using JEA programmatically</span></span>

<span data-ttu-id="694d9-142">JEA también se puede usar en sistemas de automatización y en aplicaciones de usuario, como sitios web y aplicaciones de soporte técnico internos.</span><span class="sxs-lookup"><span data-stu-id="694d9-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="694d9-143">El enfoque es el mismo que para crear aplicaciones que se comunican con puntos de conexión de PowerShell sin restricciones.</span><span class="sxs-lookup"><span data-stu-id="694d9-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="694d9-144">Asegúrese de que el programa está diseñado para funcionar con la limitación impuesta por JEA.</span><span class="sxs-lookup"><span data-stu-id="694d9-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="694d9-145">Para tareas simples y de uso único, puede usar [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) para ejecutar comandos en una sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="694d9-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="694d9-146">Para comprobar qué comandos están disponibles para su uso cuando se conecta a una sesión de JEA, ejecute `Get-Command` e itere los resultados para comprobar los parámetros permitidos.</span><span class="sxs-lookup"><span data-stu-id="694d9-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="694d9-147">Si va a compilar una aplicación de C#, puede crear un espacio de ejecución de PowerShell que se conecte a una sesión de JEA si especifica el nombre de la configuración de un objeto [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo).</span><span class="sxs-lookup"><span data-stu-id="694d9-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

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
    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),
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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="694d9-148">Usar JEA con PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="694d9-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="694d9-149">Hyper-V en Windows 10 y Windows Server 2016 ofrece [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), una característica que permite a los administradores de Hyper-V administrar máquinas virtuales con PowerShell, con independencia de la configuración de red o de administración remota de la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="694d9-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="694d9-150">Puede usar PowerShell Direct con JEA para proporcionar a un administrador de Hyper-V acceso limitado a la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="694d9-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="694d9-151">Esto puede ser útil si pierde la conectividad de red a la máquina virtual y necesita un administrador de centro de datos para corregir la configuración de red.</span><span class="sxs-lookup"><span data-stu-id="694d9-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="694d9-152">No se requiere ninguna configuración adicional para usar JEA en PowerShell Direct.</span><span class="sxs-lookup"><span data-stu-id="694d9-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="694d9-153">Pero el sistema operativo invitado que se ejecuta dentro de la máquina virtual debe ser Windows 10, Windows Server 2016 o una versión posterior.</span><span class="sxs-lookup"><span data-stu-id="694d9-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="694d9-154">El administrador de Hyper-V puede conectarse al punto de conexión de JEA mediante los parámetros `-VMName` o `-VMId` en los cmdlets de PSRemoting:</span><span class="sxs-lookup"><span data-stu-id="694d9-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="694d9-155">Se recomienda crear una cuenta de usuario dedicada con los derechos mínimos necesarios para administrar el sistema para uso por parte de un administrador de Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="694d9-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="694d9-156">Recuerde que incluso un usuario sin privilegios puede iniciar sesión en una máquina de Windows de manera predeterminada, incluido con PowerShell sin restricciones.</span><span class="sxs-lookup"><span data-stu-id="694d9-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="694d9-157">Eso le permite examinar el sistema de archivos y obtener más información sobre el entorno del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="694d9-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="694d9-158">Para bloquear a un administrador de Hyper-V y limitar su acceso a una máquina virtual solo mediante PowerShell Direct con JEA, tendrá que denegar los derechos de inicio de sesión local a la cuenta de JEA del administrador de Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="694d9-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
