---
title: Elemento CustomControlName para ExpressionBinding para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066624"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>Elemento CustomControlName para ExpressionBinding for CustomControl for View (formato)

Especifica el nombre de un control común o un control de vista. Este elemento se usa al definir una vista de control personalizado.

Configuración (formato) elemento ViewDefinitions (formato) Vista (formato) del elemento control personalizado elemento de vista (formato) del elemento CustomEntries para el control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para CustomItem vista (formato) Elemento para CustomEntry de vista (formato) del elemento ExpressionBinding CustomItem (formato) CustomControlName elemento de enlace de expresiones para CustomItem (formato)

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
|[Elemento ExpressionBinding para CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Define los datos que se muestran el control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del control.

## <a name="remarks"></a>Observaciones

Puede crear controles comunes que pueden usarse en todas las vistas de un archivo de formato y puede crear controles de vista que se pueden utilizar una vista específica. Los nombres de estos controles se especifican mediante los siguientes elementos.

- [Elemento Name de Control para los controles de configuración (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name de Control para los controles de vista (formato)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Véase también

[Elemento Name de Control para los controles de configuración (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name de Control para los controles de vista (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento ExpressionBinding para CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
