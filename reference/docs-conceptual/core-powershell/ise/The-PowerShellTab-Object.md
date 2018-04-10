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
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="190a0-103">El objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="190a0-103">The PowerShellTab Object</span></span>

<span data-ttu-id="190a0-104">El objeto **PowerShellTab** representa un entorno de runtime de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="190a0-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="190a0-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="190a0-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="190a0-106">Invoke\( Script \)</span><span class="sxs-lookup"><span data-stu-id="190a0-106">Invoke\( Script \)</span></span>

<span data-ttu-id="190a0-107">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="190a0-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="190a0-108">Ejecuta el script especificado en la pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="190a0-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="190a0-109">Este método solo funciona en otras pestañas de PowerShell, no en la pestaña de PowerShell desde la que se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="190a0-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="190a0-110">No devuelve ningún objeto o valor.</span><span class="sxs-lookup"><span data-stu-id="190a0-110">It does not return any object or value.</span></span> <span data-ttu-id="190a0-111">Si el código modifica cualquier variable, esos cambios se conservan en la pestaña en la que se invocó el comando.</span><span class="sxs-lookup"><span data-stu-id="190a0-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="190a0-112">**Script**: System.Management.Automation.ScriptBlock o cadena. El bloque de script para ejecutar.</span><span class="sxs-lookup"><span data-stu-id="190a0-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="190a0-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="190a0-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="190a0-114">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="190a0-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="190a0-115">Ejecuta el script especificado en la pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="190a0-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="190a0-116">Este método solo funciona en otras pestañas de PowerShell, no en la pestaña de PowerShell desde la que se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="190a0-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="190a0-117">El bloque de script se ejecuta y cualquier valor que se devuelve desde el script se devuelve al entorno de ejecución desde el que se invocó el comando.</span><span class="sxs-lookup"><span data-stu-id="190a0-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="190a0-118">Si el comando tarda más tiempo en ejecutarse que lo que especifica el valor de **tiempoEsperaMilisegundos**, el comando no se ejecuta correctamente e inicia una excepción: "La operación ha agotado el tiempo de espera.".</span><span class="sxs-lookup"><span data-stu-id="190a0-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="190a0-119">**Script**: System.Management.Automation.ScriptBlock o cadena. El bloque de script para ejecutar.</span><span class="sxs-lookup"><span data-stu-id="190a0-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="190a0-120">**\[useNewScope\]**: booleano opcional cuyo valor predeterminado es **$true**. Si está establecido en **$true**, se crea un nuevo ámbito en el que ejecutar el comando.</span><span class="sxs-lookup"><span data-stu-id="190a0-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true** If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="190a0-121">No modifica el entorno de tiempo de ejecución de la pestaña de PowerShell que se especifica mediante el comando.</span><span class="sxs-lookup"><span data-stu-id="190a0-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="190a0-122">**\[millisecondsTimeout\]**: entero opcional cuyo valor predeterminado es **500**.</span><span class="sxs-lookup"><span data-stu-id="190a0-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="190a0-123">Si el comando no finaliza dentro del tiempo especificado, inicia **TimeoutException** con el mensaje "La operación ha agotado el tiempo de espera.".</span><span class="sxs-lookup"><span data-stu-id="190a0-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

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

## <a name="properties"></a><span data-ttu-id="190a0-124">Propiedades</span><span class="sxs-lookup"><span data-stu-id="190a0-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="190a0-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="190a0-125">AddOnsMenu</span></span>

<span data-ttu-id="190a0-126">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="190a0-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="190a0-127">La propiedad de solo lectura que obtiene el menú Complementos para la pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="190a0-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

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

### <a name="caninvoke"></a><span data-ttu-id="190a0-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="190a0-128">CanInvoke</span></span>

<span data-ttu-id="190a0-129">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="190a0-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="190a0-130">La propiedad booleana de solo lectura que devuelve un valor **$true** si se puede invocar un script con el método [Invoke( Script )](#invoke-script-).</span><span class="sxs-lookup"><span data-stu-id="190a0-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

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

### <a name="consolepane"></a><span data-ttu-id="190a0-131">Consolepane</span><span class="sxs-lookup"><span data-stu-id="190a0-131">Consolepane</span></span>

<span data-ttu-id="190a0-132">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="190a0-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="190a0-133">En Windows PowerShell ISE 2.0 esto se llamaba **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="190a0-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="190a0-134">La propiedad de solo lectura que obtiene el objeto [editor](../ise/The-ISEEditor-Object.md) del panel de consola.</span><span class="sxs-lookup"><span data-stu-id="190a0-134">The read-only property that gets the Console pane [editor](../ise/The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="190a0-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="190a0-135">DisplayName</span></span>

<span data-ttu-id="190a0-136">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="190a0-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="190a0-137">La propiedad de lectura y escritura que obtiene o establece el texto que se muestra en la pestaña de PowerShell. De forma predeterminada, las pestañas se denominan "PowerShell #", donde # representa un número.</span><span class="sxs-lookup"><span data-stu-id="190a0-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="190a0-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="190a0-138">ExpandedScript</span></span>

<span data-ttu-id="190a0-139">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="190a0-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="190a0-140">La propiedad booleana de lectura y escritura que determina si el panel de scripts se expande o se oculta.</span><span class="sxs-lookup"><span data-stu-id="190a0-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="190a0-141">Archivos</span><span class="sxs-lookup"><span data-stu-id="190a0-141">Files</span></span>

<span data-ttu-id="190a0-142">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="190a0-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="190a0-143">La propiedad de solo lectura que obtiene la [colección de archivos de scripts](../ise/The-ISEFileCollection-Object.md) que están abiertos en la pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="190a0-143">The read-only property that gets the [collection of script files](../ise/The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="190a0-144">Salida</span><span class="sxs-lookup"><span data-stu-id="190a0-144">Output</span></span>

<span data-ttu-id="190a0-145">Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.</span><span class="sxs-lookup"><span data-stu-id="190a0-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="190a0-146">En versiones posteriores de Windows PowerShell ISE, puede usar el objeto **ConsolePane** con el mismo propósito.</span><span class="sxs-lookup"><span data-stu-id="190a0-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="190a0-147">La propiedad de solo lectura que obtiene el panel de salida del [editor](../ise/The-ISEEditor-Object.md) actual .</span><span class="sxs-lookup"><span data-stu-id="190a0-147">The read-only property that gets the Output pane of the current [editor](../ise/The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="190a0-148">Prompt</span><span class="sxs-lookup"><span data-stu-id="190a0-148">Prompt</span></span>

<span data-ttu-id="190a0-149">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="190a0-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="190a0-150">La propiedad de solo lectura que obtiene el texto de la petición actual.</span><span class="sxs-lookup"><span data-stu-id="190a0-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="190a0-151">Nota: El perfil del usuario puede reemplazar a la función **Prompt**.</span><span class="sxs-lookup"><span data-stu-id="190a0-151">Note: the **Prompt** function can be overridden by the user'™s profile.</span></span> <span data-ttu-id="190a0-152">Si el resultado es distinto de una cadena simple, esta propiedad no devuelve nada.</span><span class="sxs-lookup"><span data-stu-id="190a0-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="190a0-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="190a0-153">ShowCommands</span></span>

<span data-ttu-id="190a0-154">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="190a0-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="190a0-155">La propiedad de lectura y escritura que indica si actualmente se muestra el panel de comandos.</span><span class="sxs-lookup"><span data-stu-id="190a0-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="190a0-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="190a0-156">StatusText</span></span>

<span data-ttu-id="190a0-157">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="190a0-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="190a0-158">La propiedad de solo lectura que obtiene el texto de estado de **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="190a0-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="190a0-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="190a0-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="190a0-160">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="190a0-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="190a0-161">La propiedad de solo lectura que indica si el panel de herramientas de complementos horizontal está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="190a0-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="190a0-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="190a0-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="190a0-163">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="190a0-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="190a0-164">La propiedad de solo lectura que indica si el panel de herramientas de complementos vertical está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="190a0-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="190a0-165">Véase también</span><span class="sxs-lookup"><span data-stu-id="190a0-165">See Also</span></span>

- [<span data-ttu-id="190a0-166">El objeto PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="190a0-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="190a0-167">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="190a0-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="190a0-168">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="190a0-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)