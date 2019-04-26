---
title: Elemento EnumerableExpansions (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066097"
---
# <a name="enumerableexpansions-element-format"></a>Elemento EnumerableExpansions (formato)

Define cómo se expanden los objetos de colección de .NET cuando se muestran en una vista.

Configuración (formato) elemento DefaultSettings (formato) EnumerableExpansions elemento (formato)

## <a name="syntax"></a>Sintaxis

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `EnumerableExpansions` elemento. No hay ningún límite al número de elementos secundarios que puede usar.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EnumerableExpansion (formato)](./enumerableexpansion-element-format.md)|Elemento opcional.<br /><br /> Define los objetos de colección específicos de .NET que se expanden cuando se muestran en una vista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md)|Define la configuración común que se aplica a todas las vistas del archivo de formato.|

## <a name="remarks"></a>Observaciones

Este elemento se utiliza para definir cómo se muestran los objetos de colección y los objetos de la colección. En este caso, un objeto de colección hace referencia a cualquier objeto que admita la **System.Collections.ICollection** interfaz.

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
