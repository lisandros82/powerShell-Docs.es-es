---
title: Recurso WindowsOptionalFeatureSet de DSC
ms.date: 2016-05-24
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 97714d3fa9a1c00fb3d2e79cc873280ca945a840
ms.openlocfilehash: 52eb958e59ecb1d5ae3faf268933bbd544410d47

---

# Recurso WindowsOptionalFeatureSet de DSC

> Se aplica a: Windows PowerShell 5.0

El recurso **WindowsOptionalFeatureSet** de la configuración de estado deseado (DSC) de Windows PowerShell proporciona un mecanismo para asegurarse de que las características óptimas están habilitadas en un nodo de destino. Este es un [recurso compuesto](authoringResourceComposite.md) que llama el [recurso WindowsOptionalFeature](windowsOptionalFeatureResource.md) de cada una de las características especificadas en la propiedad `Name`.

Este recurso se usa cuando se desea configurar varias características opcionales de Windows para que tengan el mismo estado.

## Sintaxis

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ] 
    [ RemoveFilesOnDisable = [bool] ]  
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    
}
```

## Propiedades

|  Propiedad  |  Descripción   | 
|---|---| 
| Nombre| Indica el nombre de las características que desea asegurarse de que están habilitadas o deshabilitadas.| 
| Ensure| Especifica si las características están habilitadas. Para asegurarse de que las características están habilitadas, establezca esta propiedad en "Present"; para asegurarse de que están deshabilitadas, establezca la propiedad en "Absent".|
| Origen| Sin implementar.|
| NoWindowsUpdateCheck| Especifica si DISM se pone en contacto con Windows Update (WU) al buscar los archivos de origen para habilitar características. Si el valor es $true, DISM no se pone en contacto con WU.|
| RemoveFilesOnDisable| Establézcalo en **$true** para quitar todos los archivos asociados con las características cuando se deshabiliten (es decir, cuando el valor de **Ensure** (Asegurar) sea "Absent").|
| LogLevel| El nivel de salida máximo que se muestra en los registros. Los valores aceptados son: "ErrorsOnly" (solo se registran los errores), "ErrorsAndWarning" (se registran los errores y las advertencias) y "ErrorsAndWarningAndInformation" (se registran los errores, las advertencias y la información de depuración).|
| LogPath| La ruta de acceso al archivo de registro en el que desea que el proveedor de recursos registre la operación.| 
| DependsOn| Especifica que debe ejecutarse la configuración de otro recurso antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.| 
 






<!--HONumber=Jul16_HO1-->


