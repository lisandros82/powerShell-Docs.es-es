---
title: Elemento de control para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858891"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Elemento Control para Controls for Configuration (formato)

Define un control común que puede usarse en todas las vistas del archivo de formato y el nombre que se usa para hacer referencia al control.

Elemento de configuración elemento (formato de) los controles de elemento de Control de configuración (formato) para los controles de configuración (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario para el `Control` elemento. Debe especificar solo uno de cada elemento secundario.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de control personalizado para el Control para los controles de configuración (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Elemento necesario.<br /><br /> Define el control.|
|[Elemento Name de Control para la configuración (formato)](./name-element-for-control-for-controls-for-configuration-format.md)|Elemento necesario.<br /><br /> Especifica el nombre usado para hacer referencia al control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Los controles elemento de configuración (formato)](./controls-element-for-configuration-format.md)|Define los controles comunes que pueden usarse por todas las vistas del archivo de formato o por otros controles.|

## <a name="remarks"></a>Observaciones

El nombre asignado a este control puede hacer referencia a los siguientes elementos:

- [Elemento ExpressionBinding para CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [Elemento GroupBy para View(Format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Véase también

[Los controles elemento de configuración (formato)](./controls-element-for-configuration-format.md)

[Elemento de control personalizado para el Control de configuración (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Elemento ExpressionBinding para CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento GroupBy para View(Format)](./groupby-element-for-view-format.md)

[Elemento Name de Control para los controles de configuración (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
