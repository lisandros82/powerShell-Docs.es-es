---
title: Elemento EntrySelectedBy para CustomEntry para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: e930e4422afd203feda6a389655ff8a355e3bec0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858671"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>Elemento EntrySelectedBy para CustomEntry for Controls for Configuration (formato)

Define los tipos de .NET que usan la definición del control común o la condición que debe existir para que este control que se usará. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) EntrySelectedBy para CustomEntry para los controles de configuración (formato)

## <a name="syntax"></a>Sintaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `EntrySelectedBy` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define la condición que debe cumplirse para que la definición de control comunes que se usará.|
|[Elemento SelectionSetName para EntrySelectedBy para los controles de configuración (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de tipos de .NET que usan esta definición del control común.|
|[Elemento TypeName para EntrySelectedBy para los controles de configuración (formato)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que usa esta definición del control común.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para el control personalizado para los controles de configuración (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Proporciona una definición del control común.|

## <a name="remarks"></a>Observaciones

Como mínimo, cada definición debe tener al menos un tipo. NET, conjunto de selección o condición de selección especificada. No hay ningún límite máximo para el número de tipos, conjuntos de selección o condiciones de selección que se pueden especificar.

## <a name="see-also"></a>Véase también

[Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Elemento SelectionSetName para EntrySelectedBy para los controles de configuración (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento CustomEntry para el control personalizado para los controles de configuración (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Elemento TypeName para EntrySelectdBy para los controles de configuración (formato)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
