---
title: Referencia de esquema XML de formato | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 4dfe27a5105d82fa18e35f965f92fad16d390a2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857791"
---
# <a name="format-schema-xml-reference"></a>Referencia XML del esquema de formato

Los temas de esta sección describen los elementos XML utilizados por el formato de archivos (Format.ps1xml). Formato de archivos define cómo se muestra el objeto. NET; no cambian el propio objeto.

## <a name="in-this-section"></a>En esta sección

[Elemento Alignment para TableColumnHeader para TableControl (formato)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) define cómo se muestran los datos en un encabezado de columna.

[Elemento Alignment para TableColumnItem para TableControl (formato)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) define cómo se muestran los datos en la fila.

[Elemento AutoSize para TableControl (formato)](./autosize-element-for-tablecontrol-format.md) especifica si se ajustan el tamaño de columna y el número de columnas en función del tamaño de los datos.

[Elemento AutoSize para WideControl (formato)](./autosize-element-for-widecontrol-format.md) especifica si se ajustan el tamaño de columna y el número de columnas en función del tamaño de los datos.

[Elemento ColumnNumber para WideControl (formato)](./columnnumber-element-for-widecontrol-format.md) especifica el número de columnas mostradas en la vista ampliada.

[Elemento de configuración (formato)](./configuration-element-format.md) representa el elemento de nivel superior del archivo de formato.

[Control de elemento para los controles de configuración (formato)](./control-element-for-controls-for-configuration-format.md) define un control común que puede usarse en todas las vistas del archivo de formato y el nombre que se usa para hacer referencia al control.

[Control de elemento para los controles de vista (formato)](./control-element-for-controls-for-view-format.md) define un control que se puede usar la vista y el nombre que se usa para hacer referencia al control.

[Los controles de elemento de configuración (formato)](./controls-element-for-configuration-format.md) define los controles comunes que pueden usarse en todas las vistas del archivo de formato.

[Los controles de elemento de vista (formato)](./controls-element-for-view-format.md) define los controles de vista que se pueden utilizar una vista específica.

[Elemento de control personalizado para el Control de configuración (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) define un control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento de control personalizado para el Control para los controles de vista (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md) define un control que se usa la vista.

[Elemento de control personalizado para GroupBy (formato)](./customcontrol-element-for-groupby-format.md) define el control personalizado que muestra el nuevo grupo.

[Elemento de control personalizado (formato)](./customcontrol-element-for-groupby-format.md) define un formato de control personalizado para la vista.

[Elemento CustomControlName para ExpressionBinding para los controles de configuración (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) especifica el nombre de un control común. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento CustomControlName para ExpressionBindine para los controles de vista (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) especifica el nombre de un control común o un control de vista. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento CustomControlName de GroupBy (formato)](./customcontrolname-element-for-groupby-format.md) especifica el nombre de un control personalizado que se usa para mostrar el grupo nuevo. Este elemento se usa al definir una tabla, lista, vista de control personalizado o anchos.

[Elemento CustomEntry para el control personalizado para los controles de configuración (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) proporciona una definición de control comunes. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento CustomEntry para CustomEntries para los controles de vista (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md) proporciona una definición del control. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento CustomEntry para CustomEntries para vista (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) proporciona una definición de la vista de control personalizado.

[Elemento CustomEntry para el control personalizado para GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md) proporciona una definición del control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento CustomEntries para el control personalizado para la configuración (formato)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) proporciona las definiciones de un control común. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento CustomEntries para el control personalizado para los controles de vista (formato)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) proporciona las definiciones para el control. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento CustomEntries para el control personalizado para GroupBy (formato)](./customentries-element-for-customcontrol-for-groupby-format.md) proporciona las definiciones para el control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento CustomEntries para el control personalizado para la vista (formato)](./customentries-element-for-customcontrol-for-view-format.md) proporciona las definiciones de la vista de control personalizado. La vista de control personalizado debe especificar una o varias definiciones.

[Elemento CustomItem para CustomEntry para los controles de configuración](./customitem-element-for-customentry-for-controls-for-configuration-format.md) define qué datos se muestran el control y cómo se muestran. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento CustomItem para CustomEntry para los controles de vista (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md) define qué datos se muestran el control y cómo se muestran. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento CustomItem para CustomEntry para vista (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) define qué datos se muestran la vista de control personalizado y cómo se muestran. Este elemento se usa al definir una vista de control personalizado.

[Elemento CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md) define qué datos se muestran la vista de control personalizado y cómo se muestran. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md) define la configuración común que se aplica a todas las vistas del archivo de formato. Configuración común incluye presentación de errores, ajuste de texto en las tablas, definir cómo se expanden las colecciones y mucho más.

[Elemento DisplayError (Frmat)](./displayerror-element-format.md) especifica que se muestre la cadena #ERR cuando se produce un error al mostrar un elemento de datos.

[Elemento EntrySelectedBy para CustomEntry para los controles de configuración (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) define los tipos de .NET que usan la definición del control común o la condición que debe existir para que este control que se usará. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento EntrySelectedBy para CustomEntry para los controles de vista (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento EntrySelectedBy para CustomEntry para vista (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) define los tipos de .NET que usan esta entrada personalizada o la condición que debe existir para que esta entrada que se usará.

[Elemento EntrySelectedBy para EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md) define los tipos de .NET que usan esta definición o la condición que debe existir para que esta definición para usarse.

[Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)](./entryselectedby-element-for-customentry-for-groupby-format.md) define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento EntrySelectedBy para ListEntry para ListControl (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md) define los tipos de .NET que usan esta definición de vista de lista o la condición que debe existir para que esta definición para usarse. En la mayoría de los casos se necesita una única definición para una vista de lista. Sin embargo, puede proporcionar varias definiciones para la vista de lista si desea usar la misma vista de lista para mostrar datos diferentes para los distintos objetos.

[Elemento EntrySelectedBy para TableRowEntry (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) define los tipos de .NET cuyos valores de propiedad se muestran en la fila.

[Elemento EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md) define los tipos de .NET que usan esta definición de la vista ampliada o la condición que debe existir para que esta definición para usarse.

[Elemento EnumerableExpansion (formato)](./enumerableexpansion-element-format.md) define cómo determinados de .NET de colección, los objetos se expanden cuando se muestran en una vista.

[Elemento EnumerableExpansions (formato)](./enumerableexpansions-element-format.md) define cómo se expanden los objetos de colección de .NET cuando se muestran en una vista.

[Elemento EnumerateCollection para ExpressionBinding para los controles de configuración (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) especificado que se muestran los elementos de colecciones mediante el control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento EnumerateCollection para ExpressionBinding para los controles de vista (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) especificado que se muestran los elementos de colecciones. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento EnumerateCollection para la expresión de enlace de control personalizado para la vista (formato)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) especifica que se muestran los elementos de colecciones. Este elemento se usa al definir una vista de control personalizado.

[Elemento EnumerateCollection para ExpressionBinding para GroupBy (formato)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) especifica que se muestran los elementos de colecciones. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Expanda el elemento (formato)](./expand-element-format.md) especifica cómo se expande el objeto de colección para esta definición.

[Elemento ExpressionBinding para CustomItem para los controles de configuración (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) define los datos que se muestran el control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento ExpressionBinding para CustomItem para los controles de vista (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) define los datos que se muestran el control. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento ExpressionBinding para CustomItem para el control personalizado para la vista (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) define los datos que se muestran el control. Este elemento se usa al definir una vista de control personalizado.

[Elemento ExpressionBinding para CustomItem para GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md) define los datos que se muestran el control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento FirstLineHanging marco para los controles de configuración (formato)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) especifica cuántos caracteres de la primera línea de datos se desplaza a la izquierda. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento FirstLineHanging de marco de controles de vista (formato)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) especifica cuántos caracteres de la primera línea de datos se desplaza a la izquierda. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento FirstLineHanging para el marco de control personalizado para la vista (formato)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) especifica cuántos caracteres de la primera línea de datos se desplaza a la izquierda. Este elemento se usa al definir una vista de control personalizado.

[Elemento FirstLineHanging para marco de GroupBy (formato)](./firstlinehanging-element-for-frame-for-groupby-format.md) especifica cuántos caracteres de la primera línea de datos se desplaza a la izquierda. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento FirstLineIndent marco para los controles de configuración (formato)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) especifica cuántos caracteres de la primera línea de datos se desplaza a la derecha. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento FirstLineIndent de marco de controles de vista (formato)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) especifica cuántos caracteres de la primera línea de datos se desplaza a la derecha. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) especifica cuántos caracteres de la primera línea de datos se desplaza a la derecha. Este elemento se usa al definir una vista de control personalizado.

[Elemento FirstLineIndent marco para GroupBy (formato)](./firstlineindent-element-for-frame-for-groupby-format.md) especifica cuántos caracteres de la primera línea de datos se desplaza a la derecha. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento FormatString para ListItem (formato)](./formatstring-element-for-listitem-for-listcontrol-format.md) especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script.

[Elemento FormatString para TableColumnItem (formato)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script de la tabla.

[Elemento FormatString para WideItem para WideControl (formato)](./formatstring-element-for-wideitem-for-widecontrol-format.md) especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script en la vista.

[Elemento de marco para CustomItem para los controles de configuración (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md) define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento de marco para CustomItem para los controles de vista (formato)](./frame-element-for-customitem-for-controls-for-view-format.md) define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento de marco para CustomItem para el control personalizado para la vista (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md) define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha. Este elemento se usa al definir una vista de control personalizado.

[Elemento de marco para CustomItem para GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md) define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md) define cómo Windows PowerShell muestra un nuevo grupo de objetos.

[Elemento HideTableHeaders (formato)](./hidetableheaders-element-format.md) especifica que no se muestran los encabezados de la tabla.

[Elemento ItemSelectionCondition para ExpressionBinding para los controles de configuración (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) define la condición que debe existir para que este control que se usará. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento ItemSelectionCondition de ExpressionBinding para los controles de vista (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) define la condición que debe existir para que este control que se usará. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento ItemSelectionCondition para la expresión de enlace de control personalizado para la vista (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) define la condición que debe existir para que este control que se usará. No hay ningún límite al número de condiciones de selección que se pueden especificar para un elemento de control. Este elemento se usa al definir una vista de control personalizado.

[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) define la condición que debe existir para que este control que se usará. No hay ningún límite al número de condiciones de selección que se pueden especificar para un elemento de control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento ItemSelectionCondition para ListItem (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) define la condición que debe cumplirse para que este elemento de lista para usarse.

[Etiqueta de elemento de ListItem para ListControl(Format)](./label-element-for-listitem-for-listcontrol-format.md) especifica la etiqueta para el valor de propiedad o un script de la fila.

[Etiqueta de elemento de GroupBy (formato)](./label-element-for-groupby-format.md) especifica una etiqueta que se muestra cuando se encuentra un nuevo grupo.

[Etiqueta de elemento de TableColumnHeader (formato)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) define la etiqueta que se muestra en la parte superior de una columna.

[Elemento LeftIndent marco para los controles de configuración (formato)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) especifica cuántos caracteres de los datos se desplacen el margen izquierdo. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento LeftIndent de marco de controles de vista (formato)](./leftindent-element-for-frame-for-controls-for-view-format.md) especifica cuántos caracteres de los datos se desplacen el margen izquierdo. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento LeftIndent marco para el control personalizado para la vista (formato)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) especifica cuántos caracteres de los datos se desplacen el margen izquierdo. Este elemento se usa al definir una vista de control personalizado.

[Elemento LeftIndent marco para GroupBy (formato)](./leftindent-element-for-frame-for-groupby-format.md) especifica cuántos caracteres de los datos se desplacen el margen izquierdo. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento ListControl (formato)](./listcontrol-element-format.md) define un formato de lista para la vista.

[Elemento ListEntry (formato)](./listentry-element-for-listcontrol-format.md) proporciona una definición de la vista de lista.

[Elemento ListEntries (formato)](./listentries-element-for-listcontrol-format.md) define cómo se muestran las filas de la vista de lista.

[Elemento ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md) define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.

[Elemento ListItems (formato)](./listitems-element-for-listentry-for-listcontrol-format.md) define las propiedades y los scripts que se muestran en la vista de lista.

[Nombre de elemento de Control para los controles de configuración (formato)](./name-element-for-control-for-controls-for-configuration-format.md) especifica el nombre del control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Nombre de elemento para SelectionSet (formato)](./name-element-for-selectionset-format.md) especifica el nombre usado para hacer referencia el conjunto de selección.

[Nombre de elemento de vista (formato)](./name-element-for-view-format.md) especifica el nombre que se usa para identificar la vista.

[Elemento de nueva línea para CustomItem para los controles de configuración (formato)](./newline-element-for-customitem-for-controls-for-configuration-format.md) agrega una línea en blanco a la presentación del control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento de nueva línea para CustomItem para los controles de vista (formato)](./newline-element-for-customitem-for-controls-for-view-format.md) agrega una línea en blanco a la presentación del control. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento de nueva línea para CustomItem para el control personalizado para la vista (formato)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) agrega una línea en blanco a la presentación del control. Este elemento se usa al definir una vista de control personalizado.

[Elemento de nueva línea para CustomItem para GroupBy (formato)](./newline-element-for-customitem-for-groupby-format.md) agrega una línea en blanco a la presentación del control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento PropertyName para ExpressionBinding para los controles de configuración (formato)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) especifica la propiedad de .NET cuyo valor se muestra el control común. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento PropertyName para ExpressionBinding para los controles de vista (formato)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) especifica la propiedad de .NET cuyo valor se muestra el control. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento PropertyName para ExpressionBinding para el control personalizado para la vista (formato)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) especifica la propiedad de .NET cuyo valor se muestra el control. Este elemento se usa al definir una vista de control personalizado

[Elemento PropertyName para ExpressionBinding para GroupBy (formato)](./propertyname-element-for-expressionbinding-for-groupby-format.md) especifica la propiedad de .NET cuyo valor se muestra el control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento PropertyName para GroupBy (formato)](./propertyname-element-for-groupby-format.md) especifica la propiedad de .NET que se inicia un nuevo grupo cada vez que cambia su valor.

[Elemento PropertyName para ItemSeclectionCondition para los controles de configuración (formato)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa el control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento PropertyName para ItemSelectionCondition para los controles de vista (formato)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa el control. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento PropertyName para ItemSelectionCondition para el control personalizado para la vista (formato](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa el control. Este elemento se usa al definir una vista de control personalizado.

[Elemento PropertyName para ItemSelectionCondition para GroupBy (formato)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa el control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento PropertyName para ItemSelectionCondition para ListItem (formato)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la vista. Este elemento se usa al definir una vista de lista.

[Elemento PropertyName para ListItem para ListControl (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md) especifica la propiedad de .NET cuyo valor se muestra en la lista.

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento PropertyName para SelectionCondition para los controles de vista (formato)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento PropertyName para SelectionCondition para el control personalizado para la vista (formato)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición. Este elemento se usa al definir una vista de control personalizado.

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición.

[Elemento PropertyName para SelectionCondition para GroupBy (formato)](./propertyname-element-for-selectioncondition-for-groupby-format.md) especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento PropertyName para SelectionCondition para EmtrySelectedBy para ListEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada de la lista.

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada de tabla.

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición.

[Elemento PropertyName para TableColumnItem (formato)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) especifica la propiedad cuyo valor se muestra en la columna de la fila.

[Elemento PropertyName para WideItem (formato)](./propertyname-element-for-wideitem-for-widecontrol-format.md) especifica la propiedad del objeto cuyo valor se muestra en la vista ampliada.

[Elemento RightIndent marco para los controles de configuración (formato)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) especifica cuántos caracteres de los datos se desplazan fuera del margen derecho. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento RightIndent de marco de controles de vista (formato)](./rightindent-element-for-frame-for-controls-for-view-format.md) especifica cuántos caracteres de los datos se desplazan fuera del margen derecho. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) especifica cuántos caracteres de los datos se desplazan fuera del margen derecho. Este elemento se usa al definir una vista de control personalizado.

[Elemento RightIndent marco para GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md) especifica cuántos caracteres de los datos se desplazan fuera del margen derecho. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento de bloque de script para ExpressionBinding para los controles de configuración (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) especifica la secuencia de comandos cuyo valor se muestra el control común. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento de bloque de script para ExpressionBinding para los controles de vista (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) especifica la secuencia de comandos cuyo valor se muestra el control. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento de bloque de script para ExpressionBinding para CustomCustomControl para vista (formato)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) especifica la secuencia de comandos cuyo valor se muestra el control. Este elemento se usa al definir una vista de control personalizado.

[Elemento de bloque de script para ExpressionBinding para GroupBy (formato)](./scriptblock-element-for-expressionbinding-for-groupby-format.md) especifica la secuencia de comandos cuyo valor se muestra el control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento de bloque de script para GroupBy (formato)](./scriptblock-element-for-groupby-format.md) especifica la secuencia de comandos que se inicia un nuevo grupo cada vez que cambia su valor.

[Elemento de bloque de script para ItemSelectionCondition para los controles de configuración (formato)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) especifica la secuencia de comandos que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa el control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento de bloque de script para ItemSelectionCondition para los controles de vista (formato)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) especifica la secuencia de comandos que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa el control. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento de bloque de script para ItemSelectionCondition para el control personalizado para la vista (formato)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) especifica la secuencia de comandos que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa el control. Este elemento se usa al definir una vista de control personalizado.

[Elemento de bloque de script para ItemSelectionCondition para GroupBy (formato)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) especifica la secuencia de comandos que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa el control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento de bloque de script para ItemSelectionCondition de ListControl (formato)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) especifica la secuencia de comandos que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa el elemento de lista. Este elemento se usa al definir una vista de lista.

[Elemento de bloque de script para ListItem (formato)](./scriptblock-element-for-listitem-for-listcontrol-format.md) especifica la secuencia de comandos cuyo valor se muestra en la fila de la lista.

[Elemento de bloque de script para SelectionCondition para los controles de configuración (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) especifica la secuencia de comandos que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa la definición. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento de bloque de script para SelectionCondition para los controles de vista (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) especifica la secuencia de comandos que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa la definición. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento de bloque de script para SelectionCondition para el control personalizado para la vista (formato)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) especifica la secuencia de comandos que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa la definición. Este elemento se usa al definir una vista de control personalizado.

[Elemento de bloque de script para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) especifica la secuencia de comandos que desencadena la condición.

[Elemento de bloque de script para SelectionCondition para GroupBy (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) especifica la secuencia de comandos que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa la definición. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento de bloque de script para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) especifica la secuencia de comandos que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa la entrada de la lista.

[Elemento de bloque de script para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) especifica el bloque de script que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa la entrada de tabla.

[Elemento de bloque de script para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) especifica la secuencia de comandos que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se utiliza la definición de la entrada ancho.

[Elemento de bloque de script para TableColumnItem (formato)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) especifica la secuencia de comandos cuyo valor se muestra en la columna de la fila.

[Elemento de bloque de script para WideItem (formato)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) especifica la secuencia de comandos cuyo valor se muestra en la vista ampliada.

[Elemento SelectionCondition para EntrySelectedBy para CustomEntry para la configuración (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) define una condición que debe existir para que una definición común de control que se usará. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento SelectionCondition para EntrySelectedBy para los controles de vista (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) define una condición que debe cumplirse para que se usará la definición del control. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento SelectionCondition para EntrySelectedBy para el control personalizado para la vista (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) define una condición que debe existir para usarse en una definición de control. Este elemento se usa al definir una vista de control personalizado.

[Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) define la condición que debe existir para expandir los objetos de la colección de esta definición.

[Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) define una condición que debe existir para usarse en una definición de control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) define la condición que debe existir para usar esta definición de la vista de lista. No hay ningún límite al número de condiciones de selección que se pueden especificar para una definición de lista.

[Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) define la condición que debe existir para que use para esta definición de la vista de tabla. No hay ningún límite al número de condiciones de selección que se pueden especificar para una definición de tabla.

[Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) define la condición que debe existir para que esta definición para usarse. No hay ningún límite al número de condiciones de selección que se pueden especificar para una definición de entrada amplia.

[Elemento SelectionSet (formato)](./selectionset-element-format.md) define un conjunto de objetos .NET que se puede hacer referencia por el nombre del conjunto.

[Elemento SelectionSetName para EntrySelectedBy para los controles de configuración (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) especifica un conjunto de tipos de .NET que usan esta definición del control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento SelectionSetName para EntrySelectedBy para los controles de vista (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) especifica un conjunto de tipos de .NET que usan esta definición del control. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento SelectionSetName para EntrySelectedBy para CustomEntry (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) especifica un conjunto de objetos de .NET para la entrada de la lista. No hay ningún límite al número de conjuntos de selección que se pueden especificar para una entrada.

[Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) especifica el conjunto de tipos de .NET que se expanden por esta definición.

[Elemento SelectionSetName para EntrySelectedBy para GroupBy (formato)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) especifica un conjunto de objetos de .NET para la entrada de la lista. No hay ningún límite al número de conjuntos de selección que se pueden especificar para una entrada. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento SelectionSetName para EntrySelectedBy para ListEntry (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) especifica un conjunto de objetos de .NET para la entrada de la lista. No hay ningún límite al número de conjuntos de selección que se pueden especificar para una entrada.

[Elemento SelectionSetName para EntrySelectedBy para TableRowEntry (formato)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) especifica un conjunto de .NET tipos el uso de esta entrada de la vista de tabla. No hay ningún límite al número de conjuntos de selección que se pueden especificar para una entrada.

[Elemento SelectionSetName para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) especifica un conjunto de objetos de .NET para la definición. La definición se usa siempre que se muestra uno de estos objetos.

[Elemento SelectionSetName para SelectionCondition para los controles de configuración (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) especifica el conjunto de tipos de .NET que la condición desencadenadora. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante el uso de este control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento SelectionSetName para SelectionCondition para los controles de vista (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) especifica el conjunto de tipos de .NET que la condición desencadenadora. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra el uso de este control. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento EntrySelectedBy para CustomEntry para vista (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) especifica el conjunto de tipos de .NET que la condición desencadenadora. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra el uso de este control. Este elemento se usa al definir una vista de control personalizado.

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) especifica el conjunto de tipos de .NET que la condición desencadenadora. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición.

[Elemento SelectionSetName para SelectionCondition para GroupBy (formato)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) especifica el conjunto de tipos de .NET que la condición desencadenadora. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante el uso de este control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) especifica el conjunto de tipos de .NET que la condición desencadenadora. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante el uso de esta definición de la vista de lista.

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) especifica el conjunto de tipos de .NET que la condición desencadenadora. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante el uso de esta definición de la vista de tabla.

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) especifica el conjunto de tipos de .NET que la condición desencadenadora. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante el uso de esta definición de la vista ampliada.

[Elemento SelectionSetName para ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md) especifica un conjunto de objetos .NET que se muestran en la vista.

[Elemento SelectionSets (formato)](./selectionsets-element-format.md) define los conjuntos de objetos de .NET que se pueden usar las vistas individuales de formato.

[Elemento ShowError (formato)](./showerror-element-format.md) especifica que el registro de error completo se muestra cuando se produce un error mientras se muestra un fragmento de datos.

[Elemento TableColumnHeader para TableHeaders para TableControl (formato)](./tablecolumnheader-element-format.md) define la etiqueta, el ancho de la columna y la alineación de la etiqueta de una columna de la tabla.

[Elemento TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) define la propiedad o el script cuyo valor se muestra en la columna de la fila.

[Elemento TableColumnItems (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) define las propiedades o scripts cuyos valores se muestran en la fila.

[Elemento TableControl (formato)](./tablecontrol-element-format.md) define un formato de tabla para obtener una vista.

[Elemento TableHeaders (formato)](./tableheaders-element-format.md) define los encabezados de las columnas de una tabla.

[Elemento TableRowEntries (formato)](./tablerowentries-element-for-tablecontrol-format.md) define las filas de la tabla.

[Elemento TableRowEntry (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) define los datos que se muestran en una fila de la tabla.

[Elemento de texto para CustomItem para los controles de configuración (formato)](./text-element-for-customitem-for-controls-for-configuration-format.md) especifica texto que se agrega a los datos que se muestran el control, como una etiqueta, corchetes para encerrar los datos y los espacios para aplicar sangría a los datos. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento de texto para CustomItem para los controles de vista (formato)](./text-element-for-customitem-for-controls-for-view-format.md) especifica texto que se agrega a los datos que se muestran el control, como una etiqueta, corchetes para encerrar los datos y los espacios para aplicar sangría a los datos. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento de texto para CustomItem (formato)](./text-element-for-customitem-for-customview-for-view-format.md) especifica texto que se agrega a los datos que se muestran el control, como una etiqueta, corchetes para encerrar los datos y los espacios para aplicar sangría a los datos. Este elemento se usa al definir una vista de control personalizado.

[Elemento de texto para CustomItem para GroupBy (formato)](./text-element-for-customitem-for-groupby-format.md) especifica texto que se agrega a los datos que se muestran el control, como una etiqueta, corchetes para encerrar los datos y los espacios para aplicar sangría a los datos. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento TypeName para EntrySelectedBy para los controles de configuración (formato)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) especifica un tipo .NET que usa esta definición del control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento TypeName para EntrySelectedBy para los controles de vista (formato)](./typename-element-for-entryselectedby-for-controls-for-view-format.md) especifica un tipo .NET que usa esta definición del control. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento TypeName para EntrySelectedBy para CustomEntry para vista (formato)](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) especifica un tipo .NET que usa esta definición de la vista de control personalizado. No hay ningún límite al número de tipos que se pueden especificar para una definición.

[Elemento TypeName para EntrySelectedBy para EnumerableExpansion (formato)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) especifica un tipo .NET que se expande por esta definición. Este elemento se usa al definir una configuración predeterminada.

[Elemento TypeName para EntrySelectedBy para GroupBy (formato)](./typename-element-for-entryselectedby-for-groupby-format.md) especifica un tipo .NET que usa esta definición del control personalizado. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento TypeName para EntrySelectedBy de ListControl (formato)](./typename-element-for-entryselectedby-for-listcontrol-format.md) especifica un tipo .NET que usa esta entrada de la vista de lista. No hay ningún límite al número de tipos que se pueden especificar para una entrada de lista.

[Elemento TypeName para EntrySelectedBy para TableRowEntry (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md) especifica un tipo .NET que usa esta entrada de la vista de tabla. No hay ningún límite al número de tipos que se pueden especificar para una entrada de tabla.

[Elemento TypeName para EntrySelectedBy para WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md) especifica un tipo de .NET para la definición. La definición se usa siempre que se muestra este objeto.

[Elemento TypeName para SelectionCondition para los controles de configuración (formato)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) especifica un tipo .NET que desencadena la condición. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

[Elemento TypeName para SelectionCondition para los controles de vista (formato)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) especifica un tipo .NET que desencadena la condición. Este elemento se usa al definir los controles que pueden usarse en una vista.

[Elemento TypeName para SelectionCondition para el control personalizado para la vista (formato)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) especifica un tipo .NET que desencadena la condición. Este elemento se usa al definir una vista de control personalizado.

[Elemento TypeName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) especifica un tipo .NET que desencadena la condición.

[Elemento TypeName para SelectionCondition para GroupBy (formato)](./typename-element-for-selectioncondition-for-groupby-format.md) especifica un tipo .NET que desencadena la condición. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

[Elemento TypeName para SelectionCondition para EntrySelectedBy para ListControl (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) especifica un tipo .NET que desencadena la condición. Cuando este tipo está presente, se usa la entrada de la lista.

[Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) especifica un tipo .NET que desencadena la condición. Cuando este tipo está presente, se cumple la condición y se utiliza la fila de tabla.

[Elemento TypeName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) especifica un tipo .NET que desencadena la condición. Cuando este tipo está presente, se utiliza la definición.

[Elemento TypeName para tipos (formato)](./typename-element-for-types-format.md) especifica el tipo de .NET de un objeto al que pertenece al conjunto de selección.

[Elemento TypeName para ViewSelectedBy (formato)](./typename-element-for-viewselectedby-format.md) especifica un objeto .NET que se muestra la vista.

[Los tipos de elemento (formato)](./types-element-for-selectionset-format.md) define los objetos de .NET que están en la selección de conjunto.

[Ver elemento (formato)](./view-element-format.md) define una vista que se usa para mostrar uno o varios objetos. NET.

[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md) define las vistas que se usa para mostrar los objetos.

[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md) define los objetos de .NET que se muestran en la vista.

[Elemento WideControl (formato)](./widecontrol-element-format.md) define una lista de todo (valor single) de formato para la vista. Esta vista muestra un solo valor de propiedad o valor de la secuencia de comandos para cada objeto.

[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md) proporciona las definiciones de la vista ampliada. La vista ampliada debe especificar una o varias definiciones.

[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md) proporciona una definición de la vista ampliada.

[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md) define la propiedad o el script cuyo valor se muestra.

[Elemento ancho (formato)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) define el ancho (en caracteres) de una columna.

[Ajustar elemento (formato)](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) especifica que el texto que supera el ancho de columna se muestra en la línea siguiente.

[Elemento WrapTables (formato)](./wraptables-element-format.md) especifica que los datos de una celda de tabla se mueven a la línea siguiente si los datos están mayor que el ancho de la columna.

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
