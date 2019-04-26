---
title: Elemento CustomEntries para el control personalizado para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066607"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>Elemento CustomEntries para CustomControl for Controls for Configuration (formato)

Proporciona las definiciones de un control común. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Formato)

## <a name="syntax"></a>Sintaxis

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomEntries` elemento. Debe especificar uno o más elementos secundarios.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para el control personalizado para los controles de configuración (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Proporciona una definición del control común.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de control personalizado para el Control de configuración (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Define un control común.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, un control tiene solo una definición, que se define en una sola `CustomEntry` elemento. Sin embargo es posible tener varias definiciones si desea utilizar el mismo control para mostrar diferentes objetos. NET. En esos casos, puede definir un `CustomEntry` (elemento) para cada objeto o conjunto de objetos.

## <a name="see-also"></a>Véase también

[Elemento de control personalizado para el Control de configuración (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Elemento CustomEntry para el control personalizado para los controles de configuración (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
