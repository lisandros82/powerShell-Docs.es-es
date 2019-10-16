---
title: Elemento CustomEntry para CustomEntries para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364024"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>Elemento CustomEntry para CustomEntries for CustomControl for View (formato)

Proporciona una definición de la vista de control personalizada.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl for View (Format) elemento CustomEntry para CustomEntries for View (Format)

## <a name="syntax"></a>Sintaxis

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomEntry`. Debe especificar los elementos que se muestran en la definición.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry para View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Define los tipos .NET que usan la definición de la vista de control personalizada o la condición que debe existir para que se use esta definición.|
|[Elemento CustomItem para CustomEntry para View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Define un control para la definición del control personalizado.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntries para CustomControl para View (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Proporciona las definiciones de la vista de control personalizada. La vista de control personalizada debe especificar una o más definiciones.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, solo se requiere una definición para cada vista de control personalizada, pero es posible tener varias definiciones si se desea usar la misma vista para mostrar diferentes objetos .NET. En esos casos, puede proporcionar una definición independiente para cada objeto o conjunto de objetos.

## <a name="see-also"></a>Véase también

[Elemento CustomControl para View (Format)](./customcontrol-element-for-view-format.md)

[Elemento CustomItem para CustomEntry para View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Elemento EntrySelectedBy para CustomEntry para View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
