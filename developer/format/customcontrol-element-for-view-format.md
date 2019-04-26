---
title: Elemento de control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066675"
---
# <a name="customcontrol-element-for-view-format"></a>Elemento CustomControl para View (formato)

Define un formato de control personalizado para la vista.

Configuración elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento de control personalizado (formato)

## <a name="syntax"></a>Sintaxis

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomControl` elemento. Debe especificar un elemento secundario.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntries para el control personalizado para la vista (formato)](./customentries-element-for-customcontrol-for-view-format.md)|Elemento necesario.<br /><br /> Proporciona las definiciones de la vista de control personalizado.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de vista (formato)](./view-element-format.md)|Define una vista que se usa para mostrar uno o varios objetos. NET.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, solo una definición es necesaria para cada vista de control, pero es posible proporcionar varias definiciones si desea usar la misma vista para mostrar diferentes objetos. NET. En esos casos, puede proporcionar una definición independiente para cada objeto o conjunto de objetos.

## <a name="see-also"></a>Véase también

[Elemento CustomEntries para el control personalizado para la vista (formato)](./customentries-element-for-customcontrol-for-view-format.md)

[Elemento de vista (formato)](./view-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
