---
title: Elemento PropertyName para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362524"
---
# <a name="propertyname-element-for-groupby-format"></a>Elemento PropertyName para GroupBy (formato)

Especifica la propiedad de .NET que inicia un nuevo grupo siempre que cambia su valor.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento de PropertyName View (Format) para GroupBy (Format)

## <a name="syntax"></a>Sintaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento GroupBy para View (Format)](./groupby-element-for-view-format.md)|Define cómo se muestra un grupo de objetos .NET.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de la propiedad .NET.

## <a name="remarks"></a>Observaciones

Windows PowerShell inicia un nuevo grupo siempre que cambia el valor de esta propiedad.

Cuando se especifica este elemento, no se puede especificar el elemento [ScriptBlock](./scriptblock-element-for-groupby-format.md) para iniciar un nuevo grupo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo iniciar un nuevo grupo cuando cambia el valor de una propiedad.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Para obtener un ejemplo de un archivo de formato completo que incluye este elemento, vea [vista ancha (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Véase también

[Elemento GroupBy para View (Format)](./groupby-element-for-view-format.md)

[Elemento ScriptBlock para GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
