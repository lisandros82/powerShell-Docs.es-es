---
title: Nombre de elemento de Control para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065196"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Elemento Name para Control for Controls for Configuration (formato)

Especifica el nombre del control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

Elemento de configuración elemento (formato de) los controles de elemento de Control de configuración (formato) para los controles de elemento de nombre de configuración (formato) para el Control para los controles de configuración (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Name>NameOfControl</Name>

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
|[Elemento de control para los controles de configuración (formato)](./control-element-for-controls-for-configuration-format.md)|Define un control común que puede usarse en todas las vistas del archivo de formato y el nombre que se usa para hacer referencia al control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre que se usa para hacer referencia a este control.

## <a name="remarks"></a>Observaciones

El nombre especificado aquí se puede usar en los siguientes elementos para hacer referencia a este control.

- Al crear una tabla, lista, vista de control personalizado o amplia, se puede especificar el control con el siguiente elemento: [Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)

- Cuando se crea otro control comunes, este control se puede especificar con el siguiente elemento: [Elemento ExpressionBinding para CustomItem para los controles de configuración (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- Al crear un control que se puede usar una vista, este control puede especificarse con el siguiente elemento: [Elemento ExpressionBinding para CustomItem para los controles de vista (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Véase también

[Elemento de control para los controles de configuración (formato)](./control-element-for-controls-for-configuration-format.md)

[Elemento ExpressionBinding para CustomItem para los controles de configuración (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento ExpressionBinding para CustomItem para los controles de vista (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
