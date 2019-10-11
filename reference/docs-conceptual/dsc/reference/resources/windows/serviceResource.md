---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Service
ms.openlocfilehash: 0bef6aa6d3526c9d8d92187c1e738d5c46b5665a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953052"
---
# <a name="dsc-service-resource"></a>Recurso de DSC Service

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x

El recurso **Service** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar servicios en el nodo de destino.

## <a name="syntax"></a>Sintaxis

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|Nombre |Indica el nombre del servicio. Tenga en cuenta que a veces es distinto del nombre para mostrar. Con el cmdlet `Get-Service` puede obtener una lista de los servicios y sus estados actuales. |
|BuiltInAccount |Indica la cuenta de inicio de sesión que se utilizará para el servicio. Los valores permitidos para esta propiedad son: **LocalService**, **LocalSystem** y **NetworkService**. |
|Credential |Indica las credenciales de la cuenta en la que se ejecutará el servicio. Esta propiedad no se puede utilizar junto con la propiedad **BuiltinAccount**. |
|StartupType |Indica el tipo de inicio del servicio. Los valores permitidos para esta propiedad son: **Automatic**, **Disabled** y **Manual**. |
|Estado |Indica el estado que quiere garantizar para el servicio. Los valores son: **Running** o **Stopped**. |
|Descripción |Indica la descripción del servicio de destino. |
|DisplayName |Indica el nombre para mostrar del servicio de destino. |
|Ruta |Indica la ruta de acceso al archivo binario para un nuevo servicio. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica si el servicio de destino existe en el sistema. Establezca esta propiedad en **Absent** para asegurarse de que el servicio de destino no exista. Si la establece en **Present**, se asegura de que el servicio de destino existe. El valor predeterminado es **Present**. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).

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