---
title: Elemento CustomEntry para CustomEntries para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066454"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>Elemento CustomEntry para CustomEntries for CustomControl for View (formato)

Proporciona una definición de la vista de control personalizado.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para vista (formato)

## <a name="syntax"></a>Sintaxis

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomEntry` elemento. Debe especificar los elementos mostrados por la definición.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry para vista (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Define los tipos de .NET que usan la definición de la vista de control personalizado o la condición que debe existir para que esta definición para usarse.|
|[Elemento CustomItem para CustomEntry para vista (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Define un control para la definición de un control personalizado.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntries para el control personalizado para la vista (formato)](./customentries-element-for-customcontrol-for-view-format.md)|Proporciona las definiciones de la vista de control personalizado. La vista de control personalizado debe especificar una o varias definiciones.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, solo una definición es necesaria para cada vista de control personalizado, pero es posible tener varias definiciones si desea usar la misma vista para mostrar diferentes objetos. NET. En esos casos, puede proporcionar una definición independiente para cada objeto o conjunto de objetos.

## <a name="see-also"></a>Véase también

[Elemento de control personalizado para la vista (formato)](./customcontrol-element-for-view-format.md)

[Elemento CustomItem para CustomEntry para vista (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Elemento EntrySelectedBy para CustomEntry para vista (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
