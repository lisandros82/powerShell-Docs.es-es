---
title: Elemento CustomEntries para CustomControl para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364094"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>Elemento CustomEntries para CustomControl for GroupBy (formato)

Proporciona las definiciones para el control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para GroupBy (Format)

## <a name="syntax"></a>Sintaxis

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `CustomEntries`. No hay ningún límite máximo para el número de elementos secundarios que se pueden especificar.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomControl para GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Elemento obligatorio.<br /><br /> Proporciona una definición del control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomControl para GroupBy (Format)](./customcontrol-element-for-groupby-format.md)|Define el control personalizado que muestra el nuevo grupo.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, un control solo tiene una definición, que se especifica en un único elemento `CustomEntry`. Sin embargo, es posible proporcionar varias definiciones si desea utilizar el mismo control para mostrar grupos diferentes. En esos casos, puede definir un elemento `CustomEntry` para un grupo.

## <a name="see-also"></a>Véase también

[Elemento CustomEntry para CustomEntries para controles para View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Elemento CustomControl para GroupBy (Format)](./customcontrol-element-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
