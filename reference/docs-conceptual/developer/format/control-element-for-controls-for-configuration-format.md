---
title: Elemento control para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369014"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Elemento Control para Controls for Configuration (formato)

Define un control común que pueden usar todas las vistas del archivo de formato y el nombre que se usa para hacer referencia al control.

Elemento Configuration (Format) elemento Controls de Configuration (Format) elemento control para controles de configuración (Format)

## <a name="syntax"></a>Sintaxis

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Control`. Debe especificar solo uno de cada elemento secundario.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomControl para el control de los controles para la configuración (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Elemento necesario.<br /><br /> Define el control.|
|[Elemento Name del control para la configuración (Format)](./name-element-for-control-for-controls-for-configuration-format.md)|Elemento necesario.<br /><br /> Especifica el nombre usado para hacer referencia al control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Controls de Configuration (Format)](./controls-element-for-configuration-format.md)|Define los controles comunes que se pueden usar en todas las vistas del archivo de formato o en otros controles.|

## <a name="remarks"></a>Observaciones

Se puede hacer referencia al nombre dado a este control en los elementos siguientes:

- [Elemento ExpressionBinding para CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [Elemento GroupBy para View (Format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Véase también

[Elemento Controls de Configuration (Format)](./controls-element-for-configuration-format.md)

[Elemento CustomControl para el control de la configuración (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Elemento ExpressionBinding para CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento GroupBy para View (Format)](./groupby-element-for-view-format.md)

[Elemento Name del control para los controles de configuración (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
