---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: 7b692d33e3f86a89505b8d37c0da4177f3dff2c2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="save-script"></a>Save-Script

El cmdlet Save-Script permite revisar el archivo de script, para lo cual debe guardarse en una ubicación especificada.

## <a name="description"></a>Descripción

El cmdlet Save-Script guarda el script especificado.

## <a name="cmdlet-syntax"></a>Sintaxis de cmdlet

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Referencia de la ayuda en línea de cmdlet

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a>Comandos de ejemplo

### <a name="example-1-save-a-script-from-a-repository"></a>Ejemplo 1: guardar un script desde un repositorio
Este comando guarda la versión más reciente del script Fabrikam-ClientScript desde el repositorio GalleryINT en la carpeta local C:\ScriptSharingDemo.

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a>Ejemplo 2: guardar una versión de un script mediante la canalización desde el cmdlet Find-Script

El primer comando busca la versión 1.5 de Fabrikam-ClientScript desde el repositorio GalleryINT y lo guarda en la carpeta C:\ScriptSharingDemo.

El segundo comando valida los metadatos de script guardados.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

