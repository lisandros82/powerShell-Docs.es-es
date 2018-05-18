---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Módulos con las ediciones compatibles de PowerShell
ms.openlocfilehash: 631314e63e49723b3c393c8d8c20de9a297027fb
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="5e559-103">Módulos con las ediciones compatibles de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e559-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="5e559-104">A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.</span><span class="sxs-lookup"><span data-stu-id="5e559-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="5e559-105">**Desktop Edition:** basado en .NET Framework y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Server Core y Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="5e559-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="5e559-106">**Core Edition:** basado en .NET Core y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Nano Server y Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="5e559-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="the-running-edition-of-powershell-is-shown-in-the-psedition-property-of-psversiontable"></a><span data-ttu-id="5e559-107">La edición de ejecución de PowerShell se muestra en la propiedad PSEdition de $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="5e559-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

## <a name="module-authors-can-declare-their-modules-to-be-compatible-with-one-or-more-powershell-editions-using-the-compatiblepseditions-module-manifest-key-this-key-is-only-supported-on-powershell-51-or-later"></a><span data-ttu-id="5e559-108">Los autores de módulos pueden declarar sus módulos para hacerlos compatibles con una o varias ediciones de PowerShell mediante la clave de manifiesto del módulo CompatiblePSEditions.</span><span class="sxs-lookup"><span data-stu-id="5e559-108">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="5e559-109">Esta clave solo se admite en PowerShell 5.1 o versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="5e559-109">This key is only supported on PowerShell 5.1 or later.</span></span>

<span data-ttu-id="5e559-110">*NOTA* Una vez que se especifica un manifiesto de módulo con la clave CompatiblePSEditions, no se puede importar en versiones anteriores de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e559-110">*NOTE* Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on lower versions of PowerShell.</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
Desktop
Core

$ModuleInfo | Get-Member CompatiblePSEditions

   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}

```

<span data-ttu-id="5e559-111">Al obtener una lista de los módulos disponibles, puede filtrarla según la edición de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e559-111">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

```powershell
Get-Module -ListAvailable -PSEdition Desktop

    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions

Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
Desktop
Core

```

## <a name="module-authors-can-publish-a-single-module-targeting-to-either-or-both-powershell-editions-desktop-and-core"></a><span data-ttu-id="5e559-112">Los autores de módulos pueden publicar un único módulo destinado a una de las ediciones de PowerShell o a ambas (Core o Desktop)</span><span class="sxs-lookup"><span data-stu-id="5e559-112">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core)</span></span>

<span data-ttu-id="5e559-113">Un único módulo puede trabajar tanto en la edición Desktop como Core; en este módulo, el autor tiene que agregar la lógica necesaria en RootModule o en el manifiesto del módulo mediante la variable $PSEdition.</span><span class="sxs-lookup"><span data-stu-id="5e559-113">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span>
<span data-ttu-id="5e559-114">Los módulos pueden tener dos conjuntos de archivos DLL compilados que se dirijan a CoreCLR y a FullCLR.</span><span class="sxs-lookup"><span data-stu-id="5e559-114">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span>
<span data-ttu-id="5e559-115">A continuación, se indican un par de formas de empaquetar un módulo con la lógica correspondiente para cargar los archivos DLL adecuados.</span><span class="sxs-lookup"><span data-stu-id="5e559-115">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="5e559-116">Opción 1: empaquetar un módulo para dirigirlo a varias versiones y varias ediciones de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e559-116">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

#### <a name="module-folder-contents"></a><span data-ttu-id="5e559-117">Contenido de la carpeta del módulo</span><span class="sxs-lookup"><span data-stu-id="5e559-117">Module folder contents</span></span>

- <span data-ttu-id="5e559-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="5e559-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="5e559-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="5e559-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="5e559-120">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="5e559-120">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="5e559-121">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="5e559-121">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="5e559-122">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="5e559-122">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="5e559-123">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="5e559-123">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="5e559-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="5e559-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="5e559-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="5e559-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="5e559-126">es-ES\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="5e559-126">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="5e559-127">es-ES\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="5e559-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="5e559-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="5e559-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="5e559-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="5e559-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="5e559-130">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="5e559-130">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="5e559-131">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="5e559-131">Settings\DSC.psd1</span></span>
- <span data-ttu-id="5e559-132">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="5e559-132">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="5e559-133">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="5e559-133">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="5e559-134">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="5e559-134">Settings\ScriptSecurity.psd1</span></span>

#### <a name="contents-of-psscriptanalyzerpsd1-file"></a><span data-ttu-id="5e559-135">Contenido del archivo PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="5e559-135">Contents of PSScriptAnalyzer.psd1 file</span></span>

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

#### <a name="contents-of-psscriptanalyzerpsm1-file"></a><span data-ttu-id="5e559-136">Contenido del archivo PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="5e559-136">Contents of PSScriptAnalyzer.psm1 file</span></span>

<span data-ttu-id="5e559-137">A continuación, la lógica carga los ensamblados necesarios en función de la edición o la versión actual.</span><span class="sxs-lookup"><span data-stu-id="5e559-137">Below logic loads the required assemblies depending on the current edition or version.</span></span>

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0') {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}

```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="5e559-138">Opción 2: usar la variable $PSEdition en el archivo. PSD1 para cargar los archivos DLL adecuados y los módulos anidados o necesarios</span><span class="sxs-lookup"><span data-stu-id="5e559-138">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="5e559-139">En PS 5.1 y versiones posteriores, se permite usar la variable global $PSEdition en el archivo de manifiesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="5e559-139">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span>
<span data-ttu-id="5e559-140">Mediante esta variable el autor del módulo puede especificar los valores condicionales en el archivo de manifiesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="5e559-140">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="5e559-141">Se puede hacer referencia a la variable $PSEdition en modo de lenguaje restringido o en una sección de datos.</span><span class="sxs-lookup"><span data-stu-id="5e559-141">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

<span data-ttu-id="5e559-142">*NOTA* Una vez que se especifica un manifiesto de módulo con la clave CompatiblePSEditions (o cuando usa la variable $PSEdition), no se puede importar en versiones anteriores de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e559-142">*NOTE* Once a module manifest is specified with the CompatiblePSEditions key or uses $PSEdition variable, it can not be imported on lower versions of PowerShell.</span></span>


#### <a name="sample-module-manifest-file-with-compatiblepseditions-key"></a><span data-ttu-id="5e559-143">Ejemplo de un archivo de manifiesto de módulo con la clave CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="5e559-143">Sample module manifest file with CompatiblePSEditions key</span></span>

```powershell
@{
# - - -

# Script module or binary module file associated with this manifest.
RootModule = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrRM.dll'
}
else # Desktop
{
'clr\MyFullClrRM.dll'
}

# Supported PSEditions
CompatiblePSEditions = 'Desktop', 'Core'

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrNM1.dll',
'coreclr\MyCoreClrNM2.dll'
}
else # Desktop
{
'clr\MyFullClrNM1.dll',
'clr\MyFullClrNM2.dll'
}

# -- - -
}
```

#### <a name="module-contents"></a><span data-ttu-id="5e559-144">Contenido del módulo</span><span class="sxs-lookup"><span data-stu-id="5e559-144">Module contents</span></span>

```powershell

PS C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions> dir -Recurse

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/5/2016   1:37 PM                clr
d-----         7/5/2016   1:36 PM                coreclr
-a----         7/5/2016   1:34 PM           4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         7/5/2016   1:35 PM              0 MyFullClrNM1.dll
-a----         7/5/2016   1:35 PM              0 MyFullClrNM2.dll
-a----         7/5/2016   1:35 PM              0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM1.dll
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM2.dll
-a----         7/5/2016   1:35 PM              0 MyCoreClrRM.dl
```

## <a name="powershell-gallery-users-can-find-the-list-of-modules-supported-on-a-specific-powershell-edition-using-tags-pseditiondesktop-and-pseditioncore"></a><span data-ttu-id="5e559-145">Los usuarios de la Galería de PowerShell pueden encontrar la lista de los módulos admitidos para una edición específica de PowerShell mediante las etiquetas PSEdition_Desktop y PSEdition_Core.</span><span class="sxs-lookup"><span data-stu-id="5e559-145">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="5e559-146">Se considera que los módulos que no tienen las etiquetas PSEdition_Desktop o PSEdition_Core funcionan correctamente en las ediciones de PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="5e559-146">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell

# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core

```


## <a name="more-details"></a><span data-ttu-id="5e559-147">Más detalles</span><span class="sxs-lookup"><span data-stu-id="5e559-147">More details</span></span>

- [<span data-ttu-id="5e559-148">Scripts con PSEditions</span><span class="sxs-lookup"><span data-stu-id="5e559-148">Scripts with PSEditions</span></span>](script-psedition-support.md)
- [<span data-ttu-id="5e559-149">Compatibilidad con PSEditions en la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e559-149">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-items/searching-by-psedition.md)
- <span data-ttu-id="5e559-150">[Actualizar el manifiesto de módulo] (/powershell/module/powershellget/update-modulemanifest)</span><span class="sxs-lookup"><span data-stu-id="5e559-150">[Update module manifest] (/powershell/module/powershellget/update-modulemanifest)</span></span>