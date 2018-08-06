---
ms.date: 06/20/2018
keywords: dsc,powershell,configuration,setup
title: Recurso PackageManagement de DSC
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268099"
---
# <a name="dsc-packagemanagement-resource"></a>Recurso PackageManagement de DSC

Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1

El recurso **PackageManagement** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para instalar o desinstalar paquetes de administración de paquetes, en un nodo de destino. Este recurso requiere el módulo **PackageManagement**, disponible en [http://PowerShellGallery.com](http://PowerShellGallery.com).

> [!IMPORTANT]
> El módulo **PackageManagement** debe tener al menos la versión 1.1.7.0 para que la siguiente información de propiedad sea correcta.

## <a name="syntax"></a>Sintaxis

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Propiedades

| Propiedad | Descripción |
| --- | --- |
| Nombre| Especifica el nombre del paquete que se va a instalar o desinstalar.|
| AdditionalParameters| La tabla hash de parámetros específica del proveedor que se pasará a `Get-Package -AdditionalArguments`. Por ejemplo, para el proveedor NuGet puede pasar parámetros adicionales, como DestinationPath.|
| Ensure| Determina si el paquete se puede instalar o desinstalar.|
| MaximumVersion|Especifica la versión máxima permitida del paquete que desea encontrar. Si no agrega este parámetro, el recurso busca la versión disponible más alta del paquete.|
| MinimumVersion|Especifica la versión mínima permitida del paquete que desea encontrar. Si no se agrega este parámetro, este recurso busca la versión más alta disponible del paquete que también admite cualquier versión máxima especificada por el parámetro _MaximumVersion_.|
| ProviderName| Especifica un nombre de proveedor del paquete que se va a dirigir la búsqueda del paquete. Puede obtener los nombres de proveedor del paquete mediante la ejecución del cmdlet `Get-PackageProvider`.|
| RequiredVersion| Especifica la versión exacta del paquete que desea instalar. Si no se especifica este parámetro, este recurso de DSC instala la versión más reciente disponible del paquete que también admite cualquier versión máxima especificada por el parámetro _MaximumVersion_.|
| Origen| Especifica el nombre del origen del paquete donde se encuentra el paquete. Puede ser un URI o un origen registrado con `Register-PackageSource` o el recurso de DSC PackageManagementSource.|
| SourceCredential | Especifica una cuenta de usuario que tenga derechos para instalar un paquete para un proveedor u origen de paquetes especificado.|

## <a name="additional-parameters"></a>Parámetros adicionales

En la tabla siguiente se enumeran las opciones de la propiedad AdditionalParameters.

| Parámetro | Descripción |
| --- | --- |
| DestinationPath| Usada por proveedores como el proveedor integrado de Nuget. Especifica una ubicación del archivo donde desea que se instale el paquete.|
| InstallationPolicy| Usada por proveedores como el proveedor integrado de Nuget. Determina si puede confiar en el origen del paquete. Uno de: `Untrusted`, `Trusted`.|

## <a name="example"></a>Ejemplo

Este ejemplo se instala el paquete NuGet **JQuery** y el módulo **GistProvider** de PowerShell mediante el recurso **PackageManagement** de DSC. Este ejemplo primero garantiza que los orígenes del paquete necesarios están disponibles y después define el estado esperado de los paquetes **JQuery** y **GistProvider** (NuGet y PowerShell, respectivamente).

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```