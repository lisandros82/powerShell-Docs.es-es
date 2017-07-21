---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 3261e5a07b8181190a04de3f210da50f23bb2953
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="86d1f-102">Compatibilidad del control de versiones de módulos en paralelo para recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="86d1f-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="86d1f-103">Los módulos que contienen recursos de DSC pueden instalarse en paralelo y las configuraciones de DSC pueden usar una versión específica del recurso que está instalado en el sistema.</span><span class="sxs-lookup"><span data-stu-id="86d1f-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="86d1f-104">Para más información, consulte [Uso de recursos con varias versiones](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="86d1f-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="86d1f-105">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="86d1f-105">Known issues</span></span>

<span data-ttu-id="86d1f-106">En esta versión, se conocen los siguientes problemas de instalación en paralelo:</span><span class="sxs-lookup"><span data-stu-id="86d1f-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="86d1f-107">No se admite el uso de dos versiones diferentes del recurso de DSC en la misma configuración.</span><span class="sxs-lookup"><span data-stu-id="86d1f-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>

