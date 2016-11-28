---
title: El objeto ISEFileCollection
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
translationtype: Human Translation
ms.sourcegitcommit: 6c666e2e23cb74818e37293410dafc9033057733
ms.openlocfilehash: 86cb3485445fdb00c9b99a20694b9bf12a6e8f2c

---

# <a name="the-isefilecollection-object"></a>El objeto ISEFileCollection
  El objeto **ISEFileCollection** es una colección de objetos **ISEFile**. Un ejemplo es la colección $psISE.CurrentPowerShellTab.Files.

## <a name="methods"></a>Métodos

### <a name="add-fullpath-"></a>Add\( \[fullPath\] \)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Crea y devuelve un archivo sin título nuevo y lo agrega a la colección. La propiedad **IsUntitled** del archivo recién creado es **$true**.

 **\[fullPath\]**: cadena opcional. Ruta de acceso completamente especificada del archivo. Se genera una excepción si incluye el parámetro **rutaAccesoCompleta** y una ruta de acceso relativa, o si utiliza un nombre de archivo en lugar de la ruta de acceso completa.

```
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")

```

### <a name="remove-file-force-"></a>Remove\( File, \[Force\] \)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Quita un archivo especificado en la pestaña actual de PowerShell.

 **File**: cadena. Archivo ISEFile que quiere quitar de la colección. Si el archivo no se ha guardado, este método inicia una excepción. Utilice el parámetro modificador **Force** parámetro para forzar la eliminación de un archivo no guardado.

 **\[Force\]**: booleano opcional. Si se establece en **$true**, concede permiso para quitar el archivo incluso si no se ha guardado después del último uso. El valor predeterminado es **$false**.

```
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

 Selecciona el archivo que especifica el parámetro **archivoSeleccionado**.

 **selectedFile**: Microsoft.PowerShell.Host.ISE.ISEFile. Archivo ISEFile que quiere seleccionar.

```

# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)

```

## <a name="see-also"></a>Véase también
- [El objeto ISEFile](The-ISEFile-Object.md) 
- [El modelo de objetos de scripting de ISE de Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referencia del modelo de objetos de ISE de Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Nov16_HO4-->


