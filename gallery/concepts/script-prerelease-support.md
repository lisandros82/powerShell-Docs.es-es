---
ms.date: 10/17/2017
contributor: keithb
keywords: gallery,powershell,cmdlet,psget
title: Versiones preliminares de scripts
ms.openlocfilehash: c0198c2f575d2c004949ccebab49d93ce54716be
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2019
ms.locfileid: "58055893"
---
# <a name="prerelease-versions-of-scripts"></a>Versiones preliminares de scripts

A partir de la versión 1.6.0, PowerShellGet y la Galería de PowerShell admiten el etiquetado de versiones posteriores a 1.0.0 como versión preliminar. Antes de esta característica, los paquetes de versión preliminar se limitaban a tener una versión que comenzaba por 0. El objetivo de estas características es proporcionar mayor compatibilidad con la convención de control de versiones [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) sin interrumpir la compatibilidad con versiones anteriores de PowerShell (versión 3 y superiores) o con versiones existentes de PowerShellGet. Este tema se centra en las características específicas de los scripts. Las características equivalentes de los módulos se encuentran en el tema [Versiones preliminares de módulos](module-prerelease-support.md). Con estas características, los publicadores pueden identificar un script como versión 2.5.0-alpha y, posteriormente, publicar una versión 2.5.0 lista para producción que sustituya a la versión preliminar.

En general, las características de los scripts de versión preliminar incluyen:

- Se agrega un sufijo PrereleaseString a la cadena de versión en el manifiesto del script. Cuando los scripts se publican en la Galería de PowerShell, estos datos se extraen del manifiesto y se usan para identificar paquetes de versión preliminar.
- La adquisición de paquetes de versión preliminar exige agregar la marca -AllowPrerelease a los comandos de PowerShellGet Find-Script, Install-Script, Update-Script y Save-Script. Si no se especifica la marca, no se muestran los paquetes de versión preliminar.
- Las versiones de script mostradas por Find-Script, Get-InstalledScript y en la Galería de PowerShell se muestran con el sufijo PrereleaseString, como en 2.5.0-alpha.

A continuación se incluyen detalles de las características.

## <a name="identifying-a-script-version-as-a-prerelease"></a>Identificación de una versión de script como versión preliminar

La compatibilidad de PowerShellGet con las versiones preliminares resulta más sencilla con los scripts que con los módulos. El control de versiones de script solo es compatible con PowerShellGet, por lo que no hay ningún problema de compatibilidad debido a la adición de la cadena de versión preliminar. Para identificar un script de la Galería de PowerShell como una versión preliminar, agregue un sufijo de versión preliminar a una cadena de versión con un formato correcto en los metadatos del script.

El aspecto de una sección de ejemplo de un manifiesto de script con una versión preliminar sería similar al siguiente:

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

Para usar un sufijo de versión preliminar, la cadena de versión debe cumplir los siguientes requisitos:

- Solo se puede especificar un sufijo de versión preliminar si la versión tiene tres segmentos para Major.Minor.Build.
  Esto se alinea con SemVer v1.0.0.
- El sufijo de versión preliminar es una cadena que comienza con un guión y puede contener caracteres alfanuméricos ASCII [0-9A-Za-z-].
- De momento solo se admiten las cadenas de versión preliminar de SemVer v1.0.0, por lo que el sufijo de versión preliminar **no debe** contener ni punto ni + [.+], que sí se permiten en SemVer 2.0.
- Ejemplos de cadenas admitidas con sufijo PrereleaseString son: -alpha, -alpha1, -BETA, -update20171020.

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Impacto del control de versiones preliminares en las carpetas de instalación y en el criterio de ordenación

El criterio de ordenación cambia cuando se usa una versión preliminar, lo que es importante si se publica en la Galería de PowerShell y si se instalan scripts con comandos de PowerShellGet. Si hay dos versiones de script con el mismo número de versión, el criterio de ordenación se basa en la parte de la cadena que sigue al guión. Por lo tanto, la versión 2.5.0-alpha es menor que 2.5.0-beta, que es menor que 2.5.0-gamma. Si hay dos scripts con el mismo número de versión y solo uno tiene un sufijo PrereleaseString, se da por hecho que el script **sin** el sufijo de versión preliminar es la versión lista para producción y se ordena como una versión mayor que la versión preliminar. Por ejemplo, al comparar las versiones 2.5.0 y 2.5.0-beta, la versión 2.5.0 se considera la mayor.

Al publicar en la Galería de PowerShell, de forma predeterminada, la versión del script que se va a publicar debe ser mayor que cualquier versión publicada previamente que se encuentre en la Galería de PowerShell. Un publicador puede actualizar la versión 2.5.0-alpha con 2.5.0-beta o con 2.5.0 (sin sufijo de versión preliminar).

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Búsqueda y adquisición de paquetes de versión preliminar mediante comandos de PowerShellGet

Para trabajar con paquetes de versión preliminar mediante los comandos de PowerShellGet Find-Script, Install-Script, Update-Script y Save-Script es necesario agregar la marca -AllowPrerelease. Si se especifica -AllowPrerelease, se incluyen los paquetes de versión preliminar, siempre que estén presentes. Si no se especifica la marca -AllowPrerelease, no se muestran los paquetes de versión preliminar.

Las únicas excepciones a esto en los comandos de script de PowerShellGet son Get-InstalledScript y algunos casos con Uninstall-Script.

- Get-InstalledScript siempre muestra automáticamente la información de versión preliminar en la cadena de versión, si está presente.
- Uninstall-Script desinstala de forma predeterminada la versión más reciente de un script, si **no hay ninguna versión** especificada. Ese comportamiento no ha cambiado. Pero, si se especifica una versión preliminar con `-RequiredVersion`, se necesitará `-AllowPrerelease`.

## <a name="examples"></a>Ejemplos

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
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage)[Find-Package], Exception
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

Uninstall-Script quita la versión actual de un script si no se proporciona -RequiredVersion.
Si se especifica -RequiredVersion y es una versión preliminar, debe agregarse -AllowPrerelease al comando.

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-script


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

## <a name="more-details"></a>Más detalles

- [Versiones preliminares de módulos](module-prerelease-support.md)
- [Find-script](/powershell/module/powershellget/find-script)
- [Install-script](/powershell/module/powershellget/install-script)
- [Save-script](/powershell/module/powershellget/save-script)
- [Update-script](/powershell/module/powershellget/update-script)
- [Get-Installedscript](/powershell/module/powershellget/get-installedscript)
- [UnInstall-script](/powershell/module/powershellget/uninstall-script)
