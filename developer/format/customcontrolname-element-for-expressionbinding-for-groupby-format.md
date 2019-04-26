---
title: Elemento CustomControlName para ExpressionBinding para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066579"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>Elemento CustomControlName para ExpressionBinding for GroupBy (formato)

Especifica el nombre de un control común o un control de vista. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) CustomItem para CustomEntry para GroupBy (formato) (elemento) ExpressionBinding para CustomItem para GroupBy (formato) (elemento) CustomControlName para ExpressionBinding para GroupBy (formato)

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
|[Elemento ExpressionBinding para CustomItem para GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Define los datos que se muestran el control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del control.

## <a name="remarks"></a>Observaciones

Puede crear controles comunes que pueden usarse en todas las vistas de un archivo de formato, y puede crear controles de vista que se pueden utilizar una vista específica. Los siguientes elementos especifican los nombres de estos controles:

- [Elemento Name de Control para los controles de configuración (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name de Control para los controles de vista (formato)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Véase también

[Elemento Name de Control para los controles de configuración (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name de Control para los controles de vista (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento ExpressionBinding para CustomItem para GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
