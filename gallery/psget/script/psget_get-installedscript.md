---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_get installedscript
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: f809c5c8f5a28c01c67ee4c4453ecca7796838c4

---

# Get-InstalledScript

Obtiene los scripts instalados en un equipo.

## Descripción

El cmdlet Get-InstalledScript obtiene los scripts de PowerShell instalados en un equipo.

Para cada script instalado, Get-InstalledScript devuelve un objeto PSRepositoryItemInfo que opcionalmente se puede canalizar a Uninstall-Script para desinstalar los scripts instalados.

- Get-InstalledScript puede filtrar los scripts instalados en función de parámetros de nombre y versión.
- Get-InstalledScript puede filtrar con parámetros de versión: MinimumVersion, MaximumVersion, RequiredVersion y AllVersions.
  - Estos parámetros se excluyen mutuamente, excepto MinmimumVersion y MaximumVersion.
  - Estos parámetros de versión solo se permiten con el nombre de script único sin ningún carácter comodín.
  - Si no se especifica el parámetro RequiredVersion, Get-InstalledScript devuelve la versión más reciente del script instalado que sea igual o mayor que la versión mínima especificada, o la versión más reciente del script si no se especifica ninguna versión mínima. 
  - Si se especifica el parámetro RequiredVersion, Get-InstalledScript solo devuelve la versión del script instalado que coincida exactamente con la versión especificada.

## Sintaxis de cmdlet

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## Referencia de la ayuda en línea de cmdlet

[Get-InstalledScript](http://go.microsoft.com/fwlink/?LinkId=619790)

## Comandos de ejemplo

```powershell

# Get all scripts installed using PowerShellGet cmdlets
Get-InstalledScript

# Get a specific installed script
Get-InstalledScript Show-Tree

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      Show-Tree                           PSGallery            Script to show the layout of PowerShell namespaces (Tr...

# Get installed script with wildcards
Get-InstalledScript -Name *Azure*

# Get all versions of an installed script
Get-InstalledScript -Name Connect-O365 -AllVersions

# Get installed script with MinimumVersion
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1

# Get installed script with MaximumVersion
Get-InstalledScript -Name Connect-O365 -MaximumVersion 1.6.3

# Get installed script with version range
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.3

# Get installed script with RequiredVersion
Get-InstalledScript -Name Connect-O365 -RequiredVersion 1.4

# Properties of Get-InstalledScript returned object
Get-InstalledScript Show-Tree | Format-List * -Force

Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              : 5/4/2016 11:44:13 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


```




<!--HONumber=Oct16_HO2-->


