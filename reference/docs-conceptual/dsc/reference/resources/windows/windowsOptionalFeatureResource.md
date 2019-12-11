---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso WindowsOptionalFeature de DSC
ms.openlocfilehash: 7312edcaeb47427bf4736f466a9ed41bd7c31f6a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954652"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>Recurso WindowsOptionalFeature de DSC

> Se aplica a: Windows PowerShell 5.x

El recurso **WindowsOptionalFeature** de la configuración de estado deseado (DSC) de Windows PowerShell proporciona un mecanismo para asegurarse de que las características óptimas están habilitadas en un nodo de destino.

## <a name="syntax"></a>Sintaxis

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Source = [string[]] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|Nombre |Indica el nombre de la característica que desea asegurarse de que está habilitada o deshabilitada. |
|Origen |Sin implementar. |
|NoWindowsUpdateCheck |Especifica si DISM se pone en contacto con Windows Update (WU) al buscar los archivos de origen para habilitar una característica. Si el valor es `$true`, DISM no se pone en contacto con WU. |
|RemoveFilesOnDisable |Establézcalo en `$true` para quitar todos los archivos asociados con la característica cuando el valor de **Ensure** sea **Absent**. |
|LogLevel |El nivel de salida máximo que se muestra en los registros. Los valores aceptados son: **ErrorsOnly**, **ErrorsAndWarning**, y **ErrorsAndWarningAndInformation**. |
|LogPath |La ruta de acceso al archivo de registro en el que desea que el proveedor de recursos registre la operación. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Especifica si la característica está habilitada. Para asegurarse de que la característica está habilitada, establezca esta propiedad en _Enable_. Para asegurarse de que la característica está deshabilitada, establezca esta propiedad en _Disable_. El valor predeterminado es _Enable_. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).