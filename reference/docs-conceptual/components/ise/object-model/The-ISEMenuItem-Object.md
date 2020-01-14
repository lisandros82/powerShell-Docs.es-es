---
ms.date: 12/31/2019
keywords: powershell, cmdlet
title: El objeto ISEMenuItem
ms.openlocfilehash: c3ffe6e8f0b28987543fe0a873c552292dc5158a
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736988"
---
# <a name="the-isemenuitem-object"></a>El objeto ISEMenuItem

Un objeto **ISEMenuItem** es una instancia de la clase **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.
Todos los objetos de menú **Complementos** son instancias de la clase **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.

## <a name="properties"></a>Propiedades

### <a name="displayname"></a>DisplayName

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene el nombre para mostrar del elemento de menú.

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a>Acción

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene el bloque del script. Invoca la acción al hacer clic en el elemento de menú.

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>Método abreviado

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene el método abreviado de teclado de entrada de Windows para el elemento de menú.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>Submenus

Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene la [lista de submenús](The-ISEMenuItemCollection-Object.md) del elemento de menú.

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Ejemplo de scripting

Para entender mejor el uso del menú de complementos y sus propiedades que admiten scripts, consulte el siguiente ejemplo de scripting.

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a>Consulte también

- [El objeto ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md)
- [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)
