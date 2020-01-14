---
ms.date: 12/31/2019
keywords: powershell, cmdlet
title: El objeto ISESnippetCollection
ms.openlocfilehash: 6cdc43dd1d82e94f66122d7f7b313c02e755fed7
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736052"
---
# <a name="the-isesnippetcollection-object"></a>El objeto ISESnippetCollection

El objeto **ISESnippetCollection** es una colección de objetos **ISESnippet**. La colección de archivos que está asociada con un objeto **PowerShellTab** es un miembro de esta clase. Un ejemplo es la colección `$psISE.CurrentPowerShellTab.Files`.

## <a name="methods"></a>Métodos

### <a name="load-filepathname-"></a>Load\( FilePathName \)

Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.

Carga un archivo `.snippets.ps1xml` que contiene fragmentos de código definidos por el usuario. La manera más fácil de crear fragmentos de código es usar el cmdlet `New-IseSnippet`, que los almacena automáticamente en la carpeta de perfil para que se carguen cada vez que inicie Windows PowerShell ISE.

**FilePathName** (cadena). La ruta de acceso y el nombre de un archivo .snippets.ps1xml que contiene las definiciones de fragmento de código.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Consulte también

- [ISESnippetObject](The-ISESnippetObject.md)
- [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)
