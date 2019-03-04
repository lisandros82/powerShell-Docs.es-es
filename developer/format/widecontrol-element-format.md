---
title: Elemento WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859831"
---
# <a name="widecontrol-element-format"></a>Elemento WideControl (formato)

Define una amplia (valor single) formato de lista para la vista. Esta vista muestra un solo valor de propiedad o valor de la secuencia de comandos para cada objeto.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) WideControl elemento (formato)

## <a name="syntax"></a>Sintaxis

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `WideControl` elemento. No puede especificar el `AutoSize` y `ColumnNumber` elementos al mismo tiempo.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento AutoSize para WideControl (formato)](./autosize-element-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica si el tamaño de columna y el número de columnas se ajustan en función del tamaño de los datos.|
|[Elemento ColumnNumber para WideControl (formato)](./columnnumber-element-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica el número de columnas mostradas en la vista ampliada.|
|[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)|Elemento necesario.<br /><br /> Proporciona las definiciones de la vista ampliada.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de vista (formato)](./view-element-format.md)|Define una vista que se usa para mostrar uno o varios objetos. NET.|

## <a name="remarks"></a>Observaciones

Al definir una vista amplia, puede agregar el `AutoSize` elemento o el `ColumnNumber` pero no se puede agregar ambos.

En la mayoría de los casos, solo una definición es necesaria para cada vista amplia, pero es posible tener varias definiciones si desea usar la misma vista para mostrar diferentes objetos. NET. En esos casos, puede proporcionar una definición independiente para cada objeto o conjunto de objetos.

Para obtener más información acerca de los componentes de una vista amplia, consulte [los componentes de vista amplia](./creating-a-wide-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra un `WideControl` elemento que se usa para mostrar una propiedad de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

Para obtener un ejemplo completo de una vista amplia, consulte [vista amplia (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Véase también

[Elemento AutoSize para WideControl (formato)](./autosize-element-for-widecontrol-format.md)

[Elemento ColumnNumber para WideControl (formato)](./columnnumber-element-for-widecontrol-format.md)

[Elemento de vista (formato)](./view-element-format.md)

[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)

[Vista amplia (Basic)](./wide-view-basic.md)

[Creación de una vista amplia](./creating-a-wide-view.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
