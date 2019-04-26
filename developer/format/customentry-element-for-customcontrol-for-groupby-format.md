---
title: Elemento CustomEntry para el control personalizado para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066494"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>Elemento CustomEntry para CustomControl for GroupBy (formato)

Proporciona una definición del control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato)

## <a name="syntax"></a>Sintaxis

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y los elementos primarios de la `CustomEntry` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Elemento opcional.<br /><br /> Define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse.|
|[Elemento CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)|Elemento necesario.<br /><br /> Define cómo el control muestra los datos.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntries para el control personalizado para GroupBy (formato)](./customentries-element-for-customcontrol-for-groupby-format.md)|Proporciona las definiciones para el control.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Elemento CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)

[Elemento CustomEntries para el control personalizado para GroupBy (formato)](./customentries-element-for-customcontrol-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
