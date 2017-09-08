---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "La jerarquía del modelo de objetos de ISE"
ms.assetid: bc3300e4-9c17-4f00-a621-c8867126e3b3
ms.openlocfilehash: b6e251eac7db56896490362392e0a1c4c10a8d4a
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2017
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="caf60-103">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="caf60-103">The ISE Object Model Hierarchy</span></span>
  <span data-ttu-id="caf60-104">En este tema se muestra la jerarquía de objetos que forman parte del Entorno de scripting integrado (ISE) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="caf60-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="caf60-105">Windows PowerShell ISE se incluye en Windows PowerShell 3.0 y Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="caf60-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span> <span data-ttu-id="caf60-106">Haga clic en un objeto para ir a la documentación de referencia de la clase que define el objeto.</span><span class="sxs-lookup"><span data-stu-id="caf60-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

##  <a name="psise-object"></a><span data-ttu-id="caf60-107">**$psISE Object**</span><span class="sxs-lookup"><span data-stu-id="caf60-107">**$psISE Object**</span></span>
 <span data-ttu-id="caf60-108">El objeto **$psISE** es el [objeto raíz](The-ObjectModelRoot-Object.md) de la jerarquía de objetos de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="caf60-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span> <span data-ttu-id="caf60-109">Ubicado en el nivel superior, este objeto hace que estén disponibles para scripting los objetos siguientes:</span><span class="sxs-lookup"><span data-stu-id="caf60-109">Located at the top level, it makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="caf60-110">**[$psISE.CurrentFile]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-110">**[$psISE.CurrentFile]()**</span></span>

-   <span data-ttu-id="caf60-111">**[$psISE.CurrentPowerShellTab]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-111">**[$psISE.CurrentPowerShellTab]()**</span></span>

-   <span data-ttu-id="caf60-112">**[$psISE.CurrentVisibleHorizontalTool]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-112">**[$psISE.CurrentVisibleHorizontalTool]()**</span></span>

-   <span data-ttu-id="caf60-113">**[$psISE.CurrentVisibleVerticalTool]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-113">**[$psISE.CurrentVisibleVerticalTool]()**</span></span>

-   <span data-ttu-id="caf60-114">**[$psISE.Options]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-114">**[$psISE.Options]()**</span></span>

-   <span data-ttu-id="caf60-115">**[$psISE.PowerShellTabs]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-115">**[$psISE.PowerShellTabs]()**</span></span>

##  <a name="psisecurrentfilethe-isefile-objectmd"></a><span data-ttu-id="caf60-116">**[$psISE.CurrentFile](The-ISEFile-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-116">**[$psISE.CurrentFile](The-ISEFile-Object.md)**</span></span>
 <span data-ttu-id="caf60-117">El objeto **$psISE.CurrentFile** es una instancia de la clase [ISEFile](The-ISEFile-Object.md) y hace que estén disponibles para scripting los objetos siguientes:</span><span class="sxs-lookup"><span data-stu-id="caf60-117">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="caf60-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md)**</span></span>

-   <span data-ttu-id="caf60-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)** Este objeto es una instancia de la clase  [ISEEditor](The-ISEEditor-Object.md) y hace que estén disponibles para scripting los objetos siguientes:</span><span class="sxs-lookup"><span data-stu-id="caf60-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="caf60-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="caf60-121">**[CaretColumn](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-121">**[CaretColumn](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="caf60-122">**[CaretLine](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-122">**[CaretLine](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="caf60-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="caf60-124">**[LineCount](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-124">**[LineCount](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="caf60-125">**[SelectedText](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-125">**[SelectedText](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="caf60-126">**[Text](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-126">**[Text](The-ISEEditor-Object.md)**</span></span>

-   <span data-ttu-id="caf60-127">**[EncodingThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-127">**[EncodingThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-128">**[FullPathThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-128">**[FullPathThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-129">**[IsSavedThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-129">**[IsSavedThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-130">**[IsUntitledThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-130">**[IsUntitledThe-ISEFile-Object.md]()**</span></span>

##  <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a><span data-ttu-id="caf60-131">**[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-131">**[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span></span>
 <span data-ttu-id="caf60-132">El objeto **$psISE.CurrentPowerShellTab** es una instancia de la clase [PowerShellTab](The-PowerShellTab-Object.md) y hace que estén disponibles para scripting los objetos siguientes:</span><span class="sxs-lookup"><span data-stu-id="caf60-132">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="caf60-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)** Este objeto es una instancia de la clase [ISEMenuItem](The-ISEMenuItem-Object.md) y hace que estén disponibles para scripting los objetos siguientes:</span><span class="sxs-lookup"><span data-stu-id="caf60-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**  This object is an instance of the [ISEMenuItem](The-ISEMenuItem-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="caf60-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ActionThe-ISEMenuItem-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ActionThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="caf60-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayNameThe-ISEMenuItem-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayNameThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="caf60-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ShortcutThe-ISEMenuItem-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ShortcutThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="caf60-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span></span>

-   <span data-ttu-id="caf60-138">**[$psISE.CurrentPowerShellTab.CanInvokeThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-138">**[$psISE.CurrentPowerShellTab.CanInvokeThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)** Este objeto es una instancia de la clase [ISEEditor](The-ISEEditor-Object.md) y hace que estén disponibles para scripting los objetos siguientes:</span><span class="sxs-lookup"><span data-stu-id="caf60-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="caf60-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatchThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatchThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="caf60-141">**[CaretColumnThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-141">**[CaretColumnThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="caf60-142">**[CaretLineThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-142">**[CaretLineThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="caf60-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineTextThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineTextThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="caf60-144">**[LineCountThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-144">**[LineCountThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="caf60-145">**[SelectedTextThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-145">**[SelectedTextThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="caf60-146">**[TextThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-146">**[TextThe-ISEEditor-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-147">**[$psISE.CurrentPowerShellTab.DisplayNameThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-147">**[$psISE.CurrentPowerShellTab.DisplayNameThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-148">**[$psISE.CurrentPowerShellTab.ExpandedScriptThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-148">**[$psISE.CurrentPowerShellTab.ExpandedScriptThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span></span>

-   <span data-ttu-id="caf60-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="caf60-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-152">**[$psISE.CurrentPowerShellTab.PromptThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-152">**[$psISE.CurrentPowerShellTab.PromptThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-153">**[$psISE.CurrentPowerShellTab.ShowCommandsThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-153">**[$psISE.CurrentPowerShellTab.ShowCommandsThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span></span>

-   <span data-ttu-id="caf60-155">**[$psISE.CurrentPowerShellTab.StatusTextThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-155">**[$psISE.CurrentPowerShellTab.StatusTextThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="caf60-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="caf60-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

##  <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="caf60-160">**$psISE.CurrentVisibleHorizontalTool**</span><span class="sxs-lookup"><span data-stu-id="caf60-160">**$psISE.CurrentVisibleHorizontalTool**</span></span>
 <span data-ttu-id="caf60-161">El objeto **$psISE.CurrentVisibleHorizontalTool** es una instancia de la clase [ISEAddOnTool](The-ISEAddOnTool-Object.md).</span><span class="sxs-lookup"><span data-stu-id="caf60-161">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="caf60-162">Representa la herramienta de complemento instalada que actualmente está acoplada al borde superior de la ventana de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="caf60-162">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="caf60-163">Este objeto hace que estén disponibles para scripting los objetos siguientes:</span><span class="sxs-lookup"><span data-stu-id="caf60-163">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="caf60-164">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-164">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-166">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-166">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span></span>

##  <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="caf60-167">**$psISE.CurrentVisibleVerticalTool**</span><span class="sxs-lookup"><span data-stu-id="caf60-167">**$psISE.CurrentVisibleVerticalTool**</span></span>
 <span data-ttu-id="caf60-168">El objeto **$psISE.CurrentVisibleHorizontalTool** es una instancia de la clase [ISEAddOnTool](The-ISEAddOnTool-Object.md).</span><span class="sxs-lookup"><span data-stu-id="caf60-168">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="caf60-169">Representa la herramienta de complemento instalada que actualmente está acoplada al borde derecho de la ventana de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="caf60-169">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="caf60-170">Este objeto hace que estén disponibles para scripting los objetos siguientes:</span><span class="sxs-lookup"><span data-stu-id="caf60-170">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="caf60-171">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-171">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-173">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-173">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span></span>

##  <a name="psiseoptions"></a><span data-ttu-id="caf60-174">**$psISE.Options**</span><span class="sxs-lookup"><span data-stu-id="caf60-174">**$psISE.Options**</span></span>
 <span data-ttu-id="caf60-175">El objeto **$psISE.Options** hace que estén disponibles para scripting los objetos siguientes:</span><span class="sxs-lookup"><span data-stu-id="caf60-175">The **$psISE.Options** object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="caf60-176">**[$psISE.Options.AutoSaveMinuteIntervalThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-176">**[$psISE.Options.AutoSaveMinuteIntervalThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-177">**[$psISE.Options.ConsolePaneBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-177">**[$psISE.Options.ConsolePaneBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-178">**[$psISE.Options.ConsolePaneTextForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-178">**[$psISE.Options.ConsolePaneTextForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-179">**[$psISE.Options.ConsolePaneTextBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-179">**[$psISE.Options.ConsolePaneTextBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-180">**[$psISE.Options.ConsoleTokenColorsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-180">**[$psISE.Options.ConsoleTokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-181">**[$psISE.Options.DebugBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-181">**[$psISE.Options.DebugBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-182">**[$psISE.Options.DebugForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-182">**[$psISE.Options.DebugForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span></span>

-   <span data-ttu-id="caf60-184">**[$psISE.Options.ErrorBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-184">**[$psISE.Options.ErrorBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-185">**[$psISE.Options.ErrorForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-185">**[$psISE.Options.ErrorForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-186">**[$psISE.Options.FontNameThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-186">**[$psISE.Options.FontNameThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-187">**[$psISE.Options.FontsizeThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-187">**[$psISE.Options.FontsizeThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-188">**[$psISE.Options.IntellisenseTimeoutInSecondsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-188">**[$psISE.Options.IntellisenseTimeoutInSecondsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-189">**[$psISE.Options.MRUCountThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-189">**[$psISE.Options.MRUCountThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-190">**[$psISE.Options.ScriptPaneBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-190">**[$psISE.Options.ScriptPaneBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-191">**[$psISE.Options.ScriptPaneForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-191">**[$psISE.Options.ScriptPaneForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-192">**[$psISE.Options.SelectedScriptPaneStateThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-192">**[$psISE.Options.SelectedScriptPaneStateThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-193">**[$psISE.Options.ShowDefaultSnippetsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-193">**[$psISE.Options.ShowDefaultSnippetsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-194">**[$psISE.Options.ShowIntellisenseInConsolePaneThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-194">**[$psISE.Options.ShowIntellisenseInConsolePaneThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-195">**[$psISE.Options.ShowIntellisenseInScriptPaneThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-195">**[$psISE.Options.ShowIntellisenseInScriptPaneThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-196">**[$psISE.Options.ShowLineNumbersThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-196">**[$psISE.Options.ShowLineNumbersThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-197">**[$psISE.Options.ShowOutliningThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-197">**[$psISE.Options.ShowOutliningThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-198">**[$psISE.Options.ShowToolBarThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-198">**[$psISE.Options.ShowToolBarThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-199">**[$psISE.Options.ShowWarningBeforeSavingOnRunThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-199">**[$psISE.Options.ShowWarningBeforeSavingOnRunThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-200">**[$psISE.Options.ShowWarningForDuplicateFilesThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-200">**[$psISE.Options.ShowWarningForDuplicateFilesThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-201">**[$psISE.Options.TokenColorsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-201">**[$psISE.Options.TokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisenseThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisenseThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-203">**[$psISE.Options. UseEnterToSelectScriptPaneIntellisenseThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-203">**[$psISE.Options. UseEnterToSelectScriptPaneIntellisenseThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-204">**[$psISE.Options.UseLocalHelpThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-204">**[$psISE.Options.UseLocalHelpThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-205">**[$psISE.Options.VerboseBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-205">**[$psISE.Options.VerboseBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-206">**[$psISE.Options.VerboseForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-206">**[$psISE.Options.VerboseForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-207">**[$psISE.Options.WarningBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-207">**[$psISE.Options.WarningBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-208">**[$psISE.Options.WarningForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-208">**[$psISE.Options.WarningForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-209">**[$psISE.Options.XmlTokenColorsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-209">**[$psISE.Options.XmlTokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="caf60-210">**[$psISE.Options.ZoomThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="caf60-210">**[$psISE.Options.ZoomThe-ISEOptions-Object.md]()**</span></span>

##  <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a><span data-ttu-id="caf60-211">**[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="caf60-211">**[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span></span>
 <span data-ttu-id="caf60-212">El objeto **$psISE.PowerShellTabs** es una instancia de la clase [PowerShellTabCollection](The-PowerShellTabCollection-Object.md).</span><span class="sxs-lookup"><span data-stu-id="caf60-212">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span> <span data-ttu-id="caf60-213">Es una colección de todas las pestañas de PowerShell abiertas actualmente que representan los entornos de ejecución de Windows PowerShell disponibles en el equipo local o en equipos remotos conectados.</span><span class="sxs-lookup"><span data-stu-id="caf60-213">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="caf60-214">Cada miembro de la colección es una instancia de la clase [PowerShellTab](The-PowerShellTab-Object.md).</span><span class="sxs-lookup"><span data-stu-id="caf60-214">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="caf60-215">Véase también</span><span class="sxs-lookup"><span data-stu-id="caf60-215">See Also</span></span>
- [<span data-ttu-id="caf60-216">El modelo de objetos de scripting de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="caf60-216">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="caf60-217">Referencia del modelo de objetos de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="caf60-217">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

