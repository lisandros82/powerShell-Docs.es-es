---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Creación de una canalización de integración continua e implementación continua con DSC
ms.openlocfilehash: 2d049cd640f0df9b018a88ad106e59dbeed7bcee
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954242"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="53fff-103">Creación de una canalización de integración continua e implementación continua con DSC</span><span class="sxs-lookup"><span data-stu-id="53fff-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="53fff-104">En este ejemplo se muestra cómo crear una canalización de integración continua/implementación continua (CI/CD) con PowerShell, DSC, Pester y Visual Studio Team Foundation Server (TFS).</span><span class="sxs-lookup"><span data-stu-id="53fff-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="53fff-105">Una vez que se construye y configura la canalización, puede usarla para implementar, configurar y probar completamente un servidor DSN y los registros host asociados.</span><span class="sxs-lookup"><span data-stu-id="53fff-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="53fff-106">Este proceso simula la primera parte de una canalización que se usaría en un entorno de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="53fff-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="53fff-107">Una canalización CI/CD automatizada le ayuda a actualizar software de forma más rápida y confiable, garantizando que se pruebe todo el código y que una compilación actual del código esté disponible en todo momento.</span><span class="sxs-lookup"><span data-stu-id="53fff-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="53fff-108">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="53fff-108">Prerequisites</span></span>

<span data-ttu-id="53fff-109">Para usar este ejemplo, debe estar familiarizado con lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="53fff-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="53fff-110">Los conceptos de CI-CD.</span><span class="sxs-lookup"><span data-stu-id="53fff-110">CI-CD concepts.</span></span> <span data-ttu-id="53fff-111">Puede encontrar una excelente referencia en [el modelo de canalización de versiones](https://aka.ms/thereleasepipelinemodelpdf).</span><span class="sxs-lookup"><span data-stu-id="53fff-111">A good reference can be found at [The Release Pipeline Model](https://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="53fff-112">El control de código fuente de [Git](https://git-scm.com/)</span><span class="sxs-lookup"><span data-stu-id="53fff-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="53fff-113">El entorno de pruebas [Pester](https://github.com/pester/Pester)</span><span class="sxs-lookup"><span data-stu-id="53fff-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="53fff-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="53fff-114">Team Foundation Server</span></span>](https://visualstudio.microsoft.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="53fff-115">Qué necesitará</span><span class="sxs-lookup"><span data-stu-id="53fff-115">What you will need</span></span>

<span data-ttu-id="53fff-116">Para compilar y ejecutar este ejemplo, necesitará un entorno con varios equipos o máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="53fff-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="53fff-117">Remoto</span><span class="sxs-lookup"><span data-stu-id="53fff-117">Client</span></span>

<span data-ttu-id="53fff-118">El equipo donde llevará a cabo todo el trabajo de configuración y ejecución del ejemplo.</span><span class="sxs-lookup"><span data-stu-id="53fff-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="53fff-119">El equipo cliente debe ser un equipo Windows que tenga instalado lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="53fff-119">The client computer must be a Windows computer with the following installed:</span></span>

- [<span data-ttu-id="53fff-120">Git</span><span class="sxs-lookup"><span data-stu-id="53fff-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="53fff-121">Un repositorio Git local clonado a partir de https://github.com/PowerShell/Demo_CI</span><span class="sxs-lookup"><span data-stu-id="53fff-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="53fff-122">Un editor de texto, como [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="53fff-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="53fff-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="53fff-123">TFSSrv1</span></span>

<span data-ttu-id="53fff-124">El equipo que hospeda el servidor TFS donde definirá la compilación y la versión.</span><span class="sxs-lookup"><span data-stu-id="53fff-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="53fff-125">Este equipo debe tener instalado [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/).</span><span class="sxs-lookup"><span data-stu-id="53fff-125">This computer must have [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="53fff-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="53fff-126">BuildAgent</span></span>

<span data-ttu-id="53fff-127">El equipo que ejecuta el agente de compilación Windows que compila el proyecto.</span><span class="sxs-lookup"><span data-stu-id="53fff-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="53fff-128">Este equipo debe tener instalado y en ejecución un agente de compilación Windows.</span><span class="sxs-lookup"><span data-stu-id="53fff-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="53fff-129">Consulte [Implementación de un agente en Windows](/azure/devops/pipelines/agents/v2-windows) para instrucciones sobre cómo instalar y ejecutar un agente de compilación Windows.</span><span class="sxs-lookup"><span data-stu-id="53fff-129">See [Deploy an agent on Windows](/azure/devops/pipelines/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="53fff-130">También necesita instalar los módulos `xDnsServer` y `xNetworking` de DSC en este equipo.</span><span class="sxs-lookup"><span data-stu-id="53fff-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="53fff-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="53fff-131">TestAgent1</span></span>

<span data-ttu-id="53fff-132">El equipo que la configuración de DSC configuró como servidor DNS en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="53fff-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="53fff-133">El equipo debe ejecutar [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="53fff-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="53fff-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="53fff-134">TestAgent2</span></span>

<span data-ttu-id="53fff-135">El equipo que hospeda el sitio web que se configura en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="53fff-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="53fff-136">El equipo debe ejecutar [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="53fff-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="53fff-137">Incorporación del código en TFS</span><span class="sxs-lookup"><span data-stu-id="53fff-137">Add the code to TFS</span></span>

<span data-ttu-id="53fff-138">Para comenzar, crearemos un repositorio Git en TFS e importaremos el código desde el repositorio local del equipo cliente.</span><span class="sxs-lookup"><span data-stu-id="53fff-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="53fff-139">Si todavía no clonó el repositorio Demo_CI en el equipo cliente, ejecute el siguiente comando de git para hacerlo ahora:</span><span class="sxs-lookup"><span data-stu-id="53fff-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="53fff-140">En el equipo cliente, vaya al servidor TFS en un explorador web.</span><span class="sxs-lookup"><span data-stu-id="53fff-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="53fff-141">En TFS, [cree un nuevo proyecto de equipo](/azure/devops/organizations/projects/create-project) llamado Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="53fff-141">In TFS, [Create a new team project](/azure/devops/organizations/projects/create-project) named Demo_CI.</span></span>

   <span data-ttu-id="53fff-142">Asegúrese de que el **control de versiones** esté establecido en **Git**.</span><span class="sxs-lookup"><span data-stu-id="53fff-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="53fff-143">En el equipo cliente, agregue un elemento remoto en el repositorio que acaba de crear en TFS con el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="53fff-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

   `git remote add tfs <YourTFSRepoURL>`

   <span data-ttu-id="53fff-144">Donde `<YourTFSRepoURL>` es la dirección URL de clonación al repositorio TFS que creó que en el paso anterior.</span><span class="sxs-lookup"><span data-stu-id="53fff-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

   <span data-ttu-id="53fff-145">Si no sabe dónde encontrar esta dirección URL, consulte cómo [clonar un repositorio Git existente](/azure/devops/repos/git/clone).</span><span class="sxs-lookup"><span data-stu-id="53fff-145">If you don't know where to find this URL, see [Clone an existing Git repo](/azure/devops/repos/git/clone).</span></span>
1. <span data-ttu-id="53fff-146">Inserte el código del repositorio local en el repositorio TFS con el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="53fff-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

   `git push tfs --all`
1. <span data-ttu-id="53fff-147">El repositorio TFS se rellenará con el código de Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="53fff-147">The TFS repository will be populated with the Demo_CI code.</span></span>

> [!NOTE]
> <span data-ttu-id="53fff-148">En este ejemplo se usa el código que se encuentra en la rama `ci-cd-example` del repositorio GIT.</span><span class="sxs-lookup"><span data-stu-id="53fff-148">This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
> <span data-ttu-id="53fff-149">Asegúrese de especificarla como la rama predeterminada del proyecto TFS y para los desencadenadores de CI/CD que crea.</span><span class="sxs-lookup"><span data-stu-id="53fff-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="53fff-150">Descripción del código</span><span class="sxs-lookup"><span data-stu-id="53fff-150">Understanding the code</span></span>

<span data-ttu-id="53fff-151">Antes de crear las canalizaciones de compilación e implementación, observemos parte del código para comprender qué es lo que pasa.</span><span class="sxs-lookup"><span data-stu-id="53fff-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="53fff-152">En el equipo cliente, abra el editor de texto de su preferencia y vaya a la raíz del repositorio Git de Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="53fff-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="53fff-153">La configuración de DSC</span><span class="sxs-lookup"><span data-stu-id="53fff-153">The DSC configuration</span></span>

<span data-ttu-id="53fff-154">Abra el archivo `DNSServer.ps1` (en la raíz del repositorio Demo_CI local, `./InfraDNS/Configs/DNSServer.ps1`).</span><span class="sxs-lookup"><span data-stu-id="53fff-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="53fff-155">Este archivo contiene la configuración de DSC que configura el servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="53fff-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="53fff-156">A continuación se muestra en su totalidad:</span><span class="sxs-lookup"><span data-stu-id="53fff-156">Here it is in its entirety:</span></span>

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

<span data-ttu-id="53fff-157">Observe la instrucción `Node`:</span><span class="sxs-lookup"><span data-stu-id="53fff-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="53fff-158">Esta instrucción encuentra cualquier nodo que se haya definido con un rol de `DNSServer` en los [datos de configuración](../configurations/configData.md), creados por el script `DevEnv.ps1`.</span><span class="sxs-lookup"><span data-stu-id="53fff-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](../configurations/configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="53fff-159">Puede obtener más información sobre el método `Where` en [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays).</span><span class="sxs-lookup"><span data-stu-id="53fff-159">You can read more about the `Where` method in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span></span>

<span data-ttu-id="53fff-160">Usar datos de configuración para definir nodos es importantes cuando se hace CI, porque es probable que la información de los nodos cambie entre los entornos y usar los datos de configuración le permite hacer cambios con facilidad en la información de los nodos sin cambiar el código de configuración.</span><span class="sxs-lookup"><span data-stu-id="53fff-160">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="53fff-161">En el primer bloque de recursos, la configuración llama a **WindowsFeature** para asegurarse de que la característica DNS está habilitada.</span><span class="sxs-lookup"><span data-stu-id="53fff-161">In the first resource block, the configuration calls the **WindowsFeature** to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="53fff-162">Los bloques de recursos siguientes llaman a recursos del módulo [xDnsServer](https://github.com/PowerShell/xDnsServer) para configurar la zona principal y los registros DNS.</span><span class="sxs-lookup"><span data-stu-id="53fff-162">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="53fff-163">Tenga en cuenta que los dos bloques `xDnsRecord` están encapsulados en bucles `foreach` que iteran a través de matrices en los datos de configuración.</span><span class="sxs-lookup"><span data-stu-id="53fff-163">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="53fff-164">Como ya indicamos, el script `DevEnv.ps1` crea los datos de configuración, los que analizaremos a continuación.</span><span class="sxs-lookup"><span data-stu-id="53fff-164">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="53fff-165">Datos de configuración</span><span class="sxs-lookup"><span data-stu-id="53fff-165">Configuration data</span></span>

<span data-ttu-id="53fff-166">El archivo `DevEnv.ps1` (de la raíz del repositorio Demo_CI local, `./InfraDNS/DevEnv.ps1`) especifica los datos de configuración específicos del entorno en una tabla hash y, luego, pasa esa tabla hash a una llamada a la función `New-DscConfigurationDataDocument`, que se define en `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span><span class="sxs-lookup"><span data-stu-id="53fff-166">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="53fff-167">El archivo `DevEnv.ps1`:</span><span class="sxs-lookup"><span data-stu-id="53fff-167">The `DevEnv.ps1` file:</span></span>

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

<span data-ttu-id="53fff-168">La función `New-DscConfigurationDataDocument` (que se define en `\Assets\DscPipelineTools\DscPipelineTools.psm1`) crea mediante programación un documento de datos de configuración desde la tabla hash (datos de nodo) y la matriz (datos no de nodo) que se pasan como los parámetros `RawEnvData` y `OtherEnvData`.</span><span class="sxs-lookup"><span data-stu-id="53fff-168">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="53fff-169">En el caso en cuestión, solo se usa el parámetro `RawEnvData`.</span><span class="sxs-lookup"><span data-stu-id="53fff-169">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="53fff-170">El script de compilación psake</span><span class="sxs-lookup"><span data-stu-id="53fff-170">The psake build script</span></span>

<span data-ttu-id="53fff-171">El script de compilación [psake](https://github.com/psake/psake) definido en `Build.ps1` (de la raíz del repositorio Demo_CI, `./InfraDNS/Build.ps1`) define las tareas que forman parte de la compilación.</span><span class="sxs-lookup"><span data-stu-id="53fff-171">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="53fff-172">También define las otras tareas de las que depende cada tarea.</span><span class="sxs-lookup"><span data-stu-id="53fff-172">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="53fff-173">Cuando se invoca, el script psake garantiza que la tarea especificada (o la tarea llamada `Default`, si no se especifica ninguna) se ejecute y que también se ejecuten todas las dependencias (esta acción es recursiva, por lo que se ejecutan las dependencias de las dependencias, y así sucesivamente).</span><span class="sxs-lookup"><span data-stu-id="53fff-173">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="53fff-174">En este ejemplo, la tarea `Default` se define de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="53fff-174">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="53fff-175">La tarea `Default` no tiene implementación, pero sí tiene una dependencia de la tarea `CompileConfigs`.</span><span class="sxs-lookup"><span data-stu-id="53fff-175">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="53fff-176">La cadena de dependencias de tareas resultante asegura que se ejecuten todas las tareas del script de compilación.</span><span class="sxs-lookup"><span data-stu-id="53fff-176">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="53fff-177">En este ejemplo, el script psake se invoca con una llamada a `Invoke-PSake` en el archivo `Initiate.ps1` (ubicado en la raíz del repositorio Demo_CI):</span><span class="sxs-lookup"><span data-stu-id="53fff-177">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

<span data-ttu-id="53fff-178">Cuando creamos la definición de compilación del ejemplo en TFS, proporcionamos el archivo de script psake como el parámetro `fileName` de este script.</span><span class="sxs-lookup"><span data-stu-id="53fff-178">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="53fff-179">El script de compilación define las siguientes tareas:</span><span class="sxs-lookup"><span data-stu-id="53fff-179">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="53fff-180">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="53fff-180">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="53fff-181">Ejecuta `DevEnv.ps1`, que genera el archivo de datos de configuración.</span><span class="sxs-lookup"><span data-stu-id="53fff-181">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="53fff-182">InstallModules</span><span class="sxs-lookup"><span data-stu-id="53fff-182">InstallModules</span></span>

<span data-ttu-id="53fff-183">Instala los módulos que requiere la configuración `DNSServer.ps1`.</span><span class="sxs-lookup"><span data-stu-id="53fff-183">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="53fff-184">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="53fff-184">ScriptAnalysis</span></span>

<span data-ttu-id="53fff-185">Llama al [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="53fff-185">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="53fff-186">UnitTests</span><span class="sxs-lookup"><span data-stu-id="53fff-186">UnitTests</span></span>

<span data-ttu-id="53fff-187">Ejecuta las pruebas unitarias [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="53fff-187">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="53fff-188">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="53fff-188">CompileConfigs</span></span>

<span data-ttu-id="53fff-189">Compila la configuración (`DNSServer.ps1`) en un archivo MOF, usando los datos de configuración que genera la tarea `GenerateEnvironmentFiles`.</span><span class="sxs-lookup"><span data-stu-id="53fff-189">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="53fff-190">Clean</span><span class="sxs-lookup"><span data-stu-id="53fff-190">Clean</span></span>

<span data-ttu-id="53fff-191">Crea la carpeta que se usa en el ejemplo y quita los resultados de pruebas, los archivos de datos de configuración y los módulos de ejecuciones anteriores.</span><span class="sxs-lookup"><span data-stu-id="53fff-191">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="53fff-192">El script de implementación psake</span><span class="sxs-lookup"><span data-stu-id="53fff-192">The psake deploy script</span></span>

<span data-ttu-id="53fff-193">El script de implementación [psake](https://github.com/psake/psake) definido en `Deploy.ps1` (de la raíz del repositorio Demo_CI, `./InfraDNS/Deploy.ps1`) define las tareas que implementan y ejecutan la configuración.</span><span class="sxs-lookup"><span data-stu-id="53fff-193">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="53fff-194">`Deploy.ps1` define las tareas siguientes:</span><span class="sxs-lookup"><span data-stu-id="53fff-194">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="53fff-195">DeployModules</span><span class="sxs-lookup"><span data-stu-id="53fff-195">DeployModules</span></span>

<span data-ttu-id="53fff-196">Inicia una sesión de PowerShell en `TestAgent1` e instala los módulos que contienen los recursos de DSC que se requieren en la configuración.</span><span class="sxs-lookup"><span data-stu-id="53fff-196">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="53fff-197">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="53fff-197">DeployConfigs</span></span>

<span data-ttu-id="53fff-198">Llama al cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) para ejecutar la configuración en `TestAgent1`.</span><span class="sxs-lookup"><span data-stu-id="53fff-198">Calls the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="53fff-199">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="53fff-199">IntegrationTests</span></span>

<span data-ttu-id="53fff-200">Ejecuta las pruebas de integración [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="53fff-200">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="53fff-201">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="53fff-201">AcceptanceTests</span></span>

<span data-ttu-id="53fff-202">Ejecuta las pruebas de aceptación [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="53fff-202">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="53fff-203">Clean</span><span class="sxs-lookup"><span data-stu-id="53fff-203">Clean</span></span>

<span data-ttu-id="53fff-204">Quita los módulos que se instalaron en ejecuciones anteriores y se asegura de que exista la carpeta de resultados de pruebas.</span><span class="sxs-lookup"><span data-stu-id="53fff-204">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="53fff-205">Scripts de prueba</span><span class="sxs-lookup"><span data-stu-id="53fff-205">Test scripts</span></span>

<span data-ttu-id="53fff-206">Las pruebas unitarias, de integración y de aceptación están definidas en la carpeta `Tests` (de la raíz del repositorio Demo_CI, `./InfraDNS/Tests`), cada una en archivos llamados `DNSServer.tests.ps1` en sus respectivas carpetas.</span><span class="sxs-lookup"><span data-stu-id="53fff-206">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="53fff-207">Los scripts de prueba usan la sintaxis de [Pester](https://github.com/pester/Pester/wiki) y [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).</span><span class="sxs-lookup"><span data-stu-id="53fff-207">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="53fff-208">Pruebas unitarias</span><span class="sxs-lookup"><span data-stu-id="53fff-208">Unit tests</span></span>

<span data-ttu-id="53fff-209">Las pruebas unitarias prueban las configuraciones de DSC para asegurarse de que hagan lo esperado cuando se ejecuten.</span><span class="sxs-lookup"><span data-stu-id="53fff-209">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="53fff-210">El script de prueba unitaria usa [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="53fff-210">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="53fff-211">Pruebas de integración</span><span class="sxs-lookup"><span data-stu-id="53fff-211">Integration tests</span></span>

<span data-ttu-id="53fff-212">Las pruebas de integración prueban la configuración del sistema para garantizar que cuando se integre con otros componentes, el sistema esté configurado según lo previsto.</span><span class="sxs-lookup"><span data-stu-id="53fff-212">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="53fff-213">Estas pruebas se ejecutan en el nodo de destino una vez que se configura con DSC.</span><span class="sxs-lookup"><span data-stu-id="53fff-213">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="53fff-214">El script de prueba de integración usa una combinación de sintaxis de [Pester](https://github.com/pester/Pester/wiki) y [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).</span><span class="sxs-lookup"><span data-stu-id="53fff-214">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="53fff-215">Pruebas de aceptación</span><span class="sxs-lookup"><span data-stu-id="53fff-215">Acceptance tests</span></span>

<span data-ttu-id="53fff-216">Las pruebas de aceptación prueban el sistema para asegurarse de que se comporte según lo previsto.</span><span class="sxs-lookup"><span data-stu-id="53fff-216">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="53fff-217">Por ejemplo, se hacen pruebas para asegurarse de que una página web devuelve la información correcta cuando se consulta.</span><span class="sxs-lookup"><span data-stu-id="53fff-217">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="53fff-218">Estas pruebas se ejecutan de manera remota desde el nodo de destino para probar escenarios reales.</span><span class="sxs-lookup"><span data-stu-id="53fff-218">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="53fff-219">El script de prueba de aceptación usa una combinación de sintaxis de [Pester](https://github.com/pester/Pester/wiki) y [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).</span><span class="sxs-lookup"><span data-stu-id="53fff-219">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="53fff-220">Definición de la compilación</span><span class="sxs-lookup"><span data-stu-id="53fff-220">Define the build</span></span>

<span data-ttu-id="53fff-221">Ahora que cargamos el código en TFS y sabemos qué hace, definamos la compilación.</span><span class="sxs-lookup"><span data-stu-id="53fff-221">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="53fff-222">En esta sección, solo analizaremos los pasos de compilación que agregará a la misma.</span><span class="sxs-lookup"><span data-stu-id="53fff-222">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="53fff-223">Si desea instrucciones sobre cómo crear una definición de compilación en TFS, consulte el artículo sobre cómo [crear una definición de compilación y ponerla en cola](/azure/devops/pipelines/create-first-pipeline).</span><span class="sxs-lookup"><span data-stu-id="53fff-223">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](/azure/devops/pipelines/create-first-pipeline).</span></span>

<span data-ttu-id="53fff-224">Cree una nueva definición de compilación (seleccione la plantilla **vacía**) llamada "InfraDNS".</span><span class="sxs-lookup"><span data-stu-id="53fff-224">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="53fff-225">Agregue los pasos siguientes a la definición de compilación:</span><span class="sxs-lookup"><span data-stu-id="53fff-225">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="53fff-226">Script de PowerShell</span><span class="sxs-lookup"><span data-stu-id="53fff-226">PowerShell Script</span></span>
- <span data-ttu-id="53fff-227">Publicación de los resultados de las pruebas</span><span class="sxs-lookup"><span data-stu-id="53fff-227">Publish Test Results</span></span>
- <span data-ttu-id="53fff-228">Copia de los archivos</span><span class="sxs-lookup"><span data-stu-id="53fff-228">Copy Files</span></span>
- <span data-ttu-id="53fff-229">Publicación del artefacto</span><span class="sxs-lookup"><span data-stu-id="53fff-229">Publish Artifact</span></span>

<span data-ttu-id="53fff-230">Después de agregar estos pasos de compilación, edite las propiedades de cada paso de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="53fff-230">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="53fff-231">Script de PowerShell</span><span class="sxs-lookup"><span data-stu-id="53fff-231">PowerShell Script</span></span>

1. <span data-ttu-id="53fff-232">Establezca la propiedad **Type** (Tipo) en `File Path`.</span><span class="sxs-lookup"><span data-stu-id="53fff-232">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="53fff-233">Establezca la propiedad **Script Path** (Ruta del script) en `initiate.ps1`.</span><span class="sxs-lookup"><span data-stu-id="53fff-233">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="53fff-234">Agregue `-fileName build` a la propiedad **Arguments** (Argumentos).</span><span class="sxs-lookup"><span data-stu-id="53fff-234">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="53fff-235">Este paso de compilación ejecuta el archivo `initiate.ps1`, que llama al script de compilación psake.</span><span class="sxs-lookup"><span data-stu-id="53fff-235">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="53fff-236">Publicación de los resultados de las pruebas</span><span class="sxs-lookup"><span data-stu-id="53fff-236">Publish Test Results</span></span>

1. <span data-ttu-id="53fff-237">Establezca **Test Result Format** (Formato de resultados de las pruebas) en `NUnit`</span><span class="sxs-lookup"><span data-stu-id="53fff-237">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="53fff-238">Establezca **Test Results Files** (Archivos de resultados de las pruebas) en `InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="53fff-238">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="53fff-239">Establezca **Test Run Title** (Título de la ejecución de pruebas) en `Unit`.</span><span class="sxs-lookup"><span data-stu-id="53fff-239">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="53fff-240">Asegúrese de que estén seleccionadas las opciones **Control Options** **Enabled** y **Always run**.</span><span class="sxs-lookup"><span data-stu-id="53fff-240">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="53fff-241">Este paso de compilación ejecuta las pruebas unitarias en el script Pester que analizamos anteriormente y almacena los resultados en la carpeta `InfraDNS/Tests/Results/*.xml`.</span><span class="sxs-lookup"><span data-stu-id="53fff-241">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="53fff-242">Copia de los archivos</span><span class="sxs-lookup"><span data-stu-id="53fff-242">Copy Files</span></span>

1. <span data-ttu-id="53fff-243">Agregue cada una de las siguientes líneas a **Contents** (Contenido):</span><span class="sxs-lookup"><span data-stu-id="53fff-243">Add each of the following lines to **Contents**:</span></span>

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. <span data-ttu-id="53fff-244">Establezca **TargetFolder** en `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="53fff-244">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="53fff-245">Este paso copia los scripts de compilación y prueba en el directorio de almacenamiento provisional para que se puedan publicar como artefactos de compilación en el paso siguiente.</span><span class="sxs-lookup"><span data-stu-id="53fff-245">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="53fff-246">Publicación del artefacto</span><span class="sxs-lookup"><span data-stu-id="53fff-246">Publish Artifact</span></span>

1. <span data-ttu-id="53fff-247">Establezca **Path to Publish** (Ruta de acceso para publicar) en `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="53fff-247">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="53fff-248">Establezca **Artifact Name** (Nombre del artefacto) en `Deploy`</span><span class="sxs-lookup"><span data-stu-id="53fff-248">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="53fff-249">Establezca **Artifact Type** (Tipo de artefacto) en `Server`</span><span class="sxs-lookup"><span data-stu-id="53fff-249">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="53fff-250">Seleccione `Enabled` en **Control Options** (Opciones de control)</span><span class="sxs-lookup"><span data-stu-id="53fff-250">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="53fff-251">Habilitación de la integración continua</span><span class="sxs-lookup"><span data-stu-id="53fff-251">Enable continuous integration</span></span>

<span data-ttu-id="53fff-252">Ahora configuraremos un desencadenador que hará que el proyecto se compile cada vez que se confirme un cambio en la rama `ci-cd-example` del repositorio Git.</span><span class="sxs-lookup"><span data-stu-id="53fff-252">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="53fff-253">En TFS, haga clic en la pestaña **Build & Release** (Compilación y versión)</span><span class="sxs-lookup"><span data-stu-id="53fff-253">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="53fff-254">Seleccione la definición de compilación `DNS Infra` y haga clic en **Editar**</span><span class="sxs-lookup"><span data-stu-id="53fff-254">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="53fff-255">Haga clic en la pestaña **Desencadenadores**</span><span class="sxs-lookup"><span data-stu-id="53fff-255">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="53fff-256">Seleccione **Integración continua (CI)** y seleccione `refs/heads/ci-cd-example` en la lista desplegable de ramas</span><span class="sxs-lookup"><span data-stu-id="53fff-256">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="53fff-257">Haga clic en **Guardar** y, luego, en **Aceptar**</span><span class="sxs-lookup"><span data-stu-id="53fff-257">Click **Save** and then **OK**</span></span>

<span data-ttu-id="53fff-258">Ahora, cualquier cambio en el repositorio Git de TFS desencadena una compilación automatizada.</span><span class="sxs-lookup"><span data-stu-id="53fff-258">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="53fff-259">Creación de la definición de versión</span><span class="sxs-lookup"><span data-stu-id="53fff-259">Create the release definition</span></span>

<span data-ttu-id="53fff-260">Vamos a crear una definición de versión para que el proyecto se implemente en el entorno de desarrollo con cada confirmación de código.</span><span class="sxs-lookup"><span data-stu-id="53fff-260">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="53fff-261">Para esto, agregue una nueva definición de versión asociada con la definición de compilación `InfraDNS` que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="53fff-261">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="53fff-262">Asegúrese de seleccionar **Implementación continua** para que una nueva versión se desencadene cada vez que se complete una nueva compilación.</span><span class="sxs-lookup"><span data-stu-id="53fff-262">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="53fff-263">([¿Cuáles son las canalizaciones de versiones? ](/azure/devops/pipelines/release/)) y configúrelo como sigue:</span><span class="sxs-lookup"><span data-stu-id="53fff-263">([What are release pipelines?](/azure/devops/pipelines/release/)) and configure it as follows:</span></span>

<span data-ttu-id="53fff-264">Agregue los pasos siguientes a la definición de versión:</span><span class="sxs-lookup"><span data-stu-id="53fff-264">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="53fff-265">Script de PowerShell</span><span class="sxs-lookup"><span data-stu-id="53fff-265">PowerShell Script</span></span>
- <span data-ttu-id="53fff-266">Publicación de los resultados de las pruebas</span><span class="sxs-lookup"><span data-stu-id="53fff-266">Publish Test Results</span></span>
- <span data-ttu-id="53fff-267">Publicación de los resultados de las pruebas</span><span class="sxs-lookup"><span data-stu-id="53fff-267">Publish Test Results</span></span>

<span data-ttu-id="53fff-268">Edite los pasos de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="53fff-268">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="53fff-269">Script de PowerShell</span><span class="sxs-lookup"><span data-stu-id="53fff-269">PowerShell Script</span></span>

1. <span data-ttu-id="53fff-270">Establezca el campo **Script Path** en `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="53fff-270">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="53fff-271">Establezca el campo **Arguments** en `-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="53fff-271">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="53fff-272">Publicación de los resultados de primera prueba</span><span class="sxs-lookup"><span data-stu-id="53fff-272">First Publish Test Results</span></span>

1. <span data-ttu-id="53fff-273">Seleccione `NUnit` en el campo **Test Result Format**</span><span class="sxs-lookup"><span data-stu-id="53fff-273">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="53fff-274">Establezca el campo **Test Result Files** en `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="53fff-274">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="53fff-275">Establezca **Test Run Title** en `Integration`</span><span class="sxs-lookup"><span data-stu-id="53fff-275">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="53fff-276">En **Control Options** (Opciones de control), active **Always run** (Ejecutar siempre)</span><span class="sxs-lookup"><span data-stu-id="53fff-276">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="53fff-277">Publicación de los resultados de la segunda prueba</span><span class="sxs-lookup"><span data-stu-id="53fff-277">Second Publish Test Results</span></span>

1. <span data-ttu-id="53fff-278">Seleccione `NUnit` en el campo **Test Result Format**</span><span class="sxs-lookup"><span data-stu-id="53fff-278">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="53fff-279">Establezca el campo **Test Result Files** en `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="53fff-279">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="53fff-280">Establezca **Test Run Title** en `Acceptance`</span><span class="sxs-lookup"><span data-stu-id="53fff-280">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="53fff-281">En **Control Options** (Opciones de control), active **Always run** (Ejecutar siempre)</span><span class="sxs-lookup"><span data-stu-id="53fff-281">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="53fff-282">Comprobación de los resultados</span><span class="sxs-lookup"><span data-stu-id="53fff-282">Verify your results</span></span>

<span data-ttu-id="53fff-283">Ahora, cada vez que inserte cambios en la rama `ci-cd-example` en TFS, se iniciará una nueva compilación.</span><span class="sxs-lookup"><span data-stu-id="53fff-283">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="53fff-284">Si la compilación se completa correctamente, se desencadena una nueva implementación.</span><span class="sxs-lookup"><span data-stu-id="53fff-284">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="53fff-285">Para comprobar el resultado de la implementación, abra un explorador en la máquina cliente y vaya a `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="53fff-285">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="53fff-286">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="53fff-286">Next steps</span></span>

<span data-ttu-id="53fff-287">En este ejemplo se configura el servidor DNS `TestAgent1` para que la dirección URL `www.contoso.com` se resuelva en `TestAgent2`, pero en realidad no implemente un sitio web.</span><span class="sxs-lookup"><span data-stu-id="53fff-287">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="53fff-288">La estructura para hacerlo se proporciona en el repositorio que se encuentra en la carpeta `WebApp`.</span><span class="sxs-lookup"><span data-stu-id="53fff-288">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="53fff-289">Puede usar los códigos auxiliares que se proporcionan para crear scripts psake, pruebas Pester y configuraciones de DSC a fin de implementar su propio sitio web.</span><span class="sxs-lookup"><span data-stu-id="53fff-289">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>
