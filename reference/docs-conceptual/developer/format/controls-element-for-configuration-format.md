---
title: Elemento Controls para Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369004"
---
# <a name="controls-element-for-configuration-format"></a>Elemento Controls para Configuration (formato)

Define los controles comunes que se pueden usar en todas las vistas del archivo de formato.

Elemento Configuration (Format) Controls de la configuración (Format)

## <a name="syntax"></a>Sintaxis

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Controls`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Control (elemento) para controles de configuración (Format)](./control-element-for-controls-for-configuration-format.md)|Elemento obligatorio.<br /><br /> Define un control común que pueden usar todas las vistas del archivo de formato.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Configuration (elemento, Format)](./configuration-element-format.md)|Representa el elemento de nivel superior de un archivo de formato.|

## <a name="remarks"></a>Observaciones

Puede crear cualquier número de controles comunes. Para cada control, debe especificar el nombre que se utiliza para hacer referencia al control y los componentes del control.

## <a name="see-also"></a>Véase también

[Configuration (elemento, Format)](./configuration-element-format.md)

[Control (elemento) para controles de configuración (Format)](./control-element-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
