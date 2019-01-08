---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso ServiceSet de DSC
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047562"
---
# <a name="dsc-serviceset-resource"></a>Recurso ServiceSet de DSC

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

El recurso **ServiceSet** del servicio de configuración de estado deseado (DSC) de Windows PowerShell (DSC) proporciona un mecanismo para administrar los servicios del nodo de destino. Este es un [recurso compuesto](../../../resources/authoringResourceComposite.md) que llama el [recurso de servicio](serviceResource.md) de cada uno de los servicios que se especifica en la propiedad `Name`.

Este recurso se usa cuando se desea configurar varios servicios para que tengan el mismo estado.

## <a name="syntax"></a>Sintaxis

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Propiedades

|  Propiedad  |  Descripción   |
|---|---|
| Nombre| Indica los nombres de servicio. Tenga en cuenta que son distintos de los nombres que se muestran. Con el cmdlet [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) puede obtener una lista de los servicios y sus estados actuales.|
| StartupType| Indica el tipo de inicio del servicio. Los valores permitidos para esta propiedad son: **Automática**, **deshabilitado**, y **Manual**|
| BuiltInAccount| Indica la cuenta de inicio de sesión que se usa para los servicios. Los valores permitidos para esta propiedad son: **LocalService**, **LocalSystem**, y **NetworkService**.|
| Estado| Indica el estado que quiere garantizar para el servicio. **Detenido** o **ejecutando**.|
| Ensure| Indica si los servicios existen en el sistema. Establezca esta propiedad en **Absent** para asegurarse de que los servicios no existen. Si la establece en **Present** (el valor predeterminado), se asegura de que los servicios de destino existen.|
| Credential| Indica las credenciales para la cuenta en la que se ejecutará el recurso del servicio. Esta propiedad no se puede utilizar junto con la propiedad **BuiltinAccount**.|
| DependsOn| Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es *ResourceName* y su tipo es *ResourceType*, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.|



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
