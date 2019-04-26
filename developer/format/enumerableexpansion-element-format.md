---
title: Elemento EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066148"
---
# <a name="enumerableexpansion-element-format"></a>Elemento EnumerableExpansion (formato)

Define cómo determinados de .NET de colección, los objetos se expanden cuando se muestran en una vista.

Elemento EnumerableExpansions (formato) EnumerableExpansion elemento de configuración (formato) del elemento elemento DefaultSettings (formato) (formato)

## <a name="syntax"></a>Sintaxis

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `EnumerableExpansion` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Define los objetos de colección de .NET se expanden por esta definición.|
|[Expanda el elemento (formato)](./expand-element-format.md)|Especifica cómo se expande el objeto de colección para esta definición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EnumerableExpansions (formato)](./enumerableexpansions-element-format.md)|Define las diferentes formas de esa colección de .NET que los objetos se expanden cuando se muestran en una vista.|

## <a name="remarks"></a>Observaciones

Este elemento se utiliza para definir cómo se muestran los objetos de colección y los objetos de la colección. En este caso, un objeto de colección hace referencia a cualquier objeto que admita la **System.Collections.ICollection** interfaz.

El comportamiento predeterminado consiste en Mostrar solo las propiedades de los objetos de la colección.

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
