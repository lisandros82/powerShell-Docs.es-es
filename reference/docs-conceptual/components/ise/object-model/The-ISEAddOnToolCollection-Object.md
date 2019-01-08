---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: El objeto ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ff4f19d1a85a592f2f4f09c62caa0971751bdff7
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403137"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="dc617-103">El objeto ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="dc617-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="dc617-104">El objeto **ISEAddOnToolCollection** es una colección de objetos **ISEAddOnTool**.</span><span class="sxs-lookup"><span data-stu-id="dc617-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="dc617-105">Un ejemplo es el objeto **$psISE.CurrentPowerShellTab.VerticalAddOnTools**.</span><span class="sxs-lookup"><span data-stu-id="dc617-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="dc617-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="dc617-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="dc617-107">Add\( Name, ControlType, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="dc617-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="dc617-108">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="dc617-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="dc617-109">Agrega una nueva herramienta de complemento a la colección.</span><span class="sxs-lookup"><span data-stu-id="dc617-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="dc617-110">Devuelve la herramienta de complemento recién agregada.</span><span class="sxs-lookup"><span data-stu-id="dc617-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="dc617-111">Antes de ejecutar este comando, debe instalar la herramienta de complemento en el equipo local y cargar el ensamblado.</span><span class="sxs-lookup"><span data-stu-id="dc617-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="dc617-112">**Name** (cadena). Especifica el nombre para mostrar de la herramienta de complemento que se agrega a Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="dc617-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="dc617-113">**ControlType** (tipo). Especifica el control que se agrega.</span><span class="sxs-lookup"><span data-stu-id="dc617-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="dc617-114">**\[IsVisible\]** (booleano opcional). Si se establece en **$true**, la herramienta de complemento está visible inmediatamente en el panel de herramientas asociado.</span><span class="sxs-lookup"><span data-stu-id="dc617-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="dc617-115">Remove\( Item \)</span><span class="sxs-lookup"><span data-stu-id="dc617-115">Remove\( Item \)</span></span>

<span data-ttu-id="dc617-116">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="dc617-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="dc617-117">Quita de la colección la herramienta de complemento especificada.</span><span class="sxs-lookup"><span data-stu-id="dc617-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="dc617-118">**Item** (Microsoft.PowerShell.Host.ISE.ISEAddOnTool). Especifica el objeto que se quitará de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="dc617-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="dc617-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="dc617-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="dc617-120">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="dc617-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="dc617-121">Selecciona la pestaña de PowerShell que el parámetro **psTab** especifica.</span><span class="sxs-lookup"><span data-stu-id="dc617-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="dc617-122">**psTab** (Microsoft.PowerShell.Host.ISE.PowerShellTab). La pestaña de PowerShell que se seleccionará.</span><span class="sxs-lookup"><span data-stu-id="dc617-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="dc617-123">Remove\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="dc617-123">Remove\( psTab \)</span></span>

<span data-ttu-id="dc617-124">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="dc617-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="dc617-125">Quita la pestaña de PowerShell que el parámetro **psTab** especifica.</span><span class="sxs-lookup"><span data-stu-id="dc617-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="dc617-126">**psTab** (Microsoft.PowerShell.Host.ISE.PowerShellTab). La pestaña de PowerShell que se quitará.</span><span class="sxs-lookup"><span data-stu-id="dc617-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="dc617-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="dc617-127">See Also</span></span>

- [<span data-ttu-id="dc617-128">El objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="dc617-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="dc617-129">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="dc617-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="dc617-130">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="dc617-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)