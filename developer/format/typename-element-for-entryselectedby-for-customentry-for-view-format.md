---
title: Elemento TypeName para EntrySelectedBy para CustomEntry para vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858841"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>Elemento TypeName para EntrySelectedBy for CustomEntry for View (formato)

Especifica un tipo .NET que usa esta definición de la vista de control personalizado. No hay ningún límite al número de tipos que se pueden especificar para una definición.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para EntrySelectedBy vista (formato) Elemento para CustomEntry de vista (formato) del elemento TypeName para EntrySelectedBy para CustomEntry para vista (formato)

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
|[Elemento EntrySelectedBy para CustomEntry para vista (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Define los tipos de .NET que utilizan esta definición de vista de control personalizado o la condición que debe existir para que esta definición para usarse.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre completo del tipo. NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observaciones

Cada definición de la vista de control personalizado debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.

Para obtener más información acerca de los componentes de una vista de control personalizado, consulte [crear controles personalizados](./creating-custom-controls.md).

## <a name="see-also"></a>Véase también

[Creación de controles personalizados](./creating-custom-controls.md)

[Elemento EntrySelectedBy para CustomEntry para vista (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
