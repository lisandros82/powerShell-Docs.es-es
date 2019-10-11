---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC Registry
ms.openlocfilehash: be2f9134368784ad2d208362104ce046c49492e0
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953082"
---
# <a name="dsc-registry-resource"></a>Recursos de DSC Registry

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x

El recurso **Registry** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar valores y claves del Registro en un nodo de destino.

## <a name="syntax"></a>Sintaxis

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|Clave |Indica la ruta de acceso de la clave del Registro para la que quiere garantizar un estado específico. Esta ruta de acceso debe incluir el subárbol. |
|ValueName |Indica el nombre del valor del Registro. Para agregar o quitar una clave del Registro, especifique esta propiedad como una cadena vacía sin especificar **ValueType** ni **ValueData**. Para modificar o quitar el valor predeterminado de una clave del Registro, especifique esta propiedad como una cadena vacía y especifique también **ValueType** o **ValueData**. |
|Force |Si la clave del Registro especificada existe, **Force** la sobrescribirá con el nuevo valor. Si elimina una clave del Registro con subclaves, debe ser `$true`. |
|Hex |Indica si los datos se expresarán en formato hexadecimal. Si se especifica, los datos de valores DWORD o QWORD se muestran en formato hexadecimal. No es válido para otros tipos. El valor predeterminado es `$false`. |
|ValueData |Los datos para el valor del Registro. |
|ValueType |Indica el tipo del valor. Los tipos admitidos son: **cadena** (REG_SZ), **Binario** (REG-BINARY), **Dword** (REG_DWORD de 32 bits), **Qword** (REG_QWORD de 64 bits), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ). |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica si existen la clave y valor. Para asegurarse de que existan, establezca esta propiedad en **Present**. Para asegurarse de que no existan, establezca esta propiedad en **Absent**. El valor predeterminado es **Present**. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).

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
> Cambiar una configuración de registro en el subárbol `HKEY_CURRENT_USER` requiere que la configuración se ejecute con las credenciales de usuario y no como el sistema. Puede usar la propiedad **PsDscRunAsCredential** para especificar las credenciales de usuario para la configuración. Para obtener un ejemplo, consulte [DSC de ejecución con las credenciales de usuario](../../../configurations/runAsUser.md).