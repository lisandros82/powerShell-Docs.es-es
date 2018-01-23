---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso PackageManagementSource de DSC
ms.openlocfilehash: 1c904c70369a75802484c3c0520df63602760361
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagementsource-resource"></a>Recurso PackageManagementSource de DSC

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

El recurso **PackageManagementSource** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para registrar o anular el registro de los orígenes de administración de paquetes en un nodo de destino. **Los orígenes de administración de paquetes registrados de este modo se registran en el contexto del sistema y pueden usarse por la cuenta del sistema o por el motor de DSC.** Este recurso requiere el módulo **PackageManagement**, disponible en http://PowerShellGallery.com.

## <a name="syntax"></a>Sintaxis

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades
|  Propiedad  |  Descripción   | 
|---|---| 
| Nombre| Especifica el nombre del origen del paquete que se registra o se anula su registro del sistema.| 
| Ensure| Determina si el origen del paquete se registra o no.| 
| InstallationPolicy| Determina si se puede confiar en el origen del paquete. Uno de los valores siguientes: "No es de confianza", "De confianza".| 
| ProviderName| Especifica el nombre del proveedor de OneGet que permite la interoperabilidad con el origen del paquete.| 
| SourceUri| Especifica el URI del origen del paquete.| 
| SourceCredential| Proporciona acceso al paquete en un origen remoto.| 

## <a name="example"></a>Ejemplo

Este ejemplo registra el origen del paquete http://nuget.org mediante el recurso **PackageManagementSource** de DSC.

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```

