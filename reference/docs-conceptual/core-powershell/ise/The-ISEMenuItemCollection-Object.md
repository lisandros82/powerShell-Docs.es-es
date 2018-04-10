---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: El objeto ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="c4ed4-103">El objeto ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="c4ed4-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="c4ed4-104">Un objeto **ISEMenuItemCollection** es una colección de objetos **ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="c4ed4-105">Es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="c4ed4-106">Un ejemplo es el objeto **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** que se usa para personalizar el menú **Complemento** en el Entorno de scripting integrado (ISE) de Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="c4ed4-107">Método</span><span class="sxs-lookup"><span data-stu-id="c4ed4-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="c4ed4-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut\)</span><span class="sxs-lookup"><span data-stu-id="c4ed4-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="c4ed4-109">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c4ed4-110">Agrega un elemento de menú a la colección.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="c4ed4-111">**DisplayName** El nombre para mostrar del menú que se va a agregar.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="c4ed4-112">**Action** El objeto **System.Management.Automation.ScriptBlock** que especifica la acción que está asociada con este elemento de menú.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="c4ed4-113">**Shortcut** El método abreviado de teclado para la acción.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="c4ed4-114">**Returns** El objeto ISEMenuItem que se acaba de agregar.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="c4ed4-115">Borrar\(\)</span><span class="sxs-lookup"><span data-stu-id="c4ed4-115">Clear\(\)</span></span>

<span data-ttu-id="c4ed4-116">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c4ed4-117">Quita todos los submenús del elemento de menú.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="c4ed4-118">Véase también</span><span class="sxs-lookup"><span data-stu-id="c4ed4-118">See Also</span></span>

- [<span data-ttu-id="c4ed4-119">El objeto ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="c4ed4-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="c4ed4-120">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c4ed4-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c4ed4-121">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="c4ed4-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)