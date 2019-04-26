---
title: Elemento DefaultSettings (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066352"
---
# <a name="defaultsettings-element-format"></a>Elemento DefaultSettings (formato)

Define la configuración común que se aplica a todas las vistas del archivo de formato. Configuración común incluye presentación de errores, ajuste de texto en las tablas, definir cómo se expanden las colecciones y mucho más.

Elemento de configuración (formato) elemento DefaultSettings (formato)

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

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `DefaultSettings` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento DisplayError (formato)](./displayerror-element-format.md)|Elemento opcional.<br /><br /> Especifica que la cadena #ERR se muestra cuando se produce un error mientras se muestra un fragmento de datos.|
|[Elemento EnumerableExpansions (formato)](./enumerableexpansions-element-format.md)|Elemento opcional.<br /><br /> Define las distintas formas en que los objetos de .NET se expanden cuando se muestran en una vista.|
|[PropertyCountForTable (Format)](./propertycountfortable-element-format.md)|Elemento opcional.<br /><br /> Especifica el número mínimo de propiedades que debe tener un objeto para mostrar el objeto en una vista de tabla.|
|[Elemento ShowError (formato)](./showerror-element-format.md)|Elemento opcional.<br /><br /> Especifica que el registro de error completo se muestra cuando se produce un error mientras se muestra un fragmento de datos.|
|[Elemento WrapTables (formato)](./wraptables-element-format.md)|Elemento opcional.<br /><br /> Especifica que los datos de una tabla se mueven a la línea siguiente si no cabe en el ancho de la columna.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de configuración](./configuration-element-format.md)|Representa el elemento de nivel superior de un archivo de formato.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento de configuración](./configuration-element-format.md)

[Elemento DisplayError (formato)](./displayerror-element-format.md)

[Elemento EnumerableExpansions (formato)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (Format)](./propertycountfortable-element-format.md)

[Elemento ShowError (formato)](./showerror-element-format.md)

[Elemento WrapTables (formato)](./wraptables-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
