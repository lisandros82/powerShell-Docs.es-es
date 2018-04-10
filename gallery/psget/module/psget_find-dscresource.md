---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-DscResource
ms.openlocfilehash: 522a44e25c57a7dd75a098a1f34e53e74d96f4a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="find-dscresource"></a><span data-ttu-id="31b05-103">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="31b05-103">Find-DscResource</span></span>

<span data-ttu-id="31b05-104">Encuentra recursos de DSC en módulos.</span><span class="sxs-lookup"><span data-stu-id="31b05-104">Finds DSC Resources in modules.</span></span>

## <a name="description"></a><span data-ttu-id="31b05-105">Descripción</span><span class="sxs-lookup"><span data-stu-id="31b05-105">Description</span></span>

<span data-ttu-id="31b05-106">El cmdlet Find-DscResource busca recursos de [configuración de estado deseado (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) contenidos en módulos que coincidan con los criterios especificados desde repositorios registrados.</span><span class="sxs-lookup"><span data-stu-id="31b05-106">The Find-DscResource cmdlet finds [Desired State Configuration (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) resources contained in modules that match the specified criteria from registered repositories.</span></span>
<span data-ttu-id="31b05-107">Para cada módulo detectado por este cmdlet, Find-DscResource devuelve un objeto PSGetDscResourceInfo que se puede canalizar a Install-Module para instalar los módulos que contienen los recursos que este cmdlet devuelve.</span><span class="sxs-lookup"><span data-stu-id="31b05-107">For each module that this cmdlet finds, Find-DscResource returns a PSGetDscResourceInfo object that you can pipe to Install-Module to install the modules containing the resources that this cmdlet returns.</span></span>

<span data-ttu-id="31b05-108">DSC es una nueva plataforma de administración de Windows PowerShell que permite implementar y administrar datos de configuración de servicios de software y administrar el entorno en el que se ejecutan estos servicios.</span><span class="sxs-lookup"><span data-stu-id="31b05-108">DSC is a new management platform in Windows PowerShell that enables deploying and managing configuration data for software services and managing the environment in which these services run.</span></span>

<span data-ttu-id="31b05-109">Los recursos de la configuración de estado deseado (DSC) ofrecen los bloques de creación para una configuración DSC.</span><span class="sxs-lookup"><span data-stu-id="31b05-109">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="31b05-110">Un recurso expone las propiedades que se pueden configurar (el esquema) y contiene las funciones de script de PowerShell a las que el administrador de configuración local (LCM) llama para "que sea así".</span><span class="sxs-lookup"><span data-stu-id="31b05-110">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="31b05-111">Un recurso puede modelar algo tan genérico como un archivo o tan específico como una configuración de servidor IIS.</span><span class="sxs-lookup"><span data-stu-id="31b05-111">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="31b05-112">Grupos de recursos similares se combinan en un módulo de DSC, que organiza todos los archivos necesarios en una estructura portátil que incluye los metadatos para identificar cómo están diseñados para usarse los recursos.</span><span class="sxs-lookup"><span data-stu-id="31b05-112">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

- <span data-ttu-id="31b05-113">Find-DscResource puede filtrar con parámetros de versión: MinimumVersion, RequiredVersion y AllVersions.</span><span class="sxs-lookup"><span data-stu-id="31b05-113">Find-DscResource can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="31b05-114">Estos parámetros se excluyen mutuamente.</span><span class="sxs-lookup"><span data-stu-id="31b05-114">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="31b05-115">Estos parámetros de versión solo se permiten con el nombre de módulo único sin ningún carácter comodín.</span><span class="sxs-lookup"><span data-stu-id="31b05-115">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="31b05-116">Si no se especifica el parámetro RequiredVersion, Find-DscResource devuelve la versión más reciente del módulo que sea igual o mayor que la versión mínima especificada, o la versión más reciente del módulo si no se especifica ninguna versión mínima.</span><span class="sxs-lookup"><span data-stu-id="31b05-116">If the RequiredVersion parameter is not specified, Find-DscResource returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="31b05-117">Si se especifica el parámetro RequiredVersion, Find-DscResource solo devuelve la versión del módulo que coincida exactamente con la versión especificada.</span><span class="sxs-lookup"><span data-stu-id="31b05-117">If the RequiredVersion parameter is specified, Find-DscResource only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="31b05-118">Find-DscResource puede filtrar por los metadatos del módulo con el parámetro -Tag.</span><span class="sxs-lookup"><span data-stu-id="31b05-118">Find-DscResource can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="31b05-119">Find-DscResource puede filtrar por el idioma de búsqueda específico del repositorio con el parámetro -Filter.</span><span class="sxs-lookup"><span data-stu-id="31b05-119">Find-DscResource can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="31b05-120">Find-DscResource puede filtrar por los módulos de todos o algunos de los repositorios registrados.</span><span class="sxs-lookup"><span data-stu-id="31b05-120">Find-DscResource can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="31b05-121">Sintaxis de cmdlet</span><span class="sxs-lookup"><span data-stu-id="31b05-121">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="31b05-122">Referencia de la ayuda en línea de cmdlet</span><span class="sxs-lookup"><span data-stu-id="31b05-122">Cmdlet online help reference</span></span>

[<span data-ttu-id="31b05-123">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="31b05-123">Find-DscResource</span></span>](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a><span data-ttu-id="31b05-124">Comandos de ejemplo</span><span class="sxs-lookup"><span data-stu-id="31b05-124">Example commands</span></span>
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```