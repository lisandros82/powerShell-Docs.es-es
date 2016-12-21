---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: El objeto ISEMenuItemCollection
ms.technology: powershell
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 45e9123df5f22f37d2a76e49db6df5aa98824e1c
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="the-isemenuitemcollection-object"></a>El objeto ISEMenuItemCollection
  Un objeto **ISEMenuItemCollection** es una colección de objetos **ISEMenuItem**. Es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Un ejemplo es el objeto **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** que se usa para personalizar el menú **Complemento** en el Entorno de scripting integrado (ISE) de Windows PowerShell®.

## <a name="method"></a>Método

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut\)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Agrega un elemento de menú a la colección.

 **DisplayName**
 El nombre para mostrar del menú que se va a agregar.

 **Action**
 El objeto **System.Management.Automation.ScriptBlock** que especifica la acción que está asociada con este elemento de menú.

 **Shortcut**
 El método abreviado de teclado para la acción.

 **Returns**
 El objeto ISEMenuItem que acaba de agregar.

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a>Borrar\(\)
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 Quita todos los submenús del elemento de menú.

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a>Véase también
- [El objeto ISEMenuItem](The-ISEMenuItem-Object.md) 
- [El modelo de objetos de scripting de ISE de Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referencia del modelo de objetos de ISE de Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)

  
