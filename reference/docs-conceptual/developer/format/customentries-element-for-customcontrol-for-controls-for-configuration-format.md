---
title: Elemento CustomEntries para CustomControl para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368824"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>Elemento CustomEntries para CustomControl for Controls for Configuration (formato)

Proporciona las definiciones de un control común. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Aplique

## <a name="syntax"></a>Sintaxis

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomEntries`. Debe especificar uno o varios elementos secundarios.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomControl para los controles de configuración (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Proporciona una definición del control común.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomControl para el control de la configuración (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Define un control común.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, un control solo tiene una definición, que se define en un único elemento `CustomEntry`. Sin embargo, es posible tener varias definiciones si desea utilizar el mismo control para mostrar objetos .NET diferentes. En esos casos, puede definir un elemento `CustomEntry` para cada objeto o conjunto de objetos.

## <a name="see-also"></a>Véase también

[Elemento CustomControl para el control de la configuración (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Elemento CustomEntry para CustomControl para los controles de configuración (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
