---
title: Elemento FormatString para ListItem para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363024"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>Elemento FormatString para ListItem for ListControl (formato)

Especifica un modelo de formato que define cómo se muestra el valor de la propiedad o del script.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para ListControl (Format) elemento ListEntry para ListControl (Format) elemento ListItems para ListControl (Format) Elemento ListItem para ListControl (Format) elemento FormatString para ListItem para ListControl (Format)

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
|[ListItem (elemento, Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.|

## <a name="text-value"></a>Valor de texto

Especifique el patrón que se utiliza para dar formato a los datos. Por ejemplo, puede usar este patrón para dar formato al valor de cualquier propiedad que sea del tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: HH}: {0: mm}.

## <a name="remarks"></a>Observaciones

Las cadenas de formato se pueden usar al crear vistas de tabla, vistas de lista, vistas anchas o vistas personalizadas. Para obtener más información sobre cómo dar formato a un valor que se muestra en una vista, vea [aplicar formato a los datos mostrados](./formatting-displayed-data.md).

Para obtener más información sobre el uso de cadenas de formato en las vistas de lista, vea [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo definir una cadena de formato para el valor de la propiedad `StartTime`.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>Véase también

[Crear una vista de lista](./creating-a-list-view.md)

[ListItem (elemento, Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Escribir un archivo de formato y tipos de Windows PowerShell](./writing-a-powershell-formatting-file.md)
