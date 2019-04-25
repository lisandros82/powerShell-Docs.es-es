---
title: Elemento DisplayError (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066267"
---
# <a name="displayerror-element-format"></a>Elemento DisplayError (formato)

Especifica que la cadena #ERR se muestra cuando se produce un error al mostrar un elemento de datos.

Configuración (formato) elemento DefaultSettings (formato) DisplayError elemento (formato)

## <a name="syntax"></a>Sintaxis

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `DisplayError` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md)|Define la configuración común que se aplica a todas las vistas del archivo de formato.|

## <a name="remarks"></a>Observaciones

De forma predeterminada, cuando se produce un error al intentar mostrar un elemento de datos, la ubicación de los datos se deja en blanco. Cuando este elemento se establece en true, la cadena #ERR se mostrará.

## <a name="see-also"></a>Véase también

[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
