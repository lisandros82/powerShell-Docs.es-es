---
title: Información general del archivo de formato | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863301"
---
# <a name="formatting-file-overview"></a>Información general del archivo de formato

El formato de presentación de los objetos devueltos por los comandos (cmdlets, funciones y scripts) se definen mediante archivos de formato (archivos format.ps1xml). Algunos de estos archivos se proporcionan mediante PowerShell para definir el formato de presentación para los objetos devueltos por los comandos de PowerShell proporcionado, como el [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto devuelto por la `Get-Process` cmdlet. Sin embargo, también puede crear sus propios archivos de formato personalizados para sobrescribir los formatos de presentación predeterminada o puede escribir un archivo de formato personalizado para definir la presentación de los objetos devueltos por sus propios comandos.

> [!IMPORTANT]
> Archivos de formato no determinan los elementos de un objeto que se devuelven a la canalización. Cuando se devuelve un objeto a la canalización, todos los miembros de ese objeto están disponibles incluso si no se muestran algunos.

PowerShell usa los datos de estos archivos de formato para determinar lo que se muestra y cómo se da formato a los datos mostrados. Pueden incluir los datos que se muestran las propiedades de un objeto o el valor de una secuencia de comandos. Si desea mostrar un valor que no está disponible directamente desde las propiedades de un objeto, como la suma del valor de dos propiedades de un objeto y, a continuación, mostrar la suma como un elemento de datos, se utilizan secuencias de comandos. Formato de los datos mostrados se realiza mediante la definición de vistas para los objetos que desea mostrar. Puede definir una vista única para cada objeto, puede definir una vista única para varios objetos o puede definir varias vistas para el mismo objeto. No hay ningún límite al número de vistas que se pueden definir.

## <a name="common-features-of-formatting-files"></a>Características comunes de los archivos de formato

Cada archivo de formato puede definir los siguientes componentes que se pueden compartir entre todas las vistas definidas por el archivo:

- Opción de configuración, por ejemplo, si se mostrarán los datos mostrados en las filas de tablas en la línea siguiente, si los datos están mayor que el ancho de la columna de forma predeterminada. Para obtener más información sobre estas opciones, consulte [definir opciones de configuración comunes](./defining-common-configuration-features.md).

- Conjuntos de objetos que se pueden mostrar por cualquiera de las vistas del archivo de formato. Para obtener más información acerca de estos conjuntos (denominados *conjuntos de selección*), consulte [definir se establece los objetos](./defining-selection-sets.md).

- Controles comunes que pueden usarse en todas las vistas del archivo de formato. Los controles ofrecen un control más preciso sobre cómo se muestran los datos. Para obtener más información acerca de los controles, vea [definir controles personalizados](./creating-custom-controls.md).

## <a name="formatting-views"></a>Aplicar formato a las vistas

Formato de las vistas pueden mostrar los objetos en un formato de tabla, formato de lista, formato ancho y formato personalizado. En su mayor parte, cada definición de formato se describe mediante un conjunto de etiquetas XML que describen la vista. Cada vista contiene el nombre de la vista, los objetos que utilizan la vista y los elementos de la vista, como la información de columna y fila de una vista de tabla.

Vista de tabla se enumeran las propiedades de un objeto o un valor de bloque de script en una o varias columnas. Cada columna representa una sola propiedad del objeto o un valor de la secuencia de comandos. Puede definir una vista de tabla que muestra todas las propiedades de un objeto, un subconjunto de las propiedades de un objeto o una combinación de propiedades y valores de secuencia de comandos. Cada fila de la tabla representa un objeto devuelto. Creación de una vista de tabla es muy similar a cuando canaliza un objeto a la `Format-Table` cmdlet. Para obtener más información sobre esta vista, consulte [vista de tabla](./creating-a-table-view.md).

Lista de vista muestra las propiedades de un objeto o un valor de la secuencia de comandos en una sola columna. Cada fila de la lista muestra una etiqueta opcional o el nombre de la propiedad seguido del valor de la propiedad o el script. Creación de una vista de lista es muy similar a canalizar un objeto a la `Format-List` cmdlet. Para obtener más información sobre esta vista, consulte [vista de lista](./creating-a-list-view.md).

Vista ampliada muestra una propiedad única de un objeto o un valor de la secuencia de comandos en una o varias columnas. No hay ninguna etiqueta ni el encabezado para esta vista. Creación de una vista amplia es muy similar a canalizar un objeto a la `Format-Wide` cmdlet. Para obtener más información sobre esta vista, consulte [vista amplia](./creating-a-wide-view.md).

Vista personalizada muestra una vista personalizable de las propiedades del objeto o los valores de secuencia de comandos que no se adhiere a la estructura rígida de las vistas de tablas, vistas de lista o vista amplia. Puede definir una vista personalizada independiente, o puede definir una vista personalizada que está usando otra vista, como una vista de tabla o vista de lista. Creación de una vista personalizada es muy similar a canalizar un objeto a la `Format-Custom` cmdlet. Para obtener más información sobre esta vista, consulte [vista personalizada](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Componentes de una vista

Los ejemplos XML siguientes muestran los componentes básicos de XML de una vista. Los elementos XML individuales varían según la vista que desea crear, pero los componentes básicos de las vistas son los mismos.

Para empezar, cada vista tiene un `Name` elemento que especifica un nombre descriptivo que se usa para hacer referencia a la vista. un `ViewSelectedBy` elemento que define qué objetos de .NET se muestra la vista, y un *control* elemento que define la vista.

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

Dentro del elemento de control, puede definir uno o varios *entrada* elementos. Si usa varias definiciones, debe especificar qué objetos de .NET usan cada definición. Normalmente, sólo una entrada, con una única definición, es necesaria para cada control.

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

Dentro de cada elemento de entrada de una vista, especifica el *elemento* elementos que definen las propiedades de .NET o scripts que se muestran en esa vista.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Como se muestra en los ejemplos anteriores, el archivo de formato puede contener varias vistas, una vista puede contener varias definiciones y cada definición puede contener varios elementos.

## <a name="example-of-a-table-view"></a>Ejemplo de una vista de tabla

El ejemplo siguiente muestra las etiquetas XML utilizadas para definir una vista de tabla que contiene dos columnas. El [ViewDefinitions](./viewdefinitions-element-format.md) es el elemento contenedor para todas las vistas definidas en el archivo de formato. El [vista](./view-element-format.md) elemento define la tabla específica, lista, vista amplia o personalizada. Dentro de cada [vista](./view-element-format.md) elemento, el [nombre](./name-element-for-view-format.md) elemento especifica el nombre de la vista, el [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que utilizan la vista y los diferentes los elementos del control (como el `TableControl` elemento mostrado en el ejemplo siguiente) definen el tipo de la vista.

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

[Creación de una vista de lista](./creating-a-list-view.md)

[Creación de una vista de tabla](./creating-a-table-view.md)

[Creación de una vista amplia](./creating-a-wide-view.md)

[Creación de controles personalizados](./creating-custom-controls.md)

[Escribir un formato de PowerShell y el archivo de tipos](./writing-a-powershell-formatting-file.md)
