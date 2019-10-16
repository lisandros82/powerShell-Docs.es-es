---
title: Elemento TypeName para SelectionCondition para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361484"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a>Elemento TypeName para SelectionCondition for GroupBy (formato)

Especifica un tipo .NET que desencadena la condición. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento EntrySelectedBy para CustomEntry para GroupBy (Format) elemento SelectionCondition para EntrySelectedBy para GroupBy (Format) elemento TypeName para SelectionCondition para GroupBy (Format)

## <a name="syntax"></a>Sintaxis

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Define una condición que debe existir para que se use la definición de control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observaciones

Cuando se especifica este elemento, no se puede especificar el elemento `SelectionSetName`. Para obtener más información sobre cómo definir condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
