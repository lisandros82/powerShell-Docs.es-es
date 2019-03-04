---
title: Elemento TypeName para EntrySelectedBy para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861671"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a>Elemento TypeName para EntrySelectedBy for GroupBy (formato)

Especifica un tipo .NET que usa esta definición del control personalizado. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) EntrySelectedBy para CustomEntry para TypeName GroupBy (formato) (elemento) para EntrySelectedBy para GroupBy (formato)

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
|[Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre completo del tipo. NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observaciones

Cada definición de control debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.

Para obtener más información acerca de los componentes de una vista de control personalizado, consulte [crear controles personalizados](./creating-custom-controls.md).

## <a name="see-also"></a>Véase también

[Creación de controles personalizados](./creating-custom-controls.md)

[Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
