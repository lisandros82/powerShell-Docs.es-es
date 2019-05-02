---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085335"
---
# <a name="new-guid"></a>New-Guid
A menudo en un script (o quizás al escribir un recurso de DSC), tiene la necesidad de un identificador único. Los GUID funcionan bien y es fácil llamar a la clase Guid de .NET Framework para generar uno. No obstante, tener un cmdlet facilita la detección a los usuarios finales que todavía no están familiarizados con la clase de .NET Framework:

PS C:\\&gt; New-Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
