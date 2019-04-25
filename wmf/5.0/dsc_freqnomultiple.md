---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058410"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="bd142-102">Las frecuencias de RefreshMode y ConfigurationMode no tienen que ser múltiplos una de la otra</span><span class="sxs-lookup"><span data-stu-id="bd142-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="bd142-103">En la versión anterior de DSC, LCM trataría `RefreshFrequencyMins` y `ConfigurationModeFrequencyMins` como múltiplos una de la otra.</span><span class="sxs-lookup"><span data-stu-id="bd142-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="bd142-104">En WMF 5.0 RTM, estas propiedades se procesan con independencia entre sí.</span><span class="sxs-lookup"><span data-stu-id="bd142-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="bd142-105">Para más información, consulte [Configuración del administrador de configuración local](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="bd142-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
