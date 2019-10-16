---
title: Elemento CustomControlName para ExpressionBinding para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369154"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>Elemento CustomControlName para ExpressionBinding for Controls for View (formato)

Especifica el nombre de un control común o un control de vista. Este elemento se utiliza al definir controles que se pueden usar en una vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento CustomItem View (Format) para CustomEntry para los controles del elemento ExpressionBinding View (Format) para CustomItem para los controles de View (Format) CustomControlName Elemento para ExpressionBindine para los controles de View (Format)

## <a name="syntax"></a>Sintaxis

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomControlName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem para controles para View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Define los datos que muestra el control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del control.

## <a name="remarks"></a>Observaciones

Puede crear controles comunes que se pueden usar en todas las vistas de un archivo de formato, y puede crear controles de vista que se pueden usar en una vista específica. Los elementos siguientes especifican los nombres de estos controles:

- [Elemento Name del control para los controles de configuración (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name del control para los controles de View (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Véase también

[Elemento Name del control para los controles de configuración (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name del control para los controles de View (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento ExpressionBinding para CustomItem para controles para View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
