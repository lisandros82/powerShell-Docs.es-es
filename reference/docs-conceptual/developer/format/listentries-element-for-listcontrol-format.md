---
title: Elemento ListEntries para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362764"
---
# <a name="listentries-element-for-listcontrol-format"></a>Elemento ListEntries para ListControl (formato)

Proporciona las definiciones de la vista de lista. La vista de lista debe especificar una o más definiciones.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format)

## <a name="syntax"></a>Sintaxis

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ListEntries`. Se debe especificar al menos un elemento secundario.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[ListEntry (formato)](./listentry-element-for-listcontrol-format.md)|Proporciona una definición de la vista de lista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[ListControl (elemento, Format)](./listcontrol-element-format.md)|Define un formato de lista para la vista.|

## <a name="remarks"></a>Observaciones

Para obtener más información sobre las vistas de lista, vea [vista de lista](./creating-a-list-view.md).

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

[ListControl (elemento, Format)](./listcontrol-element-format.md)

[ListEntry (formato)](./listentry-element-for-listcontrol-format.md)

[Vista de lista](./creating-a-list-view.md)

[Escribir un archivo de formato y tipos de Windows PowerShell](./writing-a-powershell-formatting-file.md)
