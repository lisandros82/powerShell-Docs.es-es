---
title: Controla el elemento de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861181"
---
# <a name="controls-element-for-configuration-format"></a>Elemento Controls para Configuration (formato)

Define los controles comunes que pueden usarse en todas las vistas del archivo de formato.

Elemento de controles de configuración (formato) del elemento de configuración (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Controls` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de control para los controles de configuración (formato)](./control-element-for-controls-for-configuration-format.md)|Elemento necesario.<br /><br /> Define un control común que puede usarse en todas las vistas del archivo de formato.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de configuración (formato)](./configuration-element-format.md)|Representa el elemento de nivel superior de un archivo de formato.|

## <a name="remarks"></a>Observaciones

Puede crear cualquier número de controles comunes. Para cada control, debe especificar el nombre que se usa para hacer referencia el control y los componentes del control.

## <a name="see-also"></a>Véase también

[Elemento de configuración (formato)](./configuration-element-format.md)

[Elemento de control para los controles de configuración (formato)](./control-element-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
