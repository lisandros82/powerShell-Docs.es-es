---
title: Archivos de formato personalizado | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369834"
---
# <a name="custom-formatting-files"></a>Archivos de formato personalizado

El formato de presentación de los objetos devueltos por los cmdlets, las funciones y los scripts se define mediante archivos de formato (archivos Format. ps1xml). Windows PowerShell proporciona algunos de estos archivos para definir el formato de presentación predeterminado para los objetos devueltos por los cmdlets de Windows PowerShell. Sin embargo, también puede crear sus propios archivos de formato personalizados para sobrescribir los formatos de presentación predeterminados o definir la presentación de los objetos devueltos por sus propios comandos.

Windows PowerShell usa los datos de estos archivos de formato para determinar lo que se muestra y cómo se da formato a los datos. Los datos mostrados pueden incluir las propiedades de un objeto o el valor de un bloque de script.  Los bloques de scripts se usan si desea mostrar algún valor que no está disponible directamente desde las propiedades de un objeto. Por ejemplo, puede que desee agregar el valor de dos propiedades de un objeto y mostrar la suma como una parte independiente de los datos. Al escribir su propio archivo de formato, deberá definir *vistas* para los objetos que desea mostrar. Puede definir una vista única para cada objeto, puede definir una vista única para varios objetos o puede definir varias vistas para el mismo objeto. No hay ningún límite en el número de vistas que puede definir.

> [!IMPORTANT]
> Los archivos de formato no determinan los elementos de un objeto que se devuelven a la canalización. Cuando se devuelve un objeto a la canalización, todos los miembros de ese objeto están disponibles.

## <a name="format-views"></a>Dar formato a vistas

Las vistas de formato pueden mostrar objetos en un formato de tabla, un formato de lista, un formato ancho y un formato personalizado. En su mayor parte, cada definición de formato se describe mediante un conjunto de etiquetas XML que describen una vista. Cada vista contiene el nombre de la vista, los objetos que utilizan la vista y los elementos de la vista, como la información de columna y de fila de una vista de tabla.

Están disponibles las siguientes vistas.

Vista de tabla enumera las propiedades de un objeto o un valor de bloque de script en una o varias columnas. Cada columna representa una propiedad del objeto o un valor de bloque de script. Puede definir una vista de tabla que muestre todas las propiedades de un objeto, un subconjunto de las propiedades de un objeto o una combinación de propiedades y valores de bloque de script. Cada fila de la tabla representa un objeto devuelto. Para obtener más información sobre esta vista, vea [vista de tabla](../format/creating-a-table-view.md).

Vista de lista muestra las propiedades de un objeto o un valor de bloque de script en una sola columna. Cada fila de la lista muestra una etiqueta opcional o el nombre de la propiedad seguido del valor de la propiedad o el bloque de script. Para obtener más información sobre esta vista, vea [vista de lista](../format/creating-a-list-view.md).

Vista ancha muestra una única propiedad de un objeto o un valor de bloque de script en una o varias columnas. No hay etiqueta o encabezado para esta vista. Para obtener más información sobre esta vista, vea [vista amplia](../format/creating-a-wide-view.md).

Vista personalizada muestra una vista personalizable de las propiedades de objeto o de los valores de bloque de script que no se adhiere a la estructura rígida de las vistas de tabla, vistas de lista o vistas anchas. Puede definir una vista personalizada independiente o puede definir una vista personalizada que se use en otra vista, como una vista de tabla o una vista de lista. Para obtener más información acerca de esta vista, vea [vista personalizada](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>Ver elementos XML

En el ejemplo siguiente se muestran las etiquetas XML utilizadas para definir una vista de tabla que contiene dos columnas. El elemento [ViewDefinitions](../format/viewdefinitions-element-format.md) es el elemento contenedor de todas las vistas definidas en el archivo de formato. El elemento de [vista](../format/view-element-format.md) define la vista de tabla, lista, ancho o personalizada específica. Dentro de cada vista, el elemento [Name](../format/name-element-for-view-format.md) especifica el nombre de la vista, el elemento [ViewSelectedBy](../format/viewselectedby-element-format.md) define los objetos que utilizan la vista y los distintos elementos control (como el elemento `TableControl`) definen el formato de la vista.

```xml
ViewDefinitions
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

[Vista de tabla](../format/creating-a-table-view.md)

[Vista de lista](../format/creating-a-list-view.md)

[Vista amplia](../format/creating-a-wide-view.md)

[Vista personalizada](../format/creating-custom-controls.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
