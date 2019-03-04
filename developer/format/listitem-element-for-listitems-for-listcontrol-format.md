---
title: ListItem (elemento) para ListItems de ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855161"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>Elemento ListItem para ListItems for ListControl (formato)

Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento de configuración (elemento) ListEntry ListControl (formato) para el elemento ListItems de ListControl (formato) de ListControl (formato) ListItem para el elemento de ListControl (formato)

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

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `ListItem` elemento. Se puede especificar solo una propiedad o una secuencia de comandos.

### <a name="attributes"></a>Atributos

Ninguno

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento FormatString para ListItem para ListControl (formato)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica una cadena de formato que define cómo se muestra el valor de propiedad o un script.|
|[Elemento ItemSelectionCondition para ListItem para ListControl (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Define la condición que debe cumplirse para que este elemento de lista para usarse.|
|[Elemento de etiqueta para ListItem para ListControl (formato)](./label-element-for-listitem-for-listcontrol-format.md)|Elemento opcional<br /><br /> Especifica la etiqueta que se muestra a la izquierda del valor de propiedad o un script en la fila.|
|[Elemento PropertyName para ListItem para ListControl (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET cuyo valor se muestra en la fila.|
|[Elemento de bloque de script para ListItem para ListControl (formato)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica la secuencia de comandos cuyo valor se muestra en la fila.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ListItems para Control de lista (formato)](./listitems-element-for-listentry-for-listcontrol-format.md)|Define las propiedades y las secuencias de comandos cuyos valores se muestran en la vista de lista.|

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de los componentes de una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

Este ejemplo muestra los elementos XML que definen tres filas de la vista de lista. Las dos primeras filas mostrar el valor de una propiedad de .NET y la última fila muestra un valor generado por una secuencia de comandos.

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

[Elemento ListItems (formato)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Elemento FormatString para ListItem (formato)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Elemento de etiqueta para ListItem (formato)](./label-element-for-listitem-for-listcontrol-format.md)

[Elemento PropertyName para ListItem (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Elemento de bloque de script para ListItem (formato)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Creación de una vista de lista](./creating-a-list-view.md)

[Escribir un formato de Windows PowerShell y los tipos de archivo](./writing-a-powershell-formatting-file.md)
