---
ms.date: 09/26/2017
contributor: keithb
keywords: gallery,powershell,cmdlet,psget
title: Versiones preliminares de módulos
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328146"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="de398-103">Versiones preliminares de módulos</span><span class="sxs-lookup"><span data-stu-id="de398-103">Prerelease Module Versions</span></span>

<span data-ttu-id="de398-104">A partir de la versión 1.6.0, PowerShellGet y la Galería de PowerShell admiten el etiquetado de versiones posteriores a 1.0.0 como versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="de398-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="de398-105">Antes de esta característica, los paquetes de versión preliminar se limitaban a tener una versión que comenzaba por 0.</span><span class="sxs-lookup"><span data-stu-id="de398-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="de398-106">El objetivo de estas características es proporcionar mayor compatibilidad con la convención de control de versiones [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) sin interrumpir la compatibilidad con versiones anteriores de PowerShell (versión 3 y superiores) o con versiones existentes de PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="de398-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="de398-107">Este tema se centra en las características específicas de los módulos.</span><span class="sxs-lookup"><span data-stu-id="de398-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="de398-108">Las características equivalentes de los scripts se encuentran en el tema [Versiones preliminares de scripts](script-prerelease-support.md).</span><span class="sxs-lookup"><span data-stu-id="de398-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="de398-109">Con estas características, los publicadores pueden identificar un módulo o script como versión 2.5.0-alpha y, posteriormente, publicar una versión 2.5.0 lista para producción que sustituya a la versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="de398-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="de398-110">En general, las características de los módulos de versión preliminar incluyen:</span><span class="sxs-lookup"><span data-stu-id="de398-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="de398-111">La adición de una cadena de versión preliminar a la sección PSData del manifiesto del módulo identifica a ese módulo como una versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="de398-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="de398-112">Cuando el módulo se publica en la Galería de PowerShell, estos datos se extraen del manifiesto y se usan para identificar paquetes de versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="de398-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="de398-113">La adquisición de paquetes de versión preliminar requiere agregar la marca `-AllowPrerelease` a los comandos `Find-Module`, `Install-Module`, `Update-Module` y `Save-Module` de PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="de398-113">Acquiring prerelease packages requires adding `-AllowPrerelease` flag to the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span> <span data-ttu-id="de398-114">Si no se especifica la marca, no se muestran los paquetes de versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="de398-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="de398-115">Las versiones de módulo mostradas mediante `Find-Module`,`Get-InstalledModule` y en la Galería de PowerShell se muestran como una sola cadena con la cadena de versión preliminar anexa, como en 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="de398-115">Module versions displayed by `Find-Module`, `Get-InstalledModule`, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="de398-116">A continuación se incluyen detalles de las características.</span><span class="sxs-lookup"><span data-stu-id="de398-116">Details for the features are included below.</span></span>

<span data-ttu-id="de398-117">Estos cambios no afectan a la compatibilidad de versión de módulo integrada en PowerShell y son compatibles con PowerShell 3.0, 4.0 y 5.</span><span class="sxs-lookup"><span data-stu-id="de398-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="de398-118">Identificación de una versión de módulo como versión preliminar</span><span class="sxs-lookup"><span data-stu-id="de398-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="de398-119">La compatibilidad de PowerShellGet con las versiones preliminares exige el uso de dos campos en el manifiesto del módulo:</span><span class="sxs-lookup"><span data-stu-id="de398-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="de398-120">Si se usa una versión preliminar, el elemento ModuleVersion incluido en el manifiesto del módulo debe ser una versión de tres partes que debe atenerse al control de versiones existente de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de398-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="de398-121">El formato de versión sería A.B.C, donde A, B y C son todos enteros.</span><span class="sxs-lookup"><span data-stu-id="de398-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="de398-122">La cadena de versión preliminar se especifica en el manifiesto del módulo, en la sección PSData de PrivateData.</span><span class="sxs-lookup"><span data-stu-id="de398-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="de398-123">A continuación se indican los requisitos detallados de la cadena de versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="de398-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="de398-124">El aspecto de una sección de ejemplo de un manifiesto de módulo que define un módulo como versión preliminar sería similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="de398-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

<span data-ttu-id="de398-125">Los requisitos detallados de la cadena de versión preliminar son:</span><span class="sxs-lookup"><span data-stu-id="de398-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="de398-126">Solo se puede especificar la cadena de versión preliminar cuando el elemento ModuleVersion tiene tres segmentos para Major.Minor.Build.</span><span class="sxs-lookup"><span data-stu-id="de398-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="de398-127">Esto se alinea con SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="de398-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="de398-128">Un guión es el delimitador entre el número de compilación y la cadena de versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="de398-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="de398-129">Se puede incluir un guión en la cadena de versión preliminar únicamente como primer carácter.</span><span class="sxs-lookup"><span data-stu-id="de398-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="de398-130">La cadena de versión preliminar solo puede contener caracteres alfanuméricos ASCII [0-9A-Za-z-].</span><span class="sxs-lookup"><span data-stu-id="de398-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="de398-131">Comenzar la cadena de versión preliminar con un carácter alfanumérico es un procedimiento recomendado, ya que facilita su identificación como una versión preliminar al examinar una lista de paquetes.</span><span class="sxs-lookup"><span data-stu-id="de398-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of packages.</span></span>
- <span data-ttu-id="de398-132">De momento solo se admiten las cadenas de versión preliminar de SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="de398-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="de398-133">La cadena de versión preliminar **no debe** contener ni punto ni + [.+], que sí se permiten en SemVer 2.0.</span><span class="sxs-lookup"><span data-stu-id="de398-133">Prerelease string **must not** contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="de398-134">Ejemplos de cadenas de versión preliminar admitidas son: -alpha, -alpha1, -BETA, -update20171020.</span><span class="sxs-lookup"><span data-stu-id="de398-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="de398-135">Impacto del control de versiones preliminares en las carpetas de instalación y en el criterio de ordenación</span><span class="sxs-lookup"><span data-stu-id="de398-135">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="de398-136">El criterio de ordenación cambia cuando se usa una versión preliminar, lo que es importante si se publica en la Galería de PowerShell y si se instalan módulos con comandos de PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="de398-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="de398-137">Si se especifica la cadena de versión preliminar para dos módulos, el criterio de ordenación se basa en la parte de la cadena que sigue al guión.</span><span class="sxs-lookup"><span data-stu-id="de398-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="de398-138">Por lo tanto, la versión 2.5.0-alpha es menor que 2.5.0-beta, que es menor que 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="de398-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="de398-139">Si hay dos módulos con el mismo elemento ModuleVersion y solo uno tiene una cadena de versión preliminar, se da por hecho que el módulo sin la cadena de versión preliminar es la versión lista para producción y se ordena como una versión mayor que la versión preliminar (que incluye la cadena de versión preliminar).</span><span class="sxs-lookup"><span data-stu-id="de398-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="de398-140">Por ejemplo, al comparar las versiones 2.5.0 y 2.5.0-beta, la versión 2.5.0 se considera la mayor.</span><span class="sxs-lookup"><span data-stu-id="de398-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="de398-141">Al publicar en la Galería de PowerShell, de forma predeterminada, la versión del módulo que se va a publicar debe ser mayor que cualquier versión publicada previamente que se encuentre en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de398-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="de398-142">Búsqueda y adquisición de paquetes de versión preliminar mediante comandos de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="de398-142">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="de398-143">Para trabajar con paquetes de versión preliminar mediante los comandos Find-Module, Install-Module, Update-Module y Save-Module de PowerShellGet es necesario agregar la marca -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="de398-143">Dealing with prerelease packages using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="de398-144">Si se especifica -AllowPrerelease, se incluyen los paquetes de versión preliminar, siempre que estén presentes.</span><span class="sxs-lookup"><span data-stu-id="de398-144">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="de398-145">Si no se especifica la marca -AllowPrerelease, no se muestran los paquetes de versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="de398-145">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="de398-146">Las únicas excepciones a esto en los comandos de módulo de PowerShellGet son Get-InstalledModule y algunos casos con Uninstall-Module.</span><span class="sxs-lookup"><span data-stu-id="de398-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="de398-147">Get-InstalledModule siempre muestra automáticamente la información de versión preliminar en la cadena de versión de los módulos.</span><span class="sxs-lookup"><span data-stu-id="de398-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="de398-148">Uninstall-Module desinstala de forma predeterminada la versión más reciente de un módulo, si __no hay ninguna versión__ especificada.</span><span class="sxs-lookup"><span data-stu-id="de398-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="de398-149">Ese comportamiento no ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="de398-149">That behavior has not changed.</span></span> <span data-ttu-id="de398-150">Pero si se especifica una versión preliminar con -RequiredVersion, se necesita -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="de398-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="de398-151">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="de398-151">Examples</span></span>

<span data-ttu-id="de398-152">Supongamos que la Galería de PowerShell tiene las versiones 1.8.0 y 1.9.0-alpha del módulo TestPackage.</span><span class="sxs-lookup"><span data-stu-id="de398-152">Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.</span></span> <span data-ttu-id="de398-153">Si no se especifica `-AllowPrerelease`, solo se devolverá la versión 1.8.0.</span><span class="sxs-lookup"><span data-stu-id="de398-153">If `-AllowPrerelease` is not specified, only version 1.8.0 will be returned.</span></span>

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="de398-154">Para instalar una versión preliminar, siempre debe especificar -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="de398-154">To install a prerelease, always specify -AllowPrerelease.</span></span> <span data-ttu-id="de398-155">No basta con especificar una cadena de versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="de398-155">Specifying a prerelease version string is not sufficient.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

<span data-ttu-id="de398-156">El comando anterior no se completó correctamente porque no se especificó -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="de398-156">The previous command failed because -AllowPrerelease was not specified.</span></span> <span data-ttu-id="de398-157">Si agrega `-AllowPrerelease`, la operación se realizará correctamente.</span><span class="sxs-lookup"><span data-stu-id="de398-157">Adding `-AllowPrerelease` will result in success.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="de398-158">No se admite la instalación en paralelo de versiones de un módulo que difieran solo debido a la versión preliminar especificada.</span><span class="sxs-lookup"><span data-stu-id="de398-158">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="de398-159">Al instalar un módulo mediante PowerShellGet, se instalan distintas versiones del mismo módulo en paralelo mediante la creación de un nombre de carpeta con el sufijo ModuleVersion.</span><span class="sxs-lookup"><span data-stu-id="de398-159">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="de398-160">El sufijo ModuleVersion, sin la cadena de versión preliminar, se usa para el nombre de carpeta.</span><span class="sxs-lookup"><span data-stu-id="de398-160">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="de398-161">Si un usuario instala MyModule versión 2.5.0-alpha, se instalará en la carpeta `MyModule\2.5.0`.</span><span class="sxs-lookup"><span data-stu-id="de398-161">If a user installs MyModule version 2.5.0-alpha, it will be installed to the `MyModule\2.5.0` folder.</span></span> <span data-ttu-id="de398-162">Si el usuario luego instala 2.5.0-beta, la versión 2.5.0-beta **sobrescribirá** el contenido de la carpeta `MyModule\2.5.0`.</span><span class="sxs-lookup"><span data-stu-id="de398-162">If the user then installs 2.5.0-beta, the 2.5.0-beta version will **overwrite** the contents of the folder `MyModule\2.5.0`.</span></span> <span data-ttu-id="de398-163">Una ventaja de este método es que no es necesario desinstalar la versión preliminar después de instalar la versión lista para producción.</span><span class="sxs-lookup"><span data-stu-id="de398-163">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="de398-164">En el ejemplo siguiente se muestra lo que se puede esperar:</span><span class="sxs-lookup"><span data-stu-id="de398-164">The example below shows what to expect:</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

<span data-ttu-id="de398-165">Uninstall-Module quita la versión más reciente de un módulo si no se proporciona -RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="de398-165">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="de398-166">Si se especifica -RequiredVersion y es una versión preliminar, debe agregarse -AllowPrerelease al comando.</span><span class="sxs-lookup"><span data-stu-id="de398-166">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a><span data-ttu-id="de398-167">Más detalles</span><span class="sxs-lookup"><span data-stu-id="de398-167">More details</span></span>

- [<span data-ttu-id="de398-168">Versiones preliminares de scripts</span><span class="sxs-lookup"><span data-stu-id="de398-168">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="de398-169">Find-Module</span><span class="sxs-lookup"><span data-stu-id="de398-169">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="de398-170">Install-Module</span><span class="sxs-lookup"><span data-stu-id="de398-170">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="de398-171">Save-Module</span><span class="sxs-lookup"><span data-stu-id="de398-171">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="de398-172">Update-Module</span><span class="sxs-lookup"><span data-stu-id="de398-172">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="de398-173">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="de398-173">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="de398-174">UnInstall-Module</span><span class="sxs-lookup"><span data-stu-id="de398-174">UnInstall-Module</span></span>](/powershell/module/powershellget/uninstall-module)
