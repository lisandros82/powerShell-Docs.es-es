---
title: Elemento DisplayError (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363994"
---
# <a name="displayerror-element-format"></a>Elemento DisplayError (formato)

Especifica que el #ERR de cadena se muestra cuando se produce un error que muestra un fragmento de datos.

Elemento Configuration (Format) elemento DefaultSettings (Format) elemento DisplayError (Format)

## <a name="syntax"></a>Sintaxis

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `DisplayError`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[DefaultSettings (elemento, Format)](./defaultsettings-element-format.md)|Define la configuración común que se aplica a todas las vistas del archivo de formato.|

## <a name="remarks"></a>Observaciones

De forma predeterminada, cuando se produce un error al intentar mostrar un fragmento de datos, la ubicación de los datos se deja en blanco. Cuando este elemento se establece en true, se mostrará la cadena de #ERR.

## <a name="see-also"></a>Véase también

[DefaultSettings (elemento, Format)](./defaultsettings-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
