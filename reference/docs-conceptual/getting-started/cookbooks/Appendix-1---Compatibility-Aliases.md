---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Apéndice 1 Alias de compatibilidad
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954643"
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