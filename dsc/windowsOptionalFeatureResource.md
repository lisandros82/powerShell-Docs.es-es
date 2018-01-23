---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso WindowsOptionalFeature de DSC
ms.openlocfilehash: d9b8cc316255f06d2de71fedc47ce4472cc8b382
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsoptionalfeature-resource"></a>Recurso WindowsOptionalFeature de DSC

> Se aplica a: Windows PowerShell 5.0

El recurso **WindowsOptionalFeature** de la configuración de estado deseado (DSC) de Windows PowerShell proporciona un mecanismo para asegurarse de que las características óptimas están habilitadas en un nodo de destino.

## <a name="syntax"></a>Sintaxis

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a>Propiedades

|  Propiedad  |  Descripción   | 
|---|---| 
| Nombre| Indica el nombre de la característica que desea asegurarse de que está habilitada o deshabilitada.| 
| Ensure| Especifica si la característica está habilitada. Para asegurarse de que la característica está habilitada, establezca esta propiedad en "Enable"; para asegurarse de que está deshabilitada, establezca la propiedad en "Disable".|
| Origen| Sin implementar.|
| NoWindowsUpdateCheck| Especifica si DISM se pone en contacto con Windows Update (WU) al buscar los archivos de origen para habilitar una característica. Si el valor es $true, DISM no se pone en contacto con WU.|
| RemoveFilesOnDisable| Establézcalo en **$true** para quitar todos los archivos asociados con la característica cuando se deshabilite (es decir, cuando el valor de **Ensure** (Asegurar) sea "Absent").|
| LogLevel| El nivel de salida máximo que se muestra en los registros. Los valores aceptados son: "ErrorsOnly" (solo se registran los errores), "ErrorsAndWarning" (se registran los errores y las advertencias) y "ErrorsAndWarningAndInformation" (se registran los errores, las advertencias y la información de depuración).|
| LogPath| La ruta de acceso al archivo de registro en el que desea que el proveedor de recursos registre la operación.| 
| DependsOn| Especifica que debe ejecutarse la configuración de otro recurso antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.| 
 



