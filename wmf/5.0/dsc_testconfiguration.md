---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 2d629d98b59c455011f4a5d955ef666218ae2f3f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="12343-102">El cmdlet Test-DscConfiguration admite configuraciones de referencia</span><span class="sxs-lookup"><span data-stu-id="12343-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="12343-103">El cmdlet Test-DscConfiguration se actualizó para permitir la prueba del estado de configuración deseado de uno o más nodos de destino mediante la especificación de un documento de configuración de referencia para comparar.</span><span class="sxs-lookup"><span data-stu-id="12343-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="12343-104">Los siguientes conjuntos de parámetros nuevos usan las configuraciones de DSC de la ruta de acceso especificada para probar, nunca para aplicar, cada configuración en los nodos de destino especificados.</span><span class="sxs-lookup"><span data-stu-id="12343-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="12343-105">Al igual que Start-DscConfiguration y otros cmdlets de DSC, el nombre de cada MOF se usa para determinar en qué nodo de destino se va a probar.</span><span class="sxs-lookup"><span data-stu-id="12343-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span> 

```PowerShell
Test-DscConfiguration   [-Path] <string> 
                        [[-ComputerName] <string[]>] 
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

<span data-ttu-id="12343-106">Los siguientes conjuntos de parámetros nuevos usan una sola configuración de DSC para probar, nunca para aplicar, la configuración en los nodos de destino especificados.</span><span class="sxs-lookup"><span data-stu-id="12343-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span> 

```PowerShell
Test-DscConfiguration   -ReferenceConfiguration <string> 
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

