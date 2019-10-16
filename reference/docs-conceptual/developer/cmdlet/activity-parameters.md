---
title: Parámetros de actividad | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364644"
---
# <a name="activity-parameters"></a>Parámetros de actividad

En la tabla siguiente se enumeran los nombres recomendados y la funcionalidad de los parámetros de actividad.

|Parámetro|Funcionalidad|
|---|---|
|**Anexar**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que el usuario pueda agregar contenido al final de un recurso cuando se especifique el parámetro.|
|**CaseSensitive**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que el usuario pueda requerir distinción de mayúsculas y minúsculas cuando se especifique el parámetro.|
|**Command**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar una cadena de comandos que se va a ejecutar.|
|**CompatibleVersion**<br>Tipo de datos: System. version (objeto)|Implemente este parámetro para que el usuario pueda especificar la semántica con la que el cmdlet debe ser compatible para la compatibilidad con versiones anteriores.|
|**Comprimir**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que se use la compresión de datos cuando se especifique el parámetro.|
|**Comprimir**<br>Tipo de datos: palabra clave|Implemente este parámetro para que el usuario pueda especificar el algoritmo que se va a utilizar para la compresión de datos.|
|**Continua**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que los datos se procesen hasta que el usuario termine el cmdlet cuando se especifique el parámetro. Si no se especifica el parámetro, el cmdlet procesa una cantidad de datos predefinida y, a continuación, finaliza la operación.|
|**A**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para indicar que se crea un recurso si aún no existe ninguno cuando se especifica el parámetro.|
|**Elimínelos**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que se eliminen los recursos cuando el cmdlet haya completado su operación cuando se especifique el parámetro.|
|**Evacua**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para indicar que los elementos de trabajo pendientes se procesan antes de que el cmdlet procese los datos nuevos cuando se especifica el parámetro. Si no se especifica el parámetro, los elementos de trabajo se procesan inmediatamente.|
|**Fondos**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario pueda especificar el número de veces que se borra un recurso antes de eliminarlo.|
|**ErrorLevel**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario pueda especificar el nivel de errores que se van a notificar.|
|**Evitar**<br>Tipo de datos: String []|Implemente este parámetro para que el usuario pueda excluir algo de una actividad. Para obtener más información sobre cómo usar los filtros de entrada, consulte [parámetros de filtro de entrada](input-filter-parameters.md).|
|**Filtro**<br>Tipo de datos: palabra clave|Implemente este parámetro para que el usuario pueda especificar un filtro que seleccione los recursos en los que se realizará la acción del cmdlet. Para obtener más información sobre cómo usar los filtros de entrada, consulte [parámetros de filtro de entrada](./input-filter-parameters.md).|
|**Cumplir**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que se realice un seguimiento del progreso cuando se especifique el parámetro.|
|**Aplica**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para indicar que el usuario puede realizar una acción incluso si se encuentran restricciones cuando se especifica el parámetro. El parámetro no permite poner en peligro la seguridad. Por ejemplo, este parámetro permite a un usuario sobrescribir un archivo de solo lectura.|
|**Inclui**<br>Tipo de datos: String []|Implemente este parámetro para que el usuario pueda incluir algo en una actividad. Para obtener más información sobre cómo usar los filtros de entrada, consulte [parámetros de filtro de entrada](input-filter-parameters.md).|
|**Incremental**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para indicar que el procesamiento se realiza de forma incremental cuando se especifica el parámetro. Por ejemplo, este parámetro permite a un usuario realizar copias de seguridad incrementales que solo realizan copias de seguridad de archivos desde la última copia de seguridad.|
|**InputObject**<br>Tipo de datos: objeto|Implemente este parámetro cuando el cmdlet tome la entrada de otros cmdlets. Al definir un parámetro **InputObject** , siempre debe especificar la palabra clave **ValueFromPipeline** al declarar el atributo **Parameter** . Para obtener más información sobre el uso de filtros de entrada, consulte [parámetros de filtro de entrada](./input-filter-parameters.md).|
|**Introducir**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que el cmdlet Inserte un elemento cuando se especifique el parámetro.|
|**Dicho**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que el cmdlet funcione interactivamente con el usuario cuando se especifica el parámetro.|
|**Interval**<br>Tipo de datos: HashTable|Implemente este parámetro para que el usuario pueda especificar una tabla hash de palabras clave que contenga los valores. En el ejemplo siguiente se muestran los valores de ejemplo para el parámetro **Interval** : `-interval @{ResumeScan=15; Retry=3}`.|
|**Log**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para auditar las acciones del cmdlet cuando se especifica el parámetro.|
|**NoClobber**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que no se sobrescriba el recurso cuando se especifique el parámetro. Este parámetro se aplica generalmente a los cmdlets que crean nuevos objetos para que se les pueda impedir que sobrescriban los objetos existentes con el mismo nombre.|
|**Notificar a**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que se notifique al usuario que la actividad se ha completado cuando se especifica el parámetro.|
|**NotifyAddress**<br>Tipo de datos: dirección de correo electrónico|Implemente este parámetro para que el usuario pueda especificar la dirección de correo electrónico que se va a usar para enviar una notificación cuando se especifique el parámetro **Notify** .|
|**Sobrescribir**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que el cmdlet sobrescriba los datos existentes cuando se especifique el parámetro.|
|**Pregunte**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar un mensaje para el cmdlet.|
|**Actividad**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que el cmdlet suprima los comentarios de los usuarios durante sus acciones cuando se especifica el parámetro.|
|**Recurse**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que el cmdlet realice de forma recursiva sus acciones en los recursos cuando se especifique el parámetro.|
|**Resolver**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que el cmdlet intente corregir algo desde un estado interrumpido cuando se especifique el parámetro.|
|**RepairString**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar una cadena que se usará cuando se especifique el parámetro de **reparación** .|
|**Realizar**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario pueda especificar el número de veces que el cmdlet intentará realizar una acción.|
|**No**<br>Tipo de datos: palabra clave array|Implemente este parámetro para que el usuario pueda especificar una matriz de los tipos de elementos.|
|**Misiones**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que el usuario pueda transmitir varios objetos de salida a través de la canalización cuando se especifique el parámetro.|
|**Contrario**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que todos los errores se controlen como errores de terminación cuando se especifica el parámetro.|
|**TempLocation**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar la ubicación de los datos temporales que se usan durante la operación del cmdlet.|
|**Super**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario pueda especificar el intervalo de tiempo de espera (en milisegundos).|
|**Truncar**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que el cmdlet trunque sus acciones cuando se especifica el parámetro. Si no se especifica el parámetro, el cmdlet realiza otra acción.|
|**Ver**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que el cmdlet pruebe para determinar si se ha producido una acción cuando se especifica el parámetro.|
|**Currir**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que el cmdlet espere la entrada del usuario antes de continuar cuando se especifique el parámetro.
|**WaitTime**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario pueda especificar la duración (en segundos) que el cmdlet va a esperar la entrada del usuario cuando se especifica el parámetro **Wait** .|

## <a name="see-also"></a>Véase también

[Parámetros de cmdlet](./cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
