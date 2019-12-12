---
title: Elemento TypeName para EntrySelectedBy para CustomEntry para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368074"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>Elemento TypeName para EntrySelectedBy for CustomEntry for View (formato)

Especifica un tipo .NET que usa esta definición de la vista de control personalizada. No hay ningún límite en el número de tipos que se pueden especificar para una definición.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl for View (Format) elemento CustomEntry para CustomEntries for View (Format) EntrySelectedBy Elemento para CustomEntry para el elemento TypeName de View (Format) para EntrySelectedBy para CustomEntry para View (Format)

## <a name="syntax"></a>Sintaxis

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry para View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Define los tipos .NET que usan esta definición de vista de control personalizada o la condición que debe existir para que se use esta definición.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observaciones

Cada definición de vista de control personalizada debe tener por lo menos un nombre de tipo, conjunto de selección o condición de selección definidos.

Para obtener más información sobre los componentes de una vista de control personalizada, vea [crear controles personalizados](./creating-custom-controls.md).

## <a name="see-also"></a>Véase también

[Creación de controles personalizados](./creating-custom-controls.md)

[Elemento EntrySelectedBy para CustomEntry para View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
