---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC Registry
ms.openlocfilehash: 649cb60578c053c04a7fcc7446881fb76daee26a
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-registry-resource"></a>Recursos de DSC Registry

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

El recurso **Registry** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar valores y claves del Registro en un nodo de destino.

## <a name="syntax"></a>Sintaxis

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Propiedades
|  Propiedad  |  Descripción   | 
|---|---| 
| Clave| Indica la ruta de acceso de la clave del Registro para la que quiere garantizar un estado específico. Esta ruta de acceso debe incluir el subárbol.| 
| ValueName| Indica el nombre del valor del Registro. Para agregar o quitar una clave del Registro, especifique esta propiedad como una cadena vacía sin especificar ValueType ni ValueData. Para modificar o quitar el valor predeterminado de una clave del Registro, especifique esta propiedad como una cadena vacía y especifique también ValueType o ValueData.| 
| Ensure| Indica si existen la clave y valor. Para asegurarse de que existan, establezca esta propiedad en "Present". Para asegurarse de que no existan, establezca esta propiedad en "Absent". El valor predeterminado es "Present".| 
| Force| Si la clave del Registro especificada existe, __Force__ la sobrescribirá con el nuevo valor. Si elimina una clave del Registro con subclaves, debe ser __$true__| 
| Hex| Indica si los datos se expresarán en formato hexadecimal. Si se especifica, los datos de valores DWORD o QWORD se muestran en formato hexadecimal. No es válido para otros tipos. El valor predeterminado es __$false__.| 
| DependsOn| Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.| 
| ValueData| Los datos para el valor del Registro.| 
| ValueType| Indica el tipo del valor. Los tipos admitidos son: 
<ul><li>Cadena (REG_SZ)</li>


<li>Binario (REG-BINARY)</li>


<li>Dword de 32 bits (REG_DWORD)</li>


<li>Qword de 64 bits (REG_QWORD)</li>


<li>Cadena múltiple (REG_MULTI_SZ)</li>


<li>Cadena expandible (REG_EXPAND_SZ)</li></ul>

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

>**Nota:** Cambiar una configuración de registro en el subárbol **HKEY\_CURRENT\_USER** requiere que la configuración se ejecute con las credenciales de usuario y no como el sistema.
>Puede usar la propiedad **PsDscRunAsCredential** para especificar las credenciales de usuario para la configuración. Para obtener un ejemplo, vea [DSC de ejecución con las credenciales de usuario](runAsUser.md).



