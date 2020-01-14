---
ms.date: 08/15/2019
keywords: dsc,powershell,configuration,setup
title: Introducción a la configuración de estado deseado (DSC) para Windows
ms.openlocfilehash: 2add2c936e60c0c9446bf4b398fbf7b4bd6407f7
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/25/2019
ms.locfileid: "75416158"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="ac756-103">Introducción a la configuración de estado deseado (DSC) para Windows</span><span class="sxs-lookup"><span data-stu-id="ac756-103">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="ac756-104">En este tema se ofrece una introducción al uso de la configuración de estado deseado (DSC) de PowerShell para Windows.</span><span class="sxs-lookup"><span data-stu-id="ac756-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span>
<span data-ttu-id="ac756-105">Para obtener información general sobre DSC, consulte [Introducción a la configuración de estado deseado de Windows PowerShell](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="ac756-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="ac756-106">Versiones de sistemas operativos Windows compatibles</span><span class="sxs-lookup"><span data-stu-id="ac756-106">Supported Windows operation system versions</span></span>

<span data-ttu-id="ac756-107">Las versiones compatibles son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="ac756-107">The following versions are supported:</span></span>

- <span data-ttu-id="ac756-108">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="ac756-108">Windows Server 2019</span></span>
- <span data-ttu-id="ac756-109">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="ac756-109">Windows Server 2016</span></span>
- <span data-ttu-id="ac756-110">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ac756-110">Windows Server 2012R2</span></span>
- <span data-ttu-id="ac756-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="ac756-111">Windows Server 2012</span></span>
- <span data-ttu-id="ac756-112">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="ac756-112">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="ac756-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="ac756-113">Windows 10</span></span>
- <span data-ttu-id="ac756-114">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="ac756-114">Windows 8.1</span></span>
- <span data-ttu-id="ac756-115">Windows 7</span><span class="sxs-lookup"><span data-stu-id="ac756-115">Windows 7</span></span>

<span data-ttu-id="ac756-116">La referencia de almacén del producto independiente de [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) no contiene una implementación de la configuración de estado deseado, por lo que ni DSC de PowerShell ni la configuración de estado de Azure Automation pueden administrarla.</span><span class="sxs-lookup"><span data-stu-id="ac756-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku doesn't contain an implementation of Desired State Configuration so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="ac756-117">Instalación de DSC</span><span class="sxs-lookup"><span data-stu-id="ac756-117">Installing DSC</span></span>

<span data-ttu-id="ac756-118">La configuración de estado deseado de PowerShell se incluye en Windows y se actualiza a través de Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="ac756-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span> <span data-ttu-id="ac756-119">La versión más reciente es [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="ac756-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="ac756-120">No es necesario habilitar la característica de Windows Server "DSC-Service" para administrar una máquina mediante DSC.</span><span class="sxs-lookup"><span data-stu-id="ac756-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="ac756-121">Esta característica solo es necesaria al crear una instancia de servidor de extracción de Windows.</span><span class="sxs-lookup"><span data-stu-id="ac756-121">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="ac756-122">Uso de DSC para Windows</span><span class="sxs-lookup"><span data-stu-id="ac756-122">Using DSC for Windows</span></span>

<span data-ttu-id="ac756-123">En las siguientes secciones se explica cómo crear y ejecutar configuraciones DSC en equipos Windows.</span><span class="sxs-lookup"><span data-stu-id="ac756-123">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="ac756-124">Creación de un documento MOF de configuración</span><span class="sxs-lookup"><span data-stu-id="ac756-124">Creating a configuration MOF document</span></span>

<span data-ttu-id="ac756-125">Se utiliza la palabra clave de PowerShell `Configuration` a fin de crear una configuración.</span><span class="sxs-lookup"><span data-stu-id="ac756-125">The Windows PowerShell `Configuration` keyword is used to create a configuration.</span></span>
<span data-ttu-id="ac756-126">En los pasos siguientes se describe la creación de un documento de configuración con Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac756-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="ac756-127">Defina una configuración y genere el documento de configuración:</span><span class="sxs-lookup"><span data-stu-id="ac756-127">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```

#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="ac756-128">Instalación de un módulo con recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="ac756-128">Install a module containing DSC resources</span></span>

<span data-ttu-id="ac756-129">La configuración de estado deseado de Windows PowerShell incluye módulos integrados con recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="ac756-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="ac756-130">También puede cargar módulos desde orígenes externos como la Galería de PowerShell, mediante los cmdlet PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="ac756-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

```PowerShell
Install-Module 'PSDscResources' -Verbose
```

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="ac756-131">Aplicación de la configuración a la máquina</span><span class="sxs-lookup"><span data-stu-id="ac756-131">Apply the configuration to the machine</span></span>

> [!NOTE]
> <span data-ttu-id="ac756-132">Para permitir la ejecución de DSC, Windows debe configurarse para recibir comandos remotos de PowerShell incluso cuando se ejecuta una configuración `localhost`.</span><span class="sxs-lookup"><span data-stu-id="ac756-132">To allow DSC to run, Windows needs to be configured to receive PowerShell remote commands even when you're running a `localhost` configuration.</span></span> <span data-ttu-id="ac756-133">Para configurar correctamente el entorno, solo tiene que ejecutar `Set-WsManQuickConfig -Force` en un terminal de PowerShell con privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="ac756-133">To easily configure your environment correctly, just run `Set-WsManQuickConfig -Force` in an elevated PowerShell Terminal.</span></span>

<span data-ttu-id="ac756-134">Los documentos de configuración (archivos MOF) se pueden aplicar a la máquina mediante el cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="ac756-134">Configuration documents (MOF files) can be applied to the machineusing the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

```powershell
Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose
```

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="ac756-135">Obtención del estado actual de la configuración</span><span class="sxs-lookup"><span data-stu-id="ac756-135">Get the current state of the configuration</span></span>

<span data-ttu-id="ac756-136">El cmdlet [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) consulta el estado actual de la máquina y devuelve los valores actuales de la configuración.</span><span class="sxs-lookup"><span data-stu-id="ac756-136">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

```powershell
Get-DscConfiguration
```

<span data-ttu-id="ac756-137">El cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) devuelve la metaconfiguración actual aplicada a la máquina.</span><span class="sxs-lookup"><span data-stu-id="ac756-137">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

```powershell
Get-DscLocalConfigurationManager
```

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="ac756-138">Eliminación de la configuración actual de una máquina</span><span class="sxs-lookup"><span data-stu-id="ac756-138">Remove the current configuration from a machine</span></span>

<span data-ttu-id="ac756-139">[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span><span class="sxs-lookup"><span data-stu-id="ac756-139">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

```powershell
Remove-DscConfigurationDocument -Stage Current -Verbose
```

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="ac756-140">Definición de configuración en el Administrador de configuración local</span><span class="sxs-lookup"><span data-stu-id="ac756-140">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="ac756-141">Aplique un archivo MOF de metaconfiguración a la máquina mediante el cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="ac756-141">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span>
<span data-ttu-id="ac756-142">Requiere la ruta de acceso al MOF de metaconfiguración.</span><span class="sxs-lookup"><span data-stu-id="ac756-142">Requires the path to the Meta Configuration MOF.</span></span>

```powershell
Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose
```

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="ac756-143">Archivos de registro de configuración de estado deseado de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ac756-143">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="ac756-144">Los registros para DSC se escriben en el registro de eventos de Windows en la ruta de acceso `Microsoft-Windows-Dsc/Operational`.</span><span class="sxs-lookup"><span data-stu-id="ac756-144">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="ac756-145">Se pueden habilitar registros adicionales con fines de depuración siguiendo los pasos en [¿Dónde se encuentran los registros de eventos de DSC?](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs)</span><span class="sxs-lookup"><span data-stu-id="ac756-145">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
