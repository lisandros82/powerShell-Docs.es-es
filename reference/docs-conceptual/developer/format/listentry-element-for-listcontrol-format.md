---
title: Elemento ListEntry para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362754"
---
# <a name="listentry-element-for-listcontrol-format"></a>Elemento ListEntry para ListControl (formato)

Proporciona una definición de la vista de lista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format)

## <a name="syntax"></a>Sintaxis

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ListEntry`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Define los objetos .NET que usan esta definición de vista de lista o la condición que debe existir para que se use esta definición.|
|[ListItems (elemento, Format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Elemento necesario.<br /><br /> Define las propiedades y los scripts cuyos valores se muestran en la vista de lista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[ListEntries (elemento, Format)](./listentries-element-for-listcontrol-format.md)|Proporciona las definiciones de la vista de lista.|

## <a name="remarks"></a>Observaciones

Una vista de lista es un formato de lista que muestra los valores de propiedad o los valores de script para cada objeto. Para obtener más información sobre las vistas de lista, vea [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestran los elementos XML que definen la vista de lista para el objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Véase también

[Crear una vista de lista](./creating-a-list-view.md)

[Elemento EntrySelectedBy para ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntries (elemento, Format)](./listentries-element-for-listcontrol-format.md)

[ListItems (elemento, Format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Escribir un archivo de formato y tipos de Windows PowerShell](./writing-a-powershell-formatting-file.md)
