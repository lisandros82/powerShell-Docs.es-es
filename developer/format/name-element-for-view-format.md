---
title: Nombre de elemento de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065077"
---
# <a name="name-element-for-view-format"></a>Elemento Name para View (formato)

Especifica el nombre que se usa para identificar la vista.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) nombre elemento (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Name` elemento. Solo un `Name` se admite el elemento para cada vista.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de vista (formato)](./view-element-format.md)|Define una vista que se usa para mostrar a los miembros de uno o varios objetos. NET.|

## <a name="text-value"></a>Valor de texto

Especifique un nombre descriptivo único para la vista. Este nombre puede incluir una referencia al tipo de la vista (por ejemplo, una vista de tabla o vista de lista), qué objeto o conjunto de objetos de utilizar la vista, ¿qué comando devuelve los objetos o una combinación de estos.

## <a name="remarks"></a>Observaciones

Para obtener más información sobre los diferentes tipos de vistas, vea los temas siguientes: [Vista de tabla](./creating-a-table-view.md), [vista de lista](./creating-a-list-view.md), [vista amplia](./creating-a-wide-view.md), y [vista personalizada](./creating-custom-controls.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra un `View` elemento que define una vista de tabla para la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto. El nombre de la vista es "servicio".

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

[Creación de una vista de lista](./creating-a-list-view.md)

[Creación de una vista de tabla](./creating-a-table-view.md)

[Creación de una vista amplia](./creating-a-wide-view.md)

[Creación de controles personalizados](./creating-custom-controls.md)

[Elemento de vista (formato)](./view-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
