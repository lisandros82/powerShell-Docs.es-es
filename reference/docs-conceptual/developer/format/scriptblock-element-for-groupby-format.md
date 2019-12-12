---
title: Elemento ScriptBlock para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364934"
---
# <a name="scriptblock-element-for-groupby-format"></a>Elemento ScriptBlock para GroupBy (formato)

Especifica el script que inicia un nuevo grupo siempre que cambia su valor.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento de elemento ScriptBlock de View (Format) para GroupBy (Format)

## <a name="syntax"></a>Sintaxis

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento GroupBy para View (Format)](./groupby-element-for-view-format.md)|Define cómo se muestra un grupo de objetos .NET.|

## <a name="text-value"></a>Valor de texto

Especifique el script que se evalúa.

## <a name="remarks"></a>Observaciones

PowerShell inicia un nuevo grupo siempre que cambia el valor de este script.

Cuando se especifica este elemento, no se puede especificar el elemento [PropertyName](propertyname-element-for-groupby-format.md) para iniciar un nuevo grupo.

## <a name="see-also"></a>Véase también

[Elemento PropertyName para GroupBy (Format)](propertyname-element-for-groupby-format.md)

[Elemento GroupBy para View (Format)](groupby-element-for-view-format.md)

[Escribir un archivo de formato de PowerShell](writing-a-powershell-formatting-file.md)
