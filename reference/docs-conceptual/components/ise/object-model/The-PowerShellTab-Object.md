---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: El objeto PowerShellTab
ms.openlocfilehash: 55e3678a8285f0ec7e8131d98c87478216c26f37
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736937"
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="46ee5-103">El objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="46ee5-103">The PowerShellTab Object</span></span>

<span data-ttu-id="46ee5-104">El objeto **PowerShellTab** representa un entorno de runtime de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46ee5-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="46ee5-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="46ee5-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="46ee5-106">Invoke\( Script \)</span><span class="sxs-lookup"><span data-stu-id="46ee5-106">Invoke\( Script \)</span></span>

<span data-ttu-id="46ee5-107">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="46ee5-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="46ee5-108">Ejecuta el script especificado en la pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46ee5-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="46ee5-109">Este método solo funciona en otras pestañas de PowerShell, no en la pestaña de PowerShell desde la que se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="46ee5-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="46ee5-110">No devuelve ningún objeto o valor.</span><span class="sxs-lookup"><span data-stu-id="46ee5-110">It does not return any object or value.</span></span> <span data-ttu-id="46ee5-111">Si el código modifica cualquier variable, esos cambios se conservan en la pestaña en la que se invocó el comando.</span><span class="sxs-lookup"><span data-stu-id="46ee5-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="46ee5-112">**Script**: System.Management.Automation.ScriptBlock o cadena. El bloque de script para ejecutar.</span><span class="sxs-lookup"><span data-stu-id="46ee5-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="46ee5-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="46ee5-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="46ee5-114">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="46ee5-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="46ee5-115">Ejecuta el script especificado en la pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46ee5-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="46ee5-116">Este método solo funciona en otras pestañas de PowerShell, no en la pestaña de PowerShell desde la que se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="46ee5-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="46ee5-117">El bloque de script se ejecuta y cualquier valor que se devuelve desde el script se devuelve al entorno de ejecución desde el que se invocó el comando.</span><span class="sxs-lookup"><span data-stu-id="46ee5-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="46ee5-118">Si el comando tarda más tiempo en ejecutarse que lo que especifica el valor de **millesecondsTimeout**, el comando no se ejecuta correctamente e inicia una excepción: "La operación ha agotado el tiempo de espera".</span><span class="sxs-lookup"><span data-stu-id="46ee5-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="46ee5-119">**Script**: System.Management.Automation.ScriptBlock o cadena. El bloque de script para ejecutar.</span><span class="sxs-lookup"><span data-stu-id="46ee5-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="46ee5-120">**\[useNewScope\]** : booleano opcional cuyo valor predeterminado es `$true`. Si está establecido en `$true`, se crea un nuevo ámbito en el que ejecutar el comando.</span><span class="sxs-lookup"><span data-stu-id="46ee5-120">**\[useNewScope\]** -  Optional Boolean that defaults to `$true` If set to `$true`, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="46ee5-121">No modifica el entorno de tiempo de ejecución de la pestaña de PowerShell que se especifica mediante el comando.</span><span class="sxs-lookup"><span data-stu-id="46ee5-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="46ee5-122">**\[millisecondsTimeout\]** : entero opcional cuyo valor predeterminado es **500**.</span><span class="sxs-lookup"><span data-stu-id="46ee5-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="46ee5-123">Si el comando no finaliza dentro del tiempo especificado, inicia **TimeoutException** con el mensaje "La operación ha agotado el tiempo de espera.".</span><span class="sxs-lookup"><span data-stu-id="46ee5-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

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

## <a name="properties"></a><span data-ttu-id="46ee5-124">Propiedades</span><span class="sxs-lookup"><span data-stu-id="46ee5-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="46ee5-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="46ee5-125">AddOnsMenu</span></span>

<span data-ttu-id="46ee5-126">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="46ee5-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="46ee5-127">La propiedad de solo lectura que obtiene el menú Complementos para la pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46ee5-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

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

### <a name="caninvoke"></a><span data-ttu-id="46ee5-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="46ee5-128">CanInvoke</span></span>

<span data-ttu-id="46ee5-129">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="46ee5-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="46ee5-130">La propiedad booleana de solo lectura que devuelve un valor `$true` si se puede invocar un script con el método [Invoke( Script )](#invoke-script-).</span><span class="sxs-lookup"><span data-stu-id="46ee5-130">The read-only Boolean property that returns a `$true` value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

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

### <a name="consolepane"></a><span data-ttu-id="46ee5-131">ConsolePane</span><span class="sxs-lookup"><span data-stu-id="46ee5-131">ConsolePane</span></span>

<span data-ttu-id="46ee5-132">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="46ee5-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> <span data-ttu-id="46ee5-133">En Windows PowerShell ISE 2.0 esto se llamaba **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="46ee5-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="46ee5-134">La propiedad de solo lectura que obtiene el objeto [editor](The-ISEEditor-Object.md) del panel de consola.</span><span class="sxs-lookup"><span data-stu-id="46ee5-134">The read-only property that gets the Console pane [editor](The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="46ee5-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="46ee5-135">DisplayName</span></span>

<span data-ttu-id="46ee5-136">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="46ee5-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="46ee5-137">La propiedad de lectura y escritura que obtiene o establece el texto que se muestra en la pestaña de PowerShell. De forma predeterminada, las pestañas se denominan "PowerShell #", donde # representa un número.</span><span class="sxs-lookup"><span data-stu-id="46ee5-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="46ee5-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="46ee5-138">ExpandedScript</span></span>

<span data-ttu-id="46ee5-139">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="46ee5-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="46ee5-140">La propiedad booleana de lectura y escritura que determina si el panel de scripts se expande o se oculta.</span><span class="sxs-lookup"><span data-stu-id="46ee5-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="46ee5-141">Archivos</span><span class="sxs-lookup"><span data-stu-id="46ee5-141">Files</span></span>

<span data-ttu-id="46ee5-142">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="46ee5-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="46ee5-143">La propiedad de solo lectura que obtiene la [colección de archivos de scripts](The-ISEFileCollection-Object.md) que están abiertos en la pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46ee5-143">The read-only property that gets the [collection of script files](The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="46ee5-144">Output</span><span class="sxs-lookup"><span data-stu-id="46ee5-144">Output</span></span>

<span data-ttu-id="46ee5-145">Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.</span><span class="sxs-lookup"><span data-stu-id="46ee5-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="46ee5-146">En versiones posteriores de Windows PowerShell ISE, puede usar el objeto **ConsolePane** con el mismo propósito.</span><span class="sxs-lookup"><span data-stu-id="46ee5-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="46ee5-147">La propiedad de solo lectura que obtiene el panel de salida del [editor](The-ISEEditor-Object.md) actual .</span><span class="sxs-lookup"><span data-stu-id="46ee5-147">The read-only property that gets the Output pane of the current [editor](The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="46ee5-148">Prompt</span><span class="sxs-lookup"><span data-stu-id="46ee5-148">Prompt</span></span>

<span data-ttu-id="46ee5-149">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="46ee5-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="46ee5-150">La propiedad de solo lectura que obtiene el texto de la petición actual.</span><span class="sxs-lookup"><span data-stu-id="46ee5-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="46ee5-151">Nota: El perfil del usuario puede reemplazar a la función **Prompt**.</span><span class="sxs-lookup"><span data-stu-id="46ee5-151">Note: the **Prompt** function can be overridden by the user'™s profile.</span></span> <span data-ttu-id="46ee5-152">Si el resultado es distinto de una cadena simple, esta propiedad no devuelve nada.</span><span class="sxs-lookup"><span data-stu-id="46ee5-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="46ee5-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="46ee5-153">ShowCommands</span></span>

<span data-ttu-id="46ee5-154">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="46ee5-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="46ee5-155">La propiedad de lectura y escritura que indica si actualmente se muestra el panel de comandos.</span><span class="sxs-lookup"><span data-stu-id="46ee5-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="46ee5-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="46ee5-156">StatusText</span></span>

<span data-ttu-id="46ee5-157">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="46ee5-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="46ee5-158">La propiedad de solo lectura que obtiene el texto de estado de **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="46ee5-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="46ee5-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="46ee5-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="46ee5-160">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="46ee5-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="46ee5-161">La propiedad de solo lectura que indica si el panel de herramientas de complementos horizontal está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="46ee5-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="46ee5-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="46ee5-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="46ee5-163">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="46ee5-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="46ee5-164">La propiedad de solo lectura que indica si el panel de herramientas de complementos vertical está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="46ee5-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="46ee5-165">Consulte también</span><span class="sxs-lookup"><span data-stu-id="46ee5-165">See Also</span></span>

- [<span data-ttu-id="46ee5-166">El objeto PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="46ee5-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="46ee5-167">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="46ee5-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="46ee5-168">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="46ee5-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
