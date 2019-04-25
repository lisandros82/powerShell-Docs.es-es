---
title: Elemento ListEntry para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065230"
---
# <a name="listentry-element-for-listcontrol-format"></a>Elemento ListEntry para ListControl (formato)

Proporciona una definición de la vista de lista.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) elemento ListEntries (formato) ListEntry elemento (formato)

## <a name="syntax"></a>Sintaxis

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ListEntry` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para ListEntry (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Define los objetos de .NET que usan esta definición de vista de lista o la condición que debe existir para que esta definición para usarse.|
|[Elemento ListItems (formato)](./listitems-element-for-listentry-for-listcontrol-format.md)|Elemento necesario.<br /><br /> Define las propiedades y las secuencias de comandos cuyos valores se muestran en la vista de lista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ListEntries (formato)](./listentries-element-for-listcontrol-format.md)|Proporciona las definiciones de la vista de lista.|

## <a name="remarks"></a>Observaciones

Una vista de lista es un formato de lista que muestra los valores de propiedad o valores de secuencia de comandos para cada objeto. Para obtener más información acerca de las vistas de lista, consulte [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra los elementos XML que definen la vista de lista para la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.

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

[Creación de una vista de lista](./creating-a-list-view.md)

[Elemento EntrySelectedBy para ListEntry (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Elemento ListEntries (formato)](./listentries-element-for-listcontrol-format.md)

[Elemento ListItems (formato)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Escribir un formato de Windows PowerShell y los tipos de archivo](./writing-a-powershell-formatting-file.md)
