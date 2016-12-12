---
title: El objeto PowerShellTabCollection
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: 79edc4e41522b187cd6421be0bd897663b42bb44
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="the-powershelltabcollection-object"></a>El objeto PowerShellTabCollection
  El objeto de colección **PowerShellTab** es una colección de objetos **PowerShellTab**. Cada objeto **PowerShellTab** funciona como un entorno de runtime independiente. Es una instancia de la clase Microsoft.PowerShell.Host.ISE.PowerShellTabs. Un ejemplo es el objeto **$psISE.PowerShellTabs**.

## <a name="methods"></a>Métodos

### <a name="add"></a>Add\(\)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Agrega una nueva pestaña de PowerShell a la colección. Devuelve la pestaña recién agregada.

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Quita la pestaña especificada por el parámetro **psTab**.

 **psTab**
 Pestaña de PowerShell que se quitará.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Selecciona la pestaña de PowerShell especificada por el parámetro **psTab** para que sea la pestaña activa de PowerShell.

 **psTab**
 Pestaña de PowerShell que se seleccionará.

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

## <a name="see-also"></a>Véase también
- [El objeto PowerShellTab](The-PowerShellTab-Object.md) 
- [El modelo de objetos de scripting de ISE de Windows PowerShell](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referencia del modelo de objetos de ISE de Windows PowerShell](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [La jerarquía del modelo de objetos de ISE](../ise/The-ISE-Object-Model-Hierarchy.md)

  
