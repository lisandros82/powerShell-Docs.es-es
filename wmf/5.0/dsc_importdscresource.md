---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680120"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="3e2de-102">La palabra clave Import-DscResource admite el parámetro -ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="3e2de-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="3e2de-103">Hemos agregado un nuevo parámetro para la palabra clave dinámica `Import-DscResource`, que está disponible al crear configuraciones de DSC.</span><span class="sxs-lookup"><span data-stu-id="3e2de-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="3e2de-104">Los autores de configuración pueden ahora especificar exactamente de qué versión del módulo se deben cargar los recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="3e2de-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="3e2de-105">La nueva sintaxis de la palabra clave es:</span><span class="sxs-lookup"><span data-stu-id="3e2de-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="3e2de-106">**Name**: nombres de uno o más recursos que se van a importar.</span><span class="sxs-lookup"><span data-stu-id="3e2de-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="3e2de-107">**ModuleName**: nombres de módulo o de objetos ModuleSpecification de uno o más módulos que se van a importar.</span><span class="sxs-lookup"><span data-stu-id="3e2de-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="3e2de-108">**ModuleVersion**: versión del módulo que se va a importar.</span><span class="sxs-lookup"><span data-stu-id="3e2de-108">**ModuleVersion**: Version of module to import.</span></span> <span data-ttu-id="3e2de-109">Si se usa, ModuleName debe representar un solo módulo por el nombre.</span><span class="sxs-lookup"><span data-stu-id="3e2de-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="3e2de-110">En Windows PowerShell ISE, se muestra con IntelliSense:</span><span class="sxs-lookup"><span data-stu-id="3e2de-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="3e2de-111">**Nota**: El parámetro `–ModuleVersion` solo puede usarse en combinación con el parámetro `–ModuleName`.</span><span class="sxs-lookup"><span data-stu-id="3e2de-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="3e2de-112">No puede usarse con nombres de recursos usando solo el parámetro `–Name`.</span><span class="sxs-lookup"><span data-stu-id="3e2de-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="3e2de-113">Anteriormente, la única manera de especificar la versión del módulo al cargar los recursos de DSC era mediante el objeto de especificación del módulo, como `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="3e2de-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>
