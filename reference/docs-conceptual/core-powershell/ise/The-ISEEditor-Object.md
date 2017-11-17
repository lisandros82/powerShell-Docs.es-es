---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: El objeto ISEEditor
ms.openlocfilehash: c593eeebf0b9a94769841efd2aa78f84a3829ca5
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/29/2017
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="b4313-103">El objeto ISEEditor</span><span class="sxs-lookup"><span data-stu-id="b4313-103">The ISEEditor Object</span></span>
  <span data-ttu-id="b4313-104">Un objeto **ISEEditor** es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="b4313-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="b4313-105">El panel de consola es un objeto **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="b4313-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="b4313-106">Cada objeto [ISEFile](The-ISEFile-Object.md) tiene asociado un objeto **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="b4313-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="b4313-107">En las secciones siguientes se enumeran los métodos y las propiedades de un objeto **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="b4313-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="b4313-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="b4313-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="b4313-109">Borrar\(\)</span><span class="sxs-lookup"><span data-stu-id="b4313-109">Clear\(\)</span></span>
  <span data-ttu-id="b4313-110">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b4313-111">Borra el texto en el editor.</span><span class="sxs-lookup"><span data-stu-id="b4313-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="b4313-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="b4313-112">EnsureVisible\(int lineNumber\)</span></span>
  <span data-ttu-id="b4313-113">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b4313-114">Desplaza el editor de modo que la línea que corresponde al valor del parámetro **lineNumber** especificado está visible.</span><span class="sxs-lookup"><span data-stu-id="b4313-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="b4313-115">Produce una excepción si el número de línea especificado está fuera del intervalo de 1, último número de línea, que define los números de línea válidos.</span><span class="sxs-lookup"><span data-stu-id="b4313-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

 <span data-ttu-id="b4313-116">**lineNumber** Número de la línea que se debe hacer visible.</span><span class="sxs-lookup"><span data-stu-id="b4313-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="b4313-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="b4313-117">Focus\(\)</span></span>
  <span data-ttu-id="b4313-118">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b4313-119">Establece el foco en el editor.</span><span class="sxs-lookup"><span data-stu-id="b4313-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="b4313-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="b4313-120">GetLineLength\(int lineNumber \)</span></span>
  <span data-ttu-id="b4313-121">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b4313-122">Obtiene la longitud de línea como un entero de la línea especificada por el número de línea.</span><span class="sxs-lookup"><span data-stu-id="b4313-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

 <span data-ttu-id="b4313-123">**lineNumber** Número de la línea de la que se obtendrá la longitud.</span><span class="sxs-lookup"><span data-stu-id="b4313-123">**lineNumber** The number of the line of which to get the length.</span></span>

 <span data-ttu-id="b4313-124">**Returns** Longitud de la línea que corresponde al número de línea especificado.</span><span class="sxs-lookup"><span data-stu-id="b4313-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="b4313-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="b4313-125">GoToMatch\(\)</span></span>
  <span data-ttu-id="b4313-126">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="b4313-127">Mueve el símbolo de intercalación al carácter coincidente si la propiedad **CanGoToMatch** del objeto del editor es **$true**, lo que ocurre cuando el símbolo de intercalación está inmediatamente antes de un paréntesis, corchete o llave de apertura \(,\[,{ - o inmediatamente después de un paréntesis, corchete o llave de cierre - \),\],}.</span><span class="sxs-lookup"><span data-stu-id="b4313-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="b4313-128">El símbolo de intercalación se coloca delante de un carácter de apertura o después de un carácter de cierre.</span><span class="sxs-lookup"><span data-stu-id="b4313-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="b4313-129">Si la propiedad **CanGoToMatch** es **$false**, el método no hace nada.</span><span class="sxs-lookup"><span data-stu-id="b4313-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### <a name="inserttext-text-"></a><span data-ttu-id="b4313-130">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="b4313-130">InsertText\( text \)</span></span>
  <span data-ttu-id="b4313-131">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b4313-132">Reemplaza la selección por texto o inserta texto en la posición del símbolo de intercalación actual.</span><span class="sxs-lookup"><span data-stu-id="b4313-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

 <span data-ttu-id="b4313-133">**text** (cadena); el texto que se inserta.</span><span class="sxs-lookup"><span data-stu-id="b4313-133">**text** - String The text to insert.</span></span>

 <span data-ttu-id="b4313-134">Vea [Ejemplo de scripting](#scripting-example) más adelante en este tema.</span><span class="sxs-lookup"><span data-stu-id="b4313-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="b4313-135">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="b4313-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>
  <span data-ttu-id="b4313-136">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b4313-137">Selecciona el texto de los parámetros **startLine**, **startColumn**, **endLine** y **endColumn**.</span><span class="sxs-lookup"><span data-stu-id="b4313-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

 <span data-ttu-id="b4313-138">**startLine** (entero); la línea donde comienza la selección.</span><span class="sxs-lookup"><span data-stu-id="b4313-138">**startLine** - Integer The line where the selection starts.</span></span>

 <span data-ttu-id="b4313-139">**startColumn** (entero); la columna de la línea de inicio en que comienza la selección.</span><span class="sxs-lookup"><span data-stu-id="b4313-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

 <span data-ttu-id="b4313-140">**endLine** (entero); la línea en que acaba la selección.</span><span class="sxs-lookup"><span data-stu-id="b4313-140">**endLine** - Integer The line where the selection ends.</span></span>

 <span data-ttu-id="b4313-141">**endColumn** (entero); la columna de la línea de fin en que acaba la selección.</span><span class="sxs-lookup"><span data-stu-id="b4313-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

 <span data-ttu-id="b4313-142">Vea [Ejemplo de scripting](#scripting-example) más adelante en este tema.</span><span class="sxs-lookup"><span data-stu-id="b4313-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="b4313-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="b4313-143">SelectCaretLine\(\)</span></span>
  <span data-ttu-id="b4313-144">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b4313-145">Selecciona toda la línea de texto que contiene actualmente el símbolo de intercalación.</span><span class="sxs-lookup"><span data-stu-id="b4313-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="b4313-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="b4313-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>
  <span data-ttu-id="b4313-147">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b4313-148">Establece la posición del símbolo de intercalación en el número de línea y el número de columna.</span><span class="sxs-lookup"><span data-stu-id="b4313-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="b4313-149">Produce una excepción si el número de línea del símbolo de intercalación o el número de columna del símbolo de intercalación están fuera de sus  intervalos válidos respectivos.</span><span class="sxs-lookup"><span data-stu-id="b4313-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

 <span data-ttu-id="b4313-150">**lineNumber** (entero); el número de línea del símbolo de intercalación.</span><span class="sxs-lookup"><span data-stu-id="b4313-150">**lineNumber** - Integer The caret line number.</span></span>

 <span data-ttu-id="b4313-151">**columnNumber** (entero); el número de columna del símbolo de intercalación.</span><span class="sxs-lookup"><span data-stu-id="b4313-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="b4313-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="b4313-152">ToggleOutliningExpansion\(\)</span></span>
  <span data-ttu-id="b4313-153">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="b4313-154">Hace que todas las secciones de esquema se expandan o se contraigan.</span><span class="sxs-lookup"><span data-stu-id="b4313-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="b4313-155">Propiedades</span><span class="sxs-lookup"><span data-stu-id="b4313-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="b4313-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="b4313-156">CanGoToMatch</span></span>
  <span data-ttu-id="b4313-157">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="b4313-158">Propiedad booleana de solo lectura que indica si el símbolo de intercalación está al lado de paréntesis, corchetes o llaves: \(\), \[\], {}.</span><span class="sxs-lookup"><span data-stu-id="b4313-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="b4313-159">Si el símbolo de intercalación está inmediatamente antes del carácter de apertura o inmediatamente después del carácter de cierre de un par, el valor de esta propiedad es **$true**.</span><span class="sxs-lookup"><span data-stu-id="b4313-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="b4313-160">Si no, es **$false**.</span><span class="sxs-lookup"><span data-stu-id="b4313-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="b4313-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="b4313-161">CaretColumn</span></span>
  <span data-ttu-id="b4313-162">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b4313-163">Propiedad de solo lectura que obtiene el número de columna que corresponde a la posición del símbolo de intercalación.</span><span class="sxs-lookup"><span data-stu-id="b4313-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="b4313-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="b4313-164">CaretLine</span></span>
  <span data-ttu-id="b4313-165">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b4313-166">Propiedad de solo lectura que obtiene el número de la línea que contiene el símbolo de intercalación.</span><span class="sxs-lookup"><span data-stu-id="b4313-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="b4313-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="b4313-167">CaretLineText</span></span>
  <span data-ttu-id="b4313-168">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b4313-169">Propiedad de solo lectura que obtiene la línea de texto completa que contiene el símbolo de intercalación.</span><span class="sxs-lookup"><span data-stu-id="b4313-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="b4313-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="b4313-170">LineCount</span></span>
  <span data-ttu-id="b4313-171">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b4313-172">Propiedad de solo lectura que obtiene el recuento de líneas del editor.</span><span class="sxs-lookup"><span data-stu-id="b4313-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="b4313-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="b4313-173">SelectedText</span></span>
  <span data-ttu-id="b4313-174">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b4313-175">Propiedad de solo lectura que obtiene el texto seleccionado del editor.</span><span class="sxs-lookup"><span data-stu-id="b4313-175">The read-only property that gets the selected text from the editor.</span></span>

 <span data-ttu-id="b4313-176">Vea [Ejemplo de scripting](#scripting-example) más adelante en este tema.</span><span class="sxs-lookup"><span data-stu-id="b4313-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="b4313-177">Texto</span><span class="sxs-lookup"><span data-stu-id="b4313-177">Text</span></span>
  <span data-ttu-id="b4313-178">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4313-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b4313-179">Propiedad de lectura y escritura que obtiene o establece el texto en el editor.</span><span class="sxs-lookup"><span data-stu-id="b4313-179">The read/write property that gets or sets the text in the editor.</span></span>

 <span data-ttu-id="b4313-180">Vea [Ejemplo de scripting](#scripting-example) más adelante en este tema.</span><span class="sxs-lookup"><span data-stu-id="b4313-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="b4313-181">Ejemplo de scripting</span><span class="sxs-lookup"><span data-stu-id="b4313-181">Scripting Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b4313-182">Véase también</span><span class="sxs-lookup"><span data-stu-id="b4313-182">See Also</span></span>
- [<span data-ttu-id="b4313-183">El objeto ISEFile</span><span class="sxs-lookup"><span data-stu-id="b4313-183">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="b4313-184">El objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="b4313-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="b4313-185">El modelo de objetos de scripting de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b4313-185">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="b4313-186">Referencia del modelo de objetos de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b4313-186">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="b4313-187">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="b4313-187">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
