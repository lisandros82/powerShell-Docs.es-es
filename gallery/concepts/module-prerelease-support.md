---
ms.date: 09/26/2017
contributor: keithb
keywords: gallery,powershell,cmdlet,psget
title: Versiones preliminares de módulos
ms.openlocfilehash: 371aae7eed4afe341755133c5ee2d356cd5876e0
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093786"
---
# <a name="prerelease-module-versions"></a>Versiones preliminares de módulos

A partir de la versión 1.6.0, PowerShellGet y la Galería de PowerShell admiten el etiquetado de versiones posteriores a 1.0.0 como versión preliminar. Antes de esta característica, los elementos de versión preliminar se limitaban a tener una versión que comenzaba por 0. El objetivo de estas características es proporcionar mayor compatibilidad con la convención de control de versiones [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) sin interrumpir la compatibilidad con versiones anteriores de PowerShell (versión 3 y superiores) o con versiones existentes de PowerShellGet. Este tema se centra en las características específicas de los módulos. Las características equivalentes de los scripts se encuentran en el tema [Versiones preliminares de scripts](script-prerelease-support.md). Con estas características, los publicadores pueden identificar un módulo o script como versión 2.5.0-alpha y, posteriormente, publicar una versión 2.5.0 lista para producción que sustituya a la versión preliminar.

En general, las características de los módulos de versión preliminar incluyen:

- La adición de una cadena de versión preliminar a la sección PSData del manifiesto del módulo identifica a ese módulo como una versión preliminar. Cuando el módulo se publica en la Galería de PowerShell, estos datos se extraen del manifiesto y se usan para identificar elementos de versión preliminar.
- La adquisición de elementos de versión preliminar exige agregar la marca -AllowPrerelease a los comandos de PowerShellGet Find-Module, Install-Module, Update-Module y Save-Module. Si no se especifica la marca, no se muestran los elementos de versión preliminar.
- Las versiones de módulo mostradas mediante Find-Module, Get-InstalledModule y en la Galería de PowerShell se muestran como una sola cadena con la cadena de versión preliminar anexa, como en 2.5.0-alpha.

A continuación se incluyen detalles de las características.

Estos cambios no afectan a la compatibilidad de versión de módulo integrada en PowerShell y son compatibles con PowerShell 3.0, 4.0 y 5.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Identificación de una versión de módulo como versión preliminar

La compatibilidad de PowerShellGet con las versiones preliminares exige el uso de dos campos en el manifiesto del módulo:

- Si se usa una versión preliminar, el elemento ModuleVersion incluido en el manifiesto del módulo debe ser una versión de tres partes que debe atenerse al control de versiones existente de PowerShell. El formato de versión sería A.B.C, donde A, B y C son todos enteros.
- La cadena de versión preliminar se especifica en el manifiesto del módulo, en la sección PSData de PrivateData.

A continuación se indican los requisitos detallados de la cadena de versión preliminar.

El aspecto de una sección de ejemplo de un manifiesto de módulo que define un módulo como versión preliminar sería similar al siguiente:

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

Los requisitos detallados de la cadena de versión preliminar son:

- Solo se puede especificar la cadena de versión preliminar cuando el elemento ModuleVersion tiene tres segmentos para Major.Minor.Build. Esto se alinea con SemVer v1.0.0.
- Un guión es el delimitador entre el número de compilación y la cadena de versión preliminar. Se puede incluir un guión en la cadena de versión preliminar únicamente como primer carácter.
- La cadena de versión preliminar solo puede contener caracteres alfanuméricos ASCII [0-9A-Za-z-]. Comenzar la cadena de versión preliminar con un carácter alfanumérico es un procedimiento recomendado, ya que facilita su identificación como una versión preliminar al examinar una lista de elementos.
- De momento solo se admiten las cadenas de versión preliminar de SemVer v1.0.0. La cadena de versión preliminar __no debe__ contener ni punto ni + [.+], que sí se permiten en SemVer 2.0.
- Ejemplos de cadenas de versión preliminar admitidas son: -alpha, -alpha1, -BETA, -update20171020.

__Impacto del control de versiones preliminares en las carpetas de instalación y en el criterio de ordenación__

El criterio de ordenación cambia cuando se usa una versión preliminar, lo que es importante si se publica en la Galería de PowerShell y si se instalan módulos con comandos de PowerShellGet. Si se especifica la cadena de versión preliminar para dos módulos, el criterio de ordenación se basa en la parte de la cadena que sigue al guión. Por lo tanto, la versión 2.5.0-alpha es menor que 2.5.0-beta, que es menor que 2.5.0-gamma. Si hay dos módulos con el mismo elemento ModuleVersion y solo uno tiene una cadena de versión preliminar, se da por hecho que el módulo sin la cadena de versión preliminar es la versión lista para producción y se ordena como una versión mayor que la versión preliminar (que incluye la cadena de versión preliminar). Por ejemplo, al comparar las versiones 2.5.0 y 2.5.0-beta, la versión 2.5.0 se considera la mayor.

Al publicar en la Galería de PowerShell, de forma predeterminada, la versión del módulo que se va a publicar debe ser mayor que cualquier versión publicada previamente que se encuentre en la Galería de PowerShell.

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Búsqueda y adquisición de elementos de versión preliminar mediante comandos de PowerShellGet

Para trabajar con elementos de versión preliminar mediante los comandos de PowerShellGet Find-Module, Install-Module, Update-Module y Save-Module es necesario agregar la marca -AllowPrerelease. Si se especifica -AllowPrerelease, se incluyen los elementos de versión preliminar, siempre que estén presentes. Si no se especifica la marca -AllowPrerelease, no se muestran los elementos de versión preliminar.

Las únicas excepciones a esto en los comandos de módulo de PowerShellGet son Get-InstalledModule y algunos casos con Uninstall-Module.

- Get-InstalledModule siempre muestra automáticamente la información de versión preliminar en la cadena de versión de los módulos.
- Uninstall-Module desinstala de forma predeterminada la versión más reciente de un módulo, si __no hay ninguna versión__ especificada. Ese comportamiento no ha cambiado. Pero si se especifica una versión preliminar con -RequiredVersion, se necesita -AllowPrerelease.

## <a name="examples"></a>Ejemplos

```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> find-module TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

# To install a prerelease, always specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
```

No se admite la instalación en paralelo de versiones de un módulo que difieran solo debido a la versión preliminar especificada. Al instalar un módulo mediante PowerShellGet, se instalan distintas versiones del mismo módulo en paralelo mediante la creación de un nombre de carpeta con el sufijo ModuleVersion. El sufijo ModuleVersion, sin la cadena de versión preliminar, se usa para el nombre de carpeta. Si un usuario instala MyModule versión 2.5.0-alpha, se instala en la carpeta MyModule\2.5.0. Si el usuario luego instala 2.5.0-beta, la versión 2.5.0-beta __sobrescribe__ el contenido de la carpeta MyModule\2.5.0. Una ventaja de este método es que no es necesario desinstalar la versión preliminar después de instalar la versión lista para producción. En el ejemplo siguiente se muestra lo que se puede esperar:

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-beta     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

Uninstall-Module quita la versión más reciente de un módulo si no se proporciona -RequiredVersion.
Si se especifica -RequiredVersion y es una versión preliminar, debe agregarse -AllowPrerelease al comando.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module



C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...


```

## <a name="more-details"></a>Más detalles

- [Versiones preliminares de scripts](script-prerelease-support.md)
- [Find-Module](/powershell/module/powershellget/find-module)
- [Install-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [UnInstall-Module](/powershell/gallery/psget/module/psget_uninstall-module)