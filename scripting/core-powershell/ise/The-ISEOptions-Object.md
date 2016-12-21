---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: El objeto ISEOptions
ms.technology: powershell
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: ef8d5ce9cd3b723c97eb94042b4c1cd00dc27b98
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="the-iseoptions-object"></a>El objeto ISEOptions
  El objeto **ISEOptions** representa distintas configuraciones de Windows PowerShell ISE. Es una instancia de la clase **Microsoft.PowerShell.Host.ISE.ISEOptions**.

 El objeto **ISEOptions** proporciona los siguientes métodos y propiedades.

 **Methods**

-   [RestoreDefaultConsoleTokenColors()](#rdctc)

-   [RestoreDefaults()](#rd)

-   [RestoreDefaultTokenColors()](#rdtc)

-   [RestoreDefaultXmlTokenColors()](#rdxtc)

 **Properties**

-   [AutoSaveMinuteInterval](#asmi)

-   [CommandPaneBackgroundColor](#cpbc)

-   [CommandPaneUp](#cpu)

-   [ConsolePaneBackgroundColor](#conpbc)

-   [ConsolePaneForegroundColor](#conpfc)

-   [ConsolePaneTextBackgroundColor](#conptbc)

-   [ConsoleTokenColors](#contc)

-   [DebugBackgroundColor](#dbc)

-   [DebugForegroundColor](#dfc)

-   [DefaultOptions](#do)

-   [ErrorBackgroundColor](#ebc)

-   [ErrorForegroundColor](#efc)

-   [FontName](#fn)

-   [FontSize](#fs)

-   [IntellisenseTimeoutInSeconds](#itis)

-   [MruCount](#mc)

-   [OutputPaneBackgroundColor](#opbc)

-   [OutputPaneTextForegroundColor](#optfc)

-   [OutputPaneTextBackgroundColor](#optbc)

-   [ScriptPaneBackgroundColor](#spbc)

-   [ScriptPaneForegroundColor](#spfc)

-   [SelectedScriptPaneState](#ssps)

-   [ShowDefaultSnippets](#sds)

-   [ShowIntellisenseInConsolePane](#siicp)

-   [ShowIntellisenseInScriptPane](#siisp)

-   [ShowLineNumbers](#sln)

-   [ShowOutlining](#so)

-   [ShowToolBar](#stb)

-   [ShowWarningBeforeSavingOnRun](#swbsor)

-   [ShowWarningForDuplicateFiles](#swfdf)

-   [TokenColors](#tc)

-   [UseEnterToSelectInConsolePaneIntellisense](#uetsicpi)

-   [UseEnterToSelectInScriptPaneIntellisense](#uetsispi)

-   [UseLocalHelp](#ulh)

-   [VerboseBackgroundColor](#vbc)

-   [VerboseForegroundColor](#vfc)

-   [WarningBackgroundColor](#wbc)

-   [WarningForegroundColor](#wfc)

-   [XmlTokenColors](#xtc)

-   [Zoom](#z)

## <a name="methods"></a>Métodos

###  <a name="a-namerdctca-restoredefaultconsoletokencolors"></a><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Restaura los valores predeterminados de los colores de token en el panel de consola.

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

###  <a name="a-namerda-restoredefaults"></a><a name="rd"></a> RestoreDefaults\(\)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Restaura los valores predeterminados de todas las configuraciones de opciones en el panel de consola. También restablece el comportamiento de varios mensajes de advertencia que proporcionan la casilla estándar para impedir que el mensaje se muestre de nuevo.

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

###  <a name="a-namerdtca-restoredefaulttokencolors"></a><a name="rdtc"></a> RestoreDefaultTokenColors\(\)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Restaura los valores predeterminados de los colores de token en el panel de scripts.

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

###  <a name="a-namerdxtca-restoredefaultxmltokencolors"></a><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Restaura los valores predeterminados de los colores de token de elementos XML que se muestran en Windows PowerShell ISE. Vea también [XmlTokenColors](#xtc).

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a>Propiedades

###  <a name="a-nameasmia-autosaveminuteinterval"></a><a name="asmi"></a> AutoSaveMinuteInterval
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica el número de minutos entre operaciones de guardado automático de los archivos realizadas por Windows PowerShell ISE. El valor predeterminado es 2 minutos. El valor es un entero.

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

###  <a name="a-namecpbca-commandpanebackgroundcolor"></a><a name="cpbc"></a> CommandPaneBackgroundColor
  Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.  Para las versiones posteriores, vea [ConsolePaneBackgroundColor](#conpbc).

 Especifica el color de fondo para el panel de comandos. Es una instancia de la clase **System.Windows.Media.Color**.

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

###  <a name="a-namecpua-commandpaneup"></a><a name="cpu"></a> CommandPaneUp
  Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.

 Especifica si el panel de comandos se encuentra encima del panel de resultados.

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

###  <a name="a-nameconpbca-consolepanebackgroundcolor"></a><a name="conpbc"></a> ConsolePaneBackgroundColor
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica el color de fondo para el panel de consola. Es una instancia de la clase **System.Windows.Media.Color**.

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

###  <a name="a-nameconpfca-consolepaneforegroundcolor"></a><a name="conpfc"></a> ConsolePaneForegroundColor
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica el color de fondo del texto en el panel de consola.

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

###  <a name="a-nameconptbca-consolepanetextbackgroundcolor"></a><a name="conptbc"></a> ConsolePaneTextBackgroundColor
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica el color de primer plano en el panel de consola.

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

###  <a name="a-namecontca-consoletokencolors"></a><a name="contc"></a> ConsoleTokenColors
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica los colores de los token de IntelliSense en el panel de consola de Windows PowerShell ISE. Esta propiedad es un objeto de diccionario que contiene pares nombre-valor de tipos y colores de token para el panel de consola. Para cambiar los colores de los token de IntelliSense en el panel de scripts, consulte [TokenColors](#tc). Para restablecer los valores predeterminados de los colores, consulte [RestoreDefaultConsoleTokenColors()](#rdctc). Los colores de token se pueden establecer para lo siguiente: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown y Variable.

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

###  <a name="a-namedbca-debugbackgroundcolor"></a><a name="dbc"></a> DebugBackgroundColor
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Especifica el color de fondo para el texto de depuración que aparece en el panel de consola. Es una instancia de la clase **System.Windows.Media.Color**.

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

###  <a name="a-namedfca-debugforegroundcolor"></a><a name="dfc"></a> DebugForegroundColor
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Especifica el color de primer plano para el texto de depuración que aparece en el panel de consola. Es una instancia de la clase **System.Windows.Media.Color**.

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

###  <a name="a-namedoa-defaultoptions"></a><a name="do"></a> DefaultOptions
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Una colección de propiedades que especifica los valores predeterminados que se utilizarán cuando se empleen los métodos Reset.

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

###  <a name="a-nameebca-errorbackgroundcolor"></a><a name="ebc"></a> ErrorBackgroundColor
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Especifica el color de fondo para el texto de error que aparece en el panel de consola. Es una instancia de la clase **System.Windows.Media.Color**.

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

###  <a name="a-nameefca-errorforegroundcolor"></a><a name="efc"></a> ErrorForegroundColor
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Especifica el color de primer plano para el texto de error que aparece en el panel de consola. Es una instancia de la clase **System.Windows.Media.Color**.

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

###  <a name="a-namefna-fontname"></a><a name="fn"></a> FontName
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Especifica el nombre de fuente que se está usando actualmente tanto en el panel de scripts como en el panel de consola.

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

###  <a name="a-namefsa-fontsize"></a><a name="fs"></a> FontSize
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Especifica el tamaño de fuente como un entero. Se usa en el panel de scripts, en el panel de comandos y en el panel de salida. El intervalo válido de valores es de 8 a 32.

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

###  <a name="a-nameitisa-intellisensetimeoutinseconds"></a><a name="itis"></a> IntellisenseTimeoutInSeconds
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica el número de segundos que IntelliSense usa para intentar resolver el texto escrito actualmente. Transcurrido este número de segundos, el tiempo de espera de IntelliSense se agota y le permite continuar escribiendo. El valor predeterminado es 3 segundos. El valor es un entero.

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

###  <a name="a-namemca-mrucount"></a><a name="mc"></a> MruCount
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica el número de archivos abiertos recientemente que Windows PowerShell ISE sigue y se muestra en la parte inferior del menú **Archivo - Abrir**. El valor predeterminado es 10. El valor es un entero.

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

###  <a name="a-nameopbca-outputpanebackgroundcolor"></a><a name="opbc"></a> OutputPaneBackgroundColor
  Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.  Para las versiones posteriores, vea [ConsolePaneBackgroundColor](#conpbc).

 La propiedad de lectura y escritura que obtiene o establece el color de fondo para el propio panel de resultado. Es una instancia de la clase **System.Windows.Media.Color**.

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

###  <a name="a-nameoptfca-outputpanetextforegroundcolor"></a><a name="optfc"></a> OutputPaneTextForegroundColor
  Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.  Para las versiones posteriores, vea [ConsolePaneForegroundColor](#conpfc).

 La propiedad de lectura y escritura que cambia el color de primer plano del texto en el panel de salida en Windows PowerShell ISE 2.0.

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

###  <a name="a-nameoptbca-outputpanetextbackgroundcolor"></a><a name="optbc"></a> OutputPaneTextBackgroundColor
  Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.  Para las versiones posteriores, vea [ConsolePaneTextBackgroundColor](#conptbc).

 La propiedad de lectura y escritura que cambia el color de fondo del texto en el panel de salida.

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

###  <a name="a-namespbca-scriptpanebackgroundcolor"></a><a name="spbc"></a> ScriptPaneBackgroundColor
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 La propiedad de lectura y escritura que obtiene o establece el color de fondo para los archivos. Es una instancia de la clase **System.Windows.Media.Color**.

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = ”yellow”

```

###  <a name="a-namespfca-scriptpaneforegroundcolor"></a><a name="spfc"></a> ScriptPaneForegroundColor
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 La propiedad de lectura y escritura que obtiene o establece el color de primer plano para archivos que no son de script en el panel de scripts.
Para establecer el color de primer plano para archivos de script, utilice la propiedad [TokenColors](The-ISEOptions-Object.md#tc).

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

###  <a name="a-namesspsa-selectedscriptpanestate"></a><a name="ssps"></a> SelectedScriptPaneState
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 La propiedad de lectura y escritura que obtiene o establece la posición del panel de scripts en la pantalla. La cadena puede ser "Maximized", "Top" o "Right".

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

###  <a name="a-namesdsa-showdefaultsnippets"></a><a name="sds"></a> ShowDefaultSnippets
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica si la lista de fragmentos de código **CTRL+J** incluye el conjunto de inicio que se incluye en Windows PowerShell. Cuando se establece en **$false**, en la lista **CTRL+J** solo aparecen los fragmentos de código definidos por el usuario. El valor predeterminado es **$true**.

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

###  <a name="a-namesiicpa-showintellisenseinconsolepane"></a><a name="siicp"></a> ShowIntellisenseInConsolePane
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica si IntelliSense ofrece sugerencias de sintaxis, parámetros y valores en el panel de consola. El valor predeterminado es **$true**.

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

###  <a name="a-namesiispa-showintellisenseinscriptpane"></a><a name="siisp"></a> ShowIntellisenseInScriptPane
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica si IntelliSense ofrece sugerencias de sintaxis, parámetros y valores en el panel de scripts. El valor predeterminado es **$true**.

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

###  <a name="a-nameslna-showlinenumbers"></a><a name="sln"></a> ShowLineNumbers
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica si el panel de scripts muestra los números de línea en el margen izquierdo. El valor predeterminado es **$true**.

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

###  <a name="a-namesoa-showoutlining"></a><a name="so"></a> ShowOutlining
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica si el panel de scripts muestra corchetes expandibles y que se puedan contraer junto a las secciones de código en el margen izquierdo. Cuando se muestren, puede hacer clic en los iconos de signo menos \(-\) junto a un bloque de texto para contraerlo o en el icono de signo más \(+\) para expandir un bloque de texto. El valor predeterminado es **$true**.

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

###  <a name="a-namestba-showtoolbar"></a><a name="stb"></a> ShowToolBar
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Especifica si la barra de herramientas de ISE aparece en la parte superior de la ventana de Windows PowerShell ISE. El valor predeterminado es **$true**.

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

###  <a name="a-nameswbsora-showwarningbeforesavingonrun"></a><a name="swbsor"></a> ShowWarningBeforeSavingOnRun
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Especifica si aparece un mensaje de advertencia cuando un script se guarda automáticamente antes de ejecutarse. El valor predeterminado es **$true**.

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

###  <a name="a-nameswfdfa-showwarningforduplicatefiles"></a><a name="swfdf"></a> ShowWarningForDuplicateFiles
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Especifica si aparece un mensaje de advertencia cuando se abre el mismo archivo en diferentes pestañas de PowerShell. Si establece en **$true**, al abrir el mismo archivo en varias pestañas aparece este mensaje: "Hay una copia de este archivo abierta en otra pestaña de Windows PowerShell. Los cambios realizados en este archivo afectarán a todas las copias abiertas.". El valor predeterminado es **$true**.

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

###  <a name="a-nametca-tokencolors"></a><a name="tc"></a> TokenColors
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Especifica los colores de los token de IntelliSense en el panel de scripts de Windows PowerShell ISE. Esta propiedad es un objeto de diccionario que contiene pares nombre-valor de tipos y colores de token para el panel de scripts. Para cambiar los colores de los token de IntelliSense en el panel de consola, consulte [ConsoleTokenColors](#contc). Para restablecer los valores predeterminados de los colores, consulte [RestoreDefaultTokenColors()](#rdtc). Los colores de token se pueden establecer para lo siguiente: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown y Variable.

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

###  <a name="a-nameuetsicpia-useentertoselectinconsolepaneintellisense"></a><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica si se puede utilizar la tecla Entrar para seleccionar un opción proporcionada por IntelliSense en el panel de consola. El valor predeterminado es **$true**.

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

###  <a name="a-nameuetsispia-useentertoselectinscriptpaneintellisense"></a><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica si se puede utilizar la tecla Entrar para seleccionar un opción proporcionada por IntelliSense en el panel de scripts. El valor predeterminado es **$true**.

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

###  <a name="a-nameulha-uselocalhelp"></a><a name="ulh"></a> UseLocalHelp
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica si la Ayuda instalada localmente o la Ayuda de la Biblioteca de TechNet en línea aparecen cuando se presiona F1 con el cursor situado en una palabra clave. Si establece en **$true**, una ventana emergente muestra el contenido de la Ayuda instalada localmente. Puede instalar los archivos de la Ayuda ejecutando el comando `Update-Help`. Si se establece en **$false**, el explorador se abre en a una página de la Biblioteca de TechNet.

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

###  <a name="a-namevbca-verbosebackgroundcolor"></a><a name="vbc"></a> VerboseBackgroundColor
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Especifica el color de fondo para el texto detallado que aparece en el panel de consola. Es un objeto **System.Windows.Media.Color**.

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

###  <a name="a-namevfca-verboseforegroundcolor"></a><a name="vfc"></a> VerboseForegroundColor
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Especifica el color de primer plano para el texto detallado que aparece en el panel de consola. Es un objeto **System.Windows.Media.Color**.

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor =”yellow”
```

###  <a name="a-namewbca-warningbackgroundcolor"></a><a name="wbc"></a> WarningBackgroundColor
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Especifica el color de fondo para el texto de advertencia que aparece en el panel de consola. Es un objeto **System.Windows.Media.Color**.

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

###  <a name="a-namewfca-warningforegroundcolor"></a><a name="wfc"></a> WarningForegroundColor
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

 Especifica el color de primer plano para el texto de advertencia que aparece en el panel de salida. Es un objeto **System.Windows.Media.Color**.

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor =”yellow”
```

###  <a name="a-namextca-xmltokencolors"></a><a name="xtc"></a> XmlTokenColors
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica un objeto de diccionario que contiene pares nombre-valor de tipos y colores de token para el contenido XML que se muestra en Windows PowerShell ISE. Los colores de token se pueden establecer para lo siguiente: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown y Variable. Vea también [RestoreDefaultXmlTokenColors()](#rdxtc).

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

###  <a name="a-nameza-zoom"></a><a name="z"></a> Zoom
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

 Especifica el tamaño relativo del texto en los paneles de consola y scripts. El valor predeterminado es 100. Los valores más pequeños hacen que el texto de Windows PowerShell ISE sea menor, mientras que números más grandes hacen que el texto aparezca más grande. El valor es un entero comprendido entre 20 y 400.

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a>Véase también
- [El modelo de objetos de scripting de ISE de Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Referencia del modelo de objetos de ISE de Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md)

