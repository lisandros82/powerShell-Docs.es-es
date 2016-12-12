---
title: "Apéndice 1 Alias de compatibilidad"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: fc715f9ba2a1dc61d2549d5370371fe2b29fa063
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
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

