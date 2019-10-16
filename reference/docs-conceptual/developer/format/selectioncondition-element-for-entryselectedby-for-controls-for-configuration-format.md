---
title: Elemento SelectionCondition para EntrySelectedBy para controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368454"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>Elemento SelectionCondition para EntrySelectedBy for Controls for Configuration (formato)

Define una condición que debe existir para que se utilice una definición de control común. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para controles para Configuration (Format) elemento CustomEntry para CustomControl para controles de configuración (Format) elemento EntrySelectedBy para CustomEntry para controles de configuración (Format) elemento SelectionCondition para EntrySelectedBy para CustomEntry para Configuración (formato)

## <a name="syntax"></a>Sintaxis

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionCondition`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento PropertyName para SelectionCondition para los controles de configuración (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica una propiedad de .NET que desencadena la condición.|
|[Elemento ScriptBlock para SelectionCondition para los controles de configuración (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica el script que desencadena la condición.|
|[Elemento SelectionSetName de SelectionCondition para controles de configuración (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica el conjunto de tipos de .NET que desencadena la condición.|
|[Elemento TypeName para SelectionCondition para los controles de configuración (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy de CustomEntry para controles de configuración (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Define los tipos .NET que usan esta entrada de la definición de control común.|

## <a name="remarks"></a>Observaciones

Se deben seguir las siguientes directrices al definir una condición de selección:

- La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.

- La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.

Para obtener más información sobre cómo se pueden usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento PropertyName para SelectionCondition para los controles de configuración (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento ScriptBlock para SelectionCondition para los controles de configuración (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento SelectionSetName de SelectionCondition para controles de configuración (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento TypeName para SelectionCondition para los controles de configuración (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento EntrySelectedBy de CustomEntry para controles de configuración (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Escribir un archivo de formato y tipos de Windows PowerShell](./writing-a-powershell-formatting-file.md)
