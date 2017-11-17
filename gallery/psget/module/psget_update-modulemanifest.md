---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Update-ModuleManifest
ms.openlocfilehash: ce3f6f173535d98648eb51adb1dbf84764e4f434
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="update-modulemanifest"></a><span data-ttu-id="a8f40-103">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="a8f40-103">Update-ModuleManifest</span></span>
<span data-ttu-id="a8f40-104">Actualiza un archivo de manifiesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="a8f40-104">Updates a module manifest file.</span></span>

## <a name="description"></a><span data-ttu-id="a8f40-105">Descripción</span><span class="sxs-lookup"><span data-stu-id="a8f40-105">Description</span></span>

<span data-ttu-id="a8f40-106">El cmdlet Update-ModuleManifest actualiza un archivo de manifiesto de módulo (.psd1).</span><span class="sxs-lookup"><span data-stu-id="a8f40-106">The Update-ModuleManifest cmdlet updates a module manifest (.psd1) file.</span></span>

### <a name="notes"></a><span data-ttu-id="a8f40-107">Notas</span><span class="sxs-lookup"><span data-stu-id="a8f40-107">Notes</span></span>
    - <span data-ttu-id="a8f40-108">DscResourcesToExport solo se admite en la versión más reciente de PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="a8f40-108">DscResourcesToExport is only supported on the latest PowerShell version 5.0.</span></span> <span data-ttu-id="a8f40-109">No podremos actualizar el campo si está ejecutando versiones anteriores de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8f40-109">We won’t be able to update the field if you are running on lower versions of PowerShell.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="a8f40-110">Sintaxis de cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8f40-110">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-ModuleManifest -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="a8f40-111">Referencia de la ayuda en línea de cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8f40-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="a8f40-112">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="a8f40-112">Update-ModuleManifest</span></span>](http://go.microsoft.com/fwlink/?LinkId=619311)

## <a name="example-commands"></a><span data-ttu-id="a8f40-113">Comandos de ejemplo</span><span class="sxs-lookup"><span data-stu-id="a8f40-113">Example commands</span></span>

<span data-ttu-id="a8f40-114">Este nuevo cmdlet se usa para ayudar a actualizar el archivo de manifiesto con los valores de propiedad de entrada.</span><span class="sxs-lookup"><span data-stu-id="a8f40-114">This new cmdlet is used to help update manifest file with input property values.</span></span> <span data-ttu-id="a8f40-115">Toma los mismos parámetros que New-ModuleManifest.</span><span class="sxs-lookup"><span data-stu-id="a8f40-115">It takes all parameters that New-ModuleManifest does.</span></span>

<span data-ttu-id="a8f40-116">Observamos que muchos autores del módulo desearían especificar “\*” en los valores exportados, como FunctionsToExport, CmdletsToExport, etc. Durante la publicación del módulo en la Galería de PowerShell, los comandos y las funciones que no estén especificados no se rellenarán correctamente en la Galería.</span><span class="sxs-lookup"><span data-stu-id="a8f40-116">We notice that a lot of module authors would like to specify “\*” in exported values such as FunctionsToExport, CmdletsToExport, etc. During module publishing to PowerShell Gallery, unspecified functions and commands will not be populated properly onto the Gallery.</span></span> <span data-ttu-id="a8f40-117">Por lo tanto, se recomienda a los autores del módulo que actualicen sus manifiestos con los valores adecuados.</span><span class="sxs-lookup"><span data-stu-id="a8f40-117">Therefore, we suggest module authors update their manifests with proper values.</span></span>

<span data-ttu-id="a8f40-118">Si tiene módulos que contienen propiedades exportadas, Update-ModuleManifest rellenará el archivo de manifiesto especificado con la información de las funciones exportadas, los cmdlets, las variables, etc.:</span><span class="sxs-lookup"><span data-stu-id="a8f40-118">If you have modules that have exported properties, Update-ModuleManifest will fill the specified manifest file with information from exported functions, cmdlets, variables etc:</span></span>
```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

<span data-ttu-id="a8f40-119">Después de Update-ModuleManifest:</span><span class="sxs-lookup"><span data-stu-id="a8f40-119">After Update-ModuleManifest:</span></span>
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

<span data-ttu-id="a8f40-120">Para cada módulo, también existen campos de metadatos asociados.</span><span class="sxs-lookup"><span data-stu-id="a8f40-120">For each module, there are also metadata fields associated with it.</span></span> <span data-ttu-id="a8f40-121">Para que se muestren correctamente los metadatos en la Galería de PowrShell, puede usar Update-ModuleManifest para rellenar dichos campos en PrivateData.</span><span class="sxs-lookup"><span data-stu-id="a8f40-121">In order to display metadata properly on PowrShell Gallery, you can use Update-ModuleManifest to populate those fields under PrivateData.</span></span>

```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```

<span data-ttu-id="a8f40-122">La tabla de hash PrivateData de la plantilla de archivo de manifiesto tiene las propiedades siguientes.</span><span class="sxs-lookup"><span data-stu-id="a8f40-122">PrivateData hashtable from the manifest file template has the following properties</span></span>

```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''
    
        # A URL to the main website for this project.
        # ProjectUri = ''
        
        # A URL to an icon representing this module.
        # IconUri = ''
        
        # ReleaseNotes of this module
        # ReleaseNotes = ''
        
        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```

