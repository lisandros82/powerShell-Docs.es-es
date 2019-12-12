---
title: Elemento CustomEntry para CustomEntries para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364054"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>Elemento CustomEntry para CustomEntries for Controls for View (formato)

Proporciona una definición del control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry View (Format) para CustomEntries para controles para View (Format)

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
|[Elemento EntrySelectedBy para CustomEntry para controles para View (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.|
|[Elemento CustomItem para CustomEntry para controles para View (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Elemento necesario.<br /><br /> Define cómo el control muestra los datos.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntries para CustomControl para View (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Proporciona las definiciones para el control.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento CustomEntries para CustomControl para View (Format)](./customentries-element-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
