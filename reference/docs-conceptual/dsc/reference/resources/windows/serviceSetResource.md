---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso ServiceSet de DSC
ms.openlocfilehash: 97c25f46940d69ed6c696e2692e29131e9a997b0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953032"
---
# <a name="dsc-serviceset-resource"></a>Recurso ServiceSet de DSC

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x

El recurso **ServiceSet** del servicio de configuración de estado deseado (DSC) de Windows PowerShell (DSC) proporciona un mecanismo para administrar los servicios del nodo de destino. Este es un [recurso compuesto](../../../resources/authoringResourceComposite.md) que llama el [recurso de servicio](serviceResource.md) de cada uno de los servicios que se especifica en la propiedad **Name**.

Este recurso se usa cuando se desea configurar varios servicios para que tengan el mismo estado.

## <a name="syntax"></a>Sintaxis

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|Nombre |Indica los nombres de servicio. Tenga en cuenta que son distintos de los nombres que se muestran. Con el cmdlet `Get-Service` puede obtener una lista de los servicios y sus estados actuales. |
|StartupType |Indica el tipo de inicio de los servicios. Los valores permitidos para esta propiedad son: **Automatic**, **Disabled** y **Manual**. |
|BuiltInAccount |Indica la cuenta de inicio de sesión que se usa para los servicios. Los valores permitidos para esta propiedad son: **LocalService**, **LocalSystem** y **NetworkService**. |
|Estado |Indica el estado que quiere comprobar para los servicios: **Stopped** o **Running**. |
|Credential |Indica las credenciales para la cuenta en la que se ejecutará el recurso del servicio. Esta propiedad no se puede utilizar junto con la propiedad **BuiltinAccount**. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica si los servicios existen en el sistema. Establezca esta propiedad en **Absent** para asegurarse de que los servicios no existen. Si la establece en **Present**, se asegura de que los servicios de destino existen. El valor predeterminado es **Present**. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Ejemplo

La siguiente configuración inicia los servicios de "Audio de Windows" y "Servicios de Escritorio remoto".

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```