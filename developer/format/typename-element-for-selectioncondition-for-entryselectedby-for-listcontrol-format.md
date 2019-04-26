---
title: Elemento TypeName para SelectionCondition para EntrySelectedBy para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083865"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Elemento TypeName para SelectionCondition for EntrySelectedBy for ListControl (formato)

Especifica un tipo .NET que desencadena la condición. Cuando este tipo está presente, se usa la entrada de la lista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento de configuración (elemento) ListEntry ListControl (formato) para ListEntries para elemento de EntrySelectedBy ListControl (formato) de ListEntry para ListControl (formato) (elemento) SelectionCondition para EntrySelectedBy para TypeName ListControl (formato) (elemento) para SelectionCondition para EntrySelectedBy para ListControl (formato)

## <a name="syntax"></a>Sintaxis

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `TypeName` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para ListControl (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Define la condición que debe existir para que esta entrada de lista para usarse.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre completo del tipo. NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observaciones

La condición de selección puede especificar cualquier número de tipos de .NET o la selección se establece, pero no puede especificar ambos. Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).

Para obtener más información acerca de otros, los componentes de una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).

## <a name="see-also"></a>Véase también

[Creación de una vista de lista](./creating-a-list-view.md)

[Definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md)

[Elemento SelectionCondition para EntrySelectedBy para ListControl (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
