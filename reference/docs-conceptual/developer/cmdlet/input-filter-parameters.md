---
title: Parámetros de filtro de entrada | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364394"
---
# <a name="input-filter-parameters"></a>Parámetros de filtros de entrada

Un cmdlet puede definir parámetros `Filter`, `Include` y `Exclude` que filtren el conjunto de objetos de entrada al que afecta el cmdlet.

Normalmente, el conjunto de objetos de entrada se especifica mediante un parámetro `InputObject`, `Path` o `Name`. Por ejemplo, un cmdlet puede tener un parámetro `Path` que acepta varias rutas de acceso mediante el uso de caracteres comodín y cada ruta de acceso señala a un objeto de entrada. En conjunto, los parámetros `Filter`, `Include` y `Exclude` califican aún más las rutas de acceso en las que funciona el cmdlet cada vez que se invoca.

## <a name="include-and-exclude-parameters"></a>Parámetros include y Exclude

Los parámetros `Include` y `Exclude` identifican los objetos que se incluyen o excluyen del conjunto de objetos de entrada pasados al cmdlet. Utilice estos parámetros cuando el filtro se puede expresar en el lenguaje de caracteres comodín estándar. (Para obtener más información sobre los caracteres comodín, vea [admitir caracteres comodín en parámetros de cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md)). El parámetro `Include` incluye todos los objetos cuyos nombres coinciden con el filtro de inclusión. El parámetro `Exclude` excluye todos los objetos cuyos nombres coinciden con el filtro.

## <a name="filter-parameter"></a>Parámetro de filtro

El parámetro `Filter` especifica un filtro que no se expresa en el lenguaje de caracteres comodín estándar. Por ejemplo, Active Directory las interfaces de servicio (ADSI) o los filtros SQL se pueden pasar al cmdlet a través de su parámetro `Filter`. En los cmdlets proporcionados por Windows PowerShell, estos filtros se especifican mediante los proveedores de Windows PowerShell que usan el cmdlet para tener acceso a un almacén de datos. Cada proveedor define normalmente su propio filtro.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Filtrar si no se especifica ningún conjunto de objetos de entrada

Si no se especifica ningún conjunto de objetos de entrada, normalmente significa que se filtren todos los objetos. Para obtener más información, vea[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)