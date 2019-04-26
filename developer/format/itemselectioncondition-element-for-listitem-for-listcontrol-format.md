---
title: Elemento ItemSelectionCondition para ListItem para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065451"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>Elemento ItemSelectionCondition para ListItem for ListControl (formato)

Define la condición que debe cumplirse para que este elemento de lista para usarse.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento de configuración (elemento) ListEntry ListControl (formato) para ListEntries elemento ListItems de ListControl (formato) para ListEntry elemento de ListItem ListControl (formato) para ListItems de ListControl (formato) ItemSelectionCondition elemento para ListItem para ListControl (formato)

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
|[Elemento PropertyName para ItemSelectionCondition de ListControl (formato)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET que desencadena la condición.|
|[Elemento de bloque de script para ItemSelectionCondition de ListControl (formato)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica la secuencia de comandos que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[ListItem (elemento) para ListItems de ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.|

## <a name="remarks"></a>Observaciones

Puede especificar un nombre de propiedad o un script para esta condición, pero no se pueden especificar ambos.

## <a name="see-also"></a>Véase también

[ListItem (elemento) para ListItems de ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Elemento PropertyName para ItemSelectionCondition de ListControl (formato)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[Elemento de bloque de script para ItemSelectionCondition de ListControl (formato)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
