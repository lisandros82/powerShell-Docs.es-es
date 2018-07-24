---
ms.date: 10/17/2017
contributor: keithb
keywords: gallery,powershell,cmdlet,psget
title: Versiones preliminares de scripts
ms.openlocfilehash: 7d4cec9d2b4ee5ad0b19ad5d9c68bb68747abd57
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093855"
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="51d48-103">Versiones preliminares de scripts</span><span class="sxs-lookup"><span data-stu-id="51d48-103">Prerelease versions of scripts</span></span>

<span data-ttu-id="51d48-104">A partir de la versión 1.6.0, PowerShellGet y la Galería de PowerShell admiten el etiquetado de versiones posteriores a 1.0.0 como versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="51d48-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="51d48-105">Antes de esta característica, los elementos de versión preliminar se limitaban a tener una versión que comenzaba por 0.</span><span class="sxs-lookup"><span data-stu-id="51d48-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="51d48-106">El objetivo de estas características es proporcionar mayor compatibilidad con la convención de control de versiones [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) sin interrumpir la compatibilidad con versiones anteriores de PowerShell (versión 3 y superiores) o con versiones existentes de PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="51d48-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="51d48-107">Este tema se centra en las características específicas de los scripts.</span><span class="sxs-lookup"><span data-stu-id="51d48-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="51d48-108">Las características equivalentes de los módulos se encuentran en el tema [Versiones preliminares de módulos](module-prerelease-support.md).</span><span class="sxs-lookup"><span data-stu-id="51d48-108">The equivalent features for modules are in the [Prerelease Module Versions](module-prerelease-support.md) topic.</span></span> <span data-ttu-id="51d48-109">Con estas características, los publicadores pueden identificar un script como versión 2.5.0-alpha y, posteriormente, publicar una versión 2.5.0 lista para producción que sustituya a la versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="51d48-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="51d48-110">En general, las características de los scripts de versión preliminar incluyen:</span><span class="sxs-lookup"><span data-stu-id="51d48-110">At a high level, the prerelease script features include:</span></span>

- <span data-ttu-id="51d48-111">Se agrega un sufijo PrereleaseString a la cadena de versión en el manifiesto del script.</span><span class="sxs-lookup"><span data-stu-id="51d48-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span> <span data-ttu-id="51d48-112">Cuando los scripts se publican en la Galería de PowerShell, estos datos se extraen del manifiesto y se usan para identificar elementos de versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="51d48-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
- <span data-ttu-id="51d48-113">La adquisición de elementos de versión preliminar exige agregar la marca -AllowPrerelease a los comandos de PowerShellGet Find-Script, Install-Script, Update-Script y Save-Script.</span><span class="sxs-lookup"><span data-stu-id="51d48-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span> <span data-ttu-id="51d48-114">Si no se especifica la marca, no se muestran los elementos de versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="51d48-114">If the flag is not specified, prerelease items will not be shown.</span></span>
- <span data-ttu-id="51d48-115">Las versiones de script mostradas por Find-Script, Get-InstalledScript y en la Galería de PowerShell se muestran con el sufijo PrereleaseString, como en 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="51d48-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="51d48-116">A continuación se incluyen detalles de las características.</span><span class="sxs-lookup"><span data-stu-id="51d48-116">Details for the features are included below.</span></span>

## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="51d48-117">Identificación de una versión de script como versión preliminar</span><span class="sxs-lookup"><span data-stu-id="51d48-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="51d48-118">La compatibilidad de PowerShellGet con las versiones preliminares resulta más sencilla con los scripts que con los módulos.</span><span class="sxs-lookup"><span data-stu-id="51d48-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span> <span data-ttu-id="51d48-119">El control de versiones de script solo es compatible con PowerShellGet, por lo que no hay ningún problema de compatibilidad debido a la adición de la cadena de versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="51d48-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span> <span data-ttu-id="51d48-120">Para identificar un script de la Galería de PowerShell como una versión preliminar, agregue un sufijo de versión preliminar a una cadena de versión con un formato correcto en los metadatos del script.</span><span class="sxs-lookup"><span data-stu-id="51d48-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="51d48-121">El aspecto de una sección de ejemplo de un manifiesto de script con una versión preliminar sería similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="51d48-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

<span data-ttu-id="51d48-122">Para usar un sufijo de versión preliminar, la cadena de versión debe cumplir los siguientes requisitos:</span><span class="sxs-lookup"><span data-stu-id="51d48-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

- <span data-ttu-id="51d48-123">Solo se puede especificar un sufijo de versión preliminar si la versión tiene tres segmentos para Major.Minor.Build.</span><span class="sxs-lookup"><span data-stu-id="51d48-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span>
  <span data-ttu-id="51d48-124">Esto se alinea con SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="51d48-124">This aligns with SemVer v1.0.0</span></span>
- <span data-ttu-id="51d48-125">El sufijo de versión preliminar es una cadena que comienza con un guión y puede contener caracteres alfanuméricos ASCII [0-9A-Za-z-].</span><span class="sxs-lookup"><span data-stu-id="51d48-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
- <span data-ttu-id="51d48-126">De momento solo se admiten las cadenas de versión preliminar de SemVer v1.0.0, por lo que el sufijo de versión preliminar __no debe__ contener ni punto ni + [.+], que sí se permiten en SemVer 2.0.</span><span class="sxs-lookup"><span data-stu-id="51d48-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix __must not__ contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
- <span data-ttu-id="51d48-127">Ejemplos de cadenas admitidas con sufijo PrereleaseString son: -alpha, -alpha1, -BETA, -update20171020.</span><span class="sxs-lookup"><span data-stu-id="51d48-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="51d48-128">__Impacto del control de versiones preliminares en las carpetas de instalación y en el criterio de ordenación__</span><span class="sxs-lookup"><span data-stu-id="51d48-128">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="51d48-129">El criterio de ordenación cambia cuando se usa una versión preliminar, lo que es importante si se publica en la Galería de PowerShell y si se instalan scripts con comandos de PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="51d48-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span> <span data-ttu-id="51d48-130">Si hay dos versiones de script con el mismo número de versión, el criterio de ordenación se basa en la parte de la cadena que sigue al guión.</span><span class="sxs-lookup"><span data-stu-id="51d48-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="51d48-131">Por lo tanto, la versión 2.5.0-alpha es menor que 2.5.0-beta, que es menor que 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="51d48-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="51d48-132">Si hay dos scripts con el mismo número de versión y solo uno tiene un sufijo PrereleaseString, se da por hecho que el script __sin__ el sufijo de versión preliminar es la versión lista para producción y se ordena como una versión mayor que la versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="51d48-132">If two scripts have the same version number, and only one has a PrereleaseString, the script __without__ the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span> <span data-ttu-id="51d48-133">Por ejemplo, al comparar las versiones 2.5.0 y 2.5.0-beta, la versión 2.5.0 se considera la mayor.</span><span class="sxs-lookup"><span data-stu-id="51d48-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="51d48-134">Al publicar en la Galería de PowerShell, de forma predeterminada, la versión del script que se va a publicar debe ser mayor que cualquier versión publicada previamente que se encuentre en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51d48-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> <span data-ttu-id="51d48-135">Un publicador puede actualizar la versión 2.5.0-alpha con 2.5.0-beta o con 2.5.0 (sin sufijo de versión preliminar).</span><span class="sxs-lookup"><span data-stu-id="51d48-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="51d48-136">Búsqueda y adquisición de elementos de versión preliminar mediante comandos de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="51d48-136">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="51d48-137">Para trabajar con elementos de versión preliminar mediante los comandos de PowerShellGet Find-Script, Install-Script, Update-Script y Save-Script es necesario agregar la marca -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="51d48-137">Dealing with prerelease items using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="51d48-138">Si se especifica -AllowPrerelease, se incluyen los elementos de versión preliminar, siempre que estén presentes.</span><span class="sxs-lookup"><span data-stu-id="51d48-138">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span> <span data-ttu-id="51d48-139">Si no se especifica la marca -AllowPrerelease, no se muestran los elementos de versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="51d48-139">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="51d48-140">Las únicas excepciones a esto en los comandos de script de PowerShellGet son Get-InstalledScript y algunos casos con Uninstall-Script.</span><span class="sxs-lookup"><span data-stu-id="51d48-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

- <span data-ttu-id="51d48-141">Get-InstalledScript siempre muestra automáticamente la información de versión preliminar en la cadena de versión, si está presente.</span><span class="sxs-lookup"><span data-stu-id="51d48-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
- <span data-ttu-id="51d48-142">Uninstall-Script desinstala de forma predeterminada la versión más reciente de un script, si __no hay ninguna versión__ especificada.</span><span class="sxs-lookup"><span data-stu-id="51d48-142">Uninstall-Script will by default uninstall the most recent version of a script, if __no version__ is specified.</span></span> <span data-ttu-id="51d48-143">Ese comportamiento no ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="51d48-143">That behavior has not changed.</span></span> <span data-ttu-id="51d48-144">Pero si se especifica una versión preliminar con -RequiredVersion, se necesita -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="51d48-144">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="51d48-145">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="51d48-145">Examples</span></span>

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

<span data-ttu-id="51d48-146">Uninstall-Script quita la versión actual de un script si no se proporciona -RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="51d48-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="51d48-147">Si se especifica -RequiredVersion y es una versión preliminar, debe agregarse -AllowPrerelease al comando.</span><span class="sxs-lookup"><span data-stu-id="51d48-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage
```

## <a name="more-details"></a><span data-ttu-id="51d48-148">Más detalles</span><span class="sxs-lookup"><span data-stu-id="51d48-148">More details</span></span>

- [<span data-ttu-id="51d48-149">Versiones preliminares de módulos</span><span class="sxs-lookup"><span data-stu-id="51d48-149">Prerelease Module Versions</span></span>](module-prerelease-support.md)
- [<span data-ttu-id="51d48-150">Find-script</span><span class="sxs-lookup"><span data-stu-id="51d48-150">Find-script</span></span>](/powershell/module/powershellget/find-script)
- [<span data-ttu-id="51d48-151">Install-script</span><span class="sxs-lookup"><span data-stu-id="51d48-151">Install-script</span></span>](/powershell/module/powershellget/install-script)
- [<span data-ttu-id="51d48-152">Save-script</span><span class="sxs-lookup"><span data-stu-id="51d48-152">Save-script</span></span>](/powershell/module/powershellget/save-script)
- [<span data-ttu-id="51d48-153">Update-script</span><span class="sxs-lookup"><span data-stu-id="51d48-153">Update-script</span></span>](/powershell/module/powershellget/update-script)
- [<span data-ttu-id="51d48-154">Get-Installedscript</span><span class="sxs-lookup"><span data-stu-id="51d48-154">Get-Installedscript</span></span>](/powershell/module/powershellget/get-installedscript)
- [<span data-ttu-id="51d48-155">UnInstall-script</span><span class="sxs-lookup"><span data-stu-id="51d48-155">UnInstall-script</span></span>](/powershell/module/powershellget/uninstall-script)