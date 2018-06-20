---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221857"
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="73552-102">Recursos de DSC basados en clases</span><span class="sxs-lookup"><span data-stu-id="73552-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="73552-103">Definir recursos de DSC con clases</span><span class="sxs-lookup"><span data-stu-id="73552-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="73552-104">En función de los comentarios, hemos simplificado la creación de recursos de DSC basados en clases y ahora son más fáciles de entender.</span><span class="sxs-lookup"><span data-stu-id="73552-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="73552-105">Las principales diferencias entre un recurso de DSC basado en clases y un proveedor de recursos de DSC de cmdlet son:</span><span class="sxs-lookup"><span data-stu-id="73552-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="73552-106">No es necesario un archivo MOF para el esquema.</span><span class="sxs-lookup"><span data-stu-id="73552-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="73552-107">No se necesita una subcarpeta **DSCResource** en la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="73552-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="73552-108">Un archivo de módulo de PowerShell puede contener varias clases de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="73552-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="73552-109">Para más información, consulte [Escribir un recurso de DSC personalizado con clases de PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="73552-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
