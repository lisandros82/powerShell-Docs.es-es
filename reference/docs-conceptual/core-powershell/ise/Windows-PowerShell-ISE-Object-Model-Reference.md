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
# <a name="windows-powershell-ise-object-model-reference"></a>Referencia del modelo de objetos de ISE de Windows PowerShell
  
## <a name="object-model-reference"></a>Referencia del modelo de objetos
 En esta sección, se proporciona una referencia sobre las clases subyacentes que definen los diversos objetos en Entorno de scripting integrado (ISE) de Windows PowerShell®. Para ver los objetos organizados en la jerarquía, consulte [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md).

 [El objeto ISEAddOnTool](The-ISEAddOnTool-Object.md) Ejemplos: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.

 [El objeto ISEAddOnTool](The-ISEAddOnTool-Object.md) [El objeto ISEEditor](The-ISEEditor-Object.md) Ejemplos: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.

 [El objeto ISEFile](The-ISEFile-Object.md) Ejemplos: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].

 [El objeto ISEFileCollection](The-ISEFileCollection-Object.md) Ejemplos: $psISE.PowerShellTabs.Files.

 [El objeto ISEMenuItem](The-ISEMenuItem-Object.md) Ejemplos: $psISE.CurrentPowerShellTab.AddOnsMenu, $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].

 [El objeto ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md) Ejemplo: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.

 [El objeto ISEOptions](The-ISEOptions-Object.md) Ejemplos: $psISE.Options, $psISE.Options.DefaultOptions.

 [El objeto ObjectModelRoot](The-ObjectModelRoot-Object.md) Ejemplo: el objeto raíz $psISE.

 [El objeto PowerShellTab](The-PowerShellTab-Object.md) Ejemplos: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].

 [El objeto PowerShellTabCollection](The-PowerShellTabCollection-Object.md) Ejemplo: $psISE.PowerShellTabs.

## <a name="see-also"></a>Véase también
- [El modelo de objetos de scripting de ISE de Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
