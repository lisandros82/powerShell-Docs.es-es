---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-Script
ms.openlocfilehash: 1f5076d94015c0b1041591144f1f0fe36819204b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="find-script"></a><span data-ttu-id="74552-103">Find-Script</span><span class="sxs-lookup"><span data-stu-id="74552-103">Find-Script</span></span>

<span data-ttu-id="74552-104">Busca los archivos de script de PowerShell de una galería en línea que coincidan con los criterios especificados.</span><span class="sxs-lookup"><span data-stu-id="74552-104">Finds the PowerShell script files from an online gallery that match specified criteria.</span></span>

## <a name="description"></a><span data-ttu-id="74552-105">Descripción</span><span class="sxs-lookup"><span data-stu-id="74552-105">Description</span></span>

<span data-ttu-id="74552-106">Find-Script detecta los archivos de script de repositorios registrados que coincidan con los criterios especificados.</span><span class="sxs-lookup"><span data-stu-id="74552-106">Find-Script discovers the script files from registered repositories that matches the specified criteria.</span></span>
<span data-ttu-id="74552-107">Para cada script detectado, Find-Script devuelve un objeto PSRepositoryItemInfo que opcionalmente se puede canalizar a Install-Script para instalar los scripts.</span><span class="sxs-lookup"><span data-stu-id="74552-107">For each script found, Find-Script returns a PSRepositoryItemInfo object which can optionally be piped to Install-Script for installing the scripts.</span></span>
<span data-ttu-id="74552-108">El cmdlet Find-Script permite detectar los archivos de script con criterios de búsqueda diferentes, tales como nombre, etiqueta, filtro, nombre de comando, intervalo de versiones, versión exacta, todas las versiones, incluidas sus dependencias y de repositorios específicos o todos los repositorios registrados.</span><span class="sxs-lookup"><span data-stu-id="74552-108">Find-Script cmdlet lets you to discover the script files with different search criteria like name, tag, filter, command name, version range, exact version, all versions, including its dependencies and from specific or all registered repositories.</span></span>

- <span data-ttu-id="74552-109">Find-Script puede filtrar por el contenido del script con los parámetros -Command e -Includes.</span><span class="sxs-lookup"><span data-stu-id="74552-109">Find-Script can filter based on script contents with the -Command and -Includes parameters.</span></span>
- <span data-ttu-id="74552-110">Find-Script puede filtrar con parámetros de versión: MinimumVersion, MaximumVersion, RequiredVersion y AllVersions.</span><span class="sxs-lookup"><span data-stu-id="74552-110">Find-Script can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="74552-111">Estos parámetros se excluyen mutuamente, excepto MinmimumVersion y MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="74552-111">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="74552-112">Estos parámetros de versión solo se permiten con el nombre de script único sin ningún carácter comodín.</span><span class="sxs-lookup"><span data-stu-id="74552-112">These version parameters are allowed only with the single script name without any wildcards.</span></span>
  - <span data-ttu-id="74552-113">Si no se especifica el parámetro RequiredVersion, Find-Script devuelve la versión más reciente del script que sea igual o mayor que la versión mínima especificada, o la versión más reciente del script si no se especifica ninguna versión mínima.</span><span class="sxs-lookup"><span data-stu-id="74552-113">If the RequiredVersion parameter is not specified, Find-Script returns the latest version of the script that is equal to or greater than the minimum version specified or the latest version of the script if no minimum version is specified.</span></span>
  - <span data-ttu-id="74552-114">Si se especifica el parámetro RequiredVersion, Find-Script solo devuelve la versión del script que coincida exactamente con la versión especificada.</span><span class="sxs-lookup"><span data-stu-id="74552-114">If the RequiredVersion parameter is specified, Find-Script only returns the version of script that exactly matches the specified version.</span></span>
- <span data-ttu-id="74552-115">Find-Script puede filtrar por los metadatos del script con el parámetro -Tag.</span><span class="sxs-lookup"><span data-stu-id="74552-115">Find-Script can filter on script metadata with the -Tag parameter.</span></span>
- <span data-ttu-id="74552-116">Find-Script puede filtrar por el idioma de búsqueda específico del repositorio con el parámetro -Filter.</span><span class="sxs-lookup"><span data-stu-id="74552-116">Find-Script can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="74552-117">Find-Script puede filtrar por los scripts de todos o algunos de los repositorios registrados.</span><span class="sxs-lookup"><span data-stu-id="74552-117">Find-Script can filter on scripts from all or few of the registered repositories.</span></span>

<span data-ttu-id="74552-118">**Nota:** el repositorio PSRepository registrado debe tener un valor de ScriptSourceLocation válido.</span><span class="sxs-lookup"><span data-stu-id="74552-118">**NOTE:** Registered PSRepository should have a valid ScriptSourceLocation.</span></span> <span data-ttu-id="74552-119">Puede usar Set-PSRepository para establecer el valor de ScriptSourceLocation.</span><span class="sxs-lookup"><span data-stu-id="74552-119">You can use the Set-PSRepository to set ScriptSourceLocation value.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="74552-120">Sintaxis de cmdlet</span><span class="sxs-lookup"><span data-stu-id="74552-120">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Find-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="74552-121">Referencia de la ayuda en línea de cmdlet</span><span class="sxs-lookup"><span data-stu-id="74552-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="74552-122">Find-Script</span><span class="sxs-lookup"><span data-stu-id="74552-122">Find-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619785)

## <a name="example-commands"></a><span data-ttu-id="74552-123">Comandos de ejemplo</span><span class="sxs-lookup"><span data-stu-id="74552-123">Example commands</span></span>

```powershell
# Find a script from the registered repository with ScriptSourceLocation
Find-Script Connect-AzureVM

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...

# Find multiple scripts
Find-Script -Name Connect-AzureVM, Show-Tree, Connect-O365

# Find scripts with wildcards in -Name
Find-Script -Name *Azure*

# Find all versions of a script
Find-Script -Name Connect-O365 -AllVersions

# Find a script with -MinimumVersion.
# With MinimumVersion we can find a script whose version is greate than or equal to the specified MinimumVersion value.
Find-Script Connect-O365 -MinimumVersion 1.4

# Find a script with MaximumVersion
Find-Script -Name Connect-O365 -MaximumVersion 1.6.2

# Find a script with both MinimumVersion and MaximumVersion range.
Find-Script -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.2

# Find a script with exact version
Find-Script -Name Connect-O365 -RequiredVersion 1.5.7

# Find a script with a specific pre-release version
Find-Script -Name Connect-O365 -RequiredVersion 1.3.2-alpha -AllowPrerelease

# Find a script from the specified repository
Find-Script -Name Fabrikam-ServerScript -Repository MyLocalRepo

# Find available scripts from all registered repositories
Find-Script

# Find available scripts from few registered repositories
Find-Script -Repository PSGallery, PrivatePSGallery

# Find a script along with its dependent modules and scripts
Find-Script -Name Connect-AzureVM -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...
1.4.0      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management
1.1.2      Azure.Storage                       PSGallery            Microsoft Azure PowerShell - Storage service cmd...
1.0.8      AzureRM.profile                     PSGallery            Microsoft Azure PowerShell - Profile credential ...

# Find all scripts with workflows
Find-Script -Includes Workflow

# Find all scripts with functions
Find-Script -Includes Function

# Find scripts with specific commands
Find-Script -Command Log-Message
Find-Script -Command Log-Message, Show-Tree -Includes Function
Find-Script -Command Connect-AzureVM -Includes Workflow

# Find scripts with -Filter based search. -Filter searches in description and names
Find-Script -Filter Windows
Find-Script -Filter Azure

# Find all scripts with tags O365 or Nano
Find-Script -Tag O365, Nano

# Properties of Find-Script returned object
Find-Script Show-Tree | Format-List * -Force
Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {versionDownloadCount, ItemType, copyright, PackageManagementProvider...}


# Includes property on PSRepositoryItemInfo object
$t = Find-Script -Includes Workflow -Repository INT -Name Fabrikam-ClientScript
$t.Includes

Name                           Value
----                           -----
Function                       {Test-FunctionFromScript_Fabrikam-ClientScript}
RoleCapability                 {}
Command                        {Test-FunctionFromScript_Fabrikam-ClientScript, Test-WorkflowFromScript_Fabrikam-Clie...
DscResource                    {}
Workflow                       {Test-WorkflowFromScript_Fabrikam-ClientScript}
Cmdlet                         {}


```