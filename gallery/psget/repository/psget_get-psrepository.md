---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_get psrepository
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 3d0b67d012528a1ef59d8f5a1b16903d931426a3

---

# Get-PSRepository

Obtiene los repositorios registrados de un equipo.

## Descripción

El cmdlet Get-PSRepository obtiene los repositorios del módulo de PowerShell que están registrados para el usuario actual de un equipo.

Para cada repositorio registrado, Get-PSRepository devuelve un objeto PSRepository que opcionalmente se puede canalizar a Unregister-PSRepository para anular el registro de un repositorio registrado.

## Sintaxis de cmdlet
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## Referencia de la ayuda en línea de cmdlet

[Get-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517127)

## Comandos de ejemplo

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```




<!--HONumber=Oct16_HO2-->


