---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: El objeto PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2017
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="7d998-103">El objeto PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="7d998-103">The PowerShellTabCollection Object</span></span>
  <span data-ttu-id="7d998-104">El objeto de colección **PowerShellTab** es una colección de objetos **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="7d998-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="7d998-105">Cada objeto **PowerShellTab** funciona como un entorno de runtime independiente.</span><span class="sxs-lookup"><span data-stu-id="7d998-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="7d998-106">Es una instancia de la clase Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="7d998-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="7d998-107">Un ejemplo es el objeto **$psISE.PowerShellTabs**.</span><span class="sxs-lookup"><span data-stu-id="7d998-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="7d998-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="7d998-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="7d998-109">Add\(\)</span><span class="sxs-lookup"><span data-stu-id="7d998-109">Add\(\)</span></span>
  <span data-ttu-id="7d998-110">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="7d998-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7d998-111">Agrega una nueva pestaña de PowerShell a la colección.</span><span class="sxs-lookup"><span data-stu-id="7d998-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="7d998-112">Devuelve la pestaña recién agregada.</span><span class="sxs-lookup"><span data-stu-id="7d998-112">It returns the newly added tab.</span></span>

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="7d998-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="7d998-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="7d998-114">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="7d998-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7d998-115">Quita la pestaña especificada por el parámetro **psTab**.</span><span class="sxs-lookup"><span data-stu-id="7d998-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

 <span data-ttu-id="7d998-116">**psTab** Pestaña de PowerShell que se quitará.</span><span class="sxs-lookup"><span data-stu-id="7d998-116">**psTab** The PowerShell tab to remove.</span></span>

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="7d998-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="7d998-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="7d998-118">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="7d998-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7d998-119">Selecciona la pestaña de PowerShell especificada por el parámetro **psTab** para que sea la pestaña activa de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d998-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

 <span data-ttu-id="7d998-120">**psTab** Pestaña de PowerShell que se seleccionará.</span><span class="sxs-lookup"><span data-stu-id="7d998-120">**psTab** The PowerShell tab to select.</span></span>

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a><span data-ttu-id="7d998-121">Véase también</span><span class="sxs-lookup"><span data-stu-id="7d998-121">See Also</span></span>
- [<span data-ttu-id="7d998-122">El objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="7d998-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="7d998-123">El modelo de objetos de scripting de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d998-123">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="7d998-124">Referencia del modelo de objetos de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d998-124">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="7d998-125">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="7d998-125">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
