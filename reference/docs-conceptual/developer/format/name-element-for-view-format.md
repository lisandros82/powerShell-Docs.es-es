---
title: Name (elemento) para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362644"
---
# <a name="name-element-for-view-format"></a>Elemento Name para View (formato)

Especifica el nombre que se utiliza para identificar la vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Name (Format)

## <a name="syntax"></a>Sintaxis

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Name`. Solo se permite un elemento `Name` para cada vista.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Define una vista que se usa para mostrar los miembros de uno o más objetos .NET.|

## <a name="text-value"></a>Valor de texto

Especifique un nombre descriptivo único para la vista. Este nombre puede incluir una referencia al tipo de la vista (por ejemplo, una vista de tabla o una vista de lista), qué objeto o conjunto de objetos usan la vista, qué comando devuelve los objetos o una combinación de ellos.

## <a name="remarks"></a>Observaciones

Para obtener más información sobre los diferentes tipos de vistas, vea los temas siguientes [: vista de tabla](./creating-a-table-view.md), vista de [lista](./creating-a-list-view.md), [vista ampliada](./creating-a-wide-view.md)y [vista personalizada](./creating-custom-controls.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un elemento `View` que define una vista de tabla para el objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) . El nombre de la vista es "Service".

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>Véase también

[Crear una vista de lista](./creating-a-list-view.md)

[Crear una vista de tabla](./creating-a-table-view.md)

[Crear una vista amplia](./creating-a-wide-view.md)

[Crear controles personalizados](./creating-custom-controls.md)

[Elemento View (Format)](./view-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
