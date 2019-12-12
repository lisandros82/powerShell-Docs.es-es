---
title: Elemento Name del control para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362714"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Elemento Name para Control for Controls for Configuration (formato)

Especifica el nombre del control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento de nombre para el control de los controles para la configuración (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Name`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Control (elemento) para controles de configuración (Format)](./control-element-for-controls-for-configuration-format.md)|Define un control común que pueden usar todas las vistas del archivo de formato y el nombre que se usa para hacer referencia al control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre que se utiliza para hacer referencia a este control.

## <a name="remarks"></a>Observaciones

El nombre especificado aquí se puede usar en los elementos siguientes para hacer referencia a este control.

- Al crear una tabla, lista, vista de control amplia o personalizada, el control puede especificarse mediante el elemento siguiente: [GroupBy (elemento) para View (Format)](./groupby-element-for-view-format.md)

- Al crear otro control común, este control se puede especificar mediante el elemento siguiente: [elemento ExpressionBinding de CustomItem para controles de configuración (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- Al crear un control que se puede usar en una vista, este control se puede especificar mediante el elemento siguiente: [ExpressionBinding para CustomItem para los controles de View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Véase también

[Control (elemento) para controles de configuración (Format)](./control-element-for-controls-for-configuration-format.md)

[Elemento ExpressionBinding de CustomItem para controles de configuración (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento ExpressionBinding para CustomItem para controles para View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento GroupBy para View (Format)](./groupby-element-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
