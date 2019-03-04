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
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251360"
---
# <a name="date-and-time-parameters"></a>Parámetros de fecha y hora

En la tabla siguiente se enumera los nombres recomendados y la funcionalidad para los parámetros que controlan la información de fecha y hora. Normalmente se usan parámetros de fecha y hora para registrar cuando algo se crea o se tiene acceso a.

|Parámetro|Funcionalidad|
|---|---|
|**Accessed**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que cuando se especifica el cmdlet funcionará en los recursos que se ha tenido acceso en función de la fecha y hora especificadas por el **antes** y **después** parámetros. Si se especifica este parámetro, el **creado** y **Modified** parámetros deben no ser especificarse.|
|**Después de**<br>Tipo de datos: DateTime|Implemente este parámetro para especificar la fecha y hora después de que se usó el cmdlet. Para el **después** parámetro funcione, el cmdlet también debe tener un **Accessed**, **creado**, o **Modified** parámetro. Y ese parámetro debe establecerse en **true** cuando se invoca el cmdlet.|
|**Antes de**<br>Tipo de datos: DateTime|Implemente este parámetro para especificar la fecha y hora antes de que se usó el cmdlet. Para el **antes** parámetro funcione, el cmdlet también debe tener un **Accessed**, **creado**, o **Modified** parámetro. Y ese parámetro debe establecerse en **true** cuando se invoca el cmdlet.|
|**Created**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que cuando se especifica el cmdlet funcionará en los recursos que se han creado según la fecha y hora especificadas por el **antes** y **después** parámetros. Si se especifica este parámetro, el **Accessed** y **Modified** no se deben especificar los parámetros.|
|**Exacta**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que cuando se especifica el término del recurso debe coincidir el nombre del recurso. Cuando no se especifica el parámetro no es necesario para que coincida exactamente con el término de recursos y el nombre.|
|**Puede modificar**<br>Tipo de datos: DateTime|Implemente este parámetro para que cuando se especifica el cmdlet funcionará en los recursos que han cambiado en función de la fecha y hora especificadas por el **antes** y **después** parámetros. Si se especifica este parámetro, el **Accessed** y **creado** no se deben especificar los parámetros.|
## <a name="see-also"></a>Véase también

[Parámetros de cmdlet](./cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
