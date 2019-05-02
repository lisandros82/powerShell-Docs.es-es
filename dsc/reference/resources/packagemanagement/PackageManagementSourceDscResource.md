---
ms.date: 06/20/2018
keywords: dsc,powershell,configuration,setup
title: Recurso PackageManagementSource de DSC
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077592"
---
# <a name="dsc-packagemanagementsource-resource"></a>Recurso PackageManagementSource de DSC

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1

El recurso **PackageManagementSource** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para registrar o anular el registro de los orígenes de administración de paquetes en un nodo de destino. **Los orígenes de administración de paquetes registrados de este modo se registran en el contexto del sistema y pueden usarse por la cuenta del sistema o por el motor de DSC.** Este recurso requiere el módulo **PackageManagement**, disponible en http://PowerShellGallery.com.

> [!IMPORTANT]
> El módulo **PackageManagement** debe tener al menos la versión 1.1.7.0 para que la siguiente información de propiedad sea correcta.

## <a name="syntax"></a>Sintaxis

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Propiedades

|  Propiedad  |  Descripción   |
|---|---|
| Nombre| Especifica el nombre del origen del paquete que se registra o se anula su registro del sistema.|
| ProviderName| Especifica el nombre del proveedor de OneGet que permite la interoperabilidad con el origen del paquete.|
| SourceLocation| Especifica el URI del origen del paquete.|
| Ensure| Determina si el origen del paquete se registra o no.|
| InstallationPolicy| Usada por proveedores como el proveedor integrado de Nuget. Determina si puede confiar en el origen del paquete. Uno de los valores siguientes: "No es de confianza", "De confianza".|
| SourceCredential| Proporciona acceso al paquete en un origen remoto.|

## <a name="example"></a>Ejemplo

En este ejemplo se registra el origen del paquete http://nuget.org con el recurso de DSC **PackageManagementSource** DSC resource.

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```