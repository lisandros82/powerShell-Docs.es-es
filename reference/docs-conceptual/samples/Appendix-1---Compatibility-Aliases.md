---
ms.date: 09/09/2019
keywords: powershell, cmdlet
title: Apéndice 1 Alias de compatibilidad
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848168"
---
# <a name="appendix-1---compatibility-aliases"></a>Apéndice 1: Alias de compatibilidad

PowerShell tiene varios alias que permiten a los usuarios de **UNIX** y **cmd.exe** utilizar comandos familiares.
Los comandos y sus alias y cmdlet de PowerShell relacionados se muestran en la siguiente tabla:

|Comando cmd.exe|Comando de UNIX|Cmdlet de PowerShell|Alias de PowerShell|
|---------------|----------------|--------------|------------|
|**cls**|**clear**|`Clear-Host` (función)|`cls`|
|**copy**|**cp**|`Copy-Item`|`cpi`|
|**dir**|**ls**|`Get-ChildItem`|`gci`|
|**type**|**cat**|`Get-Content`|`gc`|
|**move**|**mv**|`Move-Item`|`mi`|
|**md**|**mkdir**|`New-Item`|`ni`|
|**pushd**|**pushd**|`Push-Location`|`pushd`|
|**popd**|**popd**|`Pop-Location`|`popd`|
|**del**, **erase**, **rd**, **rmdir**|**rm**|`Remove-Item`|`ri`|
|**ren**|**mv**|`Rename-Item`|`rni`|
|**cd**, **chdir**|**cd**|`Set-Location`|`sl`|

Para buscar los alias de PowerShell, use el cmdlet [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias). Para mostrar los alias de un cmdlet, use el parámetro **Definition** y especifique el nombre del cmdlet.
O bien, para buscar el nombre del cmdlet de un alias, use el parámetro **Name** y especifique el alias.

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
