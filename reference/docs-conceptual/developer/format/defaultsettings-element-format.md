---
title: DefaultSettings (elemento, Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363874"
---
# <a name="defaultsettings-element-format"></a>Elemento DefaultSettings (formato)

Define la configuración común que se aplica a todas las vistas del archivo de formato. La configuración común incluye la visualización de errores, el ajuste de texto en tablas, la definición de cómo se expanden las colecciones y mucho más.

Elemento Configuration (Format) elemento DefaultSettings (Format)

## <a name="syntax"></a>Sintaxis

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `DefaultSettings`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento DisplayError (Format)](./displayerror-element-format.md)|Elemento opcional.<br /><br /> Especifica que el #ERR de cadena se muestra cuando se produce un error mientras se muestra un fragmento de datos.|
|[Elemento EnumerableExpansions (Format)](./enumerableexpansions-element-format.md)|Elemento opcional.<br /><br /> Define las diferentes formas en que los objetos .NET se expanden cuando se muestran en una vista.|
|[PropertyCountForTable (formato)](./propertycountfortable-element-format.md)|Elemento opcional.<br /><br /> Especifica el número mínimo de propiedades que un objeto debe tener para mostrar el objeto en una vista de tabla.|
|[Elemento ShowError (Format)](./showerror-element-format.md)|Elemento opcional.<br /><br /> Especifica que el registro de errores completo se muestra cuando se produce un error mientras se muestra un fragmento de datos.|
|[Elemento WrapTables (Format)](./wraptables-element-format.md)|Elemento opcional.<br /><br /> Especifica que los datos de una tabla se mueven a la línea siguiente si no caben en el ancho de la columna.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de configuración](./configuration-element-format.md)|Representa el elemento de nivel superior de un archivo de formato.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento de configuración](./configuration-element-format.md)

[Elemento DisplayError (Format)](./displayerror-element-format.md)

[Elemento EnumerableExpansions (Format)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (formato)](./propertycountfortable-element-format.md)

[Elemento ShowError (Format)](./showerror-element-format.md)

[Elemento WrapTables (Format)](./wraptables-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
