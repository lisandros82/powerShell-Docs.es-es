---
ms.date: 1/17/2019
keywords: dsc,powershell,configuration,setup
title: Reinicio de un nodo
ms.openlocfilehash: 015b82a32caefc420973651c72e272fd85baf880
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054737"
---
# <a name="reboot-a-node"></a><span data-ttu-id="8917e-103">Reinicio de un nodo</span><span class="sxs-lookup"><span data-stu-id="8917e-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="8917e-104">En este tema se trata sobre cómo reiniciar un nodo.</span><span class="sxs-lookup"><span data-stu-id="8917e-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="8917e-105">Para que el reinicio se realice correctamente, las opciones de LCM **ActionAfterReboot** y **RebootNodeIfNeeded** deben configurarse correctamente.</span><span class="sxs-lookup"><span data-stu-id="8917e-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="8917e-106">Para obtener información acerca de las opciones del administrador de configuración local, consulte [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md) o [Configuración del administrador de configuración local (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="8917e-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="8917e-107">Se pueden reiniciar los nodos desde dentro de un recurso, mediante el uso de la marca `$global:DSCMachineStatus`.</span><span class="sxs-lookup"><span data-stu-id="8917e-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="8917e-108">Al establecer esta marca como `1` en la función `Set-TargetResource`, se obliga al LCM a reiniciar el nodo directamente después del método **Set** del recurso actual.</span><span class="sxs-lookup"><span data-stu-id="8917e-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="8917e-109">Mediante el uso de esta marca, el recurso **xPendingReboot** detecta si está pendiente un reinicio fuera de DSC.</span><span class="sxs-lookup"><span data-stu-id="8917e-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="8917e-110">Sus [configuraciones](configurations.md) pueden realizar pasos que requieren que el nodo se reinicie.</span><span class="sxs-lookup"><span data-stu-id="8917e-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="8917e-111">Esto puede incluir, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8917e-111">This could include things such as:</span></span>

- <span data-ttu-id="8917e-112">Actualizaciones de Windows</span><span class="sxs-lookup"><span data-stu-id="8917e-112">Windows updates</span></span>
- <span data-ttu-id="8917e-113">Instalación de software</span><span class="sxs-lookup"><span data-stu-id="8917e-113">Software install</span></span>
- <span data-ttu-id="8917e-114">Cambios de nombre de archivo</span><span class="sxs-lookup"><span data-stu-id="8917e-114">File renames</span></span>
- <span data-ttu-id="8917e-115">Cambios de nombre de equipo</span><span class="sxs-lookup"><span data-stu-id="8917e-115">Computer rename</span></span>

<span data-ttu-id="8917e-116">El recurso **xPendingReboot** comprueba las ubicaciones de equipos específicos para determinar si está pendiente un reinicio.</span><span class="sxs-lookup"><span data-stu-id="8917e-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="8917e-117">Si el nodo requiere un reinicio fuera de DSC, el recurso **xPendingReboot** establece la marca `$global:DSCMachineStatus` en `1` y obliga a realizar un reinicio y a resolver la condición pendiente.</span><span class="sxs-lookup"><span data-stu-id="8917e-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="8917e-118">Cualquier recurso de DSC puede indicar al LCM que reinicie el nodo estableciendo esta marca en la función `Set-TargetResource`.</span><span class="sxs-lookup"><span data-stu-id="8917e-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="8917e-119">Para obtener más información, consulte [Escribir un recurso de DSC personalizado con MOF](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="8917e-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="8917e-120">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8917e-120">Syntax</span></span>

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a><span data-ttu-id="8917e-121">Propiedades</span><span class="sxs-lookup"><span data-stu-id="8917e-121">Properties</span></span>

| <span data-ttu-id="8917e-122">Propiedad</span><span class="sxs-lookup"><span data-stu-id="8917e-122">Property</span></span> | <span data-ttu-id="8917e-123">Descripción</span><span class="sxs-lookup"><span data-stu-id="8917e-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8917e-124">Nombre</span><span class="sxs-lookup"><span data-stu-id="8917e-124">Name</span></span>| <span data-ttu-id="8917e-125">Parámetro obligatorio que debe ser único para cada instancia del recurso dentro de una configuración.</span><span class="sxs-lookup"><span data-stu-id="8917e-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="8917e-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="8917e-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="8917e-127">Omite los reinicios desencadenados por el componente de servicio basado en componentes.</span><span class="sxs-lookup"><span data-stu-id="8917e-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="8917e-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="8917e-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="8917e-129">Omite los reinicios desencadenados por Windows Update.</span><span class="sxs-lookup"><span data-stu-id="8917e-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="8917e-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="8917e-130">SkipPendingFileRename</span></span> | <span data-ttu-id="8917e-131">Omite los reinicios de cambio de nombre de archivo pendientes.</span><span class="sxs-lookup"><span data-stu-id="8917e-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="8917e-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="8917e-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="8917e-133">Omite los reinicios desencadenados por el cliente de Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="8917e-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="8917e-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="8917e-134">SkipComputerRename</span></span> | <span data-ttu-id="8917e-135">Omite los reinicios desencadenados por cambios de nombre de equipo.</span><span class="sxs-lookup"><span data-stu-id="8917e-135">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="8917e-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="8917e-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="8917e-137">Admitido en la versión 5.</span><span class="sxs-lookup"><span data-stu-id="8917e-137">Supported in v5.</span></span> <span data-ttu-id="8917e-138">Ejecuta el recurso como el usuario especificado.</span><span class="sxs-lookup"><span data-stu-id="8917e-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="8917e-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8917e-139">DependsOn</span></span> | <span data-ttu-id="8917e-140">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="8917e-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8917e-141">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8917e-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="8917e-142">Para obtener más información, vea [Uso de DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="8917e-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="8917e-143">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8917e-143">Example</span></span>

<span data-ttu-id="8917e-144">El ejemplo siguiente instala Microsoft Exchange con el recurso [xExchange](https://github.com/PowerShell/xExchange).</span><span class="sxs-lookup"><span data-stu-id="8917e-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="8917e-145">A lo largo de la instalación, el recurso **xPendingReboot** se usa para reiniciar el nodo.</span><span class="sxs-lookup"><span data-stu-id="8917e-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="8917e-146">Este ejemplo requiere la credencial de una cuenta que tenga derechos para agregar un servidor de Exchange al bosque.</span><span class="sxs-lookup"><span data-stu-id="8917e-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="8917e-147">Para obtener más información sobre el uso de credenciales en DSC, vea [Control de credenciales en DSC](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="8917e-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="8917e-148">En este ejemplo se asume que se ha configurado el administrador de configuración local para permitir reinicios y continuar la configuración tras un reinicio.</span><span class="sxs-lookup"><span data-stu-id="8917e-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="8917e-149">Dónde puede realizarse la descarga</span><span class="sxs-lookup"><span data-stu-id="8917e-149">Where to Download</span></span>

<span data-ttu-id="8917e-150">Puede descargar los recursos usados en este tema en las siguientes ubicaciones, o mediante el uso de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8917e-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="8917e-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="8917e-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="8917e-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="8917e-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
