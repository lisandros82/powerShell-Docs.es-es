---
title: El objeto ISEEditor
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 0101daf8-4e31-4e4c-ab89-01d95dcb8f46
translationtype: Human Translation
ms.sourcegitcommit: 6c666e2e23cb74818e37293410dafc9033057733
ms.openlocfilehash: 9453e0ec5ce2c43a3f140e70db6f30e55c211d64

---

# El objeto ISEEditor
  Un objeto **ISEEditor** es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISEEditor. El panel de consola es un objeto **ISEEditor**. Cada objeto [ISEFile](The-ISEFile-Object.md) tiene asociado un objeto **ISEEditor**. En las secciones siguientes se enumeran los métodos y las propiedades de un objeto **ISEEditor**.

## Métodos

### Borrar\(\)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Borra el texto en el editor.

```PowerShell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### EnsureVisible\(int lineNumber\)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Desplaza el editor de modo que la línea que corresponde al valor del parámetro **lineNumber** especificado está visible. Produce una excepción si el número de línea especificado está fuera del intervalo de 1, último número de línea, que define los números de línea válidos.

 **lineNumber**
: número de la línea que se debe hacer visible.

```PowerShell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### Focus\(\)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Establece el foco en el editor.

```PowerShell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### GetLineLength\(int lineNumber \)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Obtiene la longitud de línea como un entero de la línea especificada por el número de línea.

 **lineNumber**
: número de la línea de la que se obtendrá la longitud.

 **Returns**
: longitud de la línea que corresponde al número de línea especificado.

```PowerShell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### GoToMatch\(\)
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores. 

 Mueve el símbolo de intercalación al carácter coincidente si la propiedad **CanGoToMatch** del objeto del editor es **$true**, lo que ocurre cuando el símbolo de intercalación está inmediatamente antes de un paréntesis, corchete o llave de apertura \(,\[,{ - o inmediatamente después de un paréntesis, corchete o llave de cierre - \),\],}.  El símbolo de intercalación se coloca delante de un carácter de apertura o después de un carácter de cierre. Si la propiedad **CanGoToMatch** es **$false**, el método no hace nada. Consulte [CanGoToMatch](#cangotomatch).

```PowerShell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### InsertText\( text \)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Reemplaza la selección por texto o inserta texto en la posición del símbolo de intercalación actual.

 **text** (cadena); el texto que se inserta.

 Vea [Ejemplo de scripting](#example) más adelante en este tema.

### Select\( startLine, startColumn, endLine, endColumn \)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Selecciona el texto de los parámetros **startLine**, **startColumn**, **endLine** y **endColumn**.

 **startLine** (entero); la línea donde comienza la selección.

 **startColumn** (entero); la columna de la línea de inicio en que comienza la selección.

 **endLine** (entero); la línea en que acaba la selección.

 **endColumn** (entero); la columna de la línea de fin en que acaba la selección.

 Vea [Ejemplo de scripting](#example) más adelante en este tema.

### SelectCaretLine\(\)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Selecciona toda la línea de texto que contiene actualmente el símbolo de intercalación.

```PowerShell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### SetCaretPosition\( lineNumber, columnNumber \)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Establece la posición del símbolo de intercalación en el número de línea y el número de columna. Produce una excepción si el número de línea del símbolo de intercalación o el número de columna del símbolo de intercalación están fuera de sus  intervalos válidos respectivos.

 **lineNumber** (entero); el número de línea del símbolo de intercalación.

 **columnNumber** (entero); el número de columna del símbolo de intercalación.

```PowerShell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### ToggleOutliningExpansion\(\)
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores. 

 Hace que todas las secciones de esquema se expandan o se contraigan.

```PowerShell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## Propiedades

###  <a name="CanGoToMatch"></a> CanGoToMatch
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores. 

 Propiedad booleana de solo lectura que indica si el símbolo de intercalación está al lado de paréntesis, corchetes o llaves: \(\), \[\], {}. Si el símbolo de intercalación está inmediatamente antes del carácter de apertura o inmediatamente después del carácter de cierre de un par, el valor de esta propiedad es **$true**. Si no, es **$false**.

```PowerShell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

###  <a name="CaretColumn"></a> CaretColumn
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Propiedad de solo lectura que obtiene el número de columna que corresponde a la posición del símbolo de intercalación.

```PowerShell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

###  <a name="CaretLine"></a> CaretLine
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Propiedad de solo lectura que obtiene el número de la línea que contiene el símbolo de intercalación.

```PowerShell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

###  <a name="caretlinetext"></a> CaretLineText
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Propiedad de solo lectura que obtiene la línea de texto completa que contiene el símbolo de intercalación.

```PowerShell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

###  <a name="LineCount"></a> LineCount
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Propiedad de solo lectura que obtiene el recuento de líneas del editor.

```PowerShell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

###  <a name="SelectedText"></a> SelectedText
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Propiedad de solo lectura que obtiene el texto seleccionado del editor.

 Vea [Ejemplo de scripting](#example) más adelante en este tema.

###  <a name="Text"></a> Texto
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Propiedad de lectura y escritura que obtiene o establece el texto en el editor.

 Vea [Ejemplo de scripting](#example) más adelante en este tema.

##  <a name="example"></a> Ejemplo de scripting

```PowerShell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase. 
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line. 
$endColumn= $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1,1,3,$endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## Véase también
- [El objeto ISEFile](The-ISEFile-Object.md) 
- [El objeto PowerShellTab](The-PowerShellTab-Object.md) 
- [El modelo de objetos de scripting de ISE de Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referencia del modelo de objetos de ISE de Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Oct16_HO3-->


