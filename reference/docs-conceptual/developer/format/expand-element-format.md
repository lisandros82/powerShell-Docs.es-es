---
title: Expand (elemento, Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368744"
---
# <a name="expand-element-format"></a>Elemento Expand (formato)

Especifica cómo se expande el objeto de colección para esta definición.

Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) Expand Element (Format)

## <a name="syntax"></a>Sintaxis

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Expand`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EnumerableExpansion (Format)](./enumerableexpansion-element-format.md)|Define cómo se expanden los objetos de colección .NET específicos cuando se muestran en una vista.|

## <a name="text-value"></a>Valor de texto

Especifique uno de los valores siguientes:

- EnumOnly: muestra solo las propiedades de los objetos de la colección.

- CoreOnly: muestra solo las propiedades del objeto de colección.

- Both: muestra las propiedades de los objetos de la colección y las propiedades del objeto de colección.

## <a name="remarks"></a>Observaciones

Este elemento se utiliza para definir cómo se muestran los objetos de colección y los objetos de la colección. En este caso, un objeto de colección hace referencia a cualquier objeto que admita la interfaz **System. Collections. ICollection** .

El comportamiento predeterminado es mostrar solo las propiedades de los objetos de la colección.

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
