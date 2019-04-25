---
title: Elemento ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065264"
---
# <a name="listcontrol-element-format"></a>Elemento ListControl (formato)

Define un formato de lista para la vista.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) ListControl elemento (formato)

## <a name="syntax"></a>Sintaxis

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ListControl` elemento. Este elemento debe contener sólo un único elemento secundario.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ListEntries (formato)](./listentries-element-for-listcontrol-format.md)|Elemento necesario.<br /><br /> Proporciona las definiciones de la vista de lista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de vista (formato)](./view-element-format.md)|Define una vista que se usa para mostrar a los miembros de uno o varios objetos.|

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de cómo crear una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra una vista de lista para la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.

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

[Elemento de vista (formato)](./view-element-format.md)

[Elemento ListEntries (formato)](./listentries-element-for-listcontrol-format.md)

[Creación de una vista de lista](./creating-a-list-view.md)

[Escribir un formato de Windows PowerShell y los tipos de archivo](./writing-a-powershell-formatting-file.md)
