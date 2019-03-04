---
title: Expanda el elemento (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858581"
---
# <a name="expand-element-format"></a>Elemento Expand (formato)

Especifica cómo se expande el objeto de colección para esta definición.

Elemento EnumerableExpansions (formato) EnumerableExpansion elemento de configuración (formato) del elemento elemento DefaultSettings (formato) (formato) amplía el elemento (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Expand` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EnumerableExpansion (formato)](./enumerableexpansion-element-format.md)|Define cómo determinados de .NET de colección, los objetos se expanden cuando se muestran en una vista.|

## <a name="text-value"></a>Valor de texto

Especifique uno de los valores siguientes:

- EnumOnly: Muestra solo las propiedades de los objetos de la colección.

- CoreOnly: Muestra solo las propiedades del objeto de colección.

- Ambos: Muestra las propiedades de los objetos en la colección y las propiedades del objeto de colección.

## <a name="remarks"></a>Observaciones

Este elemento se utiliza para definir cómo se muestran los objetos de colección y los objetos de la colección. En este caso, un objeto de colección hace referencia a cualquier objeto que admita la **System.Collections.ICollection** interfaz.

El comportamiento predeterminado consiste en Mostrar solo las propiedades de los objetos de la colección.

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
