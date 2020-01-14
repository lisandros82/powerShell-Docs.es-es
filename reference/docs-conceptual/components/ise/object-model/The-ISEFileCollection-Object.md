---
ms.date: 12/31/2019
keywords: powershell, cmdlet
title: El objeto ISEFileCollection
ms.openlocfilehash: 4192afa9dc91d9ea4c4c084d3ba0175483620229
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736222"
---
# <a name="the-isefilecollection-object"></a>El objeto ISEFileCollection

El objeto **ISEFileCollection** es una colección de objetos **ISEFile**. Un ejemplo es la colección `$psISE.CurrentPowerShellTab.Files`.

## <a name="methods"></a>Métodos

### <a name="add-fullpath-"></a>Add\( \[FullPath\] \)

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

Crea y devuelve un archivo sin título nuevo y lo agrega a la colección. La propiedad **IsUntitled** del archivo recién creado es `$true`.

**\[FullPath\]** : cadena opcional. La ruta de acceso completamente especificada del archivo. Se genera una excepción si incluye el parámetro **FullPath** y una ruta de acceso relativa, o bien si utiliza un nombre de archivo en lugar de la ruta de acceso completa.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Remove\( File, \[Force\] \)

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

Quita un archivo especificado en la pestaña actual de PowerShell.

**File**: cadena. Archivo ISEFile que quiere quitar de la colección. Si el archivo no se ha guardado, este método inicia una excepción. Utilice el parámetro modificador **Force** parámetro para forzar la eliminación de un archivo no guardado.

**\[Force\]** : booleano opcional. Si se establece en `$true`, concede permiso para quitar el archivo incluso si no se ha guardado después del último uso. El valor predeterminado es `$false`.

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile \)

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

Selecciona el archivo que especifica el parámetro **SelectedFile**.

**SelectedFile**: Microsoft.PowerShell.Host.ISE.ISEFile. Archivo ISEFile que quiere seleccionar.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Consulte también

- [El objeto ISEFile](The-ISEFile-Object.md)
- [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)
