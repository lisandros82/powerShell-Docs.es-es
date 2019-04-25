---
title: Elemento ColumnNumber para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066913"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>Elemento ColumnNumber para WideControl (formato)

Especifica el número de columnas mostradas en la vista ampliada.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) ColumnNumber elemento de configuración WideControl (formato)

## <a name="syntax"></a>Sintaxis

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ColumnNumber` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideControl (formato)](./widecontrol-element-format.md)|Define una amplia (valor single) formato de lista para la vista.|

## <a name="text-value"></a>Valor de texto

Especifique un valor entero positivo.

## <a name="remarks"></a>Observaciones

Al definir una vista amplia, puede agregar el `AutoSize` elemento o el `ColumnNumber` elemento, pero no se puede agregar ambos.

Para obtener más información acerca de los componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).

Para obtener un ejemplo de una vista amplia, consulte [vista amplia (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Véase también

[Elemento AutoSize para WideControl (formato)](./autosize-element-for-widecontrol-format.md)

[Creación de una vista amplia](./creating-a-wide-view.md)

[Vista amplia (Basic)](./wide-view-basic.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
