---
title: Elemento CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363364"
---
# <a name="customcontrol-element-for-view-format"></a>Elemento CustomControl para View (formato)

Define un formato de control personalizado para la vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format)

## <a name="syntax"></a>Sintaxis

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomControl`. Debe especificar un elemento secundario.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntries para CustomControl para View (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Elemento necesario.<br /><br /> Proporciona las definiciones de la vista de control personalizada.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Define una vista que se usa para mostrar uno o más objetos .NET.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, solo se requiere una definición para cada vista de control, pero es posible proporcionar varias definiciones si se desea usar la misma vista para mostrar diferentes objetos .NET. En esos casos, puede proporcionar una definición independiente para cada objeto o conjunto de objetos.

## <a name="see-also"></a>Véase también

[Elemento CustomEntries para CustomControl para View (Format)](./customentries-element-for-customcontrol-for-view-format.md)

[Elemento View (Format)](./view-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
