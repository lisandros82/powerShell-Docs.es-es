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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860611"
---
# <a name="custom-formatting-files"></a>Archivos de formato personalizado

El formato de presentación de los objetos devueltos por los cmdlets, funciones y scripts se definen mediante archivos de formato (archivos format.ps1xml). Algunos de estos archivos se proporcionan con Windows PowerShell para definir el formato de presentación predeterminado para los objetos devueltos por los cmdlets de Windows PowerShell. Sin embargo, también puede crear sus propios archivos de formato personalizados para sobrescribir los formatos de presentación predeterminado o para definir la presentación de los objetos devueltos por sus propios comandos.

Windows PowerShell usa los datos en estos archivos de formato para determinar lo que se muestra y cómo se da formato a los datos. Pueden incluir los datos que se muestran las propiedades de un objeto o el valor de un bloque de script.  Si desea mostrar un valor que no está disponible directamente desde las propiedades de un objeto, se utilizan bloques de script. Por ejemplo, es posible que desee agregar el valor de dos propiedades de un objeto y mostrar la suma como una hoja de datos independiente. Al escribir su propio formato de archivo, deberá definir *vistas* para los objetos que desea mostrar. Puede definir una vista única para cada objeto, puede definir una vista única para varios objetos o puede definir varias vistas para el mismo objeto. No hay ningún límite al número de vistas que se pueden definir.

> [!IMPORTANT]
> Archivos de formato no determinan los elementos de un objeto que se devuelven a la canalización. Cuando se devuelve un objeto a la canalización, están disponibles todos los miembros de ese objeto.

## <a name="format-views"></a>Vistas de formato

Formato de las vistas pueden mostrar los objetos en un formato de tabla, un formato de lista, un formato ancho y un formato personalizado. En su mayor parte, cada definición de formato se describe mediante un conjunto de etiquetas XML que describen una vista. Cada vista contiene el nombre de la vista, los objetos que utilizan la vista y los elementos de la vista, como la información de columna y fila de una vista de tabla.

Las vistas siguientes están disponibles.

Vista de tabla enumera las propiedades de un objeto o un valor de bloque de script en una o varias columnas. Cada columna representa una propiedad del objeto o un valor de bloque de script. Puede definir una vista de tabla que muestra todas las propiedades de un objeto, un subconjunto de las propiedades de un objeto o una combinación de propiedades y valores del bloque de script. Cada fila de la tabla representa un objeto devuelto. Para obtener más información sobre esta vista, consulte [vista de tabla](../format/creating-a-table-view.md).

Vista de lista enumera las propiedades de un objeto o un valor de bloque de script en una sola columna. Cada fila de la lista muestra una etiqueta opcional o el nombre de propiedad seguido por el valor de la propiedad o bloque de script. Para obtener más información sobre esta vista, consulte [vista de lista](../format/creating-a-list-view.md).

Vista ampliada muestra una propiedad única de un objeto o un valor de bloque de script en una o varias columnas. No hay ninguna etiqueta ni el encabezado para esta vista. Para obtener más información sobre esta vista, consulte [vista amplia](../format/creating-a-wide-view.md).

Vista personalizada muestra una vista personalizable de las propiedades del objeto o los valores del bloque de script que no se adhiere a la estructura rígida de las vistas de tablas, vistas de lista o vista amplia. Puede definir una vista personalizada independiente, o puede definir una vista personalizada que está usando otra vista, como una vista de tabla o vista de lista. Para obtener más información sobre esta vista, consulte [vista personalizada](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>Elementos de la vista XML

El ejemplo siguiente muestra las etiquetas XML utilizadas para definir una vista de tabla que contiene dos columnas. El [ViewDefinitions](../format/viewdefinitions-element-format.md) es el elemento contenedor para todas las vistas definidas en el archivo de formato. El [vista](../format/view-element-format.md) elemento define la tabla específica, lista, vista amplia o personalizada. Dentro de cada vista, el [nombre](../format/name-element-for-view-format.md) elemento especifica el nombre de la vista, el [ViewSelectedBy](../format/viewselectedby-element-format.md) elemento define los objetos que utilizan la vista y los elementos de control diferente (como el `TableControl` elemento) define el formato de la vista.

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

[Vista ampliada](../format/creating-a-wide-view.md)

[Vista personalizada](../format/creating-custom-controls.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
