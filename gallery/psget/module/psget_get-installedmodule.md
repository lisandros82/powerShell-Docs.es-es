---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_get installedmodule
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 40a79a74117f28407758367f4e27b7ae26917078

---

# Get-InstalledModule

Obtiene los módulos instalados en un equipo.

## Descripción

El cmdlet Get-InstalledModule obtiene los módulos de PowerShell que se instalaron en un equipo mediante el cmdlet Install-Module.

Para cada módulo instalado, Get-InstalledModule devuelve un objeto PSRepositoryItemInfo que opcionalmente se puede canalizar a Uninstall-Module para desinstalar los módulos instalados.

- Get-InstalledModule puede filtrar los módulos instalados en función de parámetros de nombre y versión.
- Get-InstalledModule puede filtrar con parámetros de versión: MinimumVersion, MaximumVersion, RequiredVersion y AllVersions.
  - Estos parámetros se excluyen mutuamente, excepto MinmimumVersion y MaximumVersion.
  - Estos parámetros de versión solo se permiten con el nombre de módulo único sin ningún carácter comodín.
  - Si no se especifica el parámetro RequiredVersion, Get-InstalledModule devuelve la versión más reciente del módulo instalado que sea igual o mayor que la versión mínima especificada, o la versión más reciente del módulo si no se especifica ninguna versión mínima. 
  - Si se especifica el parámetro RequiredVersion, Get-InstalledModule solo devuelve la versión del módulo instalado que coincida exactamente con la versión especificada.

## Sintaxis de cmdlet
```powershell
Get-Command -Name Get-InstalledModule -Module PowerShellGet -Syntax
```

## Referencia de la ayuda en línea de cmdlet

[Get-InstalledModule](http://go.microsoft.com/fwlink/?LinkId=526863)

## Comandos de ejemplo

```powershell

# Get all modules installed using PowerShellGet cmdlets
Get-InstalledModule

# Get a specific installed module
Get-InstalledModule DJoin

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        DJoin                               PSGallery            This is a PowerShell frontend to the DJOIN.exe c...

# Get installed module with wildcards
Get-InstalledModule -Name AzureRM*

# Get all versions of an installed module
Get-InstalledModule -Name AzureRM.Automation -AllVersions

# Get installed module with MinimumVersion
Get-InstalledModule -Name AzureRM.Automation -MinimumVersion 1.0.0

# Get installed module with MaximumVersion
Get-InstalledModule -Name AzureRM.Automation -MaximumVersion 1.0.8

# Get installed module with version range
Get-InstalledModule -Name AzureRM.Automation -MinimumVersion 1.0.0 -MaximumVersion 1.0.8

# Get installed module with RequiredVersion
Get-InstalledScript -Name AzureRM.Automation -RequiredVersion 1.0.3

# Properties of Get-InstalledModule returned object
Get-InstalledModule DJoin | Format-List * -Force

Name                       : DJoin
Version                    : 1.0
Type                       : Module
Description                : This is a PowerShell frontend to the DJOIN.exe command which provides better
                             discoverability and usability.
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 7:12:37 PM
InstalledDate              : 4/5/2016 4:13:39 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Modules\DJoin\1.0

```



## Propiedades InstalledDate y UpdatedDate en el objeto PSGetRepositoryItemInfo

    During the install operation:
        InstalledDate: current DateTime (Get-Date) value
        UpdatedDate: null

    During the Update operation:
        InstalledDate: InstalledDate from the previous installation otherwise current DateTime (Get-Date) value
        UpdatedDate: current DateTime (Get-Date) value

```powershell
Install-Module -Name ContosoServer -RequiredVersion 1.0 -Repository INT
Get-InstalledModule -Name ContosoServer | Format-Table Name, InstalledDate, UpdatedDate

Name          InstalledDate         UpdatedDate
----          -------------         -----------
ContosoServer 2/29/2016 11:59:14 AM


\Update-Module -Name ContosoServer
Get-InstalledModule -Name ContosoServer | Format-Table Name, InstalledDate, UpdatedDate

Name          InstalledDate         UpdatedDate
----          -------------         -----------
ContosoServer 2/29/2016 11:59:14 AM 2/29/2016 12:00:15 PM
```




<!--HONumber=Oct16_HO2-->


