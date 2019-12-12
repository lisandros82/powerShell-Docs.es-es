---
title: Referencia XML de esquemas de formato | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 437b3d6bb62fdd3a74f3392ec71df360c01a1974
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363724"
---
# <a name="format-schema-xml-reference"></a>Referencia XML del esquema de formato

En los temas de esta sección se describen los elementos XML que se usan en los archivos de formato (archivos Format. ps1xml). Los archivos de formato definen cómo se muestra el objeto .NET; no cambian el propio objeto.

## <a name="in-this-section"></a>En esta sección

[Elemento Alignment para TableColumnHeader para tablecontrol ((Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) Define cómo se muestran los datos en un encabezado de columna.

[Elemento Alignment para TableColumnItem para tablecontrol ((Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) Define cómo se muestran los datos de la fila.

[AutoSize (elemento) para tablecontrol ((Format)](./autosize-element-for-tablecontrol-format.md) Especifica si el tamaño de la columna y el número de columnas se ajustan en función del tamaño de los datos.

[AutoSize (elemento) para WideControl (Format)](./autosize-element-for-widecontrol-format.md) Especifica si el tamaño de la columna y el número de columnas se ajustan en función del tamaño de los datos.

[Elemento ColumnNumber para WideControl (Format)](./columnnumber-element-for-widecontrol-format.md) Especifica el número de columnas que se muestran en la vista amplia.

[Configuration (elemento, Format)](./configuration-element-format.md) Representa el elemento de nivel superior del archivo de formato.

[Control (elemento) para controles de configuración (Format)](./control-element-for-controls-for-configuration-format.md) Define un control común que pueden usar todas las vistas del archivo de formato y el nombre que se usa para hacer referencia al control.

[Control (elemento) para controles de View (Format)](./control-element-for-controls-for-view-format.md) Define un control que se puede usar en la vista y el nombre que se usa para hacer referencia al control.

[Controls (elemento) para Configuration (Format)](./controls-element-for-configuration-format.md) Define los controles comunes que se pueden usar en todas las vistas del archivo de formato.

[Controls (elemento) para View (Format)](./controls-element-for-view-format.md) Define los controles de vista que se pueden usar en una vista específica.

[Elemento CustomControl para el control de la configuración (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) Define un control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento CustomControl para el control de los controles de View (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md) Define un control utilizado por la vista.

[Elemento CustomControl para GroupBy (Format)](./customcontrol-element-for-groupby-format.md) Define el control personalizado que muestra el nuevo grupo.

[CustomControl (elemento, Format)](./customcontrol-element-for-groupby-format.md) Define un formato de control personalizado para la vista.

[Elemento CustomControlName de ExpressionBinding para controles de configuración (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) Especifica el nombre de un control común. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento CustomControlName para ExpressionBindine para controles para View (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) Especifica el nombre de un control común o un control de vista. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento CustomControlName de GroupBy (Format)](./customcontrolname-element-for-groupby-format.md) Especifica el nombre de un control personalizado que se usa para mostrar el nuevo grupo. Este elemento se utiliza al definir una vista de control de tabla, lista, ancho o personalizado.

[Elemento CustomEntry para CustomControl para los controles de configuración (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) Proporciona una definición del control común. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento CustomEntry para CustomEntries para controles para View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md) Proporciona una definición del control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento CustomEntry para CustomEntries para View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) Proporciona una definición de la vista de control personalizada.

[Elemento CustomEntry para CustomControl para GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md) Proporciona una definición del control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento CustomEntries para CustomControl para Configuration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) Proporciona las definiciones de un control común. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento CustomEntries para CustomControl para controles para View (Format)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) Proporciona las definiciones para el control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento CustomEntries para CustomControl para GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md) Proporciona las definiciones para el control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento CustomEntries para CustomControl para View (Format)](./customentries-element-for-customcontrol-for-view-format.md) Proporciona las definiciones de la vista de control personalizada. La vista de control personalizada debe especificar una o más definiciones.

[Elemento CustomItem de CustomEntry para controles de configuración](./customitem-element-for-customentry-for-controls-for-configuration-format.md) Define qué datos se muestran en el control y cómo se muestran. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento CustomItem para CustomEntry para controles para View (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md) Define qué datos se muestran en el control y cómo se muestran. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento CustomItem para CustomEntry para View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) Define qué datos se muestran en la vista de control personalizada y cómo se muestran. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento CustomItem para CustomEntry para GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md) Define qué datos se muestran en la vista de control personalizada y cómo se muestran. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[DefaultSettings (elemento, Format)](./defaultsettings-element-format.md) Define la configuración común que se aplica a todas las vistas del archivo de formato. La configuración común incluye la visualización de errores, el ajuste de texto en tablas, la definición de cómo se expanden las colecciones y mucho más.

[Elemento DisplayError (Format)](./displayerror-element-format.md) Especifica que el #ERR de cadena se muestra cuando se produce un error que muestra un fragmento de datos.

[Elemento EntrySelectedBy de CustomEntry para controles de configuración (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) Define los tipos de .NET que usan la definición del control común o la condición que debe existir para que se utilice este control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento EntrySelectedBy para CustomEntry para controles para View (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento EntrySelectedBy para CustomEntry para View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) Define los tipos .NET que usan esta entrada personalizada o la condición que debe existir para que se use esta entrada.

[Elemento EntrySelectedBy para EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md) Define los tipos .NET que usan esta definición o la condición que debe existir para que se use esta definición.

[Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md) Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento EntrySelectedBy para ListEntry para ListControl (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md) Define los tipos de .NET que usan esta definición de vista de lista o la condición que debe existir para que se use esta definición. En la mayoría de los casos, solo se necesita una definición para una vista de lista. Sin embargo, puede proporcionar varias definiciones para la vista de lista si desea utilizar la misma vista de lista para Mostrar datos diferentes para los distintos objetos.

[Elemento EntrySelectedBy para TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) Define los tipos de .NET cuyos valores de propiedad se muestran en la fila.

[Elemento EntrySelectedBy para WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md) Define los tipos de .NET que usan esta definición de la vista amplia o la condición que debe existir para que se use esta definición.

[Elemento EnumerableExpansion (Format)](./enumerableexpansion-element-format.md) Define cómo se expanden los objetos de colección .NET específicos cuando se muestran en una vista.

[Elemento EnumerableExpansions (Format)](./enumerableexpansions-element-format.md) Define cómo se expanden los objetos de la colección de .NET cuando se muestran en una vista.

[Elemento EnumerateCollection de ExpressionBinding para controles de configuración (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) Especifica que el control muestra los elementos de las colecciones. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento EnumerateCollection para ExpressionBinding para controles para View (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) Especifica que se muestran los elementos de las colecciones. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento EnumerateCollection para el enlace de expresiones para CustomControl para View (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) Especifica que se muestran los elementos de las colecciones. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento EnumerateCollection para ExpressionBinding para GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Especifica que se muestran los elementos de las colecciones. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Expand (elemento, Format)](./expand-element-format.md) Especifica cómo se expande el objeto de colección para esta definición.

[Elemento ExpressionBinding de CustomItem para controles de configuración (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) Define los datos que muestra el control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento ExpressionBinding para CustomItem para controles para View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) Define los datos que muestra el control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento ExpressionBinding para CustomItem para CustomControl para View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) Define los datos que muestra el control. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento ExpressionBinding para CustomItem para GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md) Define los datos que muestra el control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento FirstLineHanging para Frame para controles de configuración (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) Especifica el número de caracteres que la primera línea de datos se desplaza hacia la izquierda. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento FirstLineHanging del marco de controles de la vista (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) Especifica el número de caracteres que la primera línea de datos se desplaza hacia la izquierda. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento FirstLineHanging para Frame para CustomControl para View (Format)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) Especifica el número de caracteres que la primera línea de datos se desplaza hacia la izquierda. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento FirstLineHanging para Frame para GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md) Especifica el número de caracteres que la primera línea de datos se desplaza hacia la izquierda. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento FirstLineIndent para Frame para controles de configuración (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) Especifica el número de caracteres que la primera línea de datos se desplaza hacia la derecha. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento FirstLineIndent del marco de controles de la vista (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) Especifica el número de caracteres que la primera línea de datos se desplaza hacia la derecha. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) Especifica el número de caracteres que la primera línea de datos se desplaza hacia la derecha. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento FirstLineIndent para Frame para GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md) Especifica el número de caracteres que la primera línea de datos se desplaza hacia la derecha. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento FormatString para ListItem (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md) Especifica un modelo de formato que define cómo se muestra el valor de la propiedad o del script.

[Elemento FormatString para TableColumnItem (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) Especifica un modelo de formato que define cómo se muestra el valor de la propiedad o el script de la tabla.

[Elemento FormatString para WideItem para WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md) Especifica un modelo de formato que define cómo se muestra la propiedad o el valor de script en la vista.

[Elemento Frame para CustomItem para los controles de configuración (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md) Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento Frame para CustomItem para los controles de View (Format)](./frame-element-for-customitem-for-controls-for-view-format.md) Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento Frame para CustomItem para CustomControl para View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md) Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento Frame para CustomItem para GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md) Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento GroupBy para View (Format)](./groupby-element-for-view-format.md) Define cómo Windows PowerShell muestra un nuevo grupo de objetos.

[Elemento HideTableHeaders (Format)](./hidetableheaders-element-format.md) Especifica que no se muestran los encabezados de la tabla.

[Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) Define la condición que debe existir para que se utilice este control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento ItemSelectionCondition de ExpressionBinding para controles de View (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) Define la condición que debe existir para que se utilice este control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento ItemSelectionCondition para el enlace de expresiones para CustomControl para View (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) Define la condición que debe existir para que se utilice este control. No hay ningún límite en el número de condiciones de selección que se pueden especificar para un elemento de control. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) Define la condición que debe existir para que se utilice este control. No hay ningún límite en el número de condiciones de selección que se pueden especificar para un elemento de control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento ItemSelectionCondition para ListItem (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) Define la condición que debe existir para que se use este elemento de lista.

[Elemento Label de ListItem para ListControl (Format)](./label-element-for-listitem-for-listcontrol-format.md) Especifica la etiqueta de la propiedad o el valor de script de la fila.

[Elemento Label para GroupBy (Format)](./label-element-for-groupby-format.md) Especifica una etiqueta que se muestra cuando se encuentra un nuevo grupo.

[Elemento Label para TableColumnHeader (Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) Define la etiqueta que se muestra en la parte superior de una columna.

[Elemento LeftIndent para Frame para controles de configuración (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) Especifica el número de caracteres que los datos se desplazan fuera del margen izquierdo. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento LeftIndent del marco de controles de la vista (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md) Especifica el número de caracteres que los datos se desplazan fuera del margen izquierdo. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento LeftIndent para Frame para CustomControl para View (Format)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) Especifica el número de caracteres que los datos se desplazan fuera del margen izquierdo. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento LeftIndent para Frame para GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md) Especifica el número de caracteres que los datos se desplazan fuera del margen izquierdo. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[ListControl (elemento, Format)](./listcontrol-element-format.md) Define un formato de lista para la vista.

[ListEntry (formato)](./listentry-element-for-listcontrol-format.md) Proporciona una definición de la vista de lista.

[ListEntries (elemento, Format)](./listentries-element-for-listcontrol-format.md) Define cómo se muestran las filas de la vista de lista.

[ListItem (elemento, Format)](./listitem-element-for-listitems-for-listcontrol-format.md) Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.

[ListItems (elemento, Format)](./listitems-element-for-listentry-for-listcontrol-format.md) Define las propiedades y los scripts que se muestran en la vista de lista.

[Elemento Name del control para los controles de configuración (Format)](./name-element-for-control-for-controls-for-configuration-format.md) Especifica el nombre del control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento Name para SelectionSet (Format)](./name-element-for-selectionset-format.md) Especifica el nombre usado para hacer referencia al conjunto de selección.

[Name (elemento) para View (Format)](./name-element-for-view-format.md) Especifica el nombre que se utiliza para identificar la vista.

[Elemento newline para CustomItem para los controles de configuración (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md) Agrega una línea en blanco a la presentación del control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento newline para CustomItem para los controles de View (Format)](./newline-element-for-customitem-for-controls-for-view-format.md) Agrega una línea en blanco a la presentación del control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento newline para CustomItem para CustomControl para View (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) Agrega una línea en blanco a la presentación del control. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento newline para CustomItem para GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md) Agrega una línea en blanco a la presentación del control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento PropertyName para ExpressionBinding para los controles de configuración (Format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) Especifica la propiedad de .NET cuyo valor se muestra en el control común. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento PropertyName para ExpressionBinding para los controles de View (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) Especifica la propiedad de .NET cuyo valor muestra el control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento PropertyName para ExpressionBinding para CustomControl para View (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) Especifica la propiedad de .NET cuyo valor muestra el control. Este elemento se utiliza al definir una vista de control personalizada

[Elemento PropertyName para ExpressionBinding para GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md) Especifica la propiedad de .NET cuyo valor muestra el control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento PropertyName para GroupBy (Format)](./propertyname-element-for-groupby-format.md) Especifica la propiedad de .NET que inicia un nuevo grupo siempre que cambia su valor.

[Elemento PropertyName para ItemSeclectionCondition para los controles de configuración (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se utiliza el control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento PropertyName para ItemSelectionCondition para los controles de View (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se utiliza el control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento PropertyName para ItemSelectionCondition para CustomControl para View (Format](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) especifica la propiedad .net que desencadena la condición). Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se utiliza el control. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento PropertyName para ItemSelectionCondition para GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se utiliza el control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento PropertyName para ItemSelectionCondition para ListItem (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la vista. Este elemento se utiliza al definir una vista de lista.

[Elemento PropertyName para ListItem para ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md) Especifica la propiedad de .NET cuyo valor se muestra en la lista.

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListEntry (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento PropertyName para SelectionCondition para los controles de View (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento PropertyName para SelectionCondition para CustomControl para View (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición.

[Elemento PropertyName para SelectionCondition para GroupBy (Format)](./propertyname-element-for-selectioncondition-for-groupby-format.md) Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada de la lista.

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada de la tabla.

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición.

[Elemento PropertyName para TableColumnItem (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) Especifica la propiedad cuyo valor se muestra en la columna de la fila.

[Elemento PropertyName para WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md) Especifica la propiedad del objeto cuyo valor se muestra en la vista amplia.

[Elemento RightIndent para Frame para controles de configuración (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) Especifica el número de caracteres que los datos se desplazan fuera del margen derecho. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento RightIndent del marco de controles de la vista (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md) Especifica el número de caracteres que los datos se desplazan fuera del margen derecho. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) Especifica el número de caracteres que los datos se desplazan fuera del margen derecho. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento RightIndent para Frame para GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md) Especifica el número de caracteres que los datos se desplazan fuera del margen derecho. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento ScriptBlock para ExpressionBinding para los controles de configuración (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) Especifica el script cuyo valor muestra el control común. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento ScriptBlock para ExpressionBinding para los controles de View (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) Especifica el script cuyo valor muestra el control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento ScriptBlock para ExpressionBinding para CustomCustomControl para View (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) Especifica el script cuyo valor muestra el control. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento ScriptBlock para ExpressionBinding para GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md) Especifica el script cuyo valor muestra el control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento ScriptBlock para GroupBy (Format)](./scriptblock-element-for-groupby-format.md) Especifica el script que inicia un nuevo grupo siempre que cambia su valor.

[Elemento ScriptBlock para ItemSelectionCondition para los controles de configuración (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa el control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento ScriptBlock para ItemSelectionCondition para los controles de View (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa el control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento ScriptBlock para ItemSelectionCondition para CustomControl para View (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa el control. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento ScriptBlock para ItemSelectionCondition para GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa el control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento ScriptBlock para ItemSelectionCondition para ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa el elemento de lista. Este elemento se utiliza al definir una vista de lista.

[Elemento ScriptBlock para ListItem (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md) Especifica el script cuyo valor se muestra en la fila de la lista.

[Elemento ScriptBlock para SelectionCondition para los controles de configuración (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa la definición. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento ScriptBlock para SelectionCondition para los controles de View (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa la definición. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento ScriptBlock para SelectionCondition para CustomControl para View (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa la definición. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Especifica el script que desencadena la condición.

[Elemento ScriptBlock para SelectionCondition para GroupBy (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa la definición. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa la entrada de la lista.

[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Especifica el bloque de script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa la entrada de la tabla.

[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se utiliza la definición de la entrada ancha.

[Elemento ScriptBlock para TableColumnItem (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) Especifica el script cuyo valor se muestra en la columna de la fila.

[Elemento ScriptBlock para WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Especifica el script cuyo valor se muestra en la vista amplia.

[Elemento SelectionCondition para EntrySelectedBy para CustomEntry para Configuration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) Define una condición que debe existir para que se utilice una definición de control común. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento SelectionCondition para EntrySelectedBy para controles para View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) Define una condición que debe existir para que se use la definición de control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento SelectionCondition para EntrySelectedBy para CustomControl para View (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) Define una condición que debe existir para que se use una definición de control. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) Define la condición que debe existir para expandir los objetos de colección de esta definición.

[Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) Define una condición que debe existir para que se use una definición de control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento SelectionCondition para EntrySelectedBy para ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) Define la condición que debe existir para usar esta definición de la vista de lista. No hay ningún límite en el número de condiciones de selección que se pueden especificar para una definición de lista.

[Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) Define la condición que debe existir para usar para esta definición de la vista de tabla. No hay ningún límite en el número de condiciones de selección que se pueden especificar para una definición de tabla.

[Elemento SelectionCondition para EntrySelectedBy para WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) Define la condición que debe existir para que se use esta definición. No hay ningún límite en el número de condiciones de selección que se pueden especificar para una definición de entrada ancha.

[Elemento SelectionSet (Format)](./selectionset-element-format.md) Define un conjunto de objetos .NET a los que se puede hacer referencia mediante el nombre del conjunto.

[Elemento SelectionSetName de EntrySelectedBy para controles de configuración (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica un conjunto de tipos de .NET que usan esta definición del control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento SelectionSetName para EntrySelectedBy para controles para View (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) Especifica un conjunto de tipos de .NET que usan esta definición del control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento SelectionSetName para EntrySelectedBy para CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) Especifica un conjunto de objetos .NET para la entrada de la lista. No hay ningún límite en el número de conjuntos de selección que se pueden especificar para una entrada.

[Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) Especifica el conjunto de tipos de .NET que se expanden con esta definición.

[Elemento SelectionSetName para EntrySelectedBy para GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) Especifica un conjunto de objetos .NET para la entrada de la lista. No hay ningún límite en el número de conjuntos de selección que se pueden especificar para una entrada. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento SelectionSetName para EntrySelectedBy para ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) Especifica un conjunto de objetos .NET para la entrada de la lista. No hay ningún límite en el número de conjuntos de selección que se pueden especificar para una entrada.

[Elemento SelectionSetName para EntrySelectedBy para TableRowEntry (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) Especifica un conjunto de tipos de .NET que usan esta entrada de la vista de tabla. No hay ningún límite en el número de conjuntos de selección que se pueden especificar para una entrada.

[Elemento SelectionSetName para EntrySelectedBy para WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) Especifica un conjunto de objetos .NET para la definición. La definición se utiliza siempre que se muestra uno de estos objetos.

[Elemento SelectionSetName de SelectionCondition para controles de configuración (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica el conjunto de tipos de .NET que desencadenan la condición. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante este control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento SelectionSetName para SelectionCondition para controles para View (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) Especifica el conjunto de tipos de .NET que desencadenan la condición. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra utilizando este control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento EntrySelectedBy para CustomEntry para View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) Especifica el conjunto de tipos de .NET que desencadenan la condición. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra utilizando este control. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Especifica el conjunto de tipos de .NET que desencadenan la condición. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición.

[Elemento SelectionSetName para SelectionCondition para GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) Especifica el conjunto de tipos de .NET que desencadenan la condición. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante este control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) Especifica el conjunto de tipos de .NET que desencadenan la condición. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra con esta definición de la vista de lista.

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Especifica el conjunto de tipos de .NET que desencadenan la condición. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra con esta definición de la vista de tabla.

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Especifica el conjunto de tipos de .NET que desencadenan la condición. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra con esta definición de la vista ampliada.

[Elemento SelectionSetName para ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md) Especifica un conjunto de objetos .NET que se muestran en la vista.

[Elemento SelectionSets (Format)](./selectionsets-element-format.md) Define los conjuntos de objetos .NET que pueden usar las vistas de formato individuales.

[Elemento ShowError (Format)](./showerror-element-format.md) Especifica que el registro de errores completo se muestra cuando se produce un error mientras se muestra un fragmento de datos.

[Elemento TableColumnHeader para TableHeaders para tablecontrol ((Format)](./tablecolumnheader-element-format.md) Define la etiqueta, el ancho de la columna y la alineación de la etiqueta para una columna de la tabla.

[Elemento TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) Define la propiedad o el script cuyo valor se muestra en la columna de la fila.

[Elemento TableColumnItems (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) Define las propiedades o los scripts cuyos valores se muestran en la fila.

[Elemento tablecontrol ((Format)](./tablecontrol-element-format.md) Define un formato de tabla para una vista.

[Elemento TableHeaders (Format)](./tableheaders-element-format.md) Define los encabezados de las columnas de una tabla.

[Elemento TableRowEntries (Format)](./tablerowentries-element-for-tablecontrol-format.md) Define las filas de la tabla.

[Elemento TableRowEntry (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) Define los datos que se muestran en una fila de la tabla.

[Elemento de texto para CustomItem para los controles de configuración (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md) Especifica el texto que se agrega a los datos mostrados por el control, como una etiqueta, corchetes para incluir los datos y espacios para aplicar sangría a los datos. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento Text para CustomItem para los controles de View (Format)](./text-element-for-customitem-for-controls-for-view-format.md) Especifica el texto que se agrega a los datos mostrados por el control, como una etiqueta, corchetes para incluir los datos y espacios para aplicar sangría a los datos. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento Text para CustomItem (Format)](./text-element-for-customitem-for-customview-for-view-format.md) Especifica el texto que se agrega a los datos mostrados por el control, como una etiqueta, corchetes para incluir los datos y espacios para aplicar sangría a los datos. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento Text para CustomItem para GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md) Especifica el texto que se agrega a los datos mostrados por el control, como una etiqueta, corchetes para incluir los datos y espacios para aplicar sangría a los datos. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento TypeName para EntrySelectedBy para los controles de configuración (Format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) Especifica un tipo .NET que usa esta definición del control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento TypeName para EntrySelectedBy para los controles de View (Format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md) Especifica un tipo .NET que usa esta definición del control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento TypeName para EntrySelectedBy para CustomEntry para View (Format)](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) Especifica un tipo .NET que usa esta definición de la vista de control personalizada. No hay ningún límite en el número de tipos que se pueden especificar para una definición.

[Elemento TypeName para EntrySelectedBy para EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) Especifica un tipo .NET que se expande mediante esta definición. Este elemento se utiliza al definir una configuración predeterminada.

[Elemento TypeName para EntrySelectedBy para GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md) Especifica un tipo .NET que usa esta definición del control personalizado. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento TypeName para EntrySelectedBy para ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md) Especifica un tipo .NET que usa esta entrada de la vista de lista. No hay ningún límite en el número de tipos que se pueden especificar para una entrada de la lista.

[Elemento TypeName para EntrySelectedBy para TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md) Especifica un tipo .NET que usa esta entrada de la vista de tabla. No hay ningún límite en el número de tipos que se pueden especificar para una entrada de tabla.

[Elemento TypeName para EntrySelectedBy para WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md) Especifica un tipo .NET para la definición. La definición se usa siempre que se muestra este objeto.

[Elemento TypeName para SelectionCondition para los controles de configuración (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica un tipo .NET que desencadena la condición. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

[Elemento TypeName para SelectionCondition para los controles de View (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) Especifica un tipo .NET que desencadena la condición. Este elemento se utiliza al definir controles que se pueden usar en una vista.

[Elemento TypeName para SelectionCondition para CustomControl para View (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) Especifica un tipo .NET que desencadena la condición. Este elemento se utiliza al definir una vista de control personalizada.

[Elemento TypeName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Especifica un tipo .NET que desencadena la condición.

[Elemento TypeName para SelectionCondition para GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md) Especifica un tipo .NET que desencadena la condición. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

[Elemento TypeName para SelectionCondition para EntrySelectedBy para ListControl (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Especifica un tipo .NET que desencadena la condición. Cuando este tipo está presente, se usa la entrada de la lista.

[Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Especifica un tipo .NET que desencadena la condición. Cuando este tipo está presente, se cumple la condición y se usa la fila de la tabla.

[Elemento TypeName para SelectionCondition para EntrySelectedBy para WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Especifica un tipo .NET que desencadena la condición. Cuando este tipo está presente, se usa la definición.

[TypeName (elemento) para tipos (Format)](./typename-element-for-types-format.md) Especifica el tipo .NET de un objeto que pertenece al conjunto de selección.

[Elemento TypeName para ViewSelectedBy (Format)](./typename-element-for-viewselectedby-format.md) Especifica un objeto .NET que se muestra en la vista.

[Types (elemento, Format)](./types-element-for-selectionset-format.md) Define los objetos .NET que se encuentran en el conjunto de selección.

[Elemento View (Format)](./view-element-format.md) Define una vista que se usa para mostrar uno o más objetos .NET.

[Elemento ViewDefinitions (Format)](./viewdefinitions-element-format.md) Define las vistas que se usan para mostrar los objetos.

[Elemento ViewSelectedBy (Format)](./viewselectedby-element-format.md) Define los objetos .NET que se muestran en la vista.

[Elemento WideControl (Format)](./widecontrol-element-format.md) Define un formato de lista ancho (valor único) para la vista. Esta vista muestra un valor de propiedad único o un valor de script para cada objeto.

[Elemento WideEntries (Format)](./wideentries-element-for-widecontrol-format.md) Proporciona las definiciones de la vista amplia. La vista ancha debe especificar una o más definiciones.

[Elemento WideEntry (Format)](./wideentry-element-for-widecontrol-format.md) Proporciona una definición de la vista amplia.

[Elemento WideItem (Format)](./wideitem-element-for-widecontrol-format.md) Define la propiedad o el script cuyo valor se muestra.

[Width (elemento, Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) Define el ancho (en caracteres) de una columna.

[Wrap (elemento, Format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) Especifica que el texto que supera el ancho de columna se muestra en la línea siguiente.

[Elemento WrapTables (Format)](./wraptables-element-format.md) Especifica que los datos de una celda de tabla se mueven a la línea siguiente si los datos son más largos que el ancho de la columna.

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
