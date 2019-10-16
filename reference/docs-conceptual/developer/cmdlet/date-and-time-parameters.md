---
title: Parámetros de fecha y hora | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369794"
---
# <a name="date-and-time-parameters"></a>Parámetros de fecha y hora

En la tabla siguiente se enumeran los nombres recomendados y la funcionalidad de los parámetros que controlan la información de fecha y hora. Los parámetros de fecha y hora se suelen usar para registrar Cuándo se crea algo o se obtiene acceso a él.

|Parámetro|Funcionalidad|
|---|---|
|**Acceso**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que, cuando se especifique, el cmdlet opere en los recursos a los que se ha accedido en función de la fecha y la hora especificadas por los parámetros **Before** y **After** . Si se especifica este parámetro, no se deben especificar los parámetros **creados** y **modificados** .|
|**Continuación**<br>Tipo de datos: DateTime|Implemente este parámetro para especificar la fecha y hora después de la cual se usó el cmdlet. Para que el parámetro **After** funcione, el cmdlet también debe tener un parámetro **acaccessed**, **created**o **Modified** . Y este parámetro debe establecerse en **true** cuando se llama al cmdlet.|
|**Nunca**<br>Tipo de datos: DateTime|Implemente este parámetro para especificar la fecha y la hora antes de la que se usó el cmdlet. Para que el parámetro **Before** funcione, el cmdlet también debe tener un parámetro **acaccessed**, **created**o **Modified** . Y este parámetro debe establecerse en **true** cuando se llama al cmdlet.|
|**Creado**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que, cuando se especifique, el cmdlet opere en los recursos creados en función de la fecha y la hora especificadas por los parámetros **Before** y **After** . Si se especifica este parámetro, no se deben especificar los parámetros de **acceso** y **modificados** .|
|**Acto**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que, cuando se especifique, el término del recurso debe coincidir exactamente con el nombre del recurso. Cuando no se especifica el parámetro, no es necesario que el término y el nombre del recurso coincidan exactamente.|
|**Cambia**<br>Tipo de datos: DateTime|Implemente este parámetro para que, cuando se especifique, el cmdlet opere en los recursos que se han modificado en función de la fecha y la hora especificadas por los parámetros **Before** y **After** . Si se especifica este parámetro, no se deben especificar los parámetros de **acceso** y de **creación** .|
## <a name="see-also"></a>Véase también

[Parámetros de cmdlet](./cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
