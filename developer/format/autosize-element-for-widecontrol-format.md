---
title: Elemento AutoSize para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857091"
---
# <a name="autosize-element-for-widecontrol-format"></a>Elemento AutoSize para WideControl (formato)

Especifica si el tamaño de columna y el número de columnas se ajustan en función del tamaño de los datos.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) Autosize elemento de configuración WideControl (formato)

## <a name="syntax"></a>Sintaxis

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `AutoSize` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguno

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideControl (formato)](./widecontrol-element-format.md)|Define una amplia (valor single) formato de lista para la vista.|

## <a name="remarks"></a>Observaciones

Al definir una vista amplia, puede agregar el `AutoSize` elemento o el [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) elemento, pero no se puede agregar ambos.

Para obtener más información acerca de los componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).

Para obtener un ejemplo de una vista amplia, consulte [vista amplia (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Véase también

[Elemento ColumnNumber para WideControl (formato)](./columnnumber-element-for-widecontrol-format.md)

[Creación de una vista amplia](./creating-a-wide-view.md)

[Elemento WideControl (formato)](./widecontrol-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
