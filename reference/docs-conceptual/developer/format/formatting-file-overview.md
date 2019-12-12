---
title: Información general sobre el formato de archivo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363694"
---
# <a name="formatting-file-overview"></a>Información general del archivo de formato

El formato de presentación de los objetos devueltos por los comandos (cmdlets, funciones y scripts) se define mediante el uso de archivos de formato (archivos Format. ps1xml). PowerShell proporciona algunos de estos archivos para definir el formato de presentación de los objetos devueltos por los comandos proporcionados por PowerShell, como el objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) devuelto por el cmdlet `Get-Process`. Sin embargo, también puede crear sus propios archivos de formato personalizados para sobrescribir los formatos de presentación predeterminados o puede escribir un archivo de formato personalizado para definir la presentación de los objetos devueltos por sus propios comandos.

> [!IMPORTANT]
> Los archivos de formato no determinan los elementos de un objeto que se devuelven a la canalización. Cuando se devuelve un objeto a la canalización, todos los miembros de ese objeto están disponibles aunque no se muestren algunos.

PowerShell usa los datos de estos archivos de formato para determinar lo que se muestra y cómo se da formato a los datos mostrados. Los datos mostrados pueden incluir las propiedades de un objeto o el valor de un script. Los scripts se usan si desea mostrar algún valor que no está disponible directamente desde las propiedades de un objeto, como agregar el valor de dos propiedades de un objeto y, a continuación, Mostrar la suma como una parte de los datos. El formato de los datos mostrados se realiza definiendo vistas para los objetos que desea mostrar. Puede definir una vista única para cada objeto, puede definir una vista única para varios objetos o puede definir varias vistas para el mismo objeto. No hay ningún límite en el número de vistas que puede definir.

## <a name="common-features-of-formatting-files"></a>Características comunes de los archivos de formato

Cada archivo de formato puede definir los siguientes componentes que se pueden compartir entre todas las vistas definidas por el archivo:

- Valor de configuración predeterminado, como si los datos mostrados en las filas de las tablas se van a mostrar en la línea siguiente si los datos son más largos que el ancho de la columna. Para obtener más información acerca de esta configuración, consulte [definir opciones de configuración comunes](./defining-common-configuration-features.md).

- Conjuntos de objetos que se pueden mostrar en cualquiera de las vistas del archivo de formato. Para obtener más información acerca de estos conjuntos (denominados *conjuntos de selección*), consulte [definir conjuntos de objetos](./defining-selection-sets.md).

- Controles comunes que se pueden usar en todas las vistas del archivo de formato. Los controles proporcionan un control más preciso sobre cómo se muestran los datos. Para obtener más información sobre los controles, vea [definir controles personalizados](./creating-custom-controls.md).

## <a name="formatting-views"></a>Dar formato a vistas

Las vistas de formato pueden mostrar objetos en formato de tabla, formato de lista, formato ancho y formato personalizado. En su mayor parte, cada definición de formato se describe mediante un conjunto de etiquetas XML que describen la vista. Cada vista contiene el nombre de la vista, los objetos que utilizan la vista y los elementos de la vista, como la información de columna y de fila de una vista de tabla.

Vista de tabla enumera las propiedades de un objeto o un valor de bloque de script en una o varias columnas. Cada columna representa una única propiedad del objeto o un valor de script. Puede definir una vista de tabla que muestre todas las propiedades de un objeto, un subconjunto de las propiedades de un objeto o una combinación de propiedades y valores de script. Cada fila de la tabla representa un objeto devuelto. Crear una vista de tabla es muy similar a cuando se canaliza un objeto al cmdlet `Format-Table`. Para obtener más información sobre esta vista, vea [vista de tabla](./creating-a-table-view.md).

Vista de lista muestra las propiedades de un objeto o un valor de script en una sola columna. Cada fila de la lista muestra una etiqueta opcional o el nombre de la propiedad seguido del valor de la propiedad o el script. Crear una vista de lista es muy similar a canalizar un objeto al cmdlet `Format-List`. Para obtener más información sobre esta vista, vea [vista de lista](./creating-a-list-view.md).

Vista ancha muestra una única propiedad de un objeto o un valor de script en una o varias columnas. No hay etiqueta o encabezado para esta vista. La creación de una vista amplia es muy similar a la canalización de un objeto al cmdlet `Format-Wide`. Para obtener más información sobre esta vista, vea [vista amplia](./creating-a-wide-view.md).

Vista personalizada muestra una vista personalizable de las propiedades de objeto o de los valores de script que no se adhiere a la estructura rígida de las vistas de tabla, las vistas de lista o las vistas anchas. Puede definir una vista personalizada independiente o puede definir una vista personalizada que se use en otra vista, como una vista de tabla o una vista de lista. La creación de una vista personalizada es muy similar a la canalización de un objeto al cmdlet `Format-Custom`. Para obtener más información acerca de esta vista, vea [vista personalizada](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Componentes de una vista

En los siguientes ejemplos XML se muestran los componentes XML básicos de una vista. Los elementos XML individuales varían en función de la vista que desea crear, pero los componentes básicos de las vistas son los mismos.

Para empezar, cada vista tiene un elemento `Name` que especifica un nombre descriptivo que se utiliza para hacer referencia a la vista. `ViewSelectedBy` elemento que define qué objetos .NET se muestran en la vista, y un elemento de *control* que define la vista.

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

Dentro del elemento de control, puede definir uno o varios elementos de *entrada* . Si usa varias definiciones, debe especificar qué objetos .NET usan cada definición. Normalmente, solo se necesita una entrada, con una sola definición, para cada control.

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

Dentro de cada elemento de entrada de una vista, se especifican *los elementos que* definen las propiedades o los scripts .net que se muestran en esa vista.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Como se muestra en los ejemplos anteriores, el archivo de formato puede contener varias vistas, una vista puede contener varias definiciones y cada definición puede contener varios elementos.

## <a name="example-of-a-table-view"></a>Ejemplo de una vista de tabla

En el ejemplo siguiente se muestran las etiquetas XML utilizadas para definir una vista de tabla que contiene dos columnas. El elemento [ViewDefinitions](./viewdefinitions-element-format.md) es el elemento contenedor de todas las vistas definidas en el archivo de formato. El elemento de [vista](./view-element-format.md) define la vista de tabla, lista, ancho o personalizada específica. Dentro de cada elemento de [vista](./view-element-format.md) , el elemento [Name](./name-element-for-view-format.md) especifica el nombre de la vista, el elemento [ViewSelectedBy](./viewselectedby-element-format.md) define los objetos que utilizan la vista y los distintos elementos control (como el elemento `TableControl` que se muestra en el ejemplo siguiente) definen el tipo de la vista.

```xml
<ViewDefinitions>
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Véase también

[Crear una vista de lista](./creating-a-list-view.md)

[Crear una vista de tabla](./creating-a-table-view.md)

[Crear una vista amplia](./creating-a-wide-view.md)

[Creación de controles personalizados](./creating-custom-controls.md)

[Escribir un archivo de formato y tipos de PowerShell](./writing-a-powershell-formatting-file.md)
