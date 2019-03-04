---
title: Elemento GroupBy para vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859531"
---
# <a name="groupby-element-for-view-format"></a>Elemento GroupBy para View (formato)

Define cómo se muestra un nuevo grupo de objetos. Este elemento se usa al definir una tabla, lista, vista de control personalizado o anchos.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de vista (formato)

## <a name="syntax"></a>Sintaxis

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las siguientes secciones describen los atributos, elementos secundarios y elementos primarios.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de control personalizado para GroupBy (formato)](./customcontrol-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Define el control personalizado que se muestran los nuevos grupos.|
|[Elemento CustomControlName para GroupBy (formato)](./customcontrolname-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica el nombre de un control que se usa para mostrar el nuevo grupo.|
|[Elemento de etiqueta para GroupBy (formato)](./label-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica una etiqueta que se muestra cuando se encuentra un nuevo grupo.|
|[Elemento PropertyName para GroupBy (formato)](./propertyname-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET en el se inicia un nuevo grupo cada vez que cambia su valor.|
|[Elemento de bloque de script para GroupBy (formato)](./scriptblock-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica la secuencia de comandos que se inicia un nuevo grupo cada vez que cambia su valor.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de vista (formato)](./view-element-format.md)|Define una vista que muestra uno o varios objetos. NET.|

## <a name="remarks"></a>Observaciones

Al definir cómo se muestra un nuevo grupo de objetos, debe especificar la propiedad o el script que se iniciará el nuevo grupo; Sin embargo, no se puede especificar ambos.

## <a name="see-also"></a>Véase también

[Elemento CustomControlName para GroupBy (formato)](./customcontrolname-element-for-groupby-format.md)

[Elemento de etiqueta para GroupBy (formato)](./label-element-for-groupby-format.md)

[Elemento PropertyName para GroupBy (formato)](./propertyname-element-for-groupby-format.md)

[Elemento de bloque de script para GroupBy (formato)](./scriptblock-element-for-groupby-format.md)

[Elemento de vista (formato)](./view-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
