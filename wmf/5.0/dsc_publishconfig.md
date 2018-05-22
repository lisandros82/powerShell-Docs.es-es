---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: f929ce4684bb53c3039238ecd465f1c0e432f741
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="deliver-a-configuration-document-without-applying"></a>Entregar un documento de configuración sin aplicar

El cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) copia un archivo MOF de configuración en un nodo de destino, pero no aplica la configuración.
Esta configuración se aplica durante el siguiente paso de coherencia o cuando se ejecuta el cmdlet [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx).
