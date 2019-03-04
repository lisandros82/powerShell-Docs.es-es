---
title: Nombre de elemento de Control para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862391"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Elemento Name para Control for Controls for Configuration (formato)

Especifica el nombre del control.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento de configuración (formato) controla elemento del Control de elemento (formato) para los controles de vista (formato) nombre del elemento para el Control de vista (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Name` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de control para los controles de vista (formato)](./control-element-for-controls-for-view-format.md)|Define un control que puede usar la vista y el nombre que se usa para hacer referencia al control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre que se usa para hacer referencia al control.

## <a name="remarks"></a>Observaciones

El nombre especificado aquí se puede usar en los siguientes elementos para hacer referencia a este control.

- Al crear una tabla, lista, vista de control personalizado o amplia, se puede especificar el control con el siguiente elemento: [Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)

- Al crear otro control que se puede usar una vista, este control puede especificarse con el siguiente elemento: [Elemento ExpressionBinding para CustomItem para los controles de vista (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Véase también

[Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)

[Elemento ExpressionBinding para CustomItem para los controles de vista (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento de control para los controles de vista (formato)](./control-element-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
