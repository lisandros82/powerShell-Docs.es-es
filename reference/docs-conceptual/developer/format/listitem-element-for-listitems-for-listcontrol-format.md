---
title: Elemento ListItem para ListItems para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365134"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>Elemento ListItem para ListItems for ListControl (formato)

Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para ListControl (Format) elemento ListEntry para ListControl (Format) elemento ListItems para ListControl (Format) ListItem para el elemento ListControl (Format)

## <a name="syntax"></a>Sintaxis

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ListItem`. Solo se puede especificar una propiedad o un script.

### <a name="attributes"></a>Atributos

Ninguno

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento FormatString para ListItem para ListControl (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica una cadena de formato que define cómo se muestra el valor de la propiedad o del script.|
|[Elemento ItemSelectionCondition para ListItem para ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que se use este elemento de lista.|
|[Elemento Label de ListItem para ListControl (Format)](./label-element-for-listitem-for-listcontrol-format.md)|Elemento opcional<br /><br /> Especifica la etiqueta que se muestra a la izquierda de la propiedad o del valor de script de la fila.|
|[Elemento PropertyName para ListItem para ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET cuyo valor se muestra en la fila.|
|[Elemento ScriptBlock para ListItem para ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica el script cuyo valor se muestra en la fila.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ListItems para el control List (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Define las propiedades y los scripts cuyos valores se muestran en la vista de lista.|

## <a name="remarks"></a>Observaciones

Para obtener más información sobre los componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestran los elementos XML que definen tres filas de la vista de lista. Las dos primeras filas muestran el valor de una propiedad de .NET y la última fila muestra un valor generado por un script.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a>Véase también

[ListItems (elemento, Format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Elemento FormatString para ListItem (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Elemento Label para ListItem (Format)](./label-element-for-listitem-for-listcontrol-format.md)

[Elemento PropertyName para ListItem (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Elemento ScriptBlock para ListItem (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Crear una vista de lista](./creating-a-list-view.md)

[Escribir un archivo de formato y tipos de Windows PowerShell](./writing-a-powershell-formatting-file.md)
