---
title: ListControl (elemento, Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362784"
---
# <a name="listcontrol-element-format"></a>Elemento ListControl (formato)

Define un formato de lista para la vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format)

## <a name="syntax"></a>Sintaxis

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ListControl`. Este elemento debe contener un único elemento secundario.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[ListEntries (elemento, Format)](./listentries-element-for-listcontrol-format.md)|Elemento obligatorio.<br /><br /> Proporciona las definiciones de la vista de lista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Define una vista que se utiliza para mostrar los miembros de uno o más objetos.|

## <a name="remarks"></a>Observaciones

Para obtener más información sobre cómo crear una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra una vista de lista para el objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Véase también

[Elemento View (Format)](./view-element-format.md)

[ListEntries (elemento, Format)](./listentries-element-for-listcontrol-format.md)

[Crear una vista de lista](./creating-a-list-view.md)

[Escribir un archivo de formato y tipos de Windows PowerShell](./writing-a-powershell-formatting-file.md)
