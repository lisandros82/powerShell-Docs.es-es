---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: e1faf71436c8ba0ae02a166ce06d03de9f66f094
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="58ded-102">Las frecuencias de RefreshMode y ConfigurationMode no tienen que ser múltiplos una de la otra</span><span class="sxs-lookup"><span data-stu-id="58ded-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="58ded-103">En la versión anterior de DSC, LCM trataría `RefreshFrequencyMins` y `ConfigurationModeFrequencyMins` como múltiplos una de la otra.</span><span class="sxs-lookup"><span data-stu-id="58ded-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="58ded-104">En WMF 5.0 RTM, estas propiedades se procesan con independencia entre sí.</span><span class="sxs-lookup"><span data-stu-id="58ded-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="58ded-105">Para más información, consulte [Configuración del administrador de configuración local](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="58ded-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>