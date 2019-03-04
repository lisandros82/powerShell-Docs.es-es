---
title: Elemento de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856331"
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

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Configuration` elemento. Este elemento debe ser el elemento raíz de cada archivo de formato, y este elemento debe contener al menos un elemento secundario.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Controles de elemento de configuración (formato)](./controls-element-for-configuration-format.md)|Elemento opcional.<br /><br /> Define los controles comunes que pueden usarse en todas las vistas del archivo de formato.|
|[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md)|Elemento opcional.<br /><br /> Define la configuración común que se aplica a todas las vistas del archivo de formato.|
|[Formato de elemento SelectionSets](./selectionsets-element-format.md)|Elemento opcional.<br /><br /> Define los conjuntos comunes de objetos .NET que pueden usarse en todas las vistas del archivo de formato.|
|[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md)|Elemento opcional.<br /><br /> Define las vistas que se usa para mostrar los objetos.|

### <a name="parent-elements"></a>Elementos primarios

Ninguna.

## <a name="remarks"></a>Observaciones

Archivos de formato definen cómo se muestran los objetos. En la mayoría de los casos, este elemento de raíz contiene un [ViewDefinitions](./viewdefinitions-element-format.md) elemento que define la tabla, lista y vista amplia del archivo de formato. Además de las definiciones de vista, puede definir el archivo de formato comunes conjuntos de selección, configuración y los controles que pueden usar dichas vistas.

## <a name="see-also"></a>Véase también

[Controles de elemento de configuración (formato)](./controls-element-for-configuration-format.md)

[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md)

[Elemento SelectionSets (formato)](./selectionsets-element-format.md)

[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
