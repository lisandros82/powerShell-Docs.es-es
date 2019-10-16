---
title: Control (elemento) para controles de View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363474"
---
# <a name="control-element-for-controls-for-view--format"></a>Elemento Control para Controls for View (formato)

Define un control que se puede usar en la vista y el nombre que se usa para hacer referencia al control.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Controls (Format) elemento control para controles de View (Format)

## <a name="syntax"></a>Sintaxis

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Control`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Name del control para la vista (Format)](./name-element-for-control-for-controls-for-view-format.md)|Elemento obligatorio.<br /><br /> Especifica el nombre del control.|
|[Elemento CustomControl para el control de los controles de View (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Elemento obligatorio.<br /><br /> Define el control utilizado por esta vista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Controls (elemento, Format)](./controls-element-for-view-format.md)|Define los controles de vista que se pueden usar en una vista específica.|

## <a name="remarks"></a>Observaciones

Este control se puede especificar mediante los elementos siguientes:

- [Elemento CustomControlName para ExpressionBinding para controles para View (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [Elemento CustomControlName para ExpressionBinding para CustomControl para View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [Elemento CustomControlName para ExpressionBinding para GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [Elemento CustomControlName para GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Véase también

[Elemento CustomControl para el control de los controles de View (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Elemento CustomControlName para ExpressionBinding para controles para View (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento CustomControlName para ExpressionBinding para CustomControl para View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento CustomControlName para ExpressionBinding para GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento CustomControlName para ExpressionBinding para GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Controls (elemento, Format)](./controls-element-for-view-format.md)

[Elemento Name del control para los controles de View (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
