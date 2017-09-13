---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: El objeto ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: a1fbd48e872684cc578adb03f52430eabdc54c2c
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefile-object"></a>El objeto ISEFile
  Un objeto **ISEFile** representa un archivo en el Entorno de scripting integrado (ISE) de Windows PowerShell®. Es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISEFile. Este tema enumera sus métodos de miembro y propiedades de miembro. **$psISE.CurrentFile** y los archivos de la colección de archivos en una pestaña de PowerShell son todas las instancias de la clase Microsoft.PowerShell.Host.ISE.ISEFile.

## <a name="methods"></a>Métodos

### <a name="save-saveencoding-"></a>Save\( \[saveEncoding\] \)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Guarda el archivo en disco.

 **\[saveEncoding\]**: [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) opcional. Un parámetro de codificación de carácter opcional que se usará para el archivo guardado. El valor predeterminado es **UTF8**.

 **Excepciones**
 -   **System.IO.IOException**: no se pudo guardar el archivo.

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(nombre de archivo, \[saveEncoding\]\)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Guarda el archivo con el nombre de archivo y codificación especificados.

 **filename**: cadena. El nombre que se utilizará para guardar el archivo.

 **\[saveEncoding\]**: [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) opcional. Un parámetro de codificación de carácter opcional que se usará para el archivo guardado. El valor predeterminado es **UTF8**.

 **Excepciones**
 -   **System.ArgumentNullException**: el parámetro **nombre_de_archivo** es null.

- **System.ArgumentException**: el parámetro **nombre_de_archivo** está vacío.

- **System.IO.IOException**: no se pudo guardar el archivo.

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a>Propiedades

### <a name="displayname"></a>DisplayName
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 La propiedad de solo lectura que obtiene la cadena que contiene el nombre para mostrar de este archivo. El nombre se muestra en la pestaña **Archivo** en la parte superior del editor. La presencia de un asterisco \(\*\) al final del nombre indica que el archivo tiene cambios que no se han guardado.

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a>Editor
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad de solo lectura que obtiene el [objeto de editor](The-ISEEditor-Object.md) que se utiliza para el archivo especificado.

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a>Codificación
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad de solo lectura que obtiene la codificación del archivo original. Se trata de un objeto **System.Text.Encoding**.

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a>FullPath
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad de solo lectura que obtiene la cadena que especifica la ruta de acceso completa del archivo abierto.

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a>IsSaved
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad booleana de solo lectura que devuelve **$true** si el archivo se ha guardado una vez que se modificó por última vez.

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a>IsUntitled
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad de solo lectura que devuelve **$true** si nunca se asignó un título al archivo.

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a>Véase también
- [ISEFileCollectionObject](The-ISEFileCollection-Object.md) 
- [El modelo de objetos de scripting de ISE de Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referencia del modelo de objetos de ISE de Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)
