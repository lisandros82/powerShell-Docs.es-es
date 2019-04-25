---
title: Elemento PropertyName para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075875"
---
# <a name="propertyname-element-for-groupby-format"></a>Elemento PropertyName para GroupBy (formato)

Especifica la propiedad de .NET que se inicia un nuevo grupo cada vez que cambia su valor.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de vista (formato) del elemento PropertyName para GroupBy (formato)

## <a name="syntax"></a>Sintaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `PropertyName` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)|Define cómo se muestra un grupo de objetos. NET.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de propiedad. NET.

## <a name="remarks"></a>Observaciones

Windows PowerShell se inicia un nuevo grupo cada vez que cambia el valor de esta propiedad.

Cuando se especifica este elemento, no puede especificar el [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento para iniciar un nuevo grupo.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo iniciar un nuevo grupo cuando cambia el valor de una propiedad.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Para obtener un ejemplo de un archivo de formato completo que incluye este elemento, vea [vista amplia (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Véase también

[Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)

[Elemento de bloque de script para GroupBy (formato)](./scriptblock-element-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
