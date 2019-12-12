---
title: Elemento CustomControlName para ExpressionBinding para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368914"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>Elemento CustomControlName para ExpressionBinding for GroupBy (formato)

Especifica el nombre de un control común o un control de vista. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento CustomItem para CustomEntry para el elemento ExpressionBinding GroupBy (Format) para CustomItem para GroupBy (Format) CustomControlName para ExpressionBinding para GroupBy (Format)

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
|[Elemento ExpressionBinding para CustomItem para GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Define los datos que muestra el control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del control.

## <a name="remarks"></a>Observaciones

Puede crear controles comunes que se pueden usar en todas las vistas de un archivo de formato, y puede crear controles de vista que se pueden usar en una vista específica. Los elementos siguientes especifican los nombres de estos controles:

- [Elemento Name del control para los controles de configuración (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name del control para los controles de View (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Véase también

[Elemento Name del control para los controles de configuración (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name del control para los controles de View (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento ExpressionBinding para CustomItem para GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
