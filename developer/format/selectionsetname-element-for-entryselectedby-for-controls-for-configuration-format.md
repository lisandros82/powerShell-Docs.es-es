---
title: Elemento SelectionSetName para EntrySelectedBy para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064012"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a>Elemento SelectionSetName para EntrySelectedBy for Controls for Configuration (formato)

Especifica un conjunto de tipos de .NET que usan esta definición del control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) EntrySelectedBy para CustomEntry para los controles de elemento de configuración (formato) SelectionSetName para EntrySelectedBy para los controles de configuración (formato)

## <a name="syntax"></a>Sintaxis

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.

### <a name="attributes"></a>Atributos

Ninguno

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry para los controles de configuración (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

Cada definición de control debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.

Conjuntos de selección se usan normalmente cuando desea definir un grupo de objetos que se usan en varias vistas. Para obtener más información acerca de cómo definir conjuntos de selección, consulte [definir selección establece](./defining-selection-sets.md).

## <a name="see-also"></a>Véase también

[Elemento EntrySelectedBy para CustomEntry para los controles de configuración (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
