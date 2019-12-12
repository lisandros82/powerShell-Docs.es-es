---
title: Elemento CustomControlName para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368884"
---
# <a name="customcontrolname-element-for-groupby-format"></a>Elemento CustomControlName para GroupBy (formato)

Especifica el nombre de un control personalizado que se usa para mostrar el nuevo grupo. Este elemento se utiliza al definir una vista de control de tabla, lista, ancho o personalizado.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy para el elemento View (Format) CustomControlName de GroupBy (Format)

## <a name="syntax"></a>Sintaxis

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `CustomControlName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento GroupBy para View (Format)](./groupby-element-for-view-format.md)|Define cómo Windows PowerShell muestra un nuevo grupo de objetos.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del control personalizado que se usa para mostrar un nuevo grupo.

## <a name="remarks"></a>Observaciones

Puede crear controles comunes que se pueden usar en todas las vistas de un archivo de formato, y puede crear controles de vista que se pueden usar en una vista específica. Los elementos siguientes especifican los nombres de estos controles personalizados:

- [Elemento Name del control para los controles de configuración (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name del control para los controles de View (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Véase también

[Elemento GroupBy para View (Format)](./groupby-element-for-view-format.md)

[Elemento Name del control para los controles de configuración (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name del control para los controles de View (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
