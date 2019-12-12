---
title: Elemento CustomEntry para CustomControl para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364064"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>Elemento CustomEntry para CustomControl for GroupBy (formato)

Proporciona una definición del control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format)

## <a name="syntax"></a>Sintaxis

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `CustomEntry`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Elemento opcional.<br /><br /> Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.|
|[Elemento CustomItem para CustomEntry para GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Elemento necesario.<br /><br /> Define cómo el control muestra los datos.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntries para CustomControl para GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)|Proporciona las definiciones para el control.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Elemento CustomItem para CustomEntry para GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Elemento CustomEntries para CustomControl para GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
