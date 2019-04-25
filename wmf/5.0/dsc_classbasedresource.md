---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058121"
---
# <a name="class-based-dsc-resources"></a>Recursos de DSC basados en clases

## <a name="defining-dsc-resources-with-classes"></a>Definir recursos de DSC con clases

En función de los comentarios, hemos simplificado la creación de recursos de DSC basados en clases y ahora son más fáciles de entender.
Las principales diferencias entre un recurso de DSC basado en clases y un proveedor de recursos de DSC de cmdlet son:

* No es necesario un archivo MOF para el esquema.
* No se necesita una subcarpeta **DSCResource** en la carpeta del módulo.
* Un archivo de módulo de PowerShell puede contener varias clases de recursos de DSC.

Para más información, consulte [Escribir un recurso de DSC personalizado con clases de PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).
