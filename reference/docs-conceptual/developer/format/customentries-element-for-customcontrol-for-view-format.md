---
title: Elemento CustomEntries para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364084"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>Elemento CustomEntries para CustomControl for GroupBy (formato)

Proporciona las definiciones de la vista de control personalizada. La vista de control personalizada debe especificar una o más definiciones.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl para View (Format)

## <a name="syntax"></a>Sintaxis

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomControlEntries`. Debe especificar uno o varios elementos secundarios.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomEntries para View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Elemento obligatorio.<br /><br /> Proporciona una definición de la vista de control personalizada.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomControl para View (Format)](./customcontrol-element-for-view-format.md)|Elemento obligatorio.<br /><br /> Define un formato de control personalizado para la vista.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, un control solo tiene una definición, que se define en un único elemento `CustomEntry`. Sin embargo, es posible tener varias definiciones si desea utilizar el mismo control para mostrar objetos .NET diferentes. En esos casos, puede definir un elemento `CustomEntry` para cada objeto o conjunto de objetos.

## <a name="see-also"></a>Véase también

[Elemento CustomControl para View (Format)](./customcontrol-element-for-view-format.md)

[Elemento CustomEntry para CustomEntries para View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
