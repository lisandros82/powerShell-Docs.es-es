---
title: Recurso PackageManagement de DSC
ms.date: 
keywords: powershell,DSC
description: 
ms.topic: article
author: brywang-msft
manager: kriscv
ms.prod: powershell
ms.openlocfilehash: 33775be230a4e92e22784d991338510510f69889
ms.sourcegitcommit: 89e7ae30faff5f96641fc72764bdc76e0e257bc2
translationtype: HT
---
# <a name="dsc-packagemanagement-resource"></a>Recurso PackageManagement de DSC

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

El recurso **PackageManagement** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para instalar o desinstalar paquetes de administración de paquetes, en un nodo de destino. Este recurso requiere el módulo **PackageManagement**, disponible en http://PowerShellGallery.com.

## <a name="syntax"></a>Sintaxis

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a>Propiedades
|  Propiedad  |  Descripción   | 
|---|---| 
| Nombre| Especifica el nombre del paquete que se va a instalar o desinstalar.| 
| Origen| Especifica el nombre del origen del paquete donde se encuentra el paquete. Puede ser un URI o un origen registrado con el recurso de registro de DSC Register-PackageSource o PackageManagementSource. El recurso MSFT_PackageManagementSource de DSC también puede registrar un origen del paquete.| 
| Ensure| Determina si el paquete se puede instalar o desinstalar.| 
| RequiredVersion| Especifica la versión exacta del paquete que desea instalar. Si no se especifica este parámetro, este recurso de DSC instala la versión más reciente disponible del paquete que también admite cualquier versión máxima especificada por el parámetro MaximumVersion.| 
| MinimumVersion| Especifica la versión mínima permitida del paquete que desea instalar. Si no se agrega este parámetro, este recurso de DSC instala la versión más alta disponible del paquete que también admite cualquier versión máxima especificada por el parámetro MaximumVersion.| 
| MaximumVersion| Especifica la versión máxima permitida del paquete que desea instalar. Si no se especifica este parámetro, este recurso de DSC instala la versión del paquete disponible con el número mayor.| 
| SourceCredential | Especifica una cuenta de usuario que tenga derechos para instalar un paquete para un proveedor u origen de paquetes especificado.| 
| ProviderName| Especifica un nombre de proveedor del paquete que se va a dirigir la búsqueda del paquete. Puede obtener los nombres de proveedor del paquete mediante la ejecución del cmdlet Get-PackageProvider.| 
| AdditionalParameters| Parámetros específicos del proveedor que se pasan como una tabla hash. Por ejemplo, para el proveedor NuGet puede pasar parámetros adicionales, como DestinationPath.| 

## <a name="additional-parameters"></a>Parámetros adicionales
En la tabla siguiente se enumeran las opciones de la propiedad AdditionalParameters.
|  Parámetro  | Descripción   | 
|---|---|
| DestinationPath| Usada por proveedores como el proveedor integrado de Nuget. Especifica una ubicación del archivo donde desea que se instale el paquete.|
| InstallationPolicy| Usada por proveedores como el proveedor integrado de Nuget. Determina si puede confiar en el origen del paquete. Uno de los valores siguientes: "No es de confianza", "De confianza".|

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
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }    
    
    PackageManagementSource PSGallery 
    { 
        Ensure      = "Present" 
        Name        = "psgallery" 
        ProviderName= "PowerShellGet" 
        SourceUri   = "https://www.powershellgallery.com/api/v2/"   
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