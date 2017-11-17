---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-Command
ms.openlocfilehash: f867f12b1c6efad30a04581c6f36c5a77a2fb2ae
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="find-command"></a><span data-ttu-id="6e541-103">Find-Command</span><span class="sxs-lookup"><span data-stu-id="6e541-103">Find-Command</span></span>

<span data-ttu-id="6e541-104">Busca comandos de PowerShell en módulos.</span><span class="sxs-lookup"><span data-stu-id="6e541-104">Finds PowerShell commands in modules.</span></span>

## <a name="description"></a><span data-ttu-id="6e541-105">Descripción</span><span class="sxs-lookup"><span data-stu-id="6e541-105">Description</span></span>
<span data-ttu-id="6e541-106">El cmdlet Find-Command busca comandos de PowerShell, como cmdlets, alias, funciones y flujos de trabajo.</span><span class="sxs-lookup"><span data-stu-id="6e541-106">The Find-Command cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="6e541-107">Find-Command busca en los módulos de los repositorios registrados.</span><span class="sxs-lookup"><span data-stu-id="6e541-107">Find-Command searches modules in registered repositories.</span></span>
<span data-ttu-id="6e541-108">Para cada comando que este cmdlet encuentre, devuelve un objeto PSGetCommandInfo.</span><span class="sxs-lookup"><span data-stu-id="6e541-108">For each command that this cmdlet finds, it returns a PSGetCommandInfo object.</span></span> <span data-ttu-id="6e541-109">Puede pasar un objeto PSGetCommandInfo al cmdlet Install-Module para instalar el módulo que contiene el comando.</span><span class="sxs-lookup"><span data-stu-id="6e541-109">You can pass a PSGetCommandInfo object to the Install-Module cmdlet to install the module that contains the command.</span></span>

- <span data-ttu-id="6e541-110">Find-Command puede filtrar con parámetros de versión: MinimumVersion, RequiredVersion y AllVersions.</span><span class="sxs-lookup"><span data-stu-id="6e541-110">Find-Command can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="6e541-111">Estos parámetros se excluyen mutuamente.</span><span class="sxs-lookup"><span data-stu-id="6e541-111">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="6e541-112">Estos parámetros de versión solo se permiten con el nombre de módulo único sin ningún carácter comodín.</span><span class="sxs-lookup"><span data-stu-id="6e541-112">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="6e541-113">Si no se especifica el parámetro RequiredVersion, Find-Command devuelve la versión más reciente del módulo que sea igual o mayor que la versión mínima especificada, o la versión más reciente del módulo si no se especifica ninguna versión mínima.</span><span class="sxs-lookup"><span data-stu-id="6e541-113">If the RequiredVersion parameter is not specified, Find-Command returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="6e541-114">Si se especifica el parámetro RequiredVersion, Find-Command solo devuelve la versión del módulo que coincida exactamente con la versión especificada.</span><span class="sxs-lookup"><span data-stu-id="6e541-114">If the RequiredVersion parameter is specified, Find-Command only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="6e541-115">Find-Command puede filtrar por los metadatos del módulo con el parámetro -Tag.</span><span class="sxs-lookup"><span data-stu-id="6e541-115">Find-Command can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="6e541-116">Find-Command puede filtrar por el idioma de búsqueda específico del repositorio con el parámetro -Filter.</span><span class="sxs-lookup"><span data-stu-id="6e541-116">Find-Command can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="6e541-117">Find-Command puede filtrar por los módulos de todos o algunos de los repositorios registrados.</span><span class="sxs-lookup"><span data-stu-id="6e541-117">Find-Command can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="6e541-118">Sintaxis de cmdlet</span><span class="sxs-lookup"><span data-stu-id="6e541-118">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="6e541-119">Referencia de la ayuda en línea de cmdlet</span><span class="sxs-lookup"><span data-stu-id="6e541-119">Cmdlet online help reference</span></span>

[<span data-ttu-id="6e541-120">Find-Command</span><span class="sxs-lookup"><span data-stu-id="6e541-120">Find-Command</span></span>](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a><span data-ttu-id="6e541-121">Comandos de ejemplo</span><span class="sxs-lookup"><span data-stu-id="6e541-121">Example commands</span></span>
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```

