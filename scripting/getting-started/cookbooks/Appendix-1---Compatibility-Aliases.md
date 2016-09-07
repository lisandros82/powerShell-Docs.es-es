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
translationtype: Human Translation
ms.sourcegitcommit: 3222a0ba54e87b214c5ebf64e587f920d531956a
ms.openlocfilehash: 61eac49bc710a2435117409b74ba02798cf720da

---

# Apéndice 1: Alias de compatibilidad
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
|**cls**|**clear**|**Clear-Host** (función)|N/A|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**rename**|**mv**|**Rename-Item**|**rni**|
|**tipo**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|N/A|**pushd**|**Push-Location**|N/A|
|N/A|**popd**|**Pop-Location**|N/A|




<!--HONumber=Aug16_HO4-->


