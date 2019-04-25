---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057985"
---
# <a name="the-isesnippetobject"></a>ISESnippetObject

Un objeto **ISESnippet** es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISESnippet. Los miembros de la colección **$psISE.CurrentPowerShellTab.Snippets** son todos ejemplos de objetos **ISESnippet**. La manera más fácil de crear un fragmento de código es usar el cmdlet [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0).

## <a name="properties"></a>Propiedades

### <a name="author"></a>Autor

Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

La propiedad de solo lectura que obtiene el nombre del autor del fragmento de código.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

La propiedad de solo lectura que obtiene el fragmento de código que va a insertar en el editor.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Directa

Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

La propiedad de solo lectura que obtiene el método abreviado de teclado de Windows para el elemento de menú.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Véase también

- [El objeto ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)