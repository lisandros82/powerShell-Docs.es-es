---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 814b1172505e1bac59a75fee494e9741f7d1f820
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="enhanced-transcription-options"></a>Opciones de transcripción mejoradas

La transcripción de Windows PowerShell se mejoró para aplicarse a todas las aplicaciones de hospedaje (como Windows PowerShell ISE) en lugar de solo al host de consola (powershell.exe).

Además de extenderse para la transcripción, la propia funcionalidad de transcripción se actualizó para admitir el anidamiento arbitrario de transcripciones, los metadatos adicionales en el encabezado de transcripción resultante y la configuración de un directorio de salida de transcripción (para admitir la recopilación de registro centralizada).

Las opciones de transcripción (incluida la habilitación de una transcripción de todo el sistema) pueden configurarse con la opción de Directiva de grupo **Activar la transcripción de PowerShell** (en Plantillas administrativas -> Componentes de Windows -> Windows PowerShell).