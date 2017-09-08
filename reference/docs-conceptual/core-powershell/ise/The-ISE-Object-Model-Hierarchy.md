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
# <a name="the-ise-object-model-hierarchy"></a>La jerarquía del modelo de objetos de ISE
  En este tema se muestra la jerarquía de objetos que forman parte del Entorno de scripting integrado (ISE) de Windows PowerShell. Windows PowerShell ISE se incluye en Windows PowerShell 3.0 y Windows PowerShell 4.0. Haga clic en un objeto para ir a la documentación de referencia de la clase que define el objeto.

##  <a name="psise-object"></a>**$psISE Object**
 El objeto **$psISE** es el [objeto raíz](The-ObjectModelRoot-Object.md) de la jerarquía de objetos de Windows PowerShell ISE. Ubicado en el nivel superior, este objeto hace que estén disponibles para scripting los objetos siguientes:

-   **[$psISE.CurrentFile]()**

-   **[$psISE.CurrentPowerShellTab]()**

-   **[$psISE.CurrentVisibleHorizontalTool]()**

-   **[$psISE.CurrentVisibleVerticalTool]()**

-   **[$psISE.Options]()**

-   **[$psISE.PowerShellTabs]()**

##  <a name="psisecurrentfilethe-isefile-objectmd"></a>**[$psISE.CurrentFile](The-ISEFile-Object.md)**
 El objeto **$psISE.CurrentFile** es una instancia de la clase [ISEFile](The-ISEFile-Object.md) y hace que estén disponibles para scripting los objetos siguientes:

-   **[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md)**

-   **[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)** Este objeto es una instancia de la clase  [ISEEditor](The-ISEEditor-Object.md) y hace que estén disponibles para scripting los objetos siguientes:

    -   **[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md)**

    -   **[CaretColumn](The-ISEEditor-Object.md)**

    -   **[CaretLine](The-ISEEditor-Object.md)**

    -   **[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md)**

    -   **[LineCount](The-ISEEditor-Object.md)**

    -   **[SelectedText](The-ISEEditor-Object.md)**

    -   **[Text](The-ISEEditor-Object.md)**

-   **[EncodingThe-ISEFile-Object.md]()**

-   **[FullPathThe-ISEFile-Object.md]()**

-   **[IsSavedThe-ISEFile-Object.md]()**

-   **[IsUntitledThe-ISEFile-Object.md]()**

##  <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>**[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**
 El objeto **$psISE.CurrentPowerShellTab** es una instancia de la clase [PowerShellTab](The-PowerShellTab-Object.md) y hace que estén disponibles para scripting los objetos siguientes:

-   **[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)** Este objeto es una instancia de la clase [ISEMenuItem](The-ISEMenuItem-Object.md) y hace que estén disponibles para scripting los objetos siguientes:

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.ActionThe-ISEMenuItem-Object.md]()**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayNameThe-ISEMenuItem-Object.md]()**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.ShortcutThe-ISEMenuItem-Object.md]()**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.CanInvokeThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)** Este objeto es una instancia de la clase [ISEEditor](The-ISEEditor-Object.md) y hace que estén disponibles para scripting los objetos siguientes:

    -   **[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatchThe-ISEEditor-Object.md]()**

    -   **[CaretColumnThe-ISEEditor-Object.md]()**

    -   **[CaretLineThe-ISEEditor-Object.md]()**

    -   **[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineTextThe-ISEEditor-Object.md]()**

    -   **[LineCountThe-ISEEditor-Object.md]()**

    -   **[SelectedTextThe-ISEEditor-Object.md]()**

    -   **[TextThe-ISEEditor-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.DisplayNameThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.ExpandedScriptThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.PromptThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.ShowCommandsThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.StatusTextThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

##  <a name="psisecurrentvisiblehorizontaltool"></a>**$psISE.CurrentVisibleHorizontalTool**
 El objeto **$psISE.CurrentVisibleHorizontalTool** es una instancia de la clase [ISEAddOnTool](The-ISEAddOnTool-Object.md). Representa la herramienta de complemento instalada que actualmente está acoplada al borde superior de la ventana de Windows PowerShell ISE. Este objeto hace que estén disponibles para scripting los objetos siguientes:

-   **[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**

-   **[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**

-   **[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**

##  <a name="psisecurrentvisibleverticaltool"></a>**$psISE.CurrentVisibleVerticalTool**
 El objeto **$psISE.CurrentVisibleHorizontalTool** es una instancia de la clase [ISEAddOnTool](The-ISEAddOnTool-Object.md). Representa la herramienta de complemento instalada que actualmente está acoplada al borde derecho de la ventana de Windows PowerShell ISE. Este objeto hace que estén disponibles para scripting los objetos siguientes:

-   **[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**

-   **[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**

-   **[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**

##  <a name="psiseoptions"></a>**$psISE.Options**
 El objeto **$psISE.Options** hace que estén disponibles para scripting los objetos siguientes:

-   **[$psISE.Options.AutoSaveMinuteIntervalThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ConsolePaneBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ConsolePaneTextForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ConsolePaneTextBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ConsoleTokenColorsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.DebugBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.DebugForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**

-   **[$psISE.Options.ErrorBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ErrorForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.FontNameThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.FontsizeThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.IntellisenseTimeoutInSecondsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.MRUCountThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ScriptPaneBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ScriptPaneForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.SelectedScriptPaneStateThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowDefaultSnippetsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowIntellisenseInConsolePaneThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowIntellisenseInScriptPaneThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowLineNumbersThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowOutliningThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowToolBarThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowWarningBeforeSavingOnRunThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowWarningForDuplicateFilesThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.TokenColorsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.UseEnterToSelectConsolePaneIntellisenseThe-ISEOptions-Object.md]()**

-   **[$psISE.Options. UseEnterToSelectScriptPaneIntellisenseThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.UseLocalHelpThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.VerboseBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.VerboseForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.WarningBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.WarningForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.XmlTokenColorsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ZoomThe-ISEOptions-Object.md]()**

##  <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>**[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**
 El objeto **$psISE.PowerShellTabs** es una instancia de la clase [PowerShellTabCollection](The-PowerShellTabCollection-Object.md). Es una colección de todas las pestañas de PowerShell abiertas actualmente que representan los entornos de ejecución de Windows PowerShell disponibles en el equipo local o en equipos remotos conectados. Cada miembro de la colección es una instancia de la clase [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="see-also"></a>Véase también
- [El modelo de objetos de scripting de ISE de Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Referencia del modelo de objetos de ISE de Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md)

