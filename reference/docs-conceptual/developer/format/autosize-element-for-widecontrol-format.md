---
title: AutoSize (elemento) para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369054"
---
# <a name="autosize-element-for-widecontrol-format"></a>Elemento AutoSize para WideControl (formato)

Especifica si el tamaño de la columna y el número de columnas se ajustan en función del tamaño de los datos.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) AutoSize para WideControl (Format)

## <a name="syntax"></a>Sintaxis

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `AutoSize`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguno

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideControl (Format)](./widecontrol-element-format.md)|Define un formato de lista ancho (valor único) para la vista.|

## <a name="remarks"></a>Observaciones

Al definir una vista ampliada, puede Agregar el elemento `AutoSize` o el elemento [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) , pero no puede Agregar ambos.

Para obtener más información sobre los componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).

Para obtener un ejemplo de una vista amplia, vea [vista ampliada (básica)](./wide-view-basic.md).

## <a name="see-also"></a>Véase también

[Elemento ColumnNumber para WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)

[Crear una vista amplia](./creating-a-wide-view.md)

[Elemento WideControl (Format)](./widecontrol-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
