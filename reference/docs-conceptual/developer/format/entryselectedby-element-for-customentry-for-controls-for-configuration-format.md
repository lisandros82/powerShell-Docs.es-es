---
title: Elemento EntrySelectedBy para CustomEntry para controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368774"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>Elemento EntrySelectedBy para CustomEntry for Controls for Configuration (formato)

Define los tipos de .NET que usan la definición del control común o la condición que debe existir para que se utilice este control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl para controles de configuración (Format) elemento EntrySelectedBy para CustomEntry para controles de configuración (Format)

## <a name="syntax"></a>Sintaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EntrySelectedBy`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que se use la definición de control común.|
|[Elemento SelectionSetName de EntrySelectedBy para controles de configuración (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de tipos de .NET que usan esta definición del control común.|
|[Elemento TypeName para EntrySelectedBy para los controles de configuración (Format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que usa esta definición del control común.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomControl para los controles de configuración (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Proporciona una definición del control común.|

## <a name="remarks"></a>Observaciones

Como mínimo, cada definición debe tener al menos un tipo de .NET, conjunto de selección o condición de selección especificada. No hay ningún límite máximo para el número de tipos, conjuntos de selección o condiciones de selección que se pueden especificar.

## <a name="see-also"></a>Véase también

[Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Elemento SelectionSetName de EntrySelectedBy para controles de configuración (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento CustomEntry para CustomControl para los controles de configuración (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Elemento TypeName para EntrySelectedBy para los controles de configuración (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
