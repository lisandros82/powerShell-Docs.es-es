---
title: Elemento de control para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066777"
---
# <a name="control-element-for-controls-for-view--format"></a>Elemento Control para Controls for View (formato)

Define un control que puede usar la vista y el nombre que se usa para hacer referencia al control.

Elemento de vista de configuración (formato) del elemento elemento ViewDefinitions (formato) (formato) controla el elemento de Control de elemento (formato) para los controles de vista (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Control` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Nombre de elemento para el Control de vista (formato)](./name-element-for-control-for-controls-for-view-format.md)|Elemento necesario.<br /><br /> Especifica el nombre del control.|
|[Elemento de control personalizado para el Control para los controles de vista (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Elemento necesario.<br /><br /> Define el control utilizado por esta vista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Controls (elemento) (formato)](./controls-element-for-view-format.md)|Define los controles de vista que se pueden utilizar una vista específica.|

## <a name="remarks"></a>Observaciones

Este control se puede especificar mediante los siguientes elementos:

- [Elemento CustomControlName para ExpressionBinding para los controles de vista (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [Elemento CustomControlName para ExpressionBinding para el control personalizado para la vista (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [Elemento CustomControlName para ExpressionBinding para GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [Elemento CustomControlName para GroupBy (formato)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Véase también

[Elemento de control personalizado para el Control para los controles de vista (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Elemento CustomControlName para ExpressionBinding para los controles de vista (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento CustomControlName para ExpressionBinding para el control personalizado para la vista (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento CustomControlName para ExpressionBinding para GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento CustomControlName para ExpressionBinding para GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Controls (elemento) (formato)](./controls-element-for-view-format.md)

[Elemento Name de Control para los controles de vista (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
