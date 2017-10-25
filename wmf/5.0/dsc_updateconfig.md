---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: f2ddde78f436e6f03f521a9a8246dbda93e7a57a
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2017
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="fe6e8-102">Extracción a petición de configuraciones de DSC</span><span class="sxs-lookup"><span data-stu-id="fe6e8-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="fe6e8-103">El nuevo cmdlet Update-DscConfiguration desencadena una extracción de los servidores de extracción definidos en la metaconfiguración.</span><span class="sxs-lookup"><span data-stu-id="fe6e8-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="fe6e8-104">El comportamiento suele denominarse "extraer ahora".</span><span class="sxs-lookup"><span data-stu-id="fe6e8-104">The behavior is often referred to as 'Pull Now'.</span></span> 


<span data-ttu-id="fe6e8-105">Una vez desencadenada, la extracción se comporta exactamente igual que si se desencadenara durante la frecuencia regular:</span><span class="sxs-lookup"><span data-stu-id="fe6e8-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="fe6e8-106">La suma de comprobación de la configuración actual se compara con la suma de comprobación de la configuración en el servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="fe6e8-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span> 
2. <span data-ttu-id="fe6e8-107">Si son iguales, se completa correctamente sin aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="fe6e8-107">If they are the same, it completes successfully without applying the configuration.</span></span> 
3. <span data-ttu-id="fe6e8-108">Si son diferentes, la configuración se extrae del servidor de extracción y se aplica.</span><span class="sxs-lookup"><span data-stu-id="fe6e8-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="fe6e8-109">**Nota:** Si RefreshMode = 'Push' en la metaconfiguración, este cmdlet devuelve un error. Por consiguiente, este cmdlet nunca hará nada cuando un nodo de destino esté en modo de "inserción".</span><span class="sxs-lookup"><span data-stu-id="fe6e8-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>] 
                            [-Wait]
                            [-Force] 
                            [-JobName <string>] 
                            [-Credential<pscredential>] 
                            [-ThrottleLimit <int>] 
                            [-WhatIf] 
                            [-Confirm] 
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]> 
                            [-Wait] 
                            [-Force] 
                            [-JobName <string>] 
                            [-ThrottleLimit <int>]
                            [-WhatIf] 
                            [-Confirm] 
                            [<CommonParameters>]
```

