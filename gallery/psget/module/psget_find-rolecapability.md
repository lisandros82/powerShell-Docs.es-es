---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-RoleCapability
ms.openlocfilehash: 89aacd604d54f6a5e9752790be65cc3bcc77c8e1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="find-rolecapability"></a><span data-ttu-id="d594e-103">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="d594e-103">Find-RoleCapability</span></span>

<span data-ttu-id="d594e-104">Busca funcionalidades de rol en módulos.</span><span class="sxs-lookup"><span data-stu-id="d594e-104">Finds role capabilities in modules.</span></span>

## <a name="description"></a><span data-ttu-id="d594e-105">Descripción</span><span class="sxs-lookup"><span data-stu-id="d594e-105">Description</span></span>
<span data-ttu-id="d594e-106">El cmdlet Find-RoleCapability busca funcionalidades de rol de PowerShell en módulos.</span><span class="sxs-lookup"><span data-stu-id="d594e-106">The Find-RoleCapability cmdlet finds PowerShell role capabilities in modules.</span></span> <span data-ttu-id="d594e-107">Find-RoleCapability busca en los módulos de los repositorios registrados.</span><span class="sxs-lookup"><span data-stu-id="d594e-107">Find-RoleCapability searches modules in registered repositories.</span></span>
<span data-ttu-id="d594e-108">Para cada funcionalidad de rol que este cmdlet encuentre, se devuelve un objeto PSGetRoleCapabilityInfo.</span><span class="sxs-lookup"><span data-stu-id="d594e-108">For each role capability that this cmdlet finds, it returns a PSGetRoleCapabilityInfo object.</span></span> <span data-ttu-id="d594e-109">Puede pasar un objeto PSGetRoleCapabilityInfo al cmdlet Install-Module para instalar el módulo que contiene la funcionalidad de rol.</span><span class="sxs-lookup"><span data-stu-id="d594e-109">You can pass a PSGetRoleCapabilityInfo object to the Install-Module cmdlet to install the module that contains the role capability.</span></span>
<span data-ttu-id="d594e-110">Las funcionalidades de rol de PowerShell definen los comandos, las aplicaciones, etc., que están disponibles para un usuario en un punto de conexión de Just Enough Administration (JEA).</span><span class="sxs-lookup"><span data-stu-id="d594e-110">PowerShell role capabilities define which commands, applications, and so on are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="d594e-111">Las funcionalidades de rol se definen mediante archivos con la extensión .psrc.</span><span class="sxs-lookup"><span data-stu-id="d594e-111">Role capabilities are defined by files with a .psrc extension.</span></span>

- <span data-ttu-id="d594e-112">Find-RoleCapability puede filtrar con parámetros de versión: MinimumVersion, RequiredVersion y AllVersions.</span><span class="sxs-lookup"><span data-stu-id="d594e-112">Find-RoleCapability can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="d594e-113">Estos parámetros se excluyen mutuamente.</span><span class="sxs-lookup"><span data-stu-id="d594e-113">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="d594e-114">Estos parámetros de versión solo se permiten con el nombre de módulo único sin ningún carácter comodín.</span><span class="sxs-lookup"><span data-stu-id="d594e-114">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="d594e-115">Si no se especifica el parámetro RequiredVersion, Find-RoleCapability devuelve la versión más reciente del módulo que sea igual o mayor que la versión mínima especificada, o la versión más reciente del módulo si no se especifica ninguna versión mínima.</span><span class="sxs-lookup"><span data-stu-id="d594e-115">If the RequiredVersion parameter is not specified, Find-RoleCapability returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="d594e-116">Si se especifica el parámetro RequiredVersion, Find-RoleCapability solo devuelve la versión del módulo que coincida exactamente con la versión especificada.</span><span class="sxs-lookup"><span data-stu-id="d594e-116">If the RequiredVersion parameter is specified, Find-RoleCapability only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="d594e-117">Find-RoleCapability puede filtrar por los metadatos del módulo con el parámetro -Tag.</span><span class="sxs-lookup"><span data-stu-id="d594e-117">Find-RoleCapability can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="d594e-118">Find-RoleCapability puede filtrar por el idioma de búsqueda específico del repositorio con el parámetro -Filter.</span><span class="sxs-lookup"><span data-stu-id="d594e-118">Find-RoleCapability can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="d594e-119">Find-RoleCapability puede filtrar por los módulos de todos o algunos de los repositorios registrados.</span><span class="sxs-lookup"><span data-stu-id="d594e-119">Find-RoleCapability can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="d594e-120">Sintaxis de cmdlet</span><span class="sxs-lookup"><span data-stu-id="d594e-120">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="d594e-121">Referencia de la ayuda en línea de cmdlet</span><span class="sxs-lookup"><span data-stu-id="d594e-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="d594e-122">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="d594e-122">Find-RoleCapability</span></span>](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a><span data-ttu-id="d594e-123">Comandos de ejemplo</span><span class="sxs-lookup"><span data-stu-id="d594e-123">Example commands</span></span>
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```