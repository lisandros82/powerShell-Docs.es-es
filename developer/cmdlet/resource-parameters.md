---
title: Los parámetros de recursos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067457"
---
# <a name="resource-parameters"></a>Parámetros de recursos

En la tabla siguiente se enumera los nombres recomendados y la funcionalidad para los parámetros de recursos. Para estos parámetros, los recursos podrían ser el ensamblado que contiene la clase del cmdlet o la aplicación host que se está ejecutando el cmdlet.

|Parámetro|Funcionalidad|
|---|---|
|**Application**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar una aplicación.|
|**ensamblado**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar un ensamblado.|
|**Attribute**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar un atributo.|
|**Clase**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar una clase Microsoft .NET Framework.|
|**Clúster**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar un clúster.|
|**Referencia cultural**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar la referencia cultural en la que se va a ejecutar el cmdlet.|
|**Dominio**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el nombre de dominio.|
|**Drive**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar un nombre de la unidad.|
|**Evento**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar un nombre de evento.|
|**Interface**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar un nombre de la interfaz de red.|
|**IpAddress**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar una dirección IP.|
|**Trabajo**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar un trabajo.|
|**LiteralPath**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar la ruta de acceso a un recurso cuando no se admiten caracteres comodín. (Use el **ruta** parámetro cuando se admiten caracteres comodín.)|
|**Mac**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar una dirección de media access control (MAC).|
|**ParentId**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el identificador de elemento primario.|
|**Path**<br>Tipo de datos: String, String[]|Implemente este parámetro para que el usuario puede indicar las rutas de acceso a un recurso cuando se admiten caracteres comodín. (Use el **LiteralPath** parámetro cuando no se admiten caracteres comodín.) Se recomienda que desarrolle este parámetro para que admita el completo `provider:path` sintaxis utilizada por los proveedores. También se recomienda desarrollar para que funcione con proveedores de tantos como sea posible.|
|**Puerto**<br>Tipo de datos: Entero, cadena|Implemente este parámetro para que el usuario puede especificar un valor entero para la red o un valor de cadena como "biztalk" para otros tipos de puerto.|
|**Printer**<br>Tipo de datos: Entero, cadena|Implemente este parámetro para que el usuario puede especificar la impresora para usar el cmdlet.|
|**Size**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario puede especificar un tamaño.|
|**TID**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar un identificador de transacción (TID) para el cmdlet.|
|**Tipo**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el tipo de recurso en el que se va a operar.|
|**URL**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar un localizador uniforme de recursos (URL).|
|**Usuario**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar su nombre o el nombre de otro usuario.|

## <a name="see-also"></a>Véase también

[Parámetros de cmdlet](./cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
