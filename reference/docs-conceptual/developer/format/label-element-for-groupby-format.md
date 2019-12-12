---
title: Elemento Label para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365204"
---
# <a name="label-element-for-groupby-format"></a>Elemento Label para GroupBy (formato)

Especifica una etiqueta que se muestra cuando se encuentra un nuevo grupo.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy para el elemento Label (Format) para GroupBy (Format)

## <a name="syntax"></a>Sintaxis

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Label`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento GroupBy para View (Format)](./groupby-element-for-view-format.md)|Define cómo se muestra un nuevo grupo de objetos.|

## <a name="text-value"></a>Valor de texto

Especifique el texto que se muestra cuando Windows PowerShell encuentra un nuevo valor de propiedad o script.

## <a name="remarks"></a>Observaciones

Además del texto especificado por este elemento, Windows PowerShell muestra el nuevo valor que inicia el grupo y agrega una línea en blanco antes y después del grupo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la etiqueta de un nuevo grupo. La etiqueta mostrada tendría un aspecto similar al siguiente: `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Para obtener un ejemplo de un archivo de formato completo que incluye este elemento, vea [vista ancha (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Véase también

[Elemento GroupBy para View (Format)](./groupby-element-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
