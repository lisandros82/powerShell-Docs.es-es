---
title: Elemento FormatString para WideItem para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860941"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>Elemento FormatString para WideItem for WideControl (formato)

Especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script en la vista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) WideEntry elemento de configuración (elemento) WideItem WideControl (formato) para el elemento FormatString de WideControl (formato) para WideItem para WideControl (formato)

## <a name="syntax"></a>Sintaxis

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `FormatString` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideItem para WideControl (formato)](./wideitem-element-for-widecontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.|

## <a name="text-value"></a>Valor de texto

Especifique el patrón que se usa para dar formato a los datos. Por ejemplo, puede usar este patrón para dar formato al valor de cualquier propiedad que es del tipo [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.

## <a name="remarks"></a>Observaciones

Cadenas de formato pueden usarse al crear las vistas de tablas, vistas de lista, vista amplia o vistas personalizadas. Para obtener más información sobre cómo dar formato a un valor que se muestran en una vista, consulte [dar formato a datos de muestra](./formatting-displayed-data.md).

Para obtener más información sobre cómo usar cadenas de formato en vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo definir una cadena de formato para el valor de la `StartTime` propiedad.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>Véase también

[Creación de una vista amplia](./creating-a-wide-view.md)

[Elemento WideItem para WideControl (formato)](./wideitem-element-for-widecontrol-format.md)

[Escribir un formato de Windows PowerShell y los tipos de archivo](./writing-a-powershell-formatting-file.md)
