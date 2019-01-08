---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Actualización de nodos a partir de un servidor de extracción
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402153"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="18713-103">Actualización de nodos a partir de un servidor de extracción</span><span class="sxs-lookup"><span data-stu-id="18713-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="18713-104">Las secciones siguientes se suponen que ya ha configurado un servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="18713-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="18713-105">Si no ha configurado el servidor de incorporación de cambios, puede usar a las siguientes guías:</span><span class="sxs-lookup"><span data-stu-id="18713-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="18713-106">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="18713-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="18713-107">Configuración de un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="18713-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="18713-108">Cada nodo de destino puede configurarse para descargar las configuraciones, recursos e incluso notificado su estado.</span><span class="sxs-lookup"><span data-stu-id="18713-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="18713-109">En este artículo le mostrará cómo cargar recursos para que estén disponibles para descargarse y configurar clientes para descargar automáticamente los recursos.</span><span class="sxs-lookup"><span data-stu-id="18713-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="18713-110">Cuando el nodo recibe una configuración asignada, a través de **extraer** o **Push** (v5), se descarga automáticamente todos los recursos requeridos por la configuración de la ubicación especificada en el LCM.</span><span class="sxs-lookup"><span data-stu-id="18713-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="18713-111">Mediante el cmdlet Update-DSCConfiguration</span><span class="sxs-lookup"><span data-stu-id="18713-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="18713-112">A partir de PowerShell 5.0, el [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, fuerza un nodo para actualizar su configuración desde el servidor de incorporación de cambios configurado en el LCM.</span><span class="sxs-lookup"><span data-stu-id="18713-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="18713-113">Uso de Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="18713-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="18713-114">En PowerShell 4.0, puede forzar manualmente un cliente de incorporación de cambios para actualizar su configuración mediante [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="18713-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="18713-115">El ejemplo siguiente crea una sesión CIM con credenciales especificadas, invoca el método adecuado de CIM y quita la sesión.</span><span class="sxs-lookup"><span data-stu-id="18713-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="18713-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="18713-116">See Also</span></span>

[<span data-ttu-id="18713-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="18713-117">PerformRequiredConfigurationChecks</span></span>](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
