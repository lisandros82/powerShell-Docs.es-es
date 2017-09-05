---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: El objeto ISEEditor
ms.assetid: 0101daf8-4e31-4e4c-ab89-01d95dcb8f46
ms.openlocfilehash: e2ddb0de1089c832f130e1f5c7c8dcb199aca2fa
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2017
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="38c3a-103">El objeto ISEEditor</span><span class="sxs-lookup"><span data-stu-id="38c3a-103">The ISEEditor Object</span></span>
  <span data-ttu-id="38c3a-104">Un objeto **ISEEditor** es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="38c3a-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="38c3a-105">El panel de consola es un objeto **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="38c3a-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="38c3a-106">Cada objeto [ISEFile](The-ISEFile-Object.md) tiene asociado un objeto **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="38c3a-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="38c3a-107">En las secciones siguientes se enumeran los métodos y las propiedades de un objeto **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="38c3a-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="38c3a-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="38c3a-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="38c3a-109">Borrar\(\)</span><span class="sxs-lookup"><span data-stu-id="38c3a-109">Clear\(\)</span></span>
  <span data-ttu-id="38c3a-110">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38c3a-111">Borra el texto en el editor.</span><span class="sxs-lookup"><span data-stu-id="38c3a-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="38c3a-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="38c3a-112">EnsureVisible\(int lineNumber\)</span></span>
  <span data-ttu-id="38c3a-113">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38c3a-114">Desplaza el editor de modo que la línea que corresponde al valor del parámetro **lineNumber** especificado está visible.</span><span class="sxs-lookup"><span data-stu-id="38c3a-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="38c3a-115">Produce una excepción si el número de línea especificado está fuera del intervalo de 1, último número de línea, que define los números de línea válidos.</span><span class="sxs-lookup"><span data-stu-id="38c3a-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

 <span data-ttu-id="38c3a-116">**lineNumber** Número de la línea que se debe hacer visible.</span><span class="sxs-lookup"><span data-stu-id="38c3a-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="38c3a-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="38c3a-117">Focus\(\)</span></span>
  <span data-ttu-id="38c3a-118">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38c3a-119">Establece el foco en el editor.</span><span class="sxs-lookup"><span data-stu-id="38c3a-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="38c3a-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="38c3a-120">GetLineLength\(int lineNumber \)</span></span>
  <span data-ttu-id="38c3a-121">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38c3a-122">Obtiene la longitud de línea como un entero de la línea especificada por el número de línea.</span><span class="sxs-lookup"><span data-stu-id="38c3a-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

 <span data-ttu-id="38c3a-123">**lineNumber** Número de la línea de la que se obtendrá la longitud.</span><span class="sxs-lookup"><span data-stu-id="38c3a-123">**lineNumber** The number of the line of which to get the length.</span></span>

 <span data-ttu-id="38c3a-124">**Returns** Longitud de la línea que corresponde al número de línea especificado.</span><span class="sxs-lookup"><span data-stu-id="38c3a-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="38c3a-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="38c3a-125">GoToMatch\(\)</span></span>
  <span data-ttu-id="38c3a-126">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="38c3a-127">Mueve el símbolo de intercalación al carácter coincidente si la propiedad **CanGoToMatch** del objeto del editor es **$true**, lo que ocurre cuando el símbolo de intercalación está inmediatamente antes de un paréntesis, corchete o llave de apertura \(,\[,{ - o inmediatamente después de un paréntesis, corchete o llave de cierre - \),\],}.</span><span class="sxs-lookup"><span data-stu-id="38c3a-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="38c3a-128">El símbolo de intercalación se coloca delante de un carácter de apertura o después de un carácter de cierre.</span><span class="sxs-lookup"><span data-stu-id="38c3a-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="38c3a-129">Si la propiedad **CanGoToMatch** es **$false**, el método no hace nada.</span><span class="sxs-lookup"><span data-stu-id="38c3a-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span> <span data-ttu-id="38c3a-130">Consulte [CanGoToMatch]().</span><span class="sxs-lookup"><span data-stu-id="38c3a-130">See [CanGoToMatch]().</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### <a name="inserttext-text-"></a><span data-ttu-id="38c3a-131">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="38c3a-131">InsertText\( text \)</span></span>
  <span data-ttu-id="38c3a-132">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-132">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38c3a-133">Reemplaza la selección por texto o inserta texto en la posición del símbolo de intercalación actual.</span><span class="sxs-lookup"><span data-stu-id="38c3a-133">Replaces the selection with text or inserts text at the current caret position.</span></span>

 <span data-ttu-id="38c3a-134">**text** (cadena); el texto que se inserta.</span><span class="sxs-lookup"><span data-stu-id="38c3a-134">**text** - String The text to insert.</span></span>

 <span data-ttu-id="38c3a-135">Vea [Ejemplo de scripting]() más adelante en este tema.</span><span class="sxs-lookup"><span data-stu-id="38c3a-135">See the [Scripting Example]() later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="38c3a-136">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="38c3a-136">Select\( startLine, startColumn, endLine, endColumn \)</span></span>
  <span data-ttu-id="38c3a-137">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-137">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38c3a-138">Selecciona el texto de los parámetros **startLine**, **startColumn**, **endLine** y **endColumn**.</span><span class="sxs-lookup"><span data-stu-id="38c3a-138">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

 <span data-ttu-id="38c3a-139">**startLine** (entero); la línea donde comienza la selección.</span><span class="sxs-lookup"><span data-stu-id="38c3a-139">**startLine** - Integer The line where the selection starts.</span></span>

 <span data-ttu-id="38c3a-140">**startColumn** (entero); la columna de la línea de inicio en que comienza la selección.</span><span class="sxs-lookup"><span data-stu-id="38c3a-140">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

 <span data-ttu-id="38c3a-141">**endLine** (entero); la línea en que acaba la selección.</span><span class="sxs-lookup"><span data-stu-id="38c3a-141">**endLine** - Integer The line where the selection ends.</span></span>

 <span data-ttu-id="38c3a-142">**endColumn** (entero); la columna de la línea de fin en que acaba la selección.</span><span class="sxs-lookup"><span data-stu-id="38c3a-142">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

 <span data-ttu-id="38c3a-143">Vea [Ejemplo de scripting]() más adelante en este tema.</span><span class="sxs-lookup"><span data-stu-id="38c3a-143">See the  [Scripting Example]() later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="38c3a-144">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="38c3a-144">SelectCaretLine\(\)</span></span>
  <span data-ttu-id="38c3a-145">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-145">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38c3a-146">Selecciona toda la línea de texto que contiene actualmente el símbolo de intercalación.</span><span class="sxs-lookup"><span data-stu-id="38c3a-146">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="38c3a-147">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="38c3a-147">SetCaretPosition\( lineNumber, columnNumber \)</span></span>
  <span data-ttu-id="38c3a-148">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-148">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38c3a-149">Establece la posición del símbolo de intercalación en el número de línea y el número de columna.</span><span class="sxs-lookup"><span data-stu-id="38c3a-149">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="38c3a-150">Produce una excepción si el número de línea del símbolo de intercalación o el número de columna del símbolo de intercalación están fuera de sus  intervalos válidos respectivos.</span><span class="sxs-lookup"><span data-stu-id="38c3a-150">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

 <span data-ttu-id="38c3a-151">**lineNumber** (entero); el número de línea del símbolo de intercalación.</span><span class="sxs-lookup"><span data-stu-id="38c3a-151">**lineNumber** - Integer The caret line number.</span></span>

 <span data-ttu-id="38c3a-152">**columnNumber** (entero); el número de columna del símbolo de intercalación.</span><span class="sxs-lookup"><span data-stu-id="38c3a-152">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="38c3a-153">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="38c3a-153">ToggleOutliningExpansion\(\)</span></span>
  <span data-ttu-id="38c3a-154">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="38c3a-155">Hace que todas las secciones de esquema se expandan o se contraigan.</span><span class="sxs-lookup"><span data-stu-id="38c3a-155">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="38c3a-156">Propiedades</span><span class="sxs-lookup"><span data-stu-id="38c3a-156">Properties</span></span>

###  <span data-ttu-id="38c3a-157"><a name="CanGoToMatch"></a> CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="38c3a-157"><a name="CanGoToMatch"></a> CanGoToMatch</span></span>
  <span data-ttu-id="38c3a-158">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-158">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="38c3a-159">Propiedad booleana de solo lectura que indica si el símbolo de intercalación está al lado de paréntesis, corchetes o llaves: \(\), \[\], {}.</span><span class="sxs-lookup"><span data-stu-id="38c3a-159">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="38c3a-160">Si el símbolo de intercalación está inmediatamente antes del carácter de apertura o inmediatamente después del carácter de cierre de un par, el valor de esta propiedad es **$true**.</span><span class="sxs-lookup"><span data-stu-id="38c3a-160">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="38c3a-161">Si no, es **$false**.</span><span class="sxs-lookup"><span data-stu-id="38c3a-161">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

###  <span data-ttu-id="38c3a-162"><a name="CaretColumn"></a> CaretColumn</span><span class="sxs-lookup"><span data-stu-id="38c3a-162"><a name="CaretColumn"></a> CaretColumn</span></span>
  <span data-ttu-id="38c3a-163">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-163">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38c3a-164">Propiedad de solo lectura que obtiene el número de columna que corresponde a la posición del símbolo de intercalación.</span><span class="sxs-lookup"><span data-stu-id="38c3a-164">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

###  <span data-ttu-id="38c3a-165"><a name="CaretLine"></a> CaretLine</span><span class="sxs-lookup"><span data-stu-id="38c3a-165"><a name="CaretLine"></a> CaretLine</span></span>
  <span data-ttu-id="38c3a-166">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-166">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38c3a-167">Propiedad de solo lectura que obtiene el número de la línea que contiene el símbolo de intercalación.</span><span class="sxs-lookup"><span data-stu-id="38c3a-167">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

###  <span data-ttu-id="38c3a-168"><a name="CaretLineText"></a> CaretLineText</span><span class="sxs-lookup"><span data-stu-id="38c3a-168"><a name="CaretLineText"></a> CaretLineText</span></span>
  <span data-ttu-id="38c3a-169">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38c3a-170">Propiedad de solo lectura que obtiene la línea de texto completa que contiene el símbolo de intercalación.</span><span class="sxs-lookup"><span data-stu-id="38c3a-170">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

###  <span data-ttu-id="38c3a-171"><a name="LineCount"></a> LineCount</span><span class="sxs-lookup"><span data-stu-id="38c3a-171"><a name="LineCount"></a> LineCount</span></span>
  <span data-ttu-id="38c3a-172">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-172">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38c3a-173">Propiedad de solo lectura que obtiene el recuento de líneas del editor.</span><span class="sxs-lookup"><span data-stu-id="38c3a-173">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

###  <span data-ttu-id="38c3a-174"><a name="SelectedText"></a> SelectedText</span><span class="sxs-lookup"><span data-stu-id="38c3a-174"><a name="SelectedText"></a> SelectedText</span></span>
  <span data-ttu-id="38c3a-175">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-175">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38c3a-176">Propiedad de solo lectura que obtiene el texto seleccionado del editor.</span><span class="sxs-lookup"><span data-stu-id="38c3a-176">The read-only property that gets the selected text from the editor.</span></span>

 <span data-ttu-id="38c3a-177">Vea [Ejemplo de scripting]() más adelante en este tema.</span><span class="sxs-lookup"><span data-stu-id="38c3a-177">See the  [Scripting Example]() later in this topic.</span></span>

###  <span data-ttu-id="38c3a-178"><a name="Text"></a> Text</span><span class="sxs-lookup"><span data-stu-id="38c3a-178"><a name="Text"></a> Text</span></span>
  <span data-ttu-id="38c3a-179">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="38c3a-179">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38c3a-180">Propiedad de lectura y escritura que obtiene o establece el texto en el editor.</span><span class="sxs-lookup"><span data-stu-id="38c3a-180">The read/write property that gets or sets the text in the editor.</span></span>

 <span data-ttu-id="38c3a-181">Vea [Ejemplo de scripting]() más adelante en este tema.</span><span class="sxs-lookup"><span data-stu-id="38c3a-181">See the [Scripting Example]() later in this topic.</span></span>

##  <span data-ttu-id="38c3a-182"><a name="example"></a> Ejemplo de scripting</span><span class="sxs-lookup"><span data-stu-id="38c3a-182"><a name="example"></a> Scripting Example</span></span>

```powershell
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

## <a name="see-also"></a><span data-ttu-id="38c3a-183">Véase también</span><span class="sxs-lookup"><span data-stu-id="38c3a-183">See Also</span></span>
- [<span data-ttu-id="38c3a-184">El objeto ISEFile</span><span class="sxs-lookup"><span data-stu-id="38c3a-184">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="38c3a-185">El objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="38c3a-185">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="38c3a-186">El modelo de objetos de scripting de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="38c3a-186">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="38c3a-187">Referencia del modelo de objetos de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="38c3a-187">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="38c3a-188">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="38c3a-188">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
