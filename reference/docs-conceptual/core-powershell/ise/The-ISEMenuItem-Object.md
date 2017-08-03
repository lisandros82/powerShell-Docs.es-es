---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: El objeto ISEMenuItem
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 33de866d706ec2b0894c5bfe49e07fee142b95c0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="the-isemenuitem-object"></a>El objeto ISEMenuItem
  Un objeto **ISEMenuItem** es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISEMenuItem. Todos los objetos de menú **Complementos** son instancias de la clase **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.

## <a name="properties"></a>Propiedades

###  <a name="DisplayName"></a> DisplayName
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad de solo lectura que obtiene el nombre para mostrar del elemento de menú.

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

###  <a name="Action"></a> Action
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad de solo lectura que obtiene el bloque del script. Invoca la acción al hacer clic en el elemento de menú.

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

###  <a name="Shortcut"></a> Shortcut
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad de solo lectura que obtiene el método abreviado de teclado de entrada de Windows para el elemento de menú.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

###  <a name="Submenus"></a> Submenus
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad de solo lectura que obtiene la [lista de submenús](The-ISEMenuItemCollection-Object.md) del elemento de menú.

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Ejemplo de scripting
 Para entender mejor el uso del menú de complementos y sus propiedades que admiten scripts, consulte el siguiente ejemplo de scripting.

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu - a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## <a name="see-also"></a>Véase también
- [El objeto ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md) 
- [El modelo de objetos de scripting de ISE de Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referencia del modelo de objetos de ISE de Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)

  
