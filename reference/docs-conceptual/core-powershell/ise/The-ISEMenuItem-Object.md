---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: El objeto ISEMenuItem
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 5561955040e56110a6af0619c286548f5812fb47
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="ff151-103">El objeto ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="ff151-103">The ISEMenuItem Object</span></span>
  <span data-ttu-id="ff151-104">Un objeto **ISEMenuItem** es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="ff151-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="ff151-105">Todos los objetos de menú **Complementos** son instancias de la clase **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="ff151-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="ff151-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="ff151-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="ff151-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ff151-107">DisplayName</span></span>
  <span data-ttu-id="ff151-108">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="ff151-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff151-109">La propiedad de solo lectura que obtiene el nombre para mostrar del elemento de menú.</span><span class="sxs-lookup"><span data-stu-id="ff151-109">The read-only property that gets the display name of the menu item.</span></span>

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

### <a name="action"></a><span data-ttu-id="ff151-110">Acción</span><span class="sxs-lookup"><span data-stu-id="ff151-110">Action</span></span>
  <span data-ttu-id="ff151-111">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="ff151-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff151-112">La propiedad de solo lectura que obtiene el bloque del script.</span><span class="sxs-lookup"><span data-stu-id="ff151-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="ff151-113">Invoca la acción al hacer clic en el elemento de menú.</span><span class="sxs-lookup"><span data-stu-id="ff151-113">It invokes the action when you click the menu item.</span></span>

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="ff151-114">Directa</span><span class="sxs-lookup"><span data-stu-id="ff151-114">Shortcut</span></span>
  <span data-ttu-id="ff151-115">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="ff151-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff151-116">La propiedad de solo lectura que obtiene el método abreviado de teclado de entrada de Windows para el elemento de menú.</span><span class="sxs-lookup"><span data-stu-id="ff151-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="ff151-117">Submenus</span><span class="sxs-lookup"><span data-stu-id="ff151-117">Submenus</span></span>
  <span data-ttu-id="ff151-118">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="ff151-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff151-119">La propiedad de solo lectura que obtiene la [lista de submenús](The-ISEMenuItemCollection-Object.md) del elemento de menú.</span><span class="sxs-lookup"><span data-stu-id="ff151-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="ff151-120">Ejemplo de scripting</span><span class="sxs-lookup"><span data-stu-id="ff151-120">Scripting example</span></span>
 <span data-ttu-id="ff151-121">Para entender mejor el uso del menú de complementos y sus propiedades que admiten scripts, consulte el siguiente ejemplo de scripting.</span><span class="sxs-lookup"><span data-stu-id="ff151-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu - a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## <a name="see-also"></a><span data-ttu-id="ff151-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="ff151-122">See Also</span></span>
- [<span data-ttu-id="ff151-123">El objeto ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="ff151-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md) 
- [<span data-ttu-id="ff151-124">El modelo de objetos de scripting de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff151-124">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="ff151-125">Referencia del modelo de objetos de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff151-125">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="ff151-126">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="ff151-126">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
