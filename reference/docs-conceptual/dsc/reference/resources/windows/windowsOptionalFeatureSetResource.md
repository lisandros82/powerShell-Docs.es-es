---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso WindowsOptionalFeatureSet de DSC
ms.openlocfilehash: f378006a6c362ee9890d70dd76fb552dd262a544
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952872"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>Recurso WindowsOptionalFeatureSet de DSC

> Se aplica a: Windows PowerShell 5.x

El recurso **WindowsOptionalFeatureSet** de la configuración de estado deseado (DSC) de Windows PowerShell proporciona un mecanismo para asegurarse de que las características óptimas están habilitadas en un nodo de destino. Este es un [recurso compuesto](../../../resources/authoringResourceComposite.md) que llama el [recurso WindowsOptionalFeature](windowsOptionalFeatureResource.md) de cada una de las características especificadas en la propiedad **Name**.

Este recurso se usa cuando se desea configurar varias características opcionales de Windows para que tengan el mismo estado.

## <a name="syntax"></a>Sintaxis

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|Nombre |Indica el nombre de las características que desea asegurarse de que están habilitadas o deshabilitadas. |
|Origen |Sin implementar. |
|NoWindowsUpdateCheck |Especifica si DISM se pone en contacto con Windows Update (WU) al buscar los archivos de origen para habilitar características. Si el valor es `$true`, DISM no se pone en contacto con WU. |
|RemoveFilesOnDisable |Establézcalo en `$true` para quitar todos los archivos asociados con las características cuando el valor de **Ensure** sea **Absent**. |
|LogLevel |El nivel de salida máximo que se muestra en los registros. Los valores aceptados son: **ErrorsOnly**, **ErrorsAndWarning**, y **ErrorsAndWarningAndInformation**. |
|LogPath |La ruta de acceso al archivo de registro en el que desea que el proveedor de recursos registre la operación. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Especifica si las características están habilitadas. Para asegurarse de que las características están habilitadas, establezca esta propiedad en **Enable**. Para asegurarse de que las características están deshabilitadas, establezca la propiedad en **Disable**. El valor predeterminado es **Enable**. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).