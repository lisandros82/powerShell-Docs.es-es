---
title: Etiqueta de elemento de GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065417"
---
# <a name="label-element-for-groupby-format"></a>Elemento Label para GroupBy (formato)

Especifica una etiqueta que se muestra cuando se encuentra un nuevo grupo.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de configuración (formato) de la vista elemento de etiqueta para GroupBy (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `Label` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)|Define cómo se muestra un nuevo grupo de objetos.|

## <a name="text-value"></a>Valor de texto

Especifique el texto que se muestra cada vez que Windows PowerShell que se encuentra una nueva propiedad o valor de la secuencia de comandos.

## <a name="remarks"></a>Observaciones

Además del texto especificado por este elemento, Windows PowerShell muestra el nuevo valor que se inicia el grupo y agrega una línea en blanco antes y después del grupo.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra la etiqueta para un nuevo grupo. La etiqueta que aparece tendría un aspecto similar al siguiente: `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Para obtener un ejemplo de un archivo de formato completo que incluye este elemento, vea [vista amplia (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Véase también

[Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
