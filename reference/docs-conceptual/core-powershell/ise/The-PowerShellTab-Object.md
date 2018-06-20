---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: El objeto PowerShellTab
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: c10f9106e31bb05828f1e76554ebe40ddb778340
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952518"
---
# <a name="the-powershelltab-object"></a>El objeto PowerShellTab

El objeto **PowerShellTab** representa un entorno de runtime de Windows PowerShell.

## <a name="methods"></a>Métodos

### <a name="invoke-script-"></a>Invoke\( Script \)

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

Ejecuta el script especificado en la pestaña de PowerShell.

> [!NOTE]
> Este método solo funciona en otras pestañas de PowerShell, no en la pestaña de PowerShell desde la que se ejecuta. No devuelve ningún objeto o valor. Si el código modifica cualquier variable, esos cambios se conservan en la pestaña en la que se invocó el comando.

**Script**: System.Management.Automation.ScriptBlock o cadena. El bloque de script para ejecutar.

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)

Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

Ejecuta el script especificado en la pestaña de PowerShell.

> [!NOTE]
> Este método solo funciona en otras pestañas de PowerShell, no en la pestaña de PowerShell desde la que se ejecuta. El bloque de script se ejecuta y cualquier valor que se devuelve desde el script se devuelve al entorno de ejecución desde el que se invocó el comando. Si el comando tarda más tiempo en ejecutarse que lo que especifica el valor de **tiempoEsperaMilisegundos**, el comando no se ejecuta correctamente e inicia una excepción: "La operación ha agotado el tiempo de espera.".

**Script**: System.Management.Automation.ScriptBlock o cadena. El bloque de script para ejecutar.

**\[useNewScope\]**: booleano opcional cuyo valor predeterminado es **$true**. Si está establecido en **$true**, se crea un nuevo ámbito en el que ejecutar el comando. No modifica el entorno de tiempo de ejecución de la pestaña de PowerShell que se especifica mediante el comando.

**\[millisecondsTimeout\]**: entero opcional cuyo valor predeterminado es **500**.
Si el comando no finaliza dentro del tiempo especificado, inicia **TimeoutException** con el mensaje "La operación ha agotado el tiempo de espera.".

```powershell
# Create a new PowerShell tab and then switch back to the first
$psISE.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0])

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1', $false)
# You can switch to the other tab and type '$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope)
# and returns it through the pipeline to this tab to store in $a
$a = $psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z')
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
Measure-Command {$psISE.PowerShellTabs[1].InvokeSynchronous('sleep 10', $false, 5000)}
```

## <a name="properties"></a>Propiedades

### <a name="addonsmenu"></a>AddOnsMenu

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene el menú Complementos para la pestaña de PowerShell.

```powershell
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a>CanInvoke

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad booleana de solo lectura que devuelve un valor **$true** si se puede invocar un script con el método [Invoke( Script )](#invoke-script-).

```powershell
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab.
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psISE.PowerShellTabs[1]
$secondTab.CanInvoke
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke
```

### <a name="consolepane"></a>Consolepane

Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.  En Windows PowerShell ISE 2.0 esto se llamaba **CommandPane**.

La propiedad de solo lectura que obtiene el objeto [editor](../ise/The-ISEEditor-Object.md) del panel de consola.

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a>DisplayName

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de lectura y escritura que obtiene o establece el texto que se muestra en la pestaña de PowerShell. De forma predeterminada, las pestañas se denominan "PowerShell #", donde # representa un número.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a>ExpandedScript

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad booleana de lectura y escritura que determina si el panel de scripts se expande o se oculta.

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a>Archivos

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene la [colección de archivos de scripts](../ise/The-ISEFileCollection-Object.md) que están abiertos en la pestaña de PowerShell.

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Salida

Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.  En versiones posteriores de Windows PowerShell ISE, puede usar el objeto **ConsolePane** con el mismo propósito.

La propiedad de solo lectura que obtiene el panel de salida del [editor](../ise/The-ISEEditor-Object.md) actual .

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Prompt

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene el texto de la petición actual. Nota: El perfil del usuario puede reemplazar a la función **Prompt**. Si el resultado es distinto de una cadena simple, esta propiedad no devuelve nada.

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands

Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

La propiedad de lectura y escritura que indica si actualmente se muestra el panel de comandos.

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a>StatusText

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene el texto de estado de **PowerShellTab**.

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened

Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

La propiedad de solo lectura que indica si el panel de herramientas de complementos horizontal está abierto actualmente.

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened

Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

La propiedad de solo lectura que indica si el panel de herramientas de complementos vertical está abierto actualmente.

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Véase también

- [El objeto PowerShellTabCollection](The-PowerShellTabCollection-Object.md)
- [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)