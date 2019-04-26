---
title: Elemento CustomEntry para CustomEntries para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066505"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>Elemento CustomEntry para CustomEntries for Controls for View (formato)

Proporciona una definición del control. Este elemento se usa al definir los controles que pueden usarse en una vista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para los controles de vista (formato)

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
|[Elemento EntrySelectedBy para CustomEntry para los controles de vista (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse.|
|[Elemento CustomItem para CustomEntry para los controles de vista (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Elemento necesario.<br /><br /> Define cómo el control muestra los datos.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntries para el control personalizado para la vista (formato)](./customentries-element-for-customcontrol-for-view-format.md)|Proporciona las definiciones para el control.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento CustomEntries para el control personalizado para la vista (formato)](./customentries-element-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
