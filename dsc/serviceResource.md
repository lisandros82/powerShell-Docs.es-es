---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Service
ms.openlocfilehash: 59d7c0c7147bf28b92d64a25c0d67c277e0bb210
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-service-resource"></a>Recurso de DSC Service

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0


El recurso **Service** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar servicios en el nodo de destino.

## <a name="syntax"></a>Sintaxis

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a>Propiedades

|  Propiedad  |  Descripción   |
|---|---|
| Nombre| Indica el nombre del servicio. Tenga en cuenta que a veces es distinto del nombre para mostrar. Puede obtener una lista de los servicios y sus estados actuales con el cmdlet Get-Service.|
| BuiltInAccount| Indica la cuenta de inicio de sesión que se utilizará para el servicio. Los valores permitidos para esta propiedad son: **LocalService**, **LocalSystem** y **NetworkService**.|
| Credential| Indica las credenciales de la cuenta en la que se ejecutará el servicio. Esta propiedad no se puede utilizar junto con la propiedad __BuiltinAccount__.|
| DependsOn| Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.|
| StartupType| Indica el tipo de inicio del servicio. Los valores permitidos para esta propiedad son: **Automatic**, **Disabled** y **Manual**.|
| Estado| Indica el estado que quiere garantizar para el servicio.|
| Descripción | Indica la descripción del servicio de destino.|
| DisplayName | Indica el nombre para mostrar del servicio de destino.|
| Ensure | Indica si el servicio de destino existe en el sistema. Establezca esta propiedad en **Absent** para asegurarse de que el servicio de destino no exista. Si la establece en **Present** (el valor predeterminado), se asegura de que el servicio de destino existe.|
| Ruta | Indica la ruta de acceso al archivo binario para un nuevo servicio.|

## <a name="example"></a>Ejemplo

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```