---
ms.date: 12/31/2019
keywords: powershell, cmdlet
title: El objeto ISEMenuItem
ms.openlocfilehash: c3ffe6e8f0b28987543fe0a873c552292dc5158a
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736988"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="22d49-103">El objeto ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="22d49-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="22d49-104">Un objeto **ISEMenuItem** es una instancia de la clase **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="22d49-104">An **ISEMenuItem** object is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>
<span data-ttu-id="22d49-105">Todos los objetos de menú **Complementos** son instancias de la clase **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="22d49-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="22d49-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="22d49-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="22d49-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="22d49-107">DisplayName</span></span>

<span data-ttu-id="22d49-108">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="22d49-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="22d49-109">La propiedad de solo lectura que obtiene el nombre para mostrar del elemento de menú.</span><span class="sxs-lookup"><span data-stu-id="22d49-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="22d49-110">Acción</span><span class="sxs-lookup"><span data-stu-id="22d49-110">Action</span></span>

<span data-ttu-id="22d49-111">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="22d49-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="22d49-112">La propiedad de solo lectura que obtiene el bloque del script.</span><span class="sxs-lookup"><span data-stu-id="22d49-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="22d49-113">Invoca la acción al hacer clic en el elemento de menú.</span><span class="sxs-lookup"><span data-stu-id="22d49-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="22d49-114">Método abreviado</span><span class="sxs-lookup"><span data-stu-id="22d49-114">Shortcut</span></span>

<span data-ttu-id="22d49-115">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="22d49-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="22d49-116">La propiedad de solo lectura que obtiene el método abreviado de teclado de entrada de Windows para el elemento de menú.</span><span class="sxs-lookup"><span data-stu-id="22d49-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="22d49-117">Submenus</span><span class="sxs-lookup"><span data-stu-id="22d49-117">Submenus</span></span>

<span data-ttu-id="22d49-118">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="22d49-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="22d49-119">La propiedad de solo lectura que obtiene la [lista de submenús](The-ISEMenuItemCollection-Object.md) del elemento de menú.</span><span class="sxs-lookup"><span data-stu-id="22d49-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="22d49-120">Ejemplo de scripting</span><span class="sxs-lookup"><span data-stu-id="22d49-120">Scripting example</span></span>

<span data-ttu-id="22d49-121">Para entender mejor el uso del menú de complementos y sus propiedades que admiten scripts, consulte el siguiente ejemplo de scripting.</span><span class="sxs-lookup"><span data-stu-id="22d49-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a><span data-ttu-id="22d49-122">Consulte también</span><span class="sxs-lookup"><span data-stu-id="22d49-122">See Also</span></span>

- [<span data-ttu-id="22d49-123">El objeto ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="22d49-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="22d49-124">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="22d49-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="22d49-125">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="22d49-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
