---
title: Elemento CustomEntries para CustomControl para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368814"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>Elemento CustomEntries para CustomControl for Controls for View (formato)

Proporciona las definiciones para el control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para controles para View (Format)

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
|[Elemento CustomEntry para CustomEntries para controles para View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Elemento obligatorio.<br /><br /> Proporciona una definición del control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomControl para el control de los controles de View (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Define el control utilizado por la vista.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, un control solo tiene una definición, que se especifica en un único elemento `CustomEntry`. Sin embargo, es posible proporcionar varias definiciones si desea utilizar el mismo control para mostrar objetos .NET diferentes. En esos casos, puede definir un elemento `CustomEntry` para cada objeto o conjunto de objetos.

## <a name="see-also"></a>Véase también

[Elemento CustomEntry para CustomEntries para controles para View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Elemento CustomControl para el control de los controles de View (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
