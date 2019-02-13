---
ms.date: 1/17/2019
keywords: dsc,powershell,configuration,setup
title: Reiniciar un nodo
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680745"
---
# <a name="reboot-a-node"></a><span data-ttu-id="85732-103">Reiniciar un nodo</span><span class="sxs-lookup"><span data-stu-id="85732-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="85732-104">En este tema trata sobre cómo reiniciar un nodo.</span><span class="sxs-lookup"><span data-stu-id="85732-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="85732-105">En orden para el reinicio se realice correctamente la **ActionAfterReboot** y **RebootNodeIfNeeded** configuración del LCM debe configurarse correctamente.</span><span class="sxs-lookup"><span data-stu-id="85732-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="85732-106">Para obtener información acerca de la configuración del Administrador de configuración Local, consulte [configurar el Administrador de configuración Local](../managing-nodes/metaConfig.md), o [configurar el Administrador de configuración Local (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="85732-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="85732-107">Se pueden reiniciar los nodos desde dentro de un recurso, mediante el uso de la `$global:DSCMachineStatus` marca.</span><span class="sxs-lookup"><span data-stu-id="85732-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="85732-108">Al establecer esta marca en `1` en el `Set-TargetResource` función fuerza el LCM para reiniciar el nodo directamente después de la **establecer** método del recurso actual.</span><span class="sxs-lookup"><span data-stu-id="85732-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="85732-109">Usar esta marca, el **xPendingReboot** recursos detecta si está pendiente un reinicio fuera de DSC.</span><span class="sxs-lookup"><span data-stu-id="85732-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="85732-110">Su [configuraciones](configurations.md) es posible que lleve a cabo los pasos que requieren el nodo se reinicie.</span><span class="sxs-lookup"><span data-stu-id="85732-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="85732-111">Esto puede incluir cosas como:</span><span class="sxs-lookup"><span data-stu-id="85732-111">This could include things such as:</span></span>

- <span data-ttu-id="85732-112">Windows: Actualizaciones</span><span class="sxs-lookup"><span data-stu-id="85732-112">Windows updates</span></span>
- <span data-ttu-id="85732-113">Instalación del software</span><span class="sxs-lookup"><span data-stu-id="85732-113">Software install</span></span>
- <span data-ttu-id="85732-114">Cambia el nombre de archivo</span><span class="sxs-lookup"><span data-stu-id="85732-114">File renames</span></span>
- <span data-ttu-id="85732-115">Cambio de nombre de equipo</span><span class="sxs-lookup"><span data-stu-id="85732-115">Computer rename</span></span>

<span data-ttu-id="85732-116">El **xPendingReboot** recursos comprueba las ubicaciones de equipo específico para determinar si está pendiente un reinicio.</span><span class="sxs-lookup"><span data-stu-id="85732-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="85732-117">Si el nodo requiere un reinicio fuera de DSC, el **xPendingReboot** conjuntos de recursos el `$global:DSCMachineStatus` marca `1` forzar un reinicio y resolver la condición pendiente.</span><span class="sxs-lookup"><span data-stu-id="85732-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="85732-118">Cualquier recurso de DSC puede indicar que el LCM para reiniciar el nodo al establecer esta marca el `Set-TargetResource` función.</span><span class="sxs-lookup"><span data-stu-id="85732-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="85732-119">Para obtener más información, consulte [escribir un recurso de DSC personalizado con MOF](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="85732-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="85732-120">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="85732-120">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="85732-121">Propiedades</span><span class="sxs-lookup"><span data-stu-id="85732-121">Properties</span></span>

| <span data-ttu-id="85732-122">Propiedad</span><span class="sxs-lookup"><span data-stu-id="85732-122">Property</span></span> | <span data-ttu-id="85732-123">Descripción</span><span class="sxs-lookup"><span data-stu-id="85732-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="85732-124">Nombre</span><span class="sxs-lookup"><span data-stu-id="85732-124">Name</span></span>| <span data-ttu-id="85732-125">Parámetro obligatorio que debe ser único para cada instancia del recurso dentro de una configuración.</span><span class="sxs-lookup"><span data-stu-id="85732-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="85732-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="85732-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="85732-127">Reinicios de Skip desencadenados por el componente de servicio basado en componentes.</span><span class="sxs-lookup"><span data-stu-id="85732-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="85732-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="85732-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="85732-129">Reinicios de Skip desencadenados por Windows Update.</span><span class="sxs-lookup"><span data-stu-id="85732-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="85732-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="85732-130">SkipPendingFileRename</span></span> | <span data-ttu-id="85732-131">Omitir los reinicios de cambio de nombre de archivo pendiente.</span><span class="sxs-lookup"><span data-stu-id="85732-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="85732-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="85732-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="85732-133">Reinicios de Skip desencadenados por el cliente de Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="85732-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="85732-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="85732-134">SkipComputerRename</span></span> | <span data-ttu-id="85732-135">Omitir reinicia desencadenada por cambios de nombre de equipo.</span><span class="sxs-lookup"><span data-stu-id="85732-135">Skip reboots triggerd by Computer renames.</span></span> |
| <span data-ttu-id="85732-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="85732-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="85732-137">Se admiten en v5.</span><span class="sxs-lookup"><span data-stu-id="85732-137">Supported in v5.</span></span> <span data-ttu-id="85732-138">El recurso se ejecuta como el usuario especificado.</span><span class="sxs-lookup"><span data-stu-id="85732-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="85732-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="85732-139">DependsOn</span></span> | <span data-ttu-id="85732-140">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="85732-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="85732-141">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="85732-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="85732-142">Para obtener más información, consulte [utilizando DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="85732-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="85732-143">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="85732-143">Example</span></span>

<span data-ttu-id="85732-144">El ejemplo siguiente, instala con Microsoft Exchange el [xExchange](https://github.com/PowerShell/xExchange) recursos.</span><span class="sxs-lookup"><span data-stu-id="85732-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="85732-145">A lo largo de la instalación, el **xPendingReboot** recurso se usa para reiniciar el nodo.</span><span class="sxs-lookup"><span data-stu-id="85732-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="85732-146">Este ejemplo requiere la credencial de una cuenta que tenga derechos para agregar un servidor de Exchange en el bosque.</span><span class="sxs-lookup"><span data-stu-id="85732-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="85732-147">Para obtener más información sobre el uso de credenciales en DSC, consulte [control de credenciales en DSC](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="85732-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

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
> <span data-ttu-id="85732-148">En este ejemplo se da por supuesto que ha configurado el Administrador de configuración Local para permitir los reinicios y continuar con la configuración tras un reinicio.</span><span class="sxs-lookup"><span data-stu-id="85732-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="85732-149">Ubicación donde debe descargarse</span><span class="sxs-lookup"><span data-stu-id="85732-149">Where to Download</span></span>

<span data-ttu-id="85732-150">Puede descargar los recursos usados en este tema en las siguientes ubicaciones, o mediante el uso de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="85732-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="85732-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="85732-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="85732-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="85732-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
