---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: El objeto PowerShellTabCollection
ms.openlocfilehash: 0aad885afd3ba3ae3b00f5c11d2c62a9ff303798
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736120"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="5f575-103">El objeto PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="5f575-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="5f575-104">El objeto de colección **PowerShellTab** es una colección de objetos **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="5f575-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="5f575-105">Cada objeto **PowerShellTab** funciona como un entorno de runtime independiente.</span><span class="sxs-lookup"><span data-stu-id="5f575-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="5f575-106">Es una instancia de la clase Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="5f575-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="5f575-107">Un ejemplo es el objeto `$psISE.PowerShellTabs`.</span><span class="sxs-lookup"><span data-stu-id="5f575-107">An example is the `$psISE.PowerShellTabs` object.</span></span>

## <a name="methods"></a><span data-ttu-id="5f575-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="5f575-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="5f575-109">Add\(\)</span><span class="sxs-lookup"><span data-stu-id="5f575-109">Add\(\)</span></span>

<span data-ttu-id="5f575-110">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="5f575-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="5f575-111">Agrega una nueva pestaña de PowerShell a la colección.</span><span class="sxs-lookup"><span data-stu-id="5f575-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="5f575-112">Devuelve la pestaña recién agregada.</span><span class="sxs-lookup"><span data-stu-id="5f575-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="5f575-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="5f575-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="5f575-114">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="5f575-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="5f575-115">Quita la pestaña especificada por el parámetro **psTab**.</span><span class="sxs-lookup"><span data-stu-id="5f575-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="5f575-116">**psTab** Pestaña de PowerShell que se quitará.</span><span class="sxs-lookup"><span data-stu-id="5f575-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="5f575-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="5f575-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="5f575-118">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="5f575-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="5f575-119">Selecciona la pestaña de PowerShell especificada por el parámetro **psTab** para que sea la pestaña activa de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f575-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="5f575-120">**psTab** Pestaña de PowerShell que se seleccionará.</span><span class="sxs-lookup"><span data-stu-id="5f575-120">**psTab** The PowerShell tab to select.</span></span>

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a><span data-ttu-id="5f575-121">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5f575-121">See Also</span></span>

- [<span data-ttu-id="5f575-122">El objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="5f575-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="5f575-123">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="5f575-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="5f575-124">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="5f575-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
