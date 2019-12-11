---
ms.date: 03/28/2019
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Módulos con las ediciones compatibles de PowerShell
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328506"
---
# <a name="modules-with-compatible-powershell-editions"></a>Módulos con las ediciones compatibles de PowerShell

A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.

- **Desktop Edition:** basada en .NET Framework, se aplica a Windows PowerShell 4.0 y versiones anteriores, así como Windows PowerShell 5.1 en escritorio de Windows, Windows Server, Windows Server Core y muchas otras ediciones de Windows.
- **Core Edition:** basada en .NET Core, se aplica a PowerShell Core 6.0 y versiones posteriores, así como Windows PowerShell 5.1 en ediciones de Windows de superficie reducida, como Windows IoT y Windows Nanoserver.

Para más información sobre las ediciones de PowerShell, consulte [about_PowerShell_Editions][].

## <a name="declaring-compatible-editions"></a>Declaración de las ediciones compatibles

Los autores de módulos pueden declarar sus módulos para hacerlos compatibles con una o varias ediciones de PowerShell mediante la clave de manifiesto del módulo CompatiblePSEditions. Esta clave solo se admite en PowerShell 5.1 o versiones posteriores.

> [!NOTE]
> Una vez que se especifica un manifiesto de módulo con la clave CompatiblePSEditions, no se puede importar en la versión 4 ni en versiones anteriores de PowerShell.

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```Output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

Al obtener una lista de los módulos disponibles, puede filtrarla según la edición de PowerShell.

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```Output
Desktop
Core
```

## <a name="targeting-multiple-editions"></a>Varias ediciones como destino

Los autores de módulos pueden publicar un único módulo destinado a una de las ediciones de PowerShell o a ambas (Core o Desktop).

Un único módulo puede trabajar tanto en la edición Desktop como Core; en este módulo, el autor tiene que agregar la lógica necesaria en RootModule o en el manifiesto del módulo mediante la variable $PSEdition. Los módulos pueden tener dos conjuntos de archivos DLL compilados que se dirijan a CoreCLR y a FullCLR. A continuación, se indican un par de formas de empaquetar un módulo con la lógica correspondiente para cargar los archivos DLL adecuados.

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a>Opción 1: empaquetar un módulo para dirigirlo a varias versiones y varias ediciones de PowerShell

Contenido de la carpeta del módulo

- Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- PSScriptAnalyzer.psd1
- PSScriptAnalyzer.psm1
- ScriptAnalyzer.format.ps1xml
- ScriptAnalyzer.types.ps1xml
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- es-ES\about_PSScriptAnalyzer.help.txt
- es-ES\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- Settings\CmdletDesign.psd1
- Settings\DSC.psd1
- Settings\ScriptFunctions.psd1
- Settings\ScriptingStyle.psd1
- Settings\ScriptSecurity.psd1

Contenido del archivo PSScriptAnalyzer.psd1

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

A continuación, la lógica carga los ensamblados necesarios en función de la edición o la versión actual.

Contenido del archivo PSScriptAnalyzer.psm1:

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a>Opción 2: usar la variable $PSEdition en el archivo. PSD1 para cargar los archivos DLL adecuados y los módulos anidados o necesarios

En PS 5.1 y versiones posteriores, se permite usar la variable global $PSEdition en el archivo de manifiesto de módulo. Mediante esta variable el autor del módulo puede especificar los valores condicionales en el archivo de manifiesto de módulo. Se puede hacer referencia a la variable $PSEdition en modo de lenguaje restringido o en una sección de datos.

> [!NOTE]
> Una vez que se especifica un manifiesto de módulo con la clave CompatiblePSEditions (o cuando usa la variable `$PSEdition`), no se puede importar en versiones anteriores de PowerShell.

Ejemplo de un archivo de manifiesto de módulo con la clave CompatiblePSEditions

```powershell
@{
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
}
```

### <a name="module-contents"></a>Contenido del módulo

```powershell
dir -Recurse
```

```Output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
d-----    7/5/2016   1:37 PM          clr
d-----    7/5/2016   1:36 PM          coreclr
-a----    7/5/2016   1:34 PM     4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode           LastWriteTime    Length Name
----           -------------    ------ ----
-a----    7/5/2016   1:35 PM         0 MyFullClrNM1.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrNM2.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM1.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM2.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrRM.dl
```

Los usuarios de la Galería de PowerShell pueden encontrar la lista de los módulos admitidos para una edición específica de PowerShell mediante las etiquetas PSEdition_Desktop y PSEdition_Core.

Se considera que los módulos que no tienen las etiquetas PSEdition_Desktop o PSEdition_Core funcionan correctamente en las ediciones de PowerShell Desktop.

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a>Más detalles

[Scripts con PSEditions](script-psedition-support.md)

[Compatibilidad con PSEditions en la Galería de PowerShell](../how-to/finding-packages/searching-by-compatibility.md)

[Actualizar el manifiesto del módulo](/powershell/module/powershellget/update-modulemanifest)

[about_PowerShell_Editions][]

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
