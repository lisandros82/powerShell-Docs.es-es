---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4008a7f91af41150f26c4147135b30aa8835281c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058750"
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>El cmdlet Test-DscConfiguration admite configuraciones de referencia

El cmdlet Test-DscConfiguration se actualizó para permitir la prueba del estado de configuración deseado de uno o más nodos de destino mediante la especificación de un documento de configuración de referencia para comparar.

Los siguientes conjuntos de parámetros nuevos usan las configuraciones de DSC de la ruta de acceso especificada para probar, nunca para aplicar, cada configuración en los nodos de destino especificados. Al igual que Start-DscConfiguration y otros cmdlets de DSC, el nombre de cada MOF se usa para determinar en qué nodo de destino se va a probar.

```powershell
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

Los siguientes conjuntos de parámetros nuevos usan una sola configuración de DSC para probar, nunca para aplicar, la configuración en los nodos de destino especificados.

```powershell
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
