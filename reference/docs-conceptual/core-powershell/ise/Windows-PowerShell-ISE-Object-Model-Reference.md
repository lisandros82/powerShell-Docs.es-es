---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Referencia del modelo de objetos de ISE de Windows PowerShell
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: 624ddca3895ba3e24bf52a27babdb07e8714baae
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="windows-powershell-ise-object-model-reference"></a><span data-ttu-id="823dd-103">Referencia del modelo de objetos de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="823dd-103">Windows PowerShell ISE Object Model Reference</span></span>
  
## <a name="object-model-reference"></a><span data-ttu-id="823dd-104">Referencia del modelo de objetos</span><span class="sxs-lookup"><span data-stu-id="823dd-104">Object Model Reference</span></span>
 <span data-ttu-id="823dd-105">En esta sección, se proporciona una referencia sobre las clases subyacentes que definen los diversos objetos en Entorno de scripting integrado (ISE) de Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="823dd-105">This section provides a reference on the underlying classes that define the various objects inWindows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="823dd-106">Para ver los objetos organizados en la jerarquía, consulte [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="823dd-106">To see the objects organized in their hierarchy, see [The ISE Object Model Hierarchy](The-ISE-Object-Model-Hierarchy.md).</span></span>

 <span data-ttu-id="823dd-107">[El objeto ISEAddOnTool](The-ISEAddOnTool-Object.md) Ejemplos: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span><span class="sxs-lookup"><span data-stu-id="823dd-107">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md) Examples: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span></span>

 <span data-ttu-id="823dd-108">[El objeto ISEAddOnTool](The-ISEAddOnTool-Object.md) [El objeto ISEEditor](The-ISEEditor-Object.md) Ejemplos: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span><span class="sxs-lookup"><span data-stu-id="823dd-108">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md) [The ISEEditor Object](The-ISEEditor-Object.md) Examples: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span></span>

 <span data-ttu-id="823dd-109">[El objeto ISEFile](The-ISEFile-Object.md) Ejemplos: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span><span class="sxs-lookup"><span data-stu-id="823dd-109">[The ISEFile Object](The-ISEFile-Object.md) Examples: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span></span>

 <span data-ttu-id="823dd-110">[El objeto ISEFileCollection](The-ISEFileCollection-Object.md) Ejemplos: $psISE.PowerShellTabs.Files.</span><span class="sxs-lookup"><span data-stu-id="823dd-110">[The ISEFileCollection Object](The-ISEFileCollection-Object.md) Examples: $psISE.PowerShellTabs.Files.</span></span>

 <span data-ttu-id="823dd-111">[El objeto ISEMenuItem](The-ISEMenuItem-Object.md) Ejemplos: $psISE.CurrentPowerShellTab.AddOnsMenu, $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span><span class="sxs-lookup"><span data-stu-id="823dd-111">[The ISEMenuItem Object](The-ISEMenuItem-Object.md) Examples: $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span></span>

 <span data-ttu-id="823dd-112">[El objeto ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md) Ejemplo: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span><span class="sxs-lookup"><span data-stu-id="823dd-112">[The ISEMenuItemCollection Object](The-ISEMenuItemCollection-Object.md) Example: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span></span>

 <span data-ttu-id="823dd-113">[El objeto ISEOptions](The-ISEOptions-Object.md) Ejemplos: $psISE.Options, $psISE.Options.DefaultOptions.</span><span class="sxs-lookup"><span data-stu-id="823dd-113">[The ISEOptions Object](The-ISEOptions-Object.md) Examples: $psISE.Options, $psISE.Options.DefaultOptions.</span></span>

 <span data-ttu-id="823dd-114">[El objeto ObjectModelRoot](The-ObjectModelRoot-Object.md) Ejemplo: el objeto raíz $psISE.</span><span class="sxs-lookup"><span data-stu-id="823dd-114">[The ObjectModelRoot Object](The-ObjectModelRoot-Object.md) Example: The root $psISE object.</span></span>

 <span data-ttu-id="823dd-115">[El objeto PowerShellTab](The-PowerShellTab-Object.md) Ejemplos: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span><span class="sxs-lookup"><span data-stu-id="823dd-115">[The PowerShellTab Object](The-PowerShellTab-Object.md) Examples: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span></span>

 <span data-ttu-id="823dd-116">[El objeto PowerShellTabCollection](The-PowerShellTabCollection-Object.md) Ejemplo: $psISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="823dd-116">[The PowerShellTabCollection Object](The-PowerShellTabCollection-Object.md) Example: $psISE.PowerShellTabs.</span></span>

## <a name="see-also"></a><span data-ttu-id="823dd-117">Véase también</span><span class="sxs-lookup"><span data-stu-id="823dd-117">See Also</span></span>
- [<span data-ttu-id="823dd-118">El modelo de objetos de scripting de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="823dd-118">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
