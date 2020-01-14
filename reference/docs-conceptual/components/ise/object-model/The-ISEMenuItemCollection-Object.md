---
ms.date: 12/31/2019
keywords: powershell, cmdlet
title: El objeto ISEMenuItemCollection
ms.openlocfilehash: 39e8547c9b19ba323d4b224a46eda416542b2807
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736179"
---
# <a name="the-isemenuitemcollection-object"></a>El objeto ISEMenuItemCollection

Un objeto **ISEMenuItemCollection** es una colección de objetos **ISEMenuItem**. Es una instancia de la clase **Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection**. Un ejemplo es el objeto `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus` que se usa para personalizar el menú **Complemento** en Windows PowerShell® ISE.

## <a name="method"></a>Método

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut\)

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

Agrega un elemento de menú a la colección.

**DisplayName** El nombre para mostrar del menú que se va a agregar.

**Action** El objeto **System.Management.Automation.ScriptBlock** que especifica la acción que está asociada con este elemento de menú.

**Shortcut** El método abreviado de teclado para la acción.

**Returns** El objeto **ISEMenuItem** que se acaba de agregar.

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

## <a name="see-also"></a>Consulte también

- [El objeto ISEMenuItem](The-ISEMenuItem-Object.md)
- [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)
