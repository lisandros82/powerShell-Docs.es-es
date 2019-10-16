---
title: Elemento ScriptBlock para ItemSelectionCondition para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362104"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>Elemento ScriptBlock para ItemSelectionCondition for ListControl (formato)

Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa el elemento de lista. Este elemento se utiliza al definir una vista de lista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para ListControl (Format) elemento ListEntry para ListEntries para ListControl (Format) elemento ListItems para ListEntry para ListControl (Format) elemento ListItem para ListItems para el elemento ItemSelectionCondition del control de lista (Format) para ListItem para ListControl (Format) elemento ScriptBlock para ItemSelectionCondition para ListControl (Format)

## <a name="syntax"></a>Sintaxis

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `ScriptBlock`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ItemSelectionCondition para ListItem para ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Define la condición que debe existir para que se use este elemento de lista.|

## <a name="text-value"></a>Valor de texto

Especifique el script que se evalúa.

## <a name="remarks"></a>Observaciones

Si se usa este elemento, no se puede especificar el elemento `PropertyName` al definir la condición de selección.

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
