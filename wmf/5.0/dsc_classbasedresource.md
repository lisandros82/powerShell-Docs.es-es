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
# <a name="class-based-dsc-resources"></a><span data-ttu-id="33a3f-102">Recursos de DSC basados en clases</span><span class="sxs-lookup"><span data-stu-id="33a3f-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="33a3f-103">Definir recursos de DSC con clases</span><span class="sxs-lookup"><span data-stu-id="33a3f-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="33a3f-104">En función de los comentarios, hemos simplificado la creación de recursos de DSC basados en clases y ahora son más fáciles de entender.</span><span class="sxs-lookup"><span data-stu-id="33a3f-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span> <span data-ttu-id="33a3f-105">Las principales diferencias entre un recurso de DSC basado en clases y un proveedor de recursos de DSC de cmdlet son:</span><span class="sxs-lookup"><span data-stu-id="33a3f-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="33a3f-106">No es necesario un archivo MOF para el esquema.</span><span class="sxs-lookup"><span data-stu-id="33a3f-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="33a3f-107">No se necesita una subcarpeta **DSCResource** en la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="33a3f-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="33a3f-108">Un archivo de módulo de PowerShell puede contener varias clases de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="33a3f-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="33a3f-109">Para más información, consulte [Escribir un recurso de DSC personalizado con clases de PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="33a3f-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>

