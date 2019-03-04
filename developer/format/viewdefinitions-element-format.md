---
title: Elemento ViewDefinitions (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862091"
---
# <a name="viewdefinitions-element-format"></a>Elemento ViewDefinitions (formato)

Define las vistas que se usa para mostrar los objetos. NET. Estas vistas pueden mostrar las propiedades y valores de secuencia de comandos de un objeto en un formato de tabla, formato de lista, formato ancho y el formato de control personalizado.

Elemento de configuración (formato) del elemento ViewDefinitions (formato XML)

## <a name="syntax"></a>Sintaxis

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `ViewDefinitions` elemento. No hay ningún límite en el número de vistas que se pueden definir en un archivo de formato y se pueden agregar en cualquier orden.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de vista (formato)](./view-element-format.md)|Define una vista que se usa para mostrar uno o varios objetos. NET.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de configuración (formato)](./configuration-element-format.md)|Representa el elemento de nivel superior de un archivo de formato.|

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de los componentes de los diferentes tipos de vistas, vea los temas siguientes:

- [Creación de una vista de tabla](./creating-a-table-view.md)

- [Creación de una vista de lista](./creating-a-list-view.md)

- [Creación de una vista amplia](./creating-a-wide-view.md)

- [Controles personalizados](./creating-custom-controls.md)

## <a name="example"></a>Ejemplo

Este ejemplo se muestra un `ViewDefinitions` elemento que contiene los elementos primarios de una vista de tabla y una vista de lista.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>Véase también

[Elemento de configuración (formato)](./configuration-element-format.md)

[Elemento de vista (formato)](./view-element-format.md)

[Creación de una vista de tabla](./creating-a-table-view.md)

[Creación de una vista de lista](./creating-a-list-view.md)

[Creación de una vista amplia](./creating-a-wide-view.md)

[Controles personalizados](./creating-custom-controls.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
