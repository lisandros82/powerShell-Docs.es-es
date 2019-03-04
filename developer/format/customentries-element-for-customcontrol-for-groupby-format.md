---
title: Elemento CustomEntries para el control personalizado para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853681"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>Elemento CustomEntries para CustomControl for GroupBy (formato)

Proporciona las definiciones para el control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento para el elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado para GroupBy (formato)

## <a name="syntax"></a>Sintaxis

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elementos primarios de la `CustomEntries` elemento. No hay ningún límite máximo para el número de elementos secundarios que se pueden especificar.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para el control personalizado para GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md)|Elemento necesario.<br /><br /> Proporciona una definición del control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de control personalizado para GroupBy (formato)](./customcontrol-element-for-groupby-format.md)|Define el control personalizado que muestra el nuevo grupo.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, un control tiene solo una definición, que se especifica en una sola `CustomEntry` elemento. Sin embargo, es posible proporcionar varias definiciones si desea utilizar el mismo control para mostrar los diferentes grupos. En esos casos, puede definir un `CustomEntry` (elemento) para un grupo.

## <a name="see-also"></a>Véase también

[Elemento CustomEntry para CustomEntries para los controles de vista (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Elemento de control personalizado para GroupBy (formato)](./customcontrol-element-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
