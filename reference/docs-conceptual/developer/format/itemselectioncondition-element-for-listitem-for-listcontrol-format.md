---
title: Elemento ItemSelectionCondition para ListItem para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365194"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>Elemento ItemSelectionCondition para ListItem for ListControl (formato)

Define la condición que debe existir para que se use este elemento de lista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para ListControl (Format) elemento ListEntry para ListEntries para ListControl (Format) elemento ListItems para ListEntry para ListControl (Format) elemento ListItem para ListItems para ListControl (Format) elemento ItemSelectionCondition para ListItem para ListControl (Format)

## <a name="syntax"></a>Sintaxis

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ItemSelectionCondition`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento PropertyName para ItemSelectionCondition para ListControl (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET que desencadena la condición.|
|[Elemento ScriptBlock para ItemSelectionCondition para ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica el script que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ListItem para ListItems para ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.|

## <a name="remarks"></a>Observaciones

Puede especificar un nombre de propiedad o un script para esta condición, pero no puede especificar ambos.

## <a name="see-also"></a>Véase también

[Elemento ListItem para ListItems para ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Elemento PropertyName para ItemSelectionCondition para ListControl (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[Elemento ScriptBlock para ItemSelectionCondition para ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
