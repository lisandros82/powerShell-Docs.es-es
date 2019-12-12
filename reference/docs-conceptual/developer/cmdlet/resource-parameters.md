---
title: Parámetros de recursos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369514"
---
# <a name="resource-parameters"></a>Parámetros de recursos

En la tabla siguiente se enumeran los nombres recomendados y la funcionalidad de los parámetros de recursos. Para estos parámetros, los recursos podrían ser el ensamblado que contiene la clase de cmdlet o la aplicación host que está ejecutando el cmdlet.

|Parámetro|Funcionalidad|
|---|---|
|**Application**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar una aplicación.|
|**Ensamblaje**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar un ensamblado.|
|**Attribute**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar un atributo.|
|**Clase**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar una clase de marco de Microsoft .NET.|
|**Cluster**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar un clúster.|
|**Referencia cultural**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar la referencia cultural en la que se va a ejecutar el cmdlet.|
|**Dominio**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el nombre de dominio.|
|**Unidad**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar un nombre de unidad.|
|**Event**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar un nombre de evento.|
|**Interfaz**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar un nombre de interfaz de red.|
|**DirIP**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar una dirección IP.|
|**Trabajo**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar un trabajo.|
|**LiteralPath**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar la ruta de acceso a un recurso cuando no se admiten caracteres comodín. (Use el parámetro **path** cuando se admitan caracteres comodín).|
|**Mac**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar una dirección de controlador de acceso a medios (MAC).|
|**ParentId**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el identificador primario.|
|**Path**<br>Tipo de datos: cadena, cadena []|Implemente este parámetro para que el usuario pueda indicar las rutas de acceso a un recurso cuando se admitan caracteres comodín. (Use el parámetro **LiteralPath** cuando no se admiten caracteres comodín). Le recomendamos que desarrolle este parámetro para que admita la sintaxis completa de `provider:path` utilizada por los proveedores. También se recomienda que lo desarrolle para que funcione con tantos proveedores como sea posible.|
|**Puerto**<br>Tipo de datos: entero, cadena|Implemente este parámetro para que el usuario pueda especificar un valor entero para redes o un valor de cadena como "BizTalk" para otros tipos de puerto.|
|**Impresora**<br>Tipo de datos: entero, cadena|Implemente este parámetro para que el usuario pueda especificar la impresora que va a usar el cmdlet.|
|**Size**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario pueda especificar un tamaño.|
|**TID**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar un identificador de transacción (TID) para el cmdlet.|
|**Tipo**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el tipo de recurso en el que se va a operar.|
|**Dirección URL**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar un localizador uniforme de recursos (URL).|
|**Usuario**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar su nombre o el nombre de otro usuario.|

## <a name="see-also"></a>Véase también

[Parámetros de cmdlet](./cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
