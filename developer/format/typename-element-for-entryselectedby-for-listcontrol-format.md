---
title: Elemento TypeName para EntrySelectedBy de ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084035"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>Elemento TypeName para EntrySelectedBy for ListControl (formato)

Especifica un tipo .NET que usa esta entrada de la vista de lista. No hay ningún límite al número de tipos que se pueden especificar para una entrada de lista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento de configuración para TypeName ListEntry (formato) (elemento) para EntrySelectedBy de ListControl (formato)

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
|[Elemento EntrySelectedBy para ListEntry (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Define los tipos de .NET que usan esta entrada de lista o la condición que debe existir para que esta entrada que se usará.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre completo del tipo. NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observaciones

Cada entrada de la lista debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.

Para obtener más información sobre cómo se usa este elemento en una vista de lista, consulte [vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo especificar una conjunto para una entrada de una vista de lista de selección.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Véase también

[Creación de una vista de lista](./creating-a-list-view.md)

[Elemento EntrySelectedBy para ListEntry (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para ListEntry (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
