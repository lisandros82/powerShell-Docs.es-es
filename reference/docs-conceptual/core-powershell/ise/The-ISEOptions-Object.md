---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: El objeto ISEOptions
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: 56bdd5999b46b6e29e762c2d9a2060cebe3a1299
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="b38a9-103">El objeto ISEOptions</span><span class="sxs-lookup"><span data-stu-id="b38a9-103">The ISEOptions Object</span></span>
  <span data-ttu-id="b38a9-104">El objeto **ISEOptions** representa distintas configuraciones de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b38a9-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="b38a9-105">Es una instancia de la clase **Microsoft.PowerShell.Host.ISE.ISEOptions**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

 <span data-ttu-id="b38a9-106">El objeto **ISEOptions** proporciona los siguientes métodos y propiedades.</span><span class="sxs-lookup"><span data-stu-id="b38a9-106">The **ISEOptions** object provides the following methods and properties.</span></span>

 <span data-ttu-id="b38a9-107">**Methods**</span><span class="sxs-lookup"><span data-stu-id="b38a9-107">**Methods**</span></span>

-   [<span data-ttu-id="b38a9-108">RestoreDefaultConsoleTokenColors()</span><span class="sxs-lookup"><span data-stu-id="b38a9-108">RestoreDefaultConsoleTokenColors()</span></span>](#rdctc)

-   [<span data-ttu-id="b38a9-109">RestoreDefaults()</span><span class="sxs-lookup"><span data-stu-id="b38a9-109">RestoreDefaults()</span></span>](#rd)

-   [<span data-ttu-id="b38a9-110">RestoreDefaultTokenColors()</span><span class="sxs-lookup"><span data-stu-id="b38a9-110">RestoreDefaultTokenColors()</span></span>](#rdtc)

-   [<span data-ttu-id="b38a9-111">RestoreDefaultXmlTokenColors()</span><span class="sxs-lookup"><span data-stu-id="b38a9-111">RestoreDefaultXmlTokenColors()</span></span>](#rdxtc)

 <span data-ttu-id="b38a9-112">**Properties**</span><span class="sxs-lookup"><span data-stu-id="b38a9-112">**Properties**</span></span>

-   [<span data-ttu-id="b38a9-113">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="b38a9-113">AutoSaveMinuteInterval</span></span>](#asmi)

-   [<span data-ttu-id="b38a9-114">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-114">CommandPaneBackgroundColor</span></span>](#cpbc)

-   [<span data-ttu-id="b38a9-115">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="b38a9-115">CommandPaneUp</span></span>](#cpu)

-   [<span data-ttu-id="b38a9-116">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-116">ConsolePaneBackgroundColor</span></span>](#conpbc)

-   [<span data-ttu-id="b38a9-117">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-117">ConsolePaneForegroundColor</span></span>](#conpfc)

-   [<span data-ttu-id="b38a9-118">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-118">ConsolePaneTextBackgroundColor</span></span>](#conptbc)

-   [<span data-ttu-id="b38a9-119">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="b38a9-119">ConsoleTokenColors</span></span>](#contc)

-   [<span data-ttu-id="b38a9-120">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-120">DebugBackgroundColor</span></span>](#dbc)

-   [<span data-ttu-id="b38a9-121">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-121">DebugForegroundColor</span></span>](#dfc)

-   [<span data-ttu-id="b38a9-122">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="b38a9-122">DefaultOptions</span></span>](#do)

-   [<span data-ttu-id="b38a9-123">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-123">ErrorBackgroundColor</span></span>](#ebc)

-   [<span data-ttu-id="b38a9-124">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-124">ErrorForegroundColor</span></span>](#efc)

-   [<span data-ttu-id="b38a9-125">FontName</span><span class="sxs-lookup"><span data-stu-id="b38a9-125">FontName</span></span>](#fn)

-   [<span data-ttu-id="b38a9-126">FontSize</span><span class="sxs-lookup"><span data-stu-id="b38a9-126">FontSize</span></span>](#fs)

-   [<span data-ttu-id="b38a9-127">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="b38a9-127">IntellisenseTimeoutInSeconds</span></span>](#itis)

-   [<span data-ttu-id="b38a9-128">MruCount</span><span class="sxs-lookup"><span data-stu-id="b38a9-128">MruCount</span></span>](#mc)

-   [<span data-ttu-id="b38a9-129">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-129">OutputPaneBackgroundColor</span></span>](#opbc)

-   [<span data-ttu-id="b38a9-130">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-130">OutputPaneTextForegroundColor</span></span>](#optfc)

-   [<span data-ttu-id="b38a9-131">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-131">OutputPaneTextBackgroundColor</span></span>](#optbc)

-   [<span data-ttu-id="b38a9-132">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-132">ScriptPaneBackgroundColor</span></span>](#spbc)

-   [<span data-ttu-id="b38a9-133">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-133">ScriptPaneForegroundColor</span></span>](#spfc)

-   [<span data-ttu-id="b38a9-134">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="b38a9-134">SelectedScriptPaneState</span></span>](#ssps)

-   [<span data-ttu-id="b38a9-135">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="b38a9-135">ShowDefaultSnippets</span></span>](#sds)

-   [<span data-ttu-id="b38a9-136">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="b38a9-136">ShowIntellisenseInConsolePane</span></span>](#siicp)

-   [<span data-ttu-id="b38a9-137">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="b38a9-137">ShowIntellisenseInScriptPane</span></span>](#siisp)

-   [<span data-ttu-id="b38a9-138">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="b38a9-138">ShowLineNumbers</span></span>](#sln)

-   [<span data-ttu-id="b38a9-139">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="b38a9-139">ShowOutlining</span></span>](#so)

-   [<span data-ttu-id="b38a9-140">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="b38a9-140">ShowToolBar</span></span>](#stb)

-   [<span data-ttu-id="b38a9-141">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="b38a9-141">ShowWarningBeforeSavingOnRun</span></span>](#swbsor)

-   [<span data-ttu-id="b38a9-142">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="b38a9-142">ShowWarningForDuplicateFiles</span></span>](#swfdf)

-   [<span data-ttu-id="b38a9-143">TokenColors</span><span class="sxs-lookup"><span data-stu-id="b38a9-143">TokenColors</span></span>](#tc)

-   [<span data-ttu-id="b38a9-144">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="b38a9-144">UseEnterToSelectInConsolePaneIntellisense</span></span>](#uetsicpi)

-   [<span data-ttu-id="b38a9-145">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="b38a9-145">UseEnterToSelectInScriptPaneIntellisense</span></span>](#uetsispi)

-   [<span data-ttu-id="b38a9-146">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="b38a9-146">UseLocalHelp</span></span>](#ulh)

-   [<span data-ttu-id="b38a9-147">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-147">VerboseBackgroundColor</span></span>](#vbc)

-   [<span data-ttu-id="b38a9-148">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-148">VerboseForegroundColor</span></span>](#vfc)

-   [<span data-ttu-id="b38a9-149">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-149">WarningBackgroundColor</span></span>](#wbc)

-   [<span data-ttu-id="b38a9-150">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-150">WarningForegroundColor</span></span>](#wfc)

-   [<span data-ttu-id="b38a9-151">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="b38a9-151">XmlTokenColors</span></span>](#xtc)

-   [<span data-ttu-id="b38a9-152">Zoom</span><span class="sxs-lookup"><span data-stu-id="b38a9-152">Zoom</span></span>](#z)

## <a name="methods"></a><span data-ttu-id="b38a9-153">Métodos</span><span class="sxs-lookup"><span data-stu-id="b38a9-153">Methods</span></span>

###  <span data-ttu-id="b38a9-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="b38a9-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span></span>
  <span data-ttu-id="b38a9-155">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-155">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-156">Restaura los valores predeterminados de los colores de token en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-156">Restores the default values of the token colors in the Console pane.</span></span>

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

###  <span data-ttu-id="b38a9-157"><a name="rd"></a> RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="b38a9-157"><a name="rd"></a> RestoreDefaults\(\)</span></span>
  <span data-ttu-id="b38a9-158">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-159">Restaura los valores predeterminados de todas las configuraciones de opciones en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-159">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="b38a9-160">También restablece el comportamiento de varios mensajes de advertencia que proporcionan la casilla estándar para impedir que el mensaje se muestre de nuevo.</span><span class="sxs-lookup"><span data-stu-id="b38a9-160">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

###  <span data-ttu-id="b38a9-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="b38a9-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span></span>
  <span data-ttu-id="b38a9-162">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-163">Restaura los valores predeterminados de los colores de token en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="b38a9-163">Restores the default values of the token colors in the Script pane.</span></span>

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

###  <span data-ttu-id="b38a9-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="b38a9-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span></span>
  <span data-ttu-id="b38a9-165">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-165">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-166">Restaura los valores predeterminados de los colores de token de elementos XML que se muestran en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b38a9-166">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="b38a9-167">Vea también [XmlTokenColors](#xtc).</span><span class="sxs-lookup"><span data-stu-id="b38a9-167">Also see [XmlTokenColors](#xtc).</span></span>

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="b38a9-168">Propiedades</span><span class="sxs-lookup"><span data-stu-id="b38a9-168">Properties</span></span>

###  <span data-ttu-id="b38a9-169"><a name="asmi"></a> AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="b38a9-169"><a name="asmi"></a> AutoSaveMinuteInterval</span></span>
  <span data-ttu-id="b38a9-170">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-170">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-171">Especifica el número de minutos entre operaciones de guardado automático de los archivos realizadas por Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b38a9-171">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="b38a9-172">El valor predeterminado es 2 minutos.</span><span class="sxs-lookup"><span data-stu-id="b38a9-172">The default value is 2 minutes.</span></span> <span data-ttu-id="b38a9-173">El valor es un entero.</span><span class="sxs-lookup"><span data-stu-id="b38a9-173">The value is an integer.</span></span>

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

###  <span data-ttu-id="b38a9-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span></span>
  <span data-ttu-id="b38a9-175">Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.</span><span class="sxs-lookup"><span data-stu-id="b38a9-175">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="b38a9-176">Para las versiones posteriores, vea [ConsolePaneBackgroundColor](#conpbc).</span><span class="sxs-lookup"><span data-stu-id="b38a9-176">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="b38a9-177">Especifica el color de fondo para el panel de comandos.</span><span class="sxs-lookup"><span data-stu-id="b38a9-177">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="b38a9-178">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-178">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

###  <span data-ttu-id="b38a9-179"><a name="cpu"></a> CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="b38a9-179"><a name="cpu"></a> CommandPaneUp</span></span>
  <span data-ttu-id="b38a9-180">Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.</span><span class="sxs-lookup"><span data-stu-id="b38a9-180">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

 <span data-ttu-id="b38a9-181">Especifica si el panel de comandos se encuentra encima del panel de resultados.</span><span class="sxs-lookup"><span data-stu-id="b38a9-181">Specifies whether the Command pane is located above the Output pane.</span></span>

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

###  <span data-ttu-id="b38a9-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span></span>
  <span data-ttu-id="b38a9-183">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-183">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-184">Especifica el color de fondo para el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-184">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="b38a9-185">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-185">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

###  <span data-ttu-id="b38a9-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span></span>
  <span data-ttu-id="b38a9-187">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-188">Especifica el color de fondo del texto en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-188">Specifies the foreground color of the text in the Console pane.</span></span>

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

###  <span data-ttu-id="b38a9-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span></span>
  <span data-ttu-id="b38a9-190">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-190">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-191">Especifica el color de primer plano en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-191">Specifies the background color of the text in the Console pane.</span></span>

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="b38a9-192"><a name="contc"></a> ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="b38a9-192"><a name="contc"></a> ConsoleTokenColors</span></span>
  <span data-ttu-id="b38a9-193">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-193">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-194">Especifica los colores de los token de IntelliSense en el panel de consola de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b38a9-194">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="b38a9-195">Esta propiedad es un objeto de diccionario que contiene pares nombre-valor de tipos y colores de token para el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-195">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="b38a9-196">Para cambiar los colores de los token de IntelliSense en el panel de scripts, consulte [TokenColors](#tc).</span><span class="sxs-lookup"><span data-stu-id="b38a9-196">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tc).</span></span> <span data-ttu-id="b38a9-197">Para restablecer los valores predeterminados de los colores, consulte [RestoreDefaultConsoleTokenColors()](#rdctc).</span><span class="sxs-lookup"><span data-stu-id="b38a9-197">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors()](#rdctc).</span></span> <span data-ttu-id="b38a9-198">Los colores de token se pueden establecer para lo siguiente: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown y Variable.</span><span class="sxs-lookup"><span data-stu-id="b38a9-198">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="b38a9-199"><a name="dbc"></a> DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-199"><a name="dbc"></a> DebugBackgroundColor</span></span>
  <span data-ttu-id="b38a9-200">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-200">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-201">Especifica el color de fondo para el texto de depuración que aparece en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-201">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="b38a9-202">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-202">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="b38a9-203"><a name="dfc"></a> DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-203"><a name="dfc"></a> DebugForegroundColor</span></span>
  <span data-ttu-id="b38a9-204">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-204">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-205">Especifica el color de primer plano para el texto de depuración que aparece en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-205">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="b38a9-206">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-206">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

###  <span data-ttu-id="b38a9-207"><a name="do"></a> DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="b38a9-207"><a name="do"></a> DefaultOptions</span></span>
  <span data-ttu-id="b38a9-208">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-208">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-209">Una colección de propiedades que especifica los valores predeterminados que se utilizarán cuando se empleen los métodos Reset.</span><span class="sxs-lookup"><span data-stu-id="b38a9-209">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

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

###  <span data-ttu-id="b38a9-210"><a name="ebc"></a> ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-210"><a name="ebc"></a> ErrorBackgroundColor</span></span>
  <span data-ttu-id="b38a9-211">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-211">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-212">Especifica el color de fondo para el texto de error que aparece en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-212">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="b38a9-213">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-213">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

###  <span data-ttu-id="b38a9-214"><a name="efc"></a> ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-214"><a name="efc"></a> ErrorForegroundColor</span></span>
  <span data-ttu-id="b38a9-215">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-215">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-216">Especifica el color de primer plano para el texto de error que aparece en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-216">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="b38a9-217">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-217">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

###  <span data-ttu-id="b38a9-218"><a name="fn"></a> FontName</span><span class="sxs-lookup"><span data-stu-id="b38a9-218"><a name="fn"></a> FontName</span></span>
  <span data-ttu-id="b38a9-219">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-219">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-220">Especifica el nombre de fuente que se está usando actualmente tanto en el panel de scripts como en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-220">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

###  <span data-ttu-id="b38a9-221"><a name="fs"></a> FontSize</span><span class="sxs-lookup"><span data-stu-id="b38a9-221"><a name="fs"></a> FontSize</span></span>
  <span data-ttu-id="b38a9-222">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-222">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-223">Especifica el tamaño de fuente como un entero.</span><span class="sxs-lookup"><span data-stu-id="b38a9-223">Specifies the font size as an integer.</span></span> <span data-ttu-id="b38a9-224">Se usa en el panel de scripts, en el panel de comandos y en el panel de salida.</span><span class="sxs-lookup"><span data-stu-id="b38a9-224">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="b38a9-225">El intervalo válido de valores es de 8 a 32.</span><span class="sxs-lookup"><span data-stu-id="b38a9-225">The valid range of values is 8 through 32.</span></span>

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

###  <span data-ttu-id="b38a9-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="b38a9-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span></span>
  <span data-ttu-id="b38a9-227">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-227">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-228">Especifica el número de segundos que IntelliSense usa para intentar resolver el texto escrito actualmente.</span><span class="sxs-lookup"><span data-stu-id="b38a9-228">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="b38a9-229">Transcurrido este número de segundos, el tiempo de espera de IntelliSense se agota y le permite continuar escribiendo.</span><span class="sxs-lookup"><span data-stu-id="b38a9-229">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="b38a9-230">El valor predeterminado es 3 segundos.</span><span class="sxs-lookup"><span data-stu-id="b38a9-230">The default value is 3 seconds.</span></span> <span data-ttu-id="b38a9-231">El valor es un entero.</span><span class="sxs-lookup"><span data-stu-id="b38a9-231">The value is an integer.</span></span>

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

###  <span data-ttu-id="b38a9-232"><a name="mc"></a> MruCount</span><span class="sxs-lookup"><span data-stu-id="b38a9-232"><a name="mc"></a> MruCount</span></span>
  <span data-ttu-id="b38a9-233">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-233">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-234">Especifica el número de archivos abiertos recientemente que Windows PowerShell ISE sigue y se muestra en la parte inferior del menú **Archivo - Abrir**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-234">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="b38a9-235">El valor predeterminado es 10.</span><span class="sxs-lookup"><span data-stu-id="b38a9-235">The default value is 10.</span></span> <span data-ttu-id="b38a9-236">El valor es un entero.</span><span class="sxs-lookup"><span data-stu-id="b38a9-236">The value is an integer.</span></span>

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

###  <span data-ttu-id="b38a9-237"><a name="opbc"></a> OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-237"><a name="opbc"></a> OutputPaneBackgroundColor</span></span>
  <span data-ttu-id="b38a9-238">Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.</span><span class="sxs-lookup"><span data-stu-id="b38a9-238">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="b38a9-239">Para las versiones posteriores, vea [ConsolePaneBackgroundColor](#conpbc).</span><span class="sxs-lookup"><span data-stu-id="b38a9-239">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="b38a9-240">La propiedad de lectura y escritura que obtiene o establece el color de fondo para el propio panel de resultado.</span><span class="sxs-lookup"><span data-stu-id="b38a9-240">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="b38a9-241">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-241">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

###  <span data-ttu-id="b38a9-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span></span>
  <span data-ttu-id="b38a9-243">Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.</span><span class="sxs-lookup"><span data-stu-id="b38a9-243">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="b38a9-244">Para las versiones posteriores, vea [ConsolePaneForegroundColor](#conpfc).</span><span class="sxs-lookup"><span data-stu-id="b38a9-244">For later versions, see [ConsolePaneForegroundColor](#conpfc).</span></span>

 <span data-ttu-id="b38a9-245">La propiedad de lectura y escritura que cambia el color de primer plano del texto en el panel de salida en Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="b38a9-245">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

###  <span data-ttu-id="b38a9-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span></span>
  <span data-ttu-id="b38a9-247">Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.</span><span class="sxs-lookup"><span data-stu-id="b38a9-247">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="b38a9-248">Para las versiones posteriores, vea [ConsolePaneTextBackgroundColor](#conptbc).</span><span class="sxs-lookup"><span data-stu-id="b38a9-248">For later versions, see [ConsolePaneTextBackgroundColor](#conptbc).</span></span>

 <span data-ttu-id="b38a9-249">La propiedad de lectura y escritura que cambia el color de fondo del texto en el panel de salida.</span><span class="sxs-lookup"><span data-stu-id="b38a9-249">The read/write property that changes the background color of the text in the Output pane.</span></span>

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="b38a9-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span></span>
  <span data-ttu-id="b38a9-251">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-251">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-252">La propiedad de lectura y escritura que obtiene o establece el color de fondo para los archivos.</span><span class="sxs-lookup"><span data-stu-id="b38a9-252">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="b38a9-253">Es una instancia de la clase **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-253">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = ”yellow”

```

###  <span data-ttu-id="b38a9-254"><a name="spfc"></a> ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-254"><a name="spfc"></a> ScriptPaneForegroundColor</span></span>
  <span data-ttu-id="b38a9-255">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-255">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-256">La propiedad de lectura y escritura que obtiene o establece el color de primer plano para archivos que no son de script en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="b38a9-256">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="b38a9-257">Para establecer el color de primer plano para archivos de script, utilice la propiedad [TokenColors](The-ISEOptions-Object.md#tc).</span><span class="sxs-lookup"><span data-stu-id="b38a9-257">To set the foreground color for script files, use the [TokenColors](The-ISEOptions-Object.md#tc) property.</span></span>

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

###  <span data-ttu-id="b38a9-258"><a name="ssps"></a> SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="b38a9-258"><a name="ssps"></a> SelectedScriptPaneState</span></span>
  <span data-ttu-id="b38a9-259">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-259">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-260">La propiedad de lectura y escritura que obtiene o establece la posición del panel de scripts en la pantalla.</span><span class="sxs-lookup"><span data-stu-id="b38a9-260">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="b38a9-261">La cadena puede ser "Maximized", "Top" o "Right".</span><span class="sxs-lookup"><span data-stu-id="b38a9-261">The string can be either "Maximized", "Top", or "Right".</span></span>

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

###  <span data-ttu-id="b38a9-262"><a name="sds"></a> ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="b38a9-262"><a name="sds"></a> ShowDefaultSnippets</span></span>
  <span data-ttu-id="b38a9-263">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-264">Especifica si la lista de fragmentos de código **CTRL+J** incluye el conjunto de inicio que se incluye en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b38a9-264">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="b38a9-265">Cuando se establece en **$false**, en la lista **CTRL+J** solo aparecen los fragmentos de código definidos por el usuario.</span><span class="sxs-lookup"><span data-stu-id="b38a9-265">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="b38a9-266">El valor predeterminado es **$true**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-266">The default value is **$true**.</span></span>

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

###  <span data-ttu-id="b38a9-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="b38a9-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span></span>
  <span data-ttu-id="b38a9-268">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-268">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-269">Especifica si IntelliSense ofrece sugerencias de sintaxis, parámetros y valores en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-269">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="b38a9-270">El valor predeterminado es **$true**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-270">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

###  <span data-ttu-id="b38a9-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="b38a9-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span></span>
  <span data-ttu-id="b38a9-272">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-272">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-273">Especifica si IntelliSense ofrece sugerencias de sintaxis, parámetros y valores en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="b38a9-273">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="b38a9-274">El valor predeterminado es **$true**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-274">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

###  <span data-ttu-id="b38a9-275"><a name="sln"></a> ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="b38a9-275"><a name="sln"></a> ShowLineNumbers</span></span>
  <span data-ttu-id="b38a9-276">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-276">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-277">Especifica si el panel de scripts muestra los números de línea en el margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="b38a9-277">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="b38a9-278">El valor predeterminado es **$true**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-278">The default value is **$true**.</span></span>

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

###  <span data-ttu-id="b38a9-279"><a name="so"></a> ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="b38a9-279"><a name="so"></a> ShowOutlining</span></span>
  <span data-ttu-id="b38a9-280">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-280">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-281">Especifica si el panel de scripts muestra corchetes expandibles y que se puedan contraer junto a las secciones de código en el margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="b38a9-281">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="b38a9-282">Cuando se muestren, puede hacer clic en los iconos de signo menos \(-\) junto a un bloque de texto para contraerlo o en el icono de signo más \(+\) para expandir un bloque de texto.</span><span class="sxs-lookup"><span data-stu-id="b38a9-282">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="b38a9-283">El valor predeterminado es **$true**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-283">The default value is **$true**.</span></span>

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

###  <span data-ttu-id="b38a9-284"><a name="stb"></a> ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="b38a9-284"><a name="stb"></a> ShowToolBar</span></span>
  <span data-ttu-id="b38a9-285">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-286">Especifica si la barra de herramientas de ISE aparece en la parte superior de la ventana de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b38a9-286">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="b38a9-287">El valor predeterminado es **$true**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-287">The default value is **$true**.</span></span>

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

###  <span data-ttu-id="b38a9-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="b38a9-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span></span>
  <span data-ttu-id="b38a9-289">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-289">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-290">Especifica si aparece un mensaje de advertencia cuando un script se guarda automáticamente antes de ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="b38a9-290">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="b38a9-291">El valor predeterminado es **$true**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-291">The default value is **$true**.</span></span>

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

###  <span data-ttu-id="b38a9-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="b38a9-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span></span>
  <span data-ttu-id="b38a9-293">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-293">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-294">Especifica si aparece un mensaje de advertencia cuando se abre el mismo archivo en diferentes pestañas de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b38a9-294">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="b38a9-295">Si establece en **$true**, al abrir el mismo archivo en varias pestañas aparece este mensaje: "Hay una copia de este archivo abierta en otra pestaña de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b38a9-295">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab.</span></span> <span data-ttu-id="b38a9-296">Los cambios realizados en este archivo afectarán a todas las copias abiertas.".</span><span class="sxs-lookup"><span data-stu-id="b38a9-296">Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="b38a9-297">El valor predeterminado es **$true**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-297">The default value is **$true**.</span></span>

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

###  <span data-ttu-id="b38a9-298"><a name="tc"></a> TokenColors</span><span class="sxs-lookup"><span data-stu-id="b38a9-298"><a name="tc"></a> TokenColors</span></span>
  <span data-ttu-id="b38a9-299">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-299">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-300">Especifica los colores de los token de IntelliSense en el panel de scripts de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b38a9-300">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="b38a9-301">Esta propiedad es un objeto de diccionario que contiene pares nombre-valor de tipos y colores de token para el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="b38a9-301">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="b38a9-302">Para cambiar los colores de los token de IntelliSense en el panel de consola, consulte [ConsoleTokenColors](#contc).</span><span class="sxs-lookup"><span data-stu-id="b38a9-302">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#contc).</span></span> <span data-ttu-id="b38a9-303">Para restablecer los valores predeterminados de los colores, consulte [RestoreDefaultTokenColors()](#rdtc).</span><span class="sxs-lookup"><span data-stu-id="b38a9-303">To reset the colors to the default values, see [RestoreDefaultTokenColors()](#rdtc).</span></span> <span data-ttu-id="b38a9-304">Los colores de token se pueden establecer para lo siguiente: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown y Variable.</span><span class="sxs-lookup"><span data-stu-id="b38a9-304">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="b38a9-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="b38a9-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span></span>
  <span data-ttu-id="b38a9-306">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-306">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-307">Especifica si se puede utilizar la tecla Entrar para seleccionar un opción proporcionada por IntelliSense en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-307">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="b38a9-308">El valor predeterminado es **$true**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-308">The default value is **$true**.</span></span>

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

###  <span data-ttu-id="b38a9-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="b38a9-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span></span>
  <span data-ttu-id="b38a9-310">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-310">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-311">Especifica si se puede utilizar la tecla Entrar para seleccionar un opción proporcionada por IntelliSense en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="b38a9-311">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="b38a9-312">El valor predeterminado es **$true**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-312">The default value is **$true**.</span></span>

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

###  <span data-ttu-id="b38a9-313"><a name="ulh"></a> UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="b38a9-313"><a name="ulh"></a> UseLocalHelp</span></span>
  <span data-ttu-id="b38a9-314">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-314">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-315">Especifica si la Ayuda instalada localmente o la Ayuda de la Biblioteca de TechNet en línea aparecen cuando se presiona F1 con el cursor situado en una palabra clave.</span><span class="sxs-lookup"><span data-stu-id="b38a9-315">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="b38a9-316">Si establece en **$true**, una ventana emergente muestra el contenido de la Ayuda instalada localmente.</span><span class="sxs-lookup"><span data-stu-id="b38a9-316">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="b38a9-317">Puede instalar los archivos de la Ayuda ejecutando el comando `Update-Help`.</span><span class="sxs-lookup"><span data-stu-id="b38a9-317">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="b38a9-318">Si se establece en **$false**, el explorador se abre en a una página de la Biblioteca de TechNet.</span><span class="sxs-lookup"><span data-stu-id="b38a9-318">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

###  <span data-ttu-id="b38a9-319"><a name="vbc"></a> VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-319"><a name="vbc"></a> VerboseBackgroundColor</span></span>
  <span data-ttu-id="b38a9-320">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-320">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-321">Especifica el color de fondo para el texto detallado que aparece en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-321">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="b38a9-322">Es un objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-322">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="b38a9-323"><a name="vfc"></a> VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-323"><a name="vfc"></a> VerboseForegroundColor</span></span>
  <span data-ttu-id="b38a9-324">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-324">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-325">Especifica el color de primer plano para el texto detallado que aparece en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-325">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="b38a9-326">Es un objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-326">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor =”yellow”
```

###  <span data-ttu-id="b38a9-327"><a name="wbc"></a> WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-327"><a name="wbc"></a> WarningBackgroundColor</span></span>
  <span data-ttu-id="b38a9-328">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-328">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-329">Especifica el color de fondo para el texto de advertencia que aparece en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="b38a9-329">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="b38a9-330">Es un objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-330">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="b38a9-331"><a name="wfc"></a> WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b38a9-331"><a name="wfc"></a> WarningForegroundColor</span></span>
  <span data-ttu-id="b38a9-332">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-332">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b38a9-333">Especifica el color de primer plano para el texto de advertencia que aparece en el panel de salida.</span><span class="sxs-lookup"><span data-stu-id="b38a9-333">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="b38a9-334">Es un objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="b38a9-334">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor =”yellow”
```

###  <span data-ttu-id="b38a9-335"><a name="xtc"></a> XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="b38a9-335"><a name="xtc"></a> XmlTokenColors</span></span>
  <span data-ttu-id="b38a9-336">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-336">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-337">Especifica un objeto de diccionario que contiene pares nombre-valor de tipos y colores de token para el contenido XML que se muestra en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b38a9-337">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="b38a9-338">Los colores de token se pueden establecer para lo siguiente: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown y Variable.</span><span class="sxs-lookup"><span data-stu-id="b38a9-338">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="b38a9-339">Vea también [RestoreDefaultXmlTokenColors()](#rdxtc).</span><span class="sxs-lookup"><span data-stu-id="b38a9-339">Also see [RestoreDefaultXmlTokenColors()](#rdxtc).</span></span>

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

###  <span data-ttu-id="b38a9-340"><a name="z"></a> Zoom</span><span class="sxs-lookup"><span data-stu-id="b38a9-340"><a name="z"></a> Zoom</span></span>
  <span data-ttu-id="b38a9-341">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b38a9-341">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b38a9-342">Especifica el tamaño relativo del texto en los paneles de consola y scripts.</span><span class="sxs-lookup"><span data-stu-id="b38a9-342">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="b38a9-343">El valor predeterminado es 100.</span><span class="sxs-lookup"><span data-stu-id="b38a9-343">The default value is 100.</span></span> <span data-ttu-id="b38a9-344">Los valores más pequeños hacen que el texto de Windows PowerShell ISE sea menor, mientras que números más grandes hacen que el texto aparezca más grande.</span><span class="sxs-lookup"><span data-stu-id="b38a9-344">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="b38a9-345">El valor es un entero comprendido entre 20 y 400.</span><span class="sxs-lookup"><span data-stu-id="b38a9-345">The value is an integer that ranges from 20 to 400.</span></span>

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="b38a9-346">Véase también</span><span class="sxs-lookup"><span data-stu-id="b38a9-346">See Also</span></span>
- [<span data-ttu-id="b38a9-347">El modelo de objetos de scripting de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b38a9-347">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="b38a9-348">Referencia del modelo de objetos de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b38a9-348">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

