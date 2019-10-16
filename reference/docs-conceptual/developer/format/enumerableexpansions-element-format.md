---
title: Elemento EnumerableExpansions (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363304"
---
# <a name="enumerableexpansions-element-format"></a>Elemento EnumerableExpansions (formato)

Define cómo se expanden los objetos de la colección de .NET cuando se muestran en una vista.

Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format)

## <a name="syntax"></a>Sintaxis

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EnumerableExpansions`. No hay ningún límite en el número de elementos secundarios que puede usar.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EnumerableExpansion (Format)](./enumerableexpansion-element-format.md)|Elemento opcional.<br /><br /> Define los objetos de colección .NET específicos que se expanden cuando se muestran en una vista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[DefaultSettings (elemento, Format)](./defaultsettings-element-format.md)|Define la configuración común que se aplica a todas las vistas del archivo de formato.|

## <a name="remarks"></a>Observaciones

Este elemento se utiliza para definir cómo se muestran los objetos de colección y los objetos de la colección. En este caso, un objeto de colección hace referencia a cualquier objeto que admita la interfaz **System. Collections. ICollection** .

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
