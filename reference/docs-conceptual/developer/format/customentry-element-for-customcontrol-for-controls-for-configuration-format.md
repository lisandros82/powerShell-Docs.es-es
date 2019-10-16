---
title: Elemento CustomEntry para CustomControl para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364074"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>Elemento CustomEntry para CustomControl for Controls for Configuration (formato)

Proporciona una definición del control común. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl para controles de configuración (Format)

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
|[Elemento EntrySelectedBy de CustomEntry para controles de configuración (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define los tipos de .NET que usan la definición del control común o la condición que debe existir para que se utilice este control.|
|[Elemento CustomItem de CustomEntry para controles de configuración](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Elemento obligatorio.<br /><br /> Define qué datos se muestran en el control y cómo se muestran.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntries para CustomControl para Configuration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Proporciona las definiciones del control común.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, solo se requiere una definición para cada control personalizado común, pero es posible tener varias definiciones si se desea usar el mismo control para mostrar objetos .NET diferentes. En esos casos, puede proporcionar una definición independiente para cada objeto o conjunto de objetos.

## <a name="see-also"></a>Véase también

[Elemento CustomEntries para CustomControl para Configuration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[Elemento CustomItem de CustomEntry para controles de configuración](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
