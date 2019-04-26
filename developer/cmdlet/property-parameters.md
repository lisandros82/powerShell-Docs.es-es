---
title: Parámetros de propiedad | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067576"
---
# <a name="property-parameters"></a>Parámetros de propiedad

En la tabla siguiente se enumera los nombres recomendados y la funcionalidad para los parámetros de propiedad.

|Parámetro|Funcionalidad|
|---|---|
|**recuento**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario puede especificar el número de objetos que se procesarán.|
|**Descripción**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar una descripción para un recurso.|
|**From**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el objeto de referencia para obtener información de.|
|**Id**<br>Tipo de datos: Recursos dependientes|Implemente este parámetro para que el usuario puede especificar el identificador de un recurso.|
|**entrada**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar la especificación de archivo de entrada.|
|**Ubicación**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar la ubicación del recurso.|
|**LogName**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el nombre del archivo de registro para procesar o usar.|
|**Name**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el nombre del recurso.|
|**Salida**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el archivo de salida.|
|**Owner**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el nombre del propietario del recurso.|
|**Propiedad**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el nombre o los nombres de las propiedades que se va a usar.|
|**Reason**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar por qué se invoca este cmdlet.|
|**Regex**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que se usan expresiones regulares cuando se especifica el parámetro. Cuando se especifica este parámetro, no se resuelven los caracteres comodín.|
|**Velocidad**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario puede especificar la velocidad en baudios. El usuario establece este parámetro en la velocidad del recurso.|
|**Estado**<br>Tipo de datos: Matriz de palabra clave|Implemente este parámetro para que el usuario puede especificar los nombres de los Estados, como KEYDOWN.|
|**Valor**<br>Tipo de datos: Objeto|Implemente este parámetro para que el usuario puede especificar un valor para proporcionar al cmdlet.|
|**Versión**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar la versión de la propiedad.|

## <a name="see-also"></a>Véase también

[Parámetros de cmdlet](./cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
