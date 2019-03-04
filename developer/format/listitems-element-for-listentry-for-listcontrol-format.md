---
title: Elemento ListItems para ListEntry para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858591"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>Elemento ListItems para ListEntry for ListControl (formato)

Define las propiedades y las secuencias de comandos cuyos valores se muestran en las filas de la vista de lista.

Configuración (formato) del elemento elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento de elemento de lista (formato) del Control ListEntry para elemento de ListItems de ListControl (formato) de ListControl (formato)

## <a name="syntax"></a>Sintaxis

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `ListItems` elemento. No hay ningún límite al número de elementos secundarios que se pueden especificar. El orden de los elementos secundarios define el orden en que los valores se muestran en la vista de lista.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[ListItem (elemento) para ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Elemento necesario.<br /><br /> Define la propiedad o el script cuyo valor se muestra la vista de lista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ListEntry para ListControl (formato)](./listentry-element-for-listcontrol-format.md)|Proporciona una definición de la vista de lista.|

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de este tipo de vista, consulte [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

Este ejemplo muestra los elementos XML que definen tres filas de la vista de lista.

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

[Elemento ListEntry para ListControl (formato)](./listentry-element-for-listcontrol-format.md)

[ListItem (elemento) para ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Creación de una vista de lista](./creating-a-list-view.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
