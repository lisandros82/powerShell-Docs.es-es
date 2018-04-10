---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 136e16ae74e54f3bc9d0623178257df1e9104aac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="deliver-a-configuration-document-without-applying"></a>Entregar un documento de configuración sin aplicar

El cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) copia un archivo MOF de configuración en un nodo de destino, pero no aplica la configuración.
Esta configuración se aplica durante el siguiente paso de coherencia o cuando se ejecuta el cmdlet [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx).