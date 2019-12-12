---
title: Elemento WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367994"
---
# <a name="widecontrol-element-format"></a>Elemento WideControl (formato)

Define un formato de lista ancho (valor único) para la vista. Esta vista muestra un valor de propiedad único o un valor de script para cada objeto.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format)

## <a name="syntax"></a>Sintaxis

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `WideControl`. No se pueden especificar los elementos `AutoSize` y `ColumnNumber` al mismo tiempo.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[AutoSize (elemento) para WideControl (Format)](./autosize-element-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica si el tamaño de la columna y el número de columnas se ajustan en función del tamaño de los datos.|
|[Elemento ColumnNumber para WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica el número de columnas que se muestran en la vista amplia.|
|[Elemento WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)|Elemento necesario.<br /><br /> Proporciona las definiciones de la vista amplia.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Define una vista que se usa para mostrar uno o más objetos .NET.|

## <a name="remarks"></a>Observaciones

Al definir una vista ampliada, puede Agregar el elemento `AutoSize` o el `ColumnNumber`, pero no puede Agregar ambos.

En la mayoría de los casos, solo se requiere una definición para cada vista amplia, pero es posible tener varias definiciones si se desea usar la misma vista para mostrar diferentes objetos .NET. En esos casos, puede proporcionar una definición independiente para cada objeto o conjunto de objetos.

Para obtener más información sobre los componentes de una vista amplia, vea [componentes de vista ancha](./creating-a-wide-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un elemento `WideControl` que se usa para mostrar una propiedad del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

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

Para obtener un ejemplo completo de una vista amplia, vea [vista ampliada (básica)](./wide-view-basic.md).

## <a name="see-also"></a>Véase también

[AutoSize (elemento) para WideControl (Format)](./autosize-element-for-widecontrol-format.md)

[Elemento ColumnNumber para WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)

[Elemento View (Format)](./view-element-format.md)

[Elemento WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)

[Vista amplia (básica)](./wide-view-basic.md)

[Crear una vista amplia](./creating-a-wide-view.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
