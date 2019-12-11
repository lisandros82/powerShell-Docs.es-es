---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: El objeto ISEFile
ms.openlocfilehash: ebb5a35f6ea9d93eab633b9f4e6c84e4fddd6ae8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028965"
---
# <a name="the-isefile-object"></a>El objeto ISEFile

Un objeto **ISEFile** representa un archivo en el Entorno de scripting integrado (ISE) de Windows PowerShell®. Es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISEFile. Este tema enumera sus métodos de miembro y propiedades de miembro. **$psISE.CurrentFile** y los archivos de la colección de archivos en una pestaña de PowerShell son todas las instancias de la clase Microsoft.PowerShell.Host.ISE.ISEFile.

## <a name="methods"></a>Métodos

### <a name="save-saveencoding-"></a>Save\( \[saveEncoding\] \)

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

Guarda el archivo en disco.

**\[saveEncoding\]** : [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) opcional. Un parámetro de codificación de carácter opcional que se usará para el archivo guardado. El valor predeterminado es **UTF8**.

### <a name="exceptions"></a>Excepciones

- **System.IO.IOException**: No se pudo guardar el archivo.

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(nombre de archivo, \[saveEncoding\]\)

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

Guarda el archivo con el nombre de archivo y codificación especificados.

**filename**: cadena. El nombre que se utilizará para guardar el archivo.

**\[saveEncoding\]** : [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) opcional. Un parámetro de codificación de carácter opcional que se usará para el archivo guardado. El valor predeterminado es **UTF8**.

### <a name="exceptions"></a>Excepciones

- **System.ArgumentNullException**: El parámetro **filename** es nulo.
- **System.ArgumentException**: El parámetro **filename** está vacío.
- **System.IO.IOException**: No se pudo guardar el archivo.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Propiedades

### <a name="displayname"></a>DisplayName

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene la cadena que contiene el nombre para mostrar de este archivo. El nombre se muestra en la pestaña **Archivo** en la parte superior del editor. La presencia de un asterisco \(\*\) al final del nombre indica que el archivo tiene cambios que no se han guardado.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Editor

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene el [objeto de editor](The-ISEEditor-Object.md) que se utiliza para el archivo especificado.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Codificación

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene la codificación del archivo original. Se trata de un objeto **System.Text.Encoding**.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene la cadena que especifica la ruta de acceso completa del archivo abierto.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad booleana de solo lectura que devuelve **$true** si el archivo se ha guardado una vez que se modificó por última vez.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que devuelve **$true** si nunca se asignó un título al archivo.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Véase también

- [ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)
