---
title: Elemento FormatString para WideItem para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363034"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>Elemento FormatString para WideItem for WideControl (formato)

Especifica un modelo de formato que define cómo se muestra la propiedad o el valor de script en la vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry para WideControl (Format) WideItem Element for WideControl (Format) elemento FormatString para WideItem para WideControl (Format)

## <a name="syntax"></a>Sintaxis

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `FormatString`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideItem para WideControl (Format)](./wideitem-element-for-widecontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.|

## <a name="text-value"></a>Valor de texto

Especifique el patrón que se utiliza para dar formato a los datos. Por ejemplo, puede usar este patrón para dar formato al valor de cualquier propiedad que sea del tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: HH}: {0: mm}.

## <a name="remarks"></a>Observaciones

Las cadenas de formato se pueden usar al crear vistas de tabla, vistas de lista, vistas anchas o vistas personalizadas. Para obtener más información sobre cómo dar formato a un valor que se muestra en una vista, vea [aplicar formato a los datos mostrados](./formatting-displayed-data.md).

Para obtener más información sobre el uso de cadenas de formato en las vistas anchas, vea [crear una vista amplia](./creating-a-wide-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo definir una cadena de formato para el valor de la propiedad `StartTime`.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>Véase también

[Crear una vista amplia](./creating-a-wide-view.md)

[Elemento WideItem para WideControl (Format)](./wideitem-element-for-widecontrol-format.md)

[Escribir un archivo de formato y tipos de Windows PowerShell](./writing-a-powershell-formatting-file.md)
