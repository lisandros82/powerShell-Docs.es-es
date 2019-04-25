---
title: Elemento de bloque de script para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064516"
---
# <a name="scriptblock-element-for-groupby-format"></a>Elemento ScriptBlock para GroupBy (formato)

Especifica la secuencia de comandos que se inicia un nuevo grupo cada vez que cambia su valor.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de configuración (formato) de la vista de elemento de bloque de script para GroupBy (formato)

## <a name="syntax"></a>Sintaxis

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)|Define cómo se muestra un grupo de objetos. NET.|

## <a name="text-value"></a>Valor de texto

Especifique el script que se evalúa.

## <a name="remarks"></a>Observaciones

Windows PowerShell se inicia un nuevo grupo cada vez que cambia el valor de esta secuencia de comandos.

Cuando se especifica este elemento, no puede especificar el [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) elemento para iniciar un nuevo grupo.

## <a name="see-also"></a>Véase también

[Elemento PropertyName para GroupBy (formato)](./propertyname-element-for-groupby-format.md)

[Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
