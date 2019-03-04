---
title: Elemento CustomEntry para el control personalizado para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859811"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>Elemento CustomEntry para CustomControl for Controls for Configuration (formato)

Proporciona una definición del control común. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de configuración (formato)

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
|[Elemento EntrySelectedBy para CustomEntry para los controles de configuración (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define los tipos de .NET que usan la definición del control común o la condición que debe existir para que este control que se usará.|
|[Elemento CustomItem para CustomEntry para los controles de configuración](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Elemento necesario.<br /><br /> Define qué datos se muestran el control y cómo se muestran.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntries para el control personalizado para la configuración (formato)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Proporciona las definiciones del control común.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, solo una definición es necesaria para cada control personalizado comunes, pero es posible tener varias definiciones si desea utilizar el mismo control para mostrar diferentes objetos. NET. En esos casos, puede proporcionar una definición independiente para cada objeto o conjunto de objetos.

## <a name="see-also"></a>Véase también

[Elemento CustomEntries para el control personalizado para la configuración (formato)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[Elemento CustomItem para CustomEntry para los controles de configuración](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
