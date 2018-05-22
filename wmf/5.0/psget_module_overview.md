---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9efc640dfda7e08e59d2c56746facd9658b1f9de
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="16415-102">Detección, instalación e inventario del módulo de PowerShell con PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="16415-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>

<span data-ttu-id="16415-103">PowerShellGet se incluye en esta versión de WMF:</span><span class="sxs-lookup"><span data-stu-id="16415-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="16415-104">Find-Module puede filtrar por los metadatos del módulo con el parámetro -Tag.</span><span class="sxs-lookup"><span data-stu-id="16415-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="16415-105">Find-Module puede filtrar por el idioma de búsqueda específico del repositorio con el parámetro -Filter.</span><span class="sxs-lookup"><span data-stu-id="16415-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="16415-106">Find-Module puede filtrar por el contenido del módulo con los parámetros -Command, -DscResource e -Includes.</span><span class="sxs-lookup"><span data-stu-id="16415-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="16415-107">Find-DscResource permite la detección de recursos de DSC individuales en repositorios.</span><span class="sxs-lookup"><span data-stu-id="16415-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="16415-108">Soporte para la instalación y la publicación en recursos compartidos de archivos con NuGet.</span><span class="sxs-lookup"><span data-stu-id="16415-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="16415-109">Comandos de ejemplo</span><span class="sxs-lookup"><span data-stu-id="16415-109">Example commands</span></span>
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a><span data-ttu-id="16415-110">Nuevas características de PowerShell</span><span class="sxs-lookup"><span data-stu-id="16415-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="16415-111">Compatibilidad de versiones en paralelo en Windows PowerShell 5.0 o más reciente</span><span class="sxs-lookup"><span data-stu-id="16415-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="16415-112">Compatibilidad con la instalación de dependencias de módulo</span><span class="sxs-lookup"><span data-stu-id="16415-112">Module dependency installation support</span></span>
-   <span data-ttu-id="16415-113">Tres cmdlets nuevos</span><span class="sxs-lookup"><span data-stu-id="16415-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="16415-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="16415-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="16415-115">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="16415-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="16415-116">Save-Module</span><span class="sxs-lookup"><span data-stu-id="16415-116">Save-Module</span></span>
