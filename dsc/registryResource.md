---
title: Recursos de DSC Registry
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: d94f178fb75d15b12268ad783f78183ceba9f2b3
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="dsc-registry-resource"></a>Recursos de DSC Registry

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

El recurso **Registry** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar valores y claves del Registro en un nodo de destino.

## <a name="syntax"></a>Sintaxis

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Absent | Present }  ]
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
| ValueName| Indica el nombre del valor del Registro.| 
| Ensure| Indica si existen la clave y valor. Para asegurarse de que existan, establezca esta propiedad en "Present". Para asegurarse de que no existan, establezca esta propiedad en "Absent". El valor predeterminado es "Present".| 
| Force| Si la clave del Registro especificada existe, __Force__ la sobrescribirá con el nuevo valor.| 
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



