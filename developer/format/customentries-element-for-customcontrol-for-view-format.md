---
title: Elemento CustomEntries para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861701"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>Elemento CustomEntries para CustomControl for GroupBy (formato)

Proporciona las definiciones de la vista de control personalizado. La vista de control personalizado debe especificar una o varias definiciones.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado para la vista (formato)

## <a name="syntax"></a>Sintaxis

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomControlEntries` elemento. Debe especificar uno o más elementos secundarios.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomEntries para vista (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Elemento necesario.<br /><br /> Proporciona una definición de la vista de control personalizado.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de control personalizado para la vista (formato)](./customcontrol-element-for-view-format.md)|Elemento necesario.<br /><br /> Define un formato de control personalizado para la vista.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, un control tiene solo una definición, que se define en una sola `CustomEntry` elemento. Sin embargo es posible tener varias definiciones si desea utilizar el mismo control para mostrar diferentes objetos. NET. En esos casos, puede definir un `CustomEntry` (elemento) para cada objeto o conjunto de objetos.

## <a name="see-also"></a>Véase también

[Elemento de control personalizado para la vista (formato)](./customcontrol-element-for-view-format.md)

[Elemento CustomEntry para CustomEntries para vista (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
