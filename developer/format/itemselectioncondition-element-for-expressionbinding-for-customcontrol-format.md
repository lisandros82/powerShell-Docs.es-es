---
title: Elemento ItemSelectionCondition para ExpressionBinding para el control personalizado (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065838"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>Elemento ItemSelectionCondition para ExpressionBinding for CustomControl (formato)

Define la condición que debe existir para que este control que se usará. No hay ningún límite al número de condiciones de selección que se pueden especificar para un elemento de control. Este elemento se usa al definir una vista de control personalizado.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries de vista (formato) del elemento CustomItem para CustomEntry de vista (formato) del elemento ExpressionBinding para CustomItem para el control personalizado de vista (formato) ItemSelectionCondition del elemento de enlace de expresión para el control personalizado de vista (formato)

## <a name="syntax"></a>Sintaxis

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ItemSelectionCondition` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento PropertyName para ItemSelectionCondition para el control personalizado para (formato de vista](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET que desencadena la condición.|
|[Elemento de bloque de script para ItemSelectionCondition para el control personalizado para la vista (formato)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica la secuencia de comandos que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem para el control personalizado para la vista (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Define los datos que se muestran el control.|

## <a name="remarks"></a>Observaciones

Puede especificar un nombre de propiedad o un script para esta condición, pero no se pueden especificar ambos.

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)

[Elemento ExpressionBinding para CustomItem para el control personalizado para la vista (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
