---
title: Elemento Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363504"
---
# <a name="configuration-element-format"></a>Elemento Configuration (formato)

Representa el elemento de nivel superior de un archivo de formato.

Elemento de configuración

## <a name="syntax"></a>Sintaxis

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Configuration`. Este elemento debe ser el elemento raíz de cada archivo de formato y este elemento debe contener al menos un elemento secundario.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Controls (elemento) para Configuration (Format)](./controls-element-for-configuration-format.md)|Elemento opcional.<br /><br /> Define los controles comunes que se pueden usar en todas las vistas del archivo de formato.|
|[DefaultSettings (elemento, Format)](./defaultsettings-element-format.md)|Elemento opcional.<br /><br /> Define la configuración común que se aplica a todas las vistas del archivo de formato.|
|[Formato del elemento SelectionSets](./selectionsets-element-format.md)|Elemento opcional.<br /><br /> Define los conjuntos comunes de objetos .NET que pueden ser utilizados por todas las vistas del archivo de formato.|
|[Elemento ViewDefinitions (Format)](./viewdefinitions-element-format.md)|Elemento opcional.<br /><br /> Define las vistas que se usan para mostrar los objetos.|

### <a name="parent-elements"></a>Elementos primarios

Ninguna.

## <a name="remarks"></a>Observaciones

Los archivos de formato definen cómo se muestran los objetos. En la mayoría de los casos, este elemento raíz contiene un elemento [ViewDefinitions](./viewdefinitions-element-format.md) que define las vistas de tabla, lista y ancho del archivo de formato. Además de las definiciones de vistas, el archivo de formato puede definir conjuntos de selección comunes, opciones y controles que estas vistas pueden utilizar.

## <a name="see-also"></a>Véase también

[Controls (elemento) para Configuration (Format)](./controls-element-for-configuration-format.md)

[DefaultSettings (elemento, Format)](./defaultsettings-element-format.md)

[Elemento SelectionSets (Format)](./selectionsets-element-format.md)

[Elemento ViewDefinitions (Format)](./viewdefinitions-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
