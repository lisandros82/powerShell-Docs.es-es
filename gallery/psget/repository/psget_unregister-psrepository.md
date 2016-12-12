---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_unregister psrepository
ms.technology: powershell
ms.openlocfilehash: c90710db47dbfdc58e1ca7f84c6d6fd8f04b5109
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="unregister-psrepository"></a>Unregister-PSRepository

Anula el registro de un repositorio.

## <a name="description"></a>Descripción

El cmdlet Unregister-PSRepository anula el registro de un repositorio del usuario actual.
- Se permite la anulación del registro y el nuevo registro del repositorio PSGallery para una empresa y escenarios desconectados.
- Para que los usuarios puedan volver a registrar PSGallery, simplemente deben ejecutar `Register-PSRepository -Default`
- Puesto que PSGallery es el repositorio de publicación predeterminado de los cmdlets Publish-Module y Publish-Script, se producirá un error si PSGallery no está disponible en la lista de repositorios registrados.

## <a name="cmdlet-syntax"></a>Sintaxis de cmdlet

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Referencia de la ayuda en línea de cmdlet

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a>Comandos de ejemplo

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a>Se permite la anulación del registro y el nuevo registro del repositorio PSGallery para una empresa y escenarios desconectados.
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```

