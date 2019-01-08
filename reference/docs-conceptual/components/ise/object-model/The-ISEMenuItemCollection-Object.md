---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: El objeto ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403162"
---
# <a name="the-isemenuitemcollection-object"></a>El objeto ISEMenuItemCollection

Un objeto **ISEMenuItemCollection** es una colección de objetos **ISEMenuItem**. Es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Un ejemplo es el objeto **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** que se usa para personalizar el menú **Complemento** en el Entorno de scripting integrado (ISE) de Windows PowerShell®.

## <a name="method"></a>Método

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut\)

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

Agrega un elemento de menú a la colección.

**DisplayName** El nombre para mostrar del menú que se va a agregar.

**Action** El objeto **System.Management.Automation.ScriptBlock** que especifica la acción que está asociada con este elemento de menú.

**Shortcut** El método abreviado de teclado para la acción.

**Returns** El objeto ISEMenuItem que se acaba de agregar.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Borrar\(\)

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

Quita todos los submenús del elemento de menú.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Véase también

- [El objeto ISEMenuItem](The-ISEMenuItem-Object.md)
- [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)