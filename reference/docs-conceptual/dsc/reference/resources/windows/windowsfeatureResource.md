---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC WindowsFeature
ms.openlocfilehash: d3384b1f45324df6b6b209f25b64d9d77615ad7f
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954632"
---
# <a name="dsc-windowsfeature-resource"></a>Recurso de DSC WindowsFeature

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x

El recurso **WindowsFeature** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para asegurarse de que los roles y las características se agreguen o quiten en un nodo de destino.

## <a name="syntax"></a>Sintaxis

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ Source = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|Nombre |Indica el nombre del rol o la característica que quiere garantizar que se agregue o se quite. Esto es el mismo que la propiedad **Name** del cmdlet [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) y no el nombre para mostrar del rol o la característica. |
|Credential |Indica las credenciales que se usarán para agregar o quitar el rol o la característica. |
|IncludeAllSubFeature |Establezca esta propiedad en `$true` para garantizar el estado de todas las subcaracterísticas requeridas con el estado de la característica que se especifique con la propiedad **Name**. |
|LogPath |Indica la ruta de acceso a un archivo de registro donde quiera que el proveedor de recursos registre la operación. |
|Origen |Indica la ubicación del archivo de origen que se utilizará para la instalación, si es necesario. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica si se agrega el rol o la característica. Para asegurarse de que se agrega el rol o la característica, establezca esta propiedad en **Present**. Para asegurarse de que se quita el rol o la característica, establezca la propiedad en **Absent**. El valor predeterminado es **Present**. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Ejemplo

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```