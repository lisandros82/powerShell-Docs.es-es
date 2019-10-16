---
title: Elemento EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368754"
---
# <a name="enumerableexpansion-element-format"></a>Elemento EnumerableExpansion (formato)

Define cómo se expanden los objetos de colección .NET específicos cuando se muestran en una vista.

Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format)

## <a name="syntax"></a>Sintaxis

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EnumerableExpansion`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Define qué objetos de colección .NET se expanden mediante esta definición.|
|[Expand (elemento, Format)](./expand-element-format.md)|Especifica cómo se expande el objeto de colección para esta definición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EnumerableExpansions (Format)](./enumerableexpansions-element-format.md)|Define las diferentes formas en que los objetos de colección de .NET se expanden cuando se muestran en una vista.|

## <a name="remarks"></a>Observaciones

Este elemento se utiliza para definir cómo se muestran los objetos de colección y los objetos de la colección. En este caso, un objeto de colección hace referencia a cualquier objeto que admita la interfaz **System. Collections. ICollection** .

El comportamiento predeterminado es mostrar solo las propiedades de los objetos de la colección.

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
