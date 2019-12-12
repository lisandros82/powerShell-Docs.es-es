---
title: Elemento PropertyName para ItemSelectionCondition para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362394"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>Elemento PropertyName para ItemSelectionCondition for ListControl (formato)

Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la vista. Este elemento se utiliza al definir una vista de lista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento listent para ListControl (Format) elemento ListItems para ListEntry para ListControl (Format) ListItem Elemento para ListItems para ListControl (Format) elemento ItemSelectionCondition para ListItem para el elemento PropertyName ListControls para ItemSelectionCondition para ListControl (Format)

## <a name="syntax"></a>Sintaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `PropertyName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ItemSelectionCondition para ListItem para ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>Valor de texto

Especifique el nombre de la propiedad cuyo valor se muestra.

## <a name="remarks"></a>Observaciones

Si se usa este elemento, no se puede especificar el elemento [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) al definir la condición de selección.

## <a name="see-also"></a>Véase también

[Elemento ScriptBlock para ItemSelectionCondition para ListIControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Elemento ItemSelectionCondition para ListItem para ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
