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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067695"
---
# <a name="input-filter-parameters"></a>Parámetros de filtros de entrada

Puede definir un cmdlet `Filter`, `Include`, y `Exclude` los parámetros que filtran el conjunto de objetos de entrada que afecta el cmdlet.

Normalmente, el conjunto de objetos de entrada especificado por un `InputObject`, `Path`, o `Name` parámetro. Por ejemplo, un cmdlet puede tener un `Path` parámetro que acepta varias rutas de acceso mediante el uso de caracteres comodín y los puntos de cada ruta de acceso a un objeto de entrada. Utilizar juntos, el `Filter`, `Include`, y `Exclude` más parámetros calificar las rutas de acceso que el cmdlet funciona en cada vez que se invoca.

## <a name="include-and-exclude-parameters"></a>Incluir y excluir los parámetros

El `Include` y `Exclude` parámetros identifican los objetos que se incluyen o excluyen del conjunto de objetos de entrada pasado al cmdlet. Use estos parámetros cuando el filtro se puede expresar en el lenguaje de comodín estándar. (Para obtener más información sobre los caracteres comodín, consulte [que admiten caracteres comodín en los parámetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).) El `Include` parámetro incluye todos los objetos cuyos nombres coincidan con el filtro de inclusión. El `Exclude` parámetro excluye todos los objetos cuyos nombres coincidan con el filtro.

## <a name="filter-parameter"></a>Parámetro de filtro

El `Filter` parámetro especifica un filtro que no se expresa en el lenguaje de comodín estándar. Por ejemplo, los filtros de las Interfaces de servicio de Active Directory (ADSI) o SQL podrían pasarse al cmdlet a través de su `Filter` parámetro. En los cmdlets proporcionados por Windows PowerShell, estos filtros se especifican mediante los proveedores de Windows PowerShell que use el cmdlet para obtener acceso a un almacén de datos. Cada proveedor normalmente define su propio filtro.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Si no se especifica ningún conjunto de objetos de entrada de filtrado

Si no se especifica ningún conjunto de objetos de entrada, normalmente esto significa que se filtrará todos los objetos. Para obtener más información, consulte[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)