---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Apéndice 1 Alias de compatibilidad
ms.openlocfilehash: 553b9f01d6b5e3f4e04f1a75c25979b54dc205da
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030330"
---
# <a name="appendix-1---compatibility-aliases"></a>Apéndice 1: Alias de compatibilidad

Windows PowerShell tiene varios alias de transición que permiten a los usuarios de UNIX y Cmd usar nombres de comando conocidos en Windows PowerShell. Los alias más comunes se muestran en la tabla siguiente, junto con el comando de Windows PowerShell detrás del alias y el alias de Windows PowerShell estándar si existe uno.

Puede encontrar el comando de Windows PowerShell al que cualquier alias señala desde Windows PowerShell mediante el cmdlet Get-Alias. Por ejemplo, escriba **get-alias cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|Comando de CMD|Comando de UNIX|Comando de PS|Alias de PS|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**cls**|**clear**|**Clear-Host** (función)|**cls**|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**rename**|**mv**|**Rename-Item**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|**pushd**|**pushd**|**Push-Location**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|
