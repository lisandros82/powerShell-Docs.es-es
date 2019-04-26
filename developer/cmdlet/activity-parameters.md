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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075195"
---
# <a name="activity-parameters"></a>Parámetros de actividad

En la tabla siguiente se enumera los nombres recomendados y la funcionalidad para los parámetros de actividad.

|Parámetro|Funcionalidad|
|---|---|
|**Anexar**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que el usuario puede agregar contenido al final de un recurso cuando se especifica el parámetro.|
|**CaseSensitive**<br>Tipo de datos: SwitchParameter|Implementar este parámetro para que el usuario puede requerir mayúsculas y minúsculas cuando se especifica el parámetro.|
|**Command**<br>Tipo de datos: Cadena|Implementar este parámetro para que el usuario puede especificar una cadena de comandos para ejecutar.|
|**CompatibleVersion**<br>Tipo de datos: Objeto System.Version|Implementar este parámetro para que el usuario puede especificar la semántica que el cmdlet debe ser compatible con la compatibilidad con versiones anteriores.|
|**Comprimir**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que se emplea la compresión de datos cuando se especifica el parámetro.|
|**Comprimir**<br>Tipo de datos: Palabra clave|Implemente este parámetro para que el usuario puede especificar el algoritmo que se usará para la compresión de datos.|
|**continua**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que se procesan los datos hasta que el usuario finaliza el cmdlet cuando se especifica el parámetro. Si no se especifica el parámetro, el cmdlet procesa una cantidad predefinida de datos y, a continuación, finaliza la operación.|
|**Crear**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para indicar que se crea un recurso si aún no existe cuando se especifica el parámetro.|
|**Delete**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que los recursos se eliminan cuando el cmdlet se ha completado su operación cuando se especifica el parámetro.|
|**Purga**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para indicar que se procesan los elementos de trabajo pendientes antes de que el cmdlet procesa datos nuevos cuando se especifica el parámetro. Si el parámetro no se especifica, se procesan inmediatamente los elementos de trabajo.|
|**Borrar**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario puede especificar el número de veces que un recurso se borra antes de eliminarla.|
|**ErrorLevel**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario puede especificar el nivel de errores para informar.|
|**excluir**<br>Tipo de datos: String[]|Implemente este parámetro para que el usuario puede excluir algo de una actividad. Para obtener más información sobre cómo usar los filtros de entrada, consulte [parámetros de filtro de entrada](input-filter-parameters.md).|
|**Filter**<br>Tipo de datos: Palabra clave|Implemente este parámetro para que el usuario puede especificar un filtro que selecciona los recursos al que se va a realizar la acción de cmdlet. Para obtener más información sobre cómo usar los filtros de entrada, consulte [parámetros de filtro de entrada](./input-filter-parameters.md).|
|**Siga**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que se realiza un seguimiento de progreso cuando se especifica el parámetro.|
|**Force**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para indicar que el usuario puede realizar una acción, incluso si se encuentran restricciones cuando se especifica el parámetro. El parámetro no admite la seguridad en peligro. Por ejemplo, este parámetro permite al usuario sobrescribir un archivo de solo lectura.|
|**Include**<br>Tipo de datos: String[]|Implemente este parámetro para que el usuario puede incluir algo en una actividad. Para obtener más información sobre cómo usar los filtros de entrada, consulte [parámetros de filtro de entrada](input-filter-parameters.md).|
|**Incremental**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para indicar que el procesamiento se realiza de forma incremental cuando se especifica el parámetro. Por ejemplo, este parámetro permite al usuario realizar copias de seguridad incrementales para realizar una copia de seguridad de archivos sólo desde la última copia de seguridad.|
|**InputObject**<br>Tipo de datos: Objeto|Implemente este parámetro cuando el cmdlet toma como entrado de otros cmdlets. Al definir un **InputObject** parámetro, especifique siempre el **ValueFromPipeline** palabra clave cuando se declara el **parámetro** atributo. Para obtener más información sobre el uso de filtros de entrada, consulte [parámetros de filtro de entrada](./input-filter-parameters.md).|
|**Insert**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que el cmdlet inserta un elemento cuando se especifica el parámetro.|
|**Interactive**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que el cmdlet interactivamente funciona con el usuario cuando se especifica el parámetro.|
|**Interval**<br>Tipo de datos: HashTable|Implemente este parámetro para que el usuario puede especificar una tabla de hash de las palabras clave que contiene los valores. El ejemplo siguiente muestra los valores de ejemplo para el **intervalo** parámetro: `-interval @{ResumeScan=15; Retry=3}`.|
|**Log**<br>Tipo de datos: SwitchParameter|Implemente esta auditoría de parámetro de las acciones del cmdlet cuando se especifica el parámetro.|
|**NoClobber**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que el recurso no se sobrescribirá cuando se especifica el parámetro. Normalmente, este parámetro se aplica a los cmdlets que crean nuevos objetos para que pueden evitar que se sobrescriban los objetos existentes con el mismo nombre.|
|**Notificar**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que el usuario le notificará que la actividad está completa cuando se especifica el parámetro.|
|**NotifyAddress**<br>Tipo de datos: Dirección de correo electrónico|Implemente este parámetro para que el usuario puede especificar la dirección de correo electrónico a usar para enviar una notificación cuando la **Notify** se especifica el parámetro.|
|**Sobrescribir**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que el cmdlet sobrescribe los datos existentes cuando se especifica el parámetro.|
|**Prompt**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar un símbolo del sistema para el cmdlet.|
|**Quiet**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que el cmdlet suprime los comentarios de los usuarios durante sus acciones cuando se especifica el parámetro.|
|**Recurse**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que el cmdlet de forma recursiva lleva a cabo sus acciones en los recursos cuando se especifica el parámetro.|
|**Reparación**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que el cmdlet intentará corregir algo de mal estado cuando se especifica el parámetro.|
|**RepairString**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar una cadena para usar cuando el **reparación** se especifica el parámetro.|
|**Retry**<br>Tipo de datos: Int32|Implementar este parámetro para que el usuario puede especificar el número de veces que el cmdlet intentará una acción.|
|**Select**<br>Tipo de datos: Matriz de palabra clave|Implemente este parámetro para que el usuario puede especificar una matriz de los tipos de elementos.|
|**Stream**<br>Tipo de datos: SwitchParameter|Implementar este parámetro para que el usuario puede transmitir a varios objetos de salida a través de la canalización cuando se especifica el parámetro.|
|**Strict**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que todos los errores se tratan como errores de terminación cuando se especifica el parámetro.|
|**TempLocation**<br>Tipo de datos: Cadena|Implementar este parámetro para que el usuario puede especificar la ubicación de los datos temporales que se usan durante el funcionamiento del cmdlet.|
|**Tiempo de espera**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario puede especificar el intervalo de tiempo de espera (en milisegundos).|
|**truncar**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que el cmdlet truncará sus acciones cuando se especifica el parámetro. Si no se especifica el parámetro, el cmdlet realiza otra acción.|
|**Verify**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que el cmdlet realizará la comprobación para determinar si se ha producido una acción cuando se especifica el parámetro.|
|**Espere**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que el cmdlet esperará proporcionados por el usuario antes de continuar cuando se especifica el parámetro.
|**WaitTime**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario puede especificar la duración (en segundos) que el cmdlet esperará usuario entrada cuando el **espera** se especifica el parámetro.|

## <a name="see-also"></a>Véase también

[Parámetros de cmdlet](./cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
