---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: ISESnippetObject
ms.openlocfilehash: 60456ec90f56753fa96f141b8b8299ef3f7e41c9
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736971"
---
# <a name="the-isesnippetobject"></a>ISESnippetObject

Un objeto **ISESnippet** es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISESnippet. Todos los miembros de la colección `$psISE.CurrentPowerShellTab.Snippets` son ejemplos de objetos **ISESnippet**. La manera más fácil de crear un fragmento de código es usar el cmdlet [New-IseSnippet](/reference/5.1/ISE/New-IseSnippet.md).

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

### <a name="shortcut"></a>Método abreviado

Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

La propiedad de solo lectura que obtiene el método abreviado de teclado de Windows para el elemento de menú.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Consulte también

- [El objeto ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)
