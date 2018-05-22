---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso WindowsFeatureSet de DSC
ms.openlocfilehash: 582f9b1f439056118680f6f814d2c202d0e823be
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-windowsfeatureset-resource"></a>Recurso WindowsFeatureSet de DSC

> Se aplica a: Windows PowerShell 5.0

El recurso **WindowsFeatureSet** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para asegurarse de que los roles y las características se agreguen o quiten en un nodo de destino.
Este es un [recurso compuesto](authoringResourceComposite.md) que llama al [recurso WindowsFeature](windowsfeatureResource.md) de cada una de las características especificadas en la propiedad `Name`.

Este recurso se usa cuando se desea configurar varias características de Windows para que tengan el mismo estado.

## <a name="syntax"></a>Sintaxis

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Propiedades

|  Propiedad  |  Descripción   |
|---|---|
| Nombre| Los nombres de los roles o características que quiere garantizar que se agreguen o se quiten. Estos son los mismos que con la propiedad **Name** del cmdlet [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) y no el nombre para mostrar de los roles o características.|
| Credential| Las credenciales que se usarán para agregar o quitar los roles o las características.|
| Ensure| Indica si se agregan las funciones o características. Para asegurarse de que los roles o características se agregan, establezca esta propiedad en "Present"; para asegurarse de que se quitan los roles o características, establezca la propiedad en "Absent".|
| IncludeAllSubFeature| Establezca esta propiedad en **$true** para incluir todas las subcaracterísticas requeridas de las características que se especifican con la propiedad **Name**.|
| LogPath| La ruta de acceso al archivo de registro en el que desea que el proveedor de recursos registre la operación.|
| DependsOn| Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.|
| Origen| Indica la ubicación del archivo de origen que se utilizará para la instalación, si es necesario.|

## <a name="example"></a>Ejemplo

La siguiente configuración garantiza que las características de **Web Server** (IIS) y del **servidor SMTP**, y todas las subcaracterísticas de cada uno, se instalan.

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```