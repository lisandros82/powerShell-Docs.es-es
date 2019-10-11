---
ms.date: 08/15/2019
keywords: dsc,powershell,configuration,setup
title: Introducción a la configuración de estado deseado (DSC) para Windows
ms.openlocfilehash: a4f9db481afda65fc4ac5e553230dbba3037ac9a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954412"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="fc3c4-103">Introducción a la configuración de estado deseado (DSC) para Windows</span><span class="sxs-lookup"><span data-stu-id="fc3c4-103">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="fc3c4-104">En este tema se ofrece una introducción al uso de la configuración de estado deseado (DSC) de PowerShell para Windows.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span>
<span data-ttu-id="fc3c4-105">Para obtener información general sobre DSC, consulte [Introducción a la configuración de estado deseado de Windows PowerShell](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="fc3c4-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="fc3c4-106">Versiones de sistemas operativos Windows compatibles</span><span class="sxs-lookup"><span data-stu-id="fc3c4-106">Supported Windows operation system versions</span></span>

<span data-ttu-id="fc3c4-107">Las versiones compatibles son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="fc3c4-107">The following versions are supported:</span></span>

- <span data-ttu-id="fc3c4-108">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="fc3c4-108">Windows Server 2019</span></span>
- <span data-ttu-id="fc3c4-109">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="fc3c4-109">Windows Server 2016</span></span>
- <span data-ttu-id="fc3c4-110">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="fc3c4-110">Windows Server 2012R2</span></span>
- <span data-ttu-id="fc3c4-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="fc3c4-111">Windows Server 2012</span></span>
- <span data-ttu-id="fc3c4-112">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="fc3c4-112">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="fc3c4-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="fc3c4-113">Windows 10</span></span>
- <span data-ttu-id="fc3c4-114">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="fc3c4-114">Windows 8.1</span></span>
- <span data-ttu-id="fc3c4-115">Windows 7</span><span class="sxs-lookup"><span data-stu-id="fc3c4-115">Windows 7</span></span>

<span data-ttu-id="fc3c4-116">La referencia de almacén del producto independiente de [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) no contiene una implementación de la configuración de estado deseado, por lo que ni DSC de PowerShell ni la configuración de estado de Azure Automation pueden administrarla.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku does not contain an implementation of Desired State Configuraion so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="fc3c4-117">Instalación de DSC</span><span class="sxs-lookup"><span data-stu-id="fc3c4-117">Installing DSC</span></span>

<span data-ttu-id="fc3c4-118">La configuración de estado deseado de PowerShell se incluye en Windows y se actualiza a través de Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span>
<span data-ttu-id="fc3c4-119">La versión más reciente es [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="fc3c4-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="fc3c4-120">No es necesario habilitar la característica de Windows Server "DSC-Service" para administrar una máquina mediante DSC.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="fc3c4-121">Esta característica solo es necesaria al crear una instancia de servidor de extracción de Windows.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-121">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="fc3c4-122">Uso de DSC para Windows</span><span class="sxs-lookup"><span data-stu-id="fc3c4-122">Using DSC for Windows</span></span>

<span data-ttu-id="fc3c4-123">En las siguientes secciones se explica cómo crear y ejecutar configuraciones DSC en equipos Windows.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-123">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="fc3c4-124">Creación de un documento MOF de configuración</span><span class="sxs-lookup"><span data-stu-id="fc3c4-124">Creating a configuration MOF document</span></span>

<span data-ttu-id="fc3c4-125">Se utiliza la palabra clave de Windows PowerShell Configuration a fin de crear una configuración.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-125">The Windows PowerShell Configuration keyword is used to create a configuration.</span></span>
<span data-ttu-id="fc3c4-126">En los pasos siguientes se describe la creación de un documento de configuración con Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="fc3c4-127">Defina una configuración y genere el documento de configuración:</span><span class="sxs-lookup"><span data-stu-id="fc3c4-127">Define a configuration and generate the configuration document:</span></span>

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
#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="fc3c4-128">Instalación de un módulo con recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="fc3c4-128">Install a module containing DSC resources</span></span>

<span data-ttu-id="fc3c4-129">La configuración de estado deseado de Windows PowerShell incluye módulos integrados con recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="fc3c4-130">También puede cargar módulos desde orígenes externos como la Galería de PowerShell, mediante los cmdlet PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="fc3c4-131">Aplicación de la configuración a la máquina</span><span class="sxs-lookup"><span data-stu-id="fc3c4-131">Apply the configuration to the machine</span></span>

<span data-ttu-id="fc3c4-132">Los documentos de configuración (archivos MOF) se pueden aplicar a la máquina mediante el cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="fc3c4-132">Configuration documents (MOF files) can be applied to the machine using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="fc3c4-133">Obtención del estado actual de la configuración</span><span class="sxs-lookup"><span data-stu-id="fc3c4-133">Get the current state of the configuration</span></span>

<span data-ttu-id="fc3c4-134">El cmdlet [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) consulta el estado actual de la máquina y devuelve los valores actuales de la configuración.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-134">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

`Get-DscConfiguration`

<span data-ttu-id="fc3c4-135">El cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) devuelve la metaconfiguración actual aplicada a la máquina.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-135">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="fc3c4-136">Eliminación de la configuración actual de una máquina</span><span class="sxs-lookup"><span data-stu-id="fc3c4-136">Remove the current configuration from a machine</span></span>

<span data-ttu-id="fc3c4-137">[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span><span class="sxs-lookup"><span data-stu-id="fc3c4-137">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="fc3c4-138">Definición de configuración en el Administrador de configuración local</span><span class="sxs-lookup"><span data-stu-id="fc3c4-138">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="fc3c4-139">Aplique un archivo MOF de metaconfiguración a la máquina mediante el cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="fc3c4-139">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span>
<span data-ttu-id="fc3c4-140">Requiere la ruta de acceso al MOF de metaconfiguración.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-140">Requires the path to the Meta Configuration MOF.</span></span>

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="fc3c4-141">Archivos de registro de configuración de estado deseado de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc3c4-141">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="fc3c4-142">Los registros para DSC se escriben en el registro de eventos de Windows en la ruta de acceso `Microsoft-Windows-Dsc/Operational`.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-142">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="fc3c4-143">Se pueden habilitar registros adicionales con fines de depuración siguiendo los pasos en [¿Dónde se encuentran los registros de eventos de DSC?](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs)</span><span class="sxs-lookup"><span data-stu-id="fc3c4-143">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
