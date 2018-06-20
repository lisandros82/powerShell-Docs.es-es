---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218440"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="6b408-102">Compatibilidad del control de versiones de módulos en paralelo para recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="6b408-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="6b408-103">Los módulos que contienen recursos de DSC pueden instalarse en paralelo y las configuraciones de DSC pueden usar una versión específica del recurso que está instalado en el sistema.</span><span class="sxs-lookup"><span data-stu-id="6b408-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="6b408-104">Para más información, consulte [Uso de recursos con varias versiones](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="6b408-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="6b408-105">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="6b408-105">Known issues</span></span>

<span data-ttu-id="6b408-106">En esta versión, se conocen los siguientes problemas de instalación en paralelo:</span><span class="sxs-lookup"><span data-stu-id="6b408-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="6b408-107">No se admite el uso de dos versiones diferentes del recurso de DSC en la misma configuración.</span><span class="sxs-lookup"><span data-stu-id="6b408-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>
