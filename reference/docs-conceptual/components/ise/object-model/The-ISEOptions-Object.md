---
ms.date: 12/31/2019
keywords: powershell, cmdlet
title: El objeto ISEOptions
ms.openlocfilehash: 9caa78a70cb837c755b2eff9af6ce0aa5dbb7452
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736954"
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="79d5e-103">El objeto ISEOptions</span><span class="sxs-lookup"><span data-stu-id="79d5e-103">The ISEOptions Object</span></span>

<span data-ttu-id="79d5e-104">El objeto **ISEOptions** representa distintas configuraciones de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="79d5e-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="79d5e-105">Es una instancia de la clase **Microsoft.PowerShell.Host.ISE.ISEOptions**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="79d5e-106">El objeto **ISEOptions** proporciona los siguientes métodos y propiedades.</span><span class="sxs-lookup"><span data-stu-id="79d5e-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="79d5e-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="79d5e-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="79d5e-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="79d5e-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="79d5e-109">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-110">Restaura los valores predeterminados de los colores de token en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="79d5e-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="79d5e-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="79d5e-112">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-113">Restaura los valores predeterminados de todas las configuraciones de opciones en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="79d5e-114">También restablece el comportamiento de varios mensajes de advertencia que proporcionan la casilla estándar para impedir que el mensaje se muestre de nuevo.</span><span class="sxs-lookup"><span data-stu-id="79d5e-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="79d5e-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="79d5e-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="79d5e-116">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-117">Restaura los valores predeterminados de los colores de token en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="79d5e-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="79d5e-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="79d5e-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="79d5e-119">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-120">Restaura los valores predeterminados de los colores de token de elementos XML que se muestran en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="79d5e-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="79d5e-121">Vea también [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="79d5e-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="79d5e-122">Propiedades</span><span class="sxs-lookup"><span data-stu-id="79d5e-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="79d5e-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="79d5e-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="79d5e-124">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-125">Especifica el número de minutos entre operaciones de guardado automático de los archivos realizadas por Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="79d5e-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="79d5e-126">El valor predeterminado es 2 minutos.</span><span class="sxs-lookup"><span data-stu-id="79d5e-126">The default value is 2 minutes.</span></span> <span data-ttu-id="79d5e-127">El valor es un entero.</span><span class="sxs-lookup"><span data-stu-id="79d5e-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="79d5e-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="79d5e-129">Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.</span><span class="sxs-lookup"><span data-stu-id="79d5e-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="79d5e-130">Para las versiones posteriores, vea [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="79d5e-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="79d5e-131">Especifica el color de fondo para el panel de comandos.</span><span class="sxs-lookup"><span data-stu-id="79d5e-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="79d5e-132">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="79d5e-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="79d5e-133">CommandPaneUp</span></span>

<span data-ttu-id="79d5e-134">Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.</span><span class="sxs-lookup"><span data-stu-id="79d5e-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="79d5e-135">Especifica si el panel de comandos se encuentra encima del panel de resultados.</span><span class="sxs-lookup"><span data-stu-id="79d5e-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="79d5e-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="79d5e-137">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-138">Especifica el color de fondo para el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="79d5e-139">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="79d5e-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="79d5e-141">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-142">Especifica el color de fondo del texto en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="79d5e-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="79d5e-144">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-145">Especifica el color de primer plano en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="79d5e-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="79d5e-146">ConsoleTokenColors</span></span>

<span data-ttu-id="79d5e-147">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-148">Especifica los colores de los token de IntelliSense en el panel de consola de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="79d5e-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="79d5e-149">Esta propiedad es un objeto de diccionario que contiene pares nombre-valor de tipos y colores de token para el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="79d5e-150">Para cambiar los colores de los token de IntelliSense en el panel de scripts, consulte [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="79d5e-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span>
<span data-ttu-id="79d5e-151">Para restablecer los valores predeterminados de los colores, consulte [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="79d5e-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span>
<span data-ttu-id="79d5e-152">Los colores de token se pueden establecer para lo siguiente: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown y Variable.</span><span class="sxs-lookup"><span data-stu-id="79d5e-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="79d5e-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-153">DebugBackgroundColor</span></span>

<span data-ttu-id="79d5e-154">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-155">Especifica el color de fondo para el texto de depuración que aparece en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="79d5e-156">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="79d5e-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-157">DebugForegroundColor</span></span>

<span data-ttu-id="79d5e-158">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-159">Especifica el color de primer plano para el texto de depuración que aparece en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="79d5e-160">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="79d5e-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="79d5e-161">DefaultOptions</span></span>

<span data-ttu-id="79d5e-162">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-163">Una colección de propiedades que especifica los valores predeterminados que se utilizarán cuando se empleen los métodos Reset.</span><span class="sxs-lookup"><span data-stu-id="79d5e-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions
```

```Output
SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3
```

### <a name="errorbackgroundcolor"></a><span data-ttu-id="79d5e-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="79d5e-165">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-166">Especifica el color de fondo para el texto de error que aparece en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="79d5e-167">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="79d5e-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-168">ErrorForegroundColor</span></span>

<span data-ttu-id="79d5e-169">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-170">Especifica el color de primer plano para el texto de error que aparece en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="79d5e-171">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="79d5e-172">FontName</span><span class="sxs-lookup"><span data-stu-id="79d5e-172">FontName</span></span>

<span data-ttu-id="79d5e-173">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-174">Especifica el nombre de fuente que se está usando actualmente tanto en el panel de scripts como en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="79d5e-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="79d5e-175">FontSize</span></span>

<span data-ttu-id="79d5e-176">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-177">Especifica el tamaño de fuente como un entero.</span><span class="sxs-lookup"><span data-stu-id="79d5e-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="79d5e-178">Se usa en el panel de scripts, en el panel de comandos y en el panel de salida.</span><span class="sxs-lookup"><span data-stu-id="79d5e-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="79d5e-179">El intervalo válido de valores es de 8 a 32.</span><span class="sxs-lookup"><span data-stu-id="79d5e-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="79d5e-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="79d5e-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="79d5e-181">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-182">Especifica el número de segundos que IntelliSense usa para intentar resolver el texto escrito actualmente.</span><span class="sxs-lookup"><span data-stu-id="79d5e-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span>
<span data-ttu-id="79d5e-183">Transcurrido este número de segundos, el tiempo de espera de IntelliSense se agota y le permite continuar escribiendo.</span><span class="sxs-lookup"><span data-stu-id="79d5e-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="79d5e-184">El valor predeterminado es 3 segundos.</span><span class="sxs-lookup"><span data-stu-id="79d5e-184">The default value is 3 seconds.</span></span> <span data-ttu-id="79d5e-185">El valor es un entero.</span><span class="sxs-lookup"><span data-stu-id="79d5e-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="79d5e-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="79d5e-186">MruCount</span></span>

<span data-ttu-id="79d5e-187">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-188">Especifica el número de archivos abiertos recientemente que Windows PowerShell ISE sigue y se muestra en la parte inferior del menú **Archivo - Abrir**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="79d5e-189">El valor predeterminado es 10.</span><span class="sxs-lookup"><span data-stu-id="79d5e-189">The default value is 10.</span></span> <span data-ttu-id="79d5e-190">El valor es un entero.</span><span class="sxs-lookup"><span data-stu-id="79d5e-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="79d5e-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="79d5e-192">Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.</span><span class="sxs-lookup"><span data-stu-id="79d5e-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="79d5e-193">Para las versiones posteriores, vea [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="79d5e-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="79d5e-194">La propiedad de lectura y escritura que obtiene o establece el color de fondo para el propio panel de resultado.</span><span class="sxs-lookup"><span data-stu-id="79d5e-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="79d5e-195">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="79d5e-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="79d5e-197">Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.</span><span class="sxs-lookup"><span data-stu-id="79d5e-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="79d5e-198">Para las versiones posteriores, vea [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="79d5e-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="79d5e-199">La propiedad de lectura y escritura que cambia el color de primer plano del texto en el panel de salida en Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="79d5e-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="79d5e-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="79d5e-201">Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.</span><span class="sxs-lookup"><span data-stu-id="79d5e-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="79d5e-202">Para las versiones posteriores, vea [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="79d5e-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="79d5e-203">La propiedad de lectura y escritura que cambia el color de fondo del texto en el panel de salida.</span><span class="sxs-lookup"><span data-stu-id="79d5e-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="79d5e-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="79d5e-205">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-206">La propiedad de lectura y escritura que obtiene o establece el color de fondo para los archivos.</span><span class="sxs-lookup"><span data-stu-id="79d5e-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="79d5e-207">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="79d5e-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="79d5e-209">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-210">La propiedad de lectura y escritura que obtiene o establece el color de primer plano para archivos que no son de script en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="79d5e-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="79d5e-211">Para establecer el color de primer plano para archivos de script, use la propiedad [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="79d5e-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="79d5e-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="79d5e-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="79d5e-213">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-214">La propiedad de lectura y escritura que obtiene o establece la posición del panel de scripts en la pantalla.</span><span class="sxs-lookup"><span data-stu-id="79d5e-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="79d5e-215">La cadena puede ser "Maximized", "Top" o "Right".</span><span class="sxs-lookup"><span data-stu-id="79d5e-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="79d5e-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="79d5e-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="79d5e-217">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-218">Especifica si la lista de fragmentos de código <kbd>CTRL</kbd>+<kbd>J</kbd> incluye el conjunto de inicio que se incluye en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="79d5e-218">Specifies whether the <kbd>CTRL</kbd>+<kbd>J</kbd> list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="79d5e-219">Cuando se establece en `$false`, en la lista <kbd>CTRL</kbd>+<kbd>J</kbd> solo aparecen los fragmentos de código definidos por el usuario.</span><span class="sxs-lookup"><span data-stu-id="79d5e-219">When set to `$false`, only user-defined snippets appear in the <kbd>CTRL</kbd>+<kbd>J</kbd> list.</span></span>
<span data-ttu-id="79d5e-220">El valor predeterminado es `$true`.</span><span class="sxs-lookup"><span data-stu-id="79d5e-220">The default value is `$true`.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="79d5e-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="79d5e-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="79d5e-222">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-223">Especifica si IntelliSense ofrece sugerencias de sintaxis, parámetros y valores en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span>
<span data-ttu-id="79d5e-224">El valor predeterminado es `$true`.</span><span class="sxs-lookup"><span data-stu-id="79d5e-224">The default value is `$true`.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="79d5e-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="79d5e-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="79d5e-226">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-227">Especifica si IntelliSense ofrece sugerencias de sintaxis, parámetros y valores en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="79d5e-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span>
<span data-ttu-id="79d5e-228">El valor predeterminado es `$true`.</span><span class="sxs-lookup"><span data-stu-id="79d5e-228">The default value is `$true`.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="79d5e-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="79d5e-229">ShowLineNumbers</span></span>

<span data-ttu-id="79d5e-230">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-231">Especifica si el panel de scripts muestra los números de línea en el margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="79d5e-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="79d5e-232">El valor predeterminado es `$true`.</span><span class="sxs-lookup"><span data-stu-id="79d5e-232">The default value is `$true`.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="79d5e-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="79d5e-233">ShowOutlining</span></span>

<span data-ttu-id="79d5e-234">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-235">Especifica si el panel de scripts muestra corchetes expandibles y que se puedan contraer junto a las secciones de código en el margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="79d5e-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="79d5e-236">Cuando se muestren, puede hacer clic en los iconos de signo menos `-` junto a un bloque de texto para contraerlo o en el icono de signo más `+` para expandir un bloque de texto.</span><span class="sxs-lookup"><span data-stu-id="79d5e-236">When they are displayed, you can click the minus `-` icons next to a block of text to collapse it or click the plus `+` icon to expand a block of text.</span></span> <span data-ttu-id="79d5e-237">El valor predeterminado es `$true`.</span><span class="sxs-lookup"><span data-stu-id="79d5e-237">The default value is `$true`.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="79d5e-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="79d5e-238">ShowToolBar</span></span>

<span data-ttu-id="79d5e-239">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-240">Especifica si la barra de herramientas de ISE aparece en la parte superior de la ventana de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="79d5e-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="79d5e-241">El valor predeterminado es `$true`.</span><span class="sxs-lookup"><span data-stu-id="79d5e-241">The default value is `$true`.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="79d5e-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="79d5e-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="79d5e-243">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-244">Especifica si aparece un mensaje de advertencia cuando un script se guarda automáticamente antes de ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="79d5e-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span>
<span data-ttu-id="79d5e-245">El valor predeterminado es `$true`.</span><span class="sxs-lookup"><span data-stu-id="79d5e-245">The default value is `$true`.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="79d5e-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="79d5e-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="79d5e-247">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-248">Especifica si aparece un mensaje de advertencia cuando se abre el mismo archivo en diferentes pestañas de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="79d5e-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="79d5e-249">Si se establece en `$true`, para abrir el mismo archivo en varias pestañas se muestra este mensaje: "Una copia de este archivo está abierta en otra pestaña de Windows PowerShell. Los cambios realizados en este archivo afectarán a todas las copias abiertas.".</span><span class="sxs-lookup"><span data-stu-id="79d5e-249">If set to `$true`, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="79d5e-250">El valor predeterminado es `$true`.</span><span class="sxs-lookup"><span data-stu-id="79d5e-250">The default value is `$true`.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="79d5e-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="79d5e-251">TokenColors</span></span>

<span data-ttu-id="79d5e-252">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-253">Especifica los colores de los token de IntelliSense en el panel de scripts de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="79d5e-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="79d5e-254">Esta propiedad es un objeto de diccionario que contiene pares nombre-valor de tipos y colores de token para el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="79d5e-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="79d5e-255">Para cambiar los colores de los token de IntelliSense en el panel de consola, consulte [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="79d5e-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span>
<span data-ttu-id="79d5e-256">Para restablecer los valores predeterminados de los colores, consulte [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="79d5e-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span>
<span data-ttu-id="79d5e-257">Los colores de token se pueden establecer para lo siguiente: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown y Variable.</span><span class="sxs-lookup"><span data-stu-id="79d5e-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="79d5e-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="79d5e-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="79d5e-259">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-260">Especifica si se puede utilizar la tecla Entrar para seleccionar un opción proporcionada por IntelliSense en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="79d5e-261">El valor predeterminado es `$true`.</span><span class="sxs-lookup"><span data-stu-id="79d5e-261">The default value is `$true`.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="79d5e-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="79d5e-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="79d5e-263">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-264">Especifica si se puede utilizar la tecla Entrar para seleccionar un opción proporcionada por IntelliSense en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="79d5e-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="79d5e-265">El valor predeterminado es `$true`.</span><span class="sxs-lookup"><span data-stu-id="79d5e-265">The default value is `$true`.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="79d5e-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="79d5e-266">UseLocalHelp</span></span>

<span data-ttu-id="79d5e-267">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-268">Especifica si la Ayuda instalada localmente o la Ayuda de la Biblioteca de TechNet en línea aparecen cuando se presiona <kbd>F1</kbd> con el cursor situado en una palabra clave.</span><span class="sxs-lookup"><span data-stu-id="79d5e-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press <kbd>F1</kbd> with the cursor positioned in a keyword.</span></span> <span data-ttu-id="79d5e-269">Si establece en `$true`, una ventana emergente muestra el contenido de la Ayuda instalada localmente.</span><span class="sxs-lookup"><span data-stu-id="79d5e-269">If set to `$true`, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="79d5e-270">Puede instalar los archivos de la Ayuda ejecutando el comando `Update-Help`.</span><span class="sxs-lookup"><span data-stu-id="79d5e-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="79d5e-271">Si se establece en `$false`, el explorador se abre en a una página de la Biblioteca de TechNet.</span><span class="sxs-lookup"><span data-stu-id="79d5e-271">If set to `$false`, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="79d5e-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="79d5e-273">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-274">Especifica el color de fondo para el texto detallado que aparece en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="79d5e-275">Es un objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="79d5e-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-276">VerboseForegroundColor</span></span>

<span data-ttu-id="79d5e-277">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-278">Especifica el color de primer plano para el texto detallado que aparece en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="79d5e-279">Es un objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="79d5e-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-280">WarningBackgroundColor</span></span>

<span data-ttu-id="79d5e-281">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-282">Especifica el color de fondo para el texto de advertencia que aparece en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="79d5e-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="79d5e-283">Es un objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="79d5e-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="79d5e-284">WarningForegroundColor</span></span>

<span data-ttu-id="79d5e-285">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="79d5e-286">Especifica el color de primer plano para el texto de advertencia que aparece en el panel de salida.</span><span class="sxs-lookup"><span data-stu-id="79d5e-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="79d5e-287">Es un objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="79d5e-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="79d5e-288">XmlTokenColors</span></span>

<span data-ttu-id="79d5e-289">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-290">Especifica un objeto de diccionario que contiene pares nombre-valor de tipos y colores de token para el contenido XML que se muestra en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="79d5e-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="79d5e-291">Los colores de token se pueden establecer para lo siguiente: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown y Variable.</span><span class="sxs-lookup"><span data-stu-id="79d5e-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="79d5e-292">Consulte también [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="79d5e-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="79d5e-293">Zoom</span><span class="sxs-lookup"><span data-stu-id="79d5e-293">Zoom</span></span>

<span data-ttu-id="79d5e-294">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="79d5e-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="79d5e-295">Especifica el tamaño relativo del texto en los paneles de consola y scripts.</span><span class="sxs-lookup"><span data-stu-id="79d5e-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="79d5e-296">El valor predeterminado es 100.</span><span class="sxs-lookup"><span data-stu-id="79d5e-296">The default value is 100.</span></span>
<span data-ttu-id="79d5e-297">Los valores más pequeños hacen que el texto de Windows PowerShell ISE sea menor, mientras que números más grandes hacen que el texto aparezca más grande.</span><span class="sxs-lookup"><span data-stu-id="79d5e-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="79d5e-298">El valor es un entero comprendido entre 20 y 400.</span><span class="sxs-lookup"><span data-stu-id="79d5e-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="79d5e-299">Consulte también</span><span class="sxs-lookup"><span data-stu-id="79d5e-299">See Also</span></span>

- [<span data-ttu-id="79d5e-300">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="79d5e-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="79d5e-301">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="79d5e-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
