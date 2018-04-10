---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4def20aa95f66ab23c9eee575150bc3db02541d8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="class-based-dsc-resources"></a>Recursos de DSC basados en clases

## <a name="defining-dsc-resources-with-classes"></a>Definir recursos de DSC con clases

En función de los comentarios, hemos simplificado la creación de recursos de DSC basados en clases y ahora son más fáciles de entender.
Las principales diferencias entre un recurso de DSC basado en clases y un proveedor de recursos de DSC de cmdlet son:

* No es necesario un archivo MOF para el esquema.
* No se necesita una subcarpeta **DSCResource** en la carpeta del módulo.
* Un archivo de módulo de PowerShell puede contener varias clases de recursos de DSC.

Para más información, consulte [Escribir un recurso de DSC personalizado con clases de PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).