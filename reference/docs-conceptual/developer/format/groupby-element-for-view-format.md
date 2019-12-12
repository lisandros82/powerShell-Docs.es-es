---
title: Elemento GroupBy para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363634"
---
# <a name="groupby-element-for-view-format"></a>Elemento GroupBy para View (formato)

Define cómo se muestra un nuevo grupo de objetos. Este elemento se utiliza al definir una vista de control de tabla, lista, ancho o personalizado.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy para View (Format)

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

En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomControl para GroupBy (Format)](./customcontrol-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Define el control personalizado que muestra los nuevos grupos.|
|[Elemento CustomControlName para GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica el nombre de un control que se usa para mostrar el nuevo grupo.|
|[Elemento Label para GroupBy (Format)](./label-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica una etiqueta que se muestra cuando se encuentra un nuevo grupo.|
|[Elemento PropertyName para GroupBy (Format)](./propertyname-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET que inicia un nuevo grupo cada vez que cambia su valor.|
|[Elemento ScriptBlock para GroupBy (Format)](./scriptblock-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica el script que inicia un nuevo grupo siempre que cambia su valor.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Define una vista que muestra uno o más objetos .NET.|

## <a name="remarks"></a>Observaciones

Al definir cómo se muestra un nuevo grupo de objetos, debe especificar la propiedad o el script que iniciará el nuevo grupo. sin embargo, no puede especificar ambos.

## <a name="see-also"></a>Véase también

[Elemento CustomControlName para GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

[Elemento Label para GroupBy (Format)](./label-element-for-groupby-format.md)

[Elemento PropertyName para GroupBy (Format)](./propertyname-element-for-groupby-format.md)

[Elemento ScriptBlock para GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[Elemento View (Format)](./view-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
