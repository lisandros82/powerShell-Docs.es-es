---
title: Elemento ColumnNumber para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364224"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>Elemento ColumnNumber para WideControl (formato)

Especifica el número de columnas que se muestran en la vista amplia.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento ColumnNumber para WideControl (Format)

## <a name="syntax"></a>Sintaxis

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ColumnNumber`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideControl (Format)](./widecontrol-element-format.md)|Define un formato de lista ancho (valor único) para la vista.|

## <a name="text-value"></a>Valor de texto

Especifique un valor entero positivo.

## <a name="remarks"></a>Observaciones

Al definir una vista ampliada, puede Agregar el elemento `AutoSize` o el elemento `ColumnNumber`, pero no puede Agregar ambos.

Para obtener más información sobre los componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).

Para obtener un ejemplo de una vista amplia, vea [vista ampliada (básica)](./wide-view-basic.md).

## <a name="see-also"></a>Véase también

[AutoSize (elemento) para WideControl (Format)](./autosize-element-for-widecontrol-format.md)

[Crear una vista amplia](./creating-a-wide-view.md)

[Vista amplia (básica)](./wide-view-basic.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
