---
title: Elemento CustomControlName para ExpressionBinding para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066658"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>Elemento CustomControlName para ExpressionBinding for Controls for View (formato)

Especifica el nombre de un control común o un control de vista. Este elemento se usa al definir los controles que pueden usarse en una vista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para los controles de elemento de vista (formato) CustomItem para CustomEntry para los controles de elemento de vista (formato) ExpressionBinding para CustomItem para los controles de vista (formato) CustomControlName Elemento para ExpressionBindine para los controles de vista (formato)

## <a name="syntax"></a>Sintaxis

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomControlName` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem para los controles de vista (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Define los datos que se muestran el control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del control.

## <a name="remarks"></a>Observaciones

Puede crear controles comunes que pueden usarse en todas las vistas de un archivo de formato, y puede crear controles de vista que se pueden utilizar una vista específica. Los siguientes elementos especifican los nombres de estos controles:

- [Elemento Name de Control para los controles de configuración (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name de Control para los controles de vista (formato)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Véase también

[Elemento Name de Control para los controles de configuración (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name de Control para los controles de vista (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento ExpressionBinding para CustomItem para los controles de vista (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
