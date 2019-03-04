---
title: Elemento CustomControlName para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860311"
---
# <a name="customcontrolname-element-for-groupby-format"></a>Elemento CustomControlName para GroupBy (formato)

Especifica el nombre de un control personalizado que se usa para mostrar el grupo nuevo. Este elemento se usa al definir una tabla, lista, vista de control personalizado o anchos.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de vista (formato) del elemento CustomControlName de GroupBy (formato)

## <a name="syntax"></a>Sintaxis

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elementos primarios de la `CustomControlName` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)|Define cómo Windows PowerShell muestra un nuevo grupo de objetos.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del control personalizado que se usa para mostrar un nuevo grupo.

## <a name="remarks"></a>Observaciones

Puede crear controles comunes que pueden usarse en todas las vistas de un archivo de formato, y puede crear controles de vista que se pueden utilizar una vista específica. Los siguientes elementos especifican los nombres de estos controles personalizados:

- [Elemento Name de Control para los controles de configuración (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name de Control para los controles de vista (formato)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Véase también

[Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)

[Elemento Name de Control para los controles de configuración (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name de Control para los controles de vista (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
