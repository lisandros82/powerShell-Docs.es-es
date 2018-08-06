---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC Registry
ms.openlocfilehash: 8d74473d167b70182c3a16c1d39d2a9e797afb1b
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267728"
---
# <a name="dsc-registry-resource"></a>Recursos de DSC Registry

_Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0_

El recurso **Registry** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar valores y claves del Registro en un nodo de destino.

## <a name="syntax"></a>Sintaxis

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Propiedades

| Propiedad | Descripción |
| --- | --- |
| Clave| Indica la ruta de acceso de la clave del Registro para la que quiere garantizar un estado específico. Esta ruta de acceso debe incluir el subárbol.|
| ValueName| Indica el nombre del valor del Registro. Para agregar o quitar una clave del Registro, especifique esta propiedad como una cadena vacía sin especificar ValueType ni ValueData. Para modificar o quitar el valor predeterminado de una clave del Registro, especifique esta propiedad como una cadena vacía y especifique también ValueType o ValueData.|
| Ensure| Indica si existen la clave y valor. Para asegurarse de que existan, establezca esta propiedad en "Present". Para asegurarse de que no existan, establezca esta propiedad en "Absent". El valor predeterminado es "Present".|
| Force| Si la clave del Registro especificada existe, **Force** la sobrescribirá con el nuevo valor. Si elimina una clave del Registro con subclaves, debe ser **$true** |
| Hex| Indica si los datos se expresarán en formato hexadecimal. Si se especifica, los datos de valores DWORD o QWORD se muestran en formato hexadecimal. No es válido para otros tipos. El valor predeterminado es **$false**.|
| DependsOn| Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.|
| ValueData| Los datos para el valor del Registro.|
| ValueType| Indica el tipo del valor. Los tipos admitidos son: cadena (REG_SZ), binario (REG-BINARY), Dword de 32 bits (REG_DWORD), Qword de 64 bits (REG_QWORD), cadena múltiple (REG_MULTI_SZ), cadena expandible (REG_EXPAND_SZ) |

## <a name="example"></a>Ejemplo

Este ejemplo garantiza que una clave denominada "ExampleKey" está presente en el subárbol **HKEY\_LOCAL\_MACHINE**.

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> Cambiar una configuración de registro en el subárbol `HKEY\CURRENT\USER` requiere que la configuración se ejecute con las credenciales de usuario y no como el sistema. Puede usar la propiedad **PsDscRunAsCredential** para especificar las credenciales de usuario para la configuración. Para obtener un ejemplo, consulte [DSC de ejecución con las credenciales de usuario](runAsUser.md).