---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a>Recursos de DSC basados en clases

## <a name="defining-dsc-resources-with-classes"></a>Definir recursos de DSC con clases

En función de los comentarios, hemos simplificado la creación de recursos de DSC basados en clases y ahora son más fáciles de entender. Las principales diferencias entre un recurso de DSC basado en clases y un proveedor de recursos de DSC de cmdlet son:

* No es necesario un archivo MOF para el esquema.
* No se necesita una subcarpeta **DSCResource** en la carpeta del módulo.
* Un archivo de módulo de PowerShell puede contener varias clases de recursos de DSC.

Para más información, consulte [Escribir un recurso de DSC personalizado con clases de PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).

