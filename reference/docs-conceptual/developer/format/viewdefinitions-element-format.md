---
title: Elemento ViewDefinitions (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361424"
---
# <a name="viewdefinitions-element-format"></a>Elemento ViewDefinitions (formato)

Define las vistas que se usan para mostrar objetos .NET. Estas vistas pueden mostrar las propiedades y los valores de script de un objeto en formato de tabla, formato de lista, formato ancho y formato de control personalizado.

Elemento Configuration (Format) ViewDefinitions (Format XML) (elemento)

## <a name="syntax"></a>Sintaxis

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ViewDefinitions`. No hay ningún límite en el número de vistas que se pueden definir en un archivo de formato y se pueden agregar en cualquier orden.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Define una vista que se usa para mostrar uno o más objetos .NET.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Configuration (elemento, Format)](./configuration-element-format.md)|Representa el elemento de nivel superior de un archivo de formato.|

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de los componentes de los diferentes tipos de vistas, vea los temas siguientes:

- [Crear una vista de tabla](./creating-a-table-view.md)

- [Crear una vista de lista](./creating-a-list-view.md)

- [Crear una vista amplia](./creating-a-wide-view.md)

- [Controles personalizados](./creating-custom-controls.md)

## <a name="example"></a>Ejemplo

En este ejemplo se muestra un elemento `ViewDefinitions` que contiene los elementos primarios de una vista de tabla y una vista de lista.

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

[Configuration (elemento, Format)](./configuration-element-format.md)

[Elemento View (Format)](./view-element-format.md)

[Crear una vista de tabla](./creating-a-table-view.md)

[Crear una vista de lista](./creating-a-list-view.md)

[Crear una vista amplia](./creating-a-wide-view.md)

[Controles personalizados](./creating-custom-controls.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
