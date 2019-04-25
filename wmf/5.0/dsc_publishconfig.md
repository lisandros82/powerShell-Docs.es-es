---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db4543b788ad0a5c7aa32706246446533b901d09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085820"
---
# <a name="deliver-a-configuration-document-without-applying"></a>Entregar un documento de configuración sin aplicar

El cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) copia un archivo MOF de configuración en un nodo de destino, pero no aplica la configuración.
Esta configuración se aplica durante el siguiente paso de coherencia o cuando se ejecuta el cmdlet [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx).
