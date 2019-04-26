---
title: Elemento TypeName para EntrySelectedBy para WideEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083933"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>Elemento TypeName para EntrySelectedBy for WideEntry (formato)

Especifica un tipo de .NET para la definición. La definición se usa siempre que se muestra este objeto.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento de configuración para TypeName WideEntry (formato) (elemento) para WideEntry ( Formato)

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
|[Elemento EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)|Define los tipos de .NET que usan esta entrada del ancha o la condición que debe existir para que esta entrada que se usará.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre completo del tipo. NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observaciones

Cada entrada amplia debe especificar uno o varios tipos. NET, un conjunto de selección o la condición de selección que debe cumplirse para que la definición que se usará.

Para obtener más información sobre otros componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).

## <a name="see-also"></a>Véase también

[Creación de una vista amplia](./creating-a-wide-view.md)

[Elemento EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
