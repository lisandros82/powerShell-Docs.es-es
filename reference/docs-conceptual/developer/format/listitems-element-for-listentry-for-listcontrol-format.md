---
title: Elemento ListItems para ListEntry para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362744"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>Elemento ListItems para ListEntry for ListControl (formato)

Define las propiedades y los scripts cuyos valores se muestran en las filas de la vista de lista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para el elemento de lista (Format) elemento ListEntry para ListControl (Format) elemento ListItems para ListControl (Format)

## <a name="syntax"></a>Sintaxis

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ListItems`. No hay ningún límite en el número de elementos secundarios que se pueden especificar. El orden de los elementos secundarios define el orden en que se muestran los valores en la vista de lista.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ListItem para ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Elemento necesario.<br /><br /> Define la propiedad o el script cuyo valor se muestra en la vista de lista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ListEntry para ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Proporciona una definición de la vista de lista.|

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de este tipo de vista, vea [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestran los elementos XML que definen tres filas de la vista de lista.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>Véase también

[Elemento ListEntry para ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[Elemento ListItem para ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Crear una vista de lista](./creating-a-list-view.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
