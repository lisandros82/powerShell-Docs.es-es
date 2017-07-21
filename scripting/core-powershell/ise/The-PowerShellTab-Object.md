---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: El objeto PowerShellTab
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: d4e9374202d352a30b3eb46bcf1e4e40dea49822
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="733fc-103">El objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="733fc-103">The PowerShellTab Object</span></span>
  <span data-ttu-id="733fc-104">El objeto **PowerShellTab** representa un entorno de runtime de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="733fc-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="733fc-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="733fc-105">Methods</span></span>

###  <span data-ttu-id="733fc-106"><a name="invoke"></a> Invoke\( Script \)</span><span class="sxs-lookup"><span data-stu-id="733fc-106"><a name="invoke"></a> Invoke\( Script \)</span></span>
  <span data-ttu-id="733fc-107">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="733fc-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="733fc-108">Ejecuta el script especificado en la pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="733fc-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="733fc-109">Este método solo funciona en otras pestañas de PowerShell, no en la pestaña de PowerShell desde la que se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="733fc-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="733fc-110">No devuelve ningún objeto o valor.</span><span class="sxs-lookup"><span data-stu-id="733fc-110">It does not return any object or value.</span></span> <span data-ttu-id="733fc-111">Si el código modifica cualquier variable, esos cambios se conservan en la pestaña en la que se invocó el comando.</span><span class="sxs-lookup"><span data-stu-id="733fc-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

 <span data-ttu-id="733fc-112">**Script**: System.Management.Automation.ScriptBlock o cadena. El bloque de script para ejecutar.</span><span class="sxs-lookup"><span data-stu-id="733fc-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psise.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="733fc-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="733fc-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>
  <span data-ttu-id="733fc-114">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="733fc-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="733fc-115">Ejecuta el script especificado en la pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="733fc-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="733fc-116">Este método solo funciona en otras pestañas de PowerShell, no en la pestaña de PowerShell desde la que se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="733fc-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="733fc-117">El bloque de script se ejecuta y cualquier valor que se devuelve desde el script se devuelve al entorno de ejecución desde el que se invocó el comando.</span><span class="sxs-lookup"><span data-stu-id="733fc-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="733fc-118">Si el comando tarda más tiempo en ejecutarse que lo que especifica el valor de **tiempoEsperaMilisegundos**, el comando no se ejecuta correctamente e inicia una excepción: "La operación ha agotado el tiempo de espera.".</span><span class="sxs-lookup"><span data-stu-id="733fc-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

 <span data-ttu-id="733fc-119">**Script**: System.Management.Automation.ScriptBlock o cadena. El bloque de script para ejecutar.</span><span class="sxs-lookup"><span data-stu-id="733fc-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

 <span data-ttu-id="733fc-120">**\[useNewScope\]**: booleano opcional cuyo valor predeterminado es **$true**
. Si está establecido en **$true**, se crea un nuevo ámbito en el que ejecutar el comando.</span><span class="sxs-lookup"><span data-stu-id="733fc-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true**
 If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="733fc-121">No modifica el entorno de tiempo de ejecución de la pestaña de PowerShell que se especifica mediante el comando.</span><span class="sxs-lookup"><span data-stu-id="733fc-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

 <span data-ttu-id="733fc-122">**\[millisecondsTimeout\]**: entero opcional cuyo valor predeterminado es **500**.</span><span class="sxs-lookup"><span data-stu-id="733fc-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="733fc-123">Si el comando no finaliza dentro del tiempo especificado, inicia **TimeoutException** con el mensaje "La operación ha agotado el tiempo de espera.".</span><span class="sxs-lookup"><span data-stu-id="733fc-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

```
# create a new PowerShell tab and then switch back to the first
$PSise.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0]) 

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1',$false)
# You can switch to the other tab and type “$x” to see that the value is saved there.

# This example sets a value in the other tab (in a different scope) 
# and returns it through the pipeline to this tab to store in $a
$a=$psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z') 
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
measure-command {$psISE.PowerShellTabs[1].InvokeSynchronous("sleep 10",$false,5000)}

```

## <a name="properties"></a><span data-ttu-id="733fc-124">Propiedades</span><span class="sxs-lookup"><span data-stu-id="733fc-124">Properties</span></span>

###  <span data-ttu-id="733fc-125"><a name="AddOnsMenu"></a> AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="733fc-125"><a name="AddOnsMenu"></a> AddOnsMenu</span></span>
  <span data-ttu-id="733fc-126">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="733fc-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="733fc-127">La propiedad de solo lectura que obtiene el menú Complementos para la pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="733fc-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

```
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

###  <span data-ttu-id="733fc-128"><a name="CanExecute"></a> CanInvoke</span><span class="sxs-lookup"><span data-stu-id="733fc-128"><a name="CanExecute"></a> CanInvoke</span></span>
  <span data-ttu-id="733fc-129">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="733fc-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="733fc-130">La propiedad booleana de solo lectura que devuelve un valor **$true** si se puede invocar un script con el método [Invoke( Script )](#invoke).</span><span class="sxs-lookup"><span data-stu-id="733fc-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke) method.</span></span>

```
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab. 
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psise.PowerShellTabs[1] 
$secondTab.CanInvoke 
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke

```

###  <span data-ttu-id="733fc-131"><a name="Commandpane"></a> Consolepane</span><span class="sxs-lookup"><span data-stu-id="733fc-131"><a name="Commandpane"></a> Consolepane</span></span>
  <span data-ttu-id="733fc-132">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="733fc-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="733fc-133">En Windows PowerShell ISE 2.0 esto se llamaba **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="733fc-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

 <span data-ttu-id="733fc-134">La propiedad de solo lectura que obtiene el objeto [editor](../ise/The-ISEEditor-Object.md) del panel de consola.</span><span class="sxs-lookup"><span data-stu-id="733fc-134">The read-only property that gets the Console pane [editor](../ise/The-ISEEditor-Object.md) object.</span></span>

```
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane

```

###  <span data-ttu-id="733fc-135"><a name="Displayname"></a> DisplayName</span><span class="sxs-lookup"><span data-stu-id="733fc-135"><a name="Displayname"></a> DisplayName</span></span>
  <span data-ttu-id="733fc-136">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="733fc-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="733fc-137">La propiedad de lectura y escritura que obtiene o establece el texto que se muestra en la pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="733fc-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab.</span></span> <span data-ttu-id="733fc-138">De forma predeterminada, las pestañas se denominan "PowerShell #", donde # representa un número.</span><span class="sxs-lookup"><span data-stu-id="733fc-138">By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```
$newTab = $psise.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

###  <span data-ttu-id="733fc-139"><a name="ExpandedScript"></a> ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="733fc-139"><a name="ExpandedScript"></a> ExpandedScript</span></span>
  <span data-ttu-id="733fc-140">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="733fc-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="733fc-141">La propiedad booleana de lectura y escritura que determina si el panel de scripts se expande o se oculta.</span><span class="sxs-lookup"><span data-stu-id="733fc-141">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```
# Toggle the expanded script property to see its effect.
$PSise.CurrentPowerShellTab.ExpandedScript=!$PSise.CurrentPowerShellTab.ExpandedScript

```

###  <span data-ttu-id="733fc-142"><a name="Files"></a> Files</span><span class="sxs-lookup"><span data-stu-id="733fc-142"><a name="Files"></a> Files</span></span>
  <span data-ttu-id="733fc-143">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="733fc-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="733fc-144">La propiedad de solo lectura que obtiene la [colección de archivos de scripts](../ise/The-ISEFileCollection-Object.md) que están abiertos en la pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="733fc-144">The read-only property that gets the [collection of script files](../ise/The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb" 
# Gets the line count
$newFile.Editor.LineCount
```

###  <span data-ttu-id="733fc-145"><a name="Output"></a> Output</span><span class="sxs-lookup"><span data-stu-id="733fc-145"><a name="Output"></a> Output</span></span>
  <span data-ttu-id="733fc-146">Esta característica está presente en Windows PowerShell ISE 2.0, pero se quitó o se cambió de nombre en versiones posteriores del ISE.</span><span class="sxs-lookup"><span data-stu-id="733fc-146">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="733fc-147">En versiones posteriores de Windows PowerShell ISE, puede usar el objeto **ConsolePane** con el mismo propósito.</span><span class="sxs-lookup"><span data-stu-id="733fc-147">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

 <span data-ttu-id="733fc-148">La propiedad de solo lectura que obtiene el panel de salida del [editor](../ise/The-ISEEditor-Object.md) actual .</span><span class="sxs-lookup"><span data-stu-id="733fc-148">The read-only property that gets the Output pane of the current [editor](../ise/The-ISEEditor-Object.md).</span></span>

```
# Clears the text in the Output pane.
$psise.CurrentPowerShellTab.output.clear()
```

###  <span data-ttu-id="733fc-149"><a name="Prompt"></a> Prompt</span><span class="sxs-lookup"><span data-stu-id="733fc-149"><a name="Prompt"></a> Prompt</span></span>
  <span data-ttu-id="733fc-150">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="733fc-150">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="733fc-151">La propiedad de solo lectura que obtiene el texto de la petición actual.</span><span class="sxs-lookup"><span data-stu-id="733fc-151">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="733fc-152">Nota: El perfil del usuario puede reemplazar a la función **Prompt**.</span><span class="sxs-lookup"><span data-stu-id="733fc-152">Note: the **Prompt** function can be overridden by the user’s profile.</span></span> <span data-ttu-id="733fc-153">Si el resultado es distinto de una cadena simple, esta propiedad no devuelve nada.</span><span class="sxs-lookup"><span data-stu-id="733fc-153">If the result is other than a simple string, then this property returns nothing.</span></span>

```
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

###  <span data-ttu-id="733fc-154"><a name="ShowCommands"></a> ShowCommands</span><span class="sxs-lookup"><span data-stu-id="733fc-154"><a name="ShowCommands"></a> ShowCommands</span></span>
  <span data-ttu-id="733fc-155">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="733fc-155">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="733fc-156">La propiedad de lectura y escritura que indica si actualmente se muestra el panel de comandos.</span><span class="sxs-lookup"><span data-stu-id="733fc-156">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $True
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands=$True}
```

###  <span data-ttu-id="733fc-157"><a name="StatusText"></a> StatusText</span><span class="sxs-lookup"><span data-stu-id="733fc-157"><a name="StatusText"></a> StatusText</span></span>
  <span data-ttu-id="733fc-158">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="733fc-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="733fc-159">La propiedad de solo lectura que obtiene el texto de estado de **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="733fc-159">The read-only property that gets the **PowerShellTab** status text.</span></span>

```
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

###  <span data-ttu-id="733fc-160"><a name="HorizontalAddOnToolsPaneOpened"></a> HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="733fc-160"><a name="HorizontalAddOnToolsPaneOpened"></a> HorizontalAddOnToolsPaneOpened</span></span>
  <span data-ttu-id="733fc-161">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="733fc-161">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="733fc-162">La propiedad de solo lectura que indica si el panel de herramientas de complementos horizontal está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="733fc-162">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```
# Gets the current state of the horizontal Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

###  <span data-ttu-id="733fc-163"><a name="VerticalAddOnToolsPaneOpened"></a> **VerticalAddOnToolsPaneOpened**</span><span class="sxs-lookup"><span data-stu-id="733fc-163"><a name="VerticalAddOnToolsPaneOpened"></a> **VerticalAddOnToolsPaneOpened**</span></span>
  <span data-ttu-id="733fc-164">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="733fc-164">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="733fc-165">La propiedad de solo lectura que indica si el panel de herramientas de complementos vertical está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="733fc-165">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands=$True
# Gets the current state of the vertical Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="733fc-166">Véase también</span><span class="sxs-lookup"><span data-stu-id="733fc-166">See Also</span></span>
- [<span data-ttu-id="733fc-167">El objeto PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="733fc-167">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md) 
- [<span data-ttu-id="733fc-168">El modelo de objetos de scripting de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="733fc-168">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="733fc-169">Referencia del modelo de objetos de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="733fc-169">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="733fc-170">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="733fc-170">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
