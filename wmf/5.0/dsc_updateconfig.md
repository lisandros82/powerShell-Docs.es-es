---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 6d37fbc5091d69925d60349f3acbdecc92da1b95
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="c56bc-102">Extracción a petición de configuraciones de DSC</span><span class="sxs-lookup"><span data-stu-id="c56bc-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="c56bc-103">El nuevo cmdlet Update-DscConfiguration desencadena una extracción de los servidores de extracción definidos en la metaconfiguración.</span><span class="sxs-lookup"><span data-stu-id="c56bc-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="c56bc-104">El comportamiento suele denominarse "extraer ahora".</span><span class="sxs-lookup"><span data-stu-id="c56bc-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="c56bc-105">Una vez desencadenada, la extracción se comporta exactamente igual que si se desencadenara durante la frecuencia regular:</span><span class="sxs-lookup"><span data-stu-id="c56bc-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="c56bc-106">La suma de comprobación de la configuración actual se compara con la suma de comprobación de la configuración en el servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="c56bc-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="c56bc-107">Si son iguales, se completa correctamente sin aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="c56bc-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="c56bc-108">Si son diferentes, la configuración se extrae del servidor de extracción y se aplica.</span><span class="sxs-lookup"><span data-stu-id="c56bc-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="c56bc-109">**Nota:** Si RefreshMode = 'Push' en la metaconfiguración, este cmdlet devuelve un error. Por consiguiente, este cmdlet nunca hará nada cuando un nodo de destino esté en modo de "inserción".</span><span class="sxs-lookup"><span data-stu-id="c56bc-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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
