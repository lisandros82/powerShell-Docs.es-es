---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Actualización de nodos a partir de un servidor de extracción
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079105"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="f06ff-103">Actualización de nodos a partir de un servidor de extracción</span><span class="sxs-lookup"><span data-stu-id="f06ff-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="f06ff-104">En las secciones siguientes se supone que ya ha configurado un servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="f06ff-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="f06ff-105">De no ser así, puede usar las siguientes guías:</span><span class="sxs-lookup"><span data-stu-id="f06ff-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="f06ff-106">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="f06ff-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="f06ff-107">Configuración de un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="f06ff-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="f06ff-108">Cada nodo de destino puede configurarse para descargar configuraciones y recursos, e incluso para notificar de su estado.</span><span class="sxs-lookup"><span data-stu-id="f06ff-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="f06ff-109">Este artículo le mostrará cómo cargar recursos para que estén disponibles para su descarga, así como configurar clientes para descargar automáticamente los recursos.</span><span class="sxs-lookup"><span data-stu-id="f06ff-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="f06ff-110">Cuando el nodo recibe una configuración asignada, a través de **extracción** o **inserción** (v5), descarga automáticamente todos los recursos requeridos por la configuración de la ubicación especificada en el LCM.</span><span class="sxs-lookup"><span data-stu-id="f06ff-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="f06ff-111">Uso del cmdlet Update-DSCConfiguration</span><span class="sxs-lookup"><span data-stu-id="f06ff-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="f06ff-112">A partir de PowerShell 5.0, el cmdlet [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) obliga a un nodo a actualizar su configuración desde el servidor de extracción configurado en el LCM.</span><span class="sxs-lookup"><span data-stu-id="f06ff-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="f06ff-113">Uso de Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="f06ff-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="f06ff-114">En PowerShell 4.0, aún puede forzar manualmente a un cliente de extracción para que actualice su configuración usando [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="f06ff-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="f06ff-115">El ejemplo siguiente crea una sesión CIM con credenciales especificadas, invoca el método adecuado de CIM y quita la sesión.</span><span class="sxs-lookup"><span data-stu-id="f06ff-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="f06ff-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="f06ff-116">See Also</span></span>

[<span data-ttu-id="f06ff-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="f06ff-117">PerformRequiredConfigurationChecks</span></span>](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
