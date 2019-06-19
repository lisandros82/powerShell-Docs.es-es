---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: El objeto PowerShellTabCollection
ms.openlocfilehash: 5a1318534ddce19c2f5faa0d2013e2b38d8b79e5
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030490"
---
# <a name="the-powershelltabcollection-object"></a>El objeto PowerShellTabCollection

El objeto de colección **PowerShellTab** es una colección de objetos **PowerShellTab**. Cada objeto **PowerShellTab** funciona como un entorno de runtime independiente. Es una instancia de la clase Microsoft.PowerShell.Host.ISE.PowerShellTabs. Un ejemplo es el objeto **$psISE.PowerShellTabs**.

## <a name="methods"></a>Métodos

### <a name="add"></a>Add\(\)

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

Agrega una nueva pestaña de PowerShell a la colección. Devuelve la pestaña recién agregada.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

Quita la pestaña especificada por el parámetro **psTab**.

**psTab** Pestaña de PowerShell que se quitará.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

Selecciona la pestaña de PowerShell especificada por el parámetro **psTab** para que sea la pestaña activa de PowerShell.

**psTab** Pestaña de PowerShell que se seleccionará.

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

## <a name="see-also"></a>Véase también

- [El objeto PowerShellTab](The-PowerShellTab-Object.md)
- [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)
