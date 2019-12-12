---
title: Elemento Name del control para los controles de la vista (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365104"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Elemento Name para Control for Controls for Configuration (formato)

Especifica el nombre del control.

Elemento Configuration (Format) elemento ViewDefinitions (formato) elemento de vista (Format) elemento Controls (Format) elemento control para controles para el elemento Name de View (Format) para control para View (Format)

## <a name="syntax"></a>Sintaxis

```xml
<Name>ControlName</Name>
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
|[Control (elemento) para controles de View (Format)](./control-element-for-controls-for-view-format.md)|Define un control que se puede usar en la vista y el nombre que se usa para hacer referencia al control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre que se utiliza para hacer referencia al control.

## <a name="remarks"></a>Observaciones

El nombre especificado aquí se puede usar en los elementos siguientes para hacer referencia a este control.

- Al crear una tabla, lista, vista de control amplia o personalizada, el control puede especificarse mediante el elemento siguiente: [GroupBy (elemento) para View (Format)](./groupby-element-for-view-format.md)

- Al crear otro control que puede ser utilizado por una vista, este control se puede especificar mediante el elemento siguiente: [ExpressionBinding para CustomItem para los controles de View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Véase también

[Elemento GroupBy para View (Format)](./groupby-element-for-view-format.md)

[Elemento ExpressionBinding para CustomItem para controles para View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Control (elemento) para controles de View (Format)](./control-element-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
