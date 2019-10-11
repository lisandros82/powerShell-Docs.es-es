---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso WindowsFeatureSet de DSC
ms.openlocfilehash: 1758d248dde4fdee57bd01c157a3f9a8340d6194
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952962"
---
# <a name="dsc-windowsfeatureset-resource"></a>Recurso WindowsFeatureSet de DSC

> Se aplica a: Windows PowerShell 5.x

El recurso **WindowsFeatureSet** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para asegurarse de que los roles y las características se agreguen o quiten en un nodo de destino. Este es un [recurso compuesto](../../../resources/authoringResourceComposite.md) que llama al [recurso WindowsFeature](windowsfeatureResource.md) de cada una de las características especificadas en la propiedad **Name**.

Este recurso se usa cuando se desea configurar varias características de Windows para que tengan el mismo estado.

## <a name="syntax"></a>Sintaxis

```Syntax
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [Boolean] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|  Propiedad  |  Descripción   |
|---|---|
|Nombre |Los nombres de los roles o características que quiere garantizar que se agreguen o se quiten. Estos son los mismos que con la propiedad **Name** del cmdlet [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) y no el nombre para mostrar de los roles o características. |
|Origen |Indica la ubicación del archivo de origen que se utilizará para la instalación, si es necesario. |
|IncludeAllSubFeature |Establezca esta propiedad en `$true` para incluir todas las subcaracterísticas requeridas de las características que se especifican con la propiedad **Name**. |
|Credential |Las credenciales que se usarán para agregar o quitar los roles o las características. |
|LogPath |La ruta de acceso al archivo de registro en el que desea que el proveedor de recursos registre la operación. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica si se agregan las funciones o características. Para asegurarse de que se agregan los roles o características, establezca esta propiedad en **Present**. Para asegurarse de que se quitan los roles o características, establezca la propiedad en **Absent**. El valor predeterminado es **Present**. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).

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