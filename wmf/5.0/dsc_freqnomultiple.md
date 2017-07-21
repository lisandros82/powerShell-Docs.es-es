---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 30055cff87159df98029e25409782e0fe2f0bae4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="41993-102">Las frecuencias de RefreshMode y ConfigurationMode no tienen que ser múltiplos una de la otra</span><span class="sxs-lookup"><span data-stu-id="41993-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="41993-103">En la versión anterior de DSC, LCM trataría `RefreshFrequencyMins` y `ConfigurationModeFrequencyMins` como múltiplos una de la otra.</span><span class="sxs-lookup"><span data-stu-id="41993-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="41993-104">En WMF 5.0 RTM, estas propiedades se procesan con independencia entre sí.</span><span class="sxs-lookup"><span data-stu-id="41993-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span> 

<span data-ttu-id="41993-105">Para más información, consulte [Configuración del administrador de configuración local](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="41993-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>

