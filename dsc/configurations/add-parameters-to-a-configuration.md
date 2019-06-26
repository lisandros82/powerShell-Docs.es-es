---
ms.date: 12/12/2018
keywords: dsc,powershell,resource,gallery,setup
title: Agregar parámetros a una configuración
ms.openlocfilehash: 514bb4cf82b7adbe4cd3d3e34d5464f574cb2206
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301513"
---
# <a name="add-parameters-to-a-configuration"></a>Agregar parámetros a una configuración

Al igual que las funciones, las [configuraciones](configurations.md) se pueden parametrizar para permitir configuraciones más dinámicas basadas en la entrada del usuario. Los pasos son similares a las descritos en [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions) (Funciones con parámetros).

Este ejemplo comienza con una configuración básica que configura el servicio "Spooler" para que su estado sea "Running".

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a>Parámetros de configuración integrados

A diferencia de una función, el atributo [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) no agrega ninguna funcionalidad. Además de los [parámetros comunes](/powershell/module/microsoft.powershell.core/about/about_commonparameters), las configuraciones también pueden usar los siguiente parámetros integrados, sin necesidad que definirlos.

|Parámetro  |Descripción  |
|---------|---------|
|`-InstanceName`|Se utiliza para definir [configuraciones compuestas](compositeconfigs.md).|
|`-DependsOn`|Se utiliza para definir [configuraciones compuestas](compositeconfigs.md).|
|`-PSDSCRunAsCredential`|Se utiliza para definir [configuraciones compuestas](compositeconfigs.md).|
|`-ConfigurationData`|Se utiliza para pasar [datos de configuración](configData.md) estructurados para su uso en la configuración.|
|`-OutputPath`|Se utiliza para especificar dónde se compilará su archivo "\<computername\>.mof".|

## <a name="adding-your-own-parameters-to-configurations"></a>Adición de sus propios parámetros a las configuraciones

Además de los parámetros integrados, también puede agregar sus propios parámetros a las configuraciones. El bloque de parámetros se pasa directamente a la declaración de la configuración, igual que una función. Un bloque de parámetros de configuración debe estar fuera de cualquier declaración de **nodo** y por encima de cualquier instrucción de *importación*. Al agregar parámetros, puede hacer que sus configuraciones sean más robustas y dinámicas.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Adición de un parámetro ComputerName

El primer parámetro que podría agregar es un parámetro `-Computername`, de manera que podría compilar un archivo ".mof" para cualquier `-Computername` que pase a la configuración. Al igual que las funciones, también puede definir un valor predeterminado, en caso de que el usuario no pase un valor para `-ComputerName`.

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

Dentro de la configuración, puede especificar a continuación su parámetro `-ComputerName` al definir el bloque del nodo.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Llamada a su configuración con parámetros

Después de agregar parámetros a la configuración, puede usarlos tal como lo haría con un cmdlet.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Compilación de varios archivos .mof

El bloque de nodo también puede aceptar una lista separada por comas de nombres de equipos, y generará archivos ".mof" para cada uno. Puede ejecutar el ejemplo siguiente para generar archivos ".mof" para todos los equipos que se pasan al parámetro `-ComputerName`.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a>Parámetros avanzados en las configuraciones

Además un parámetro `-ComputerName`, podemos agregar parámetros para el nombre y el estado del servicio. En el ejemplo siguiente se agrega un bloque de parámetros con un parámetro `-ServiceName` y se usa para definir de forma dinámica el bloque de recursos **Service**. También agrega un parámetro `-State` para definir de forma dinámica el **estado** en el bloque de recursos **Service**.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> En escenarios más avanzados, es posible que tenga más sentido mover los datos dinámicos en [datos de configuración](configData.md) estructurados.

El ejemplo de configuración ahora toma un `$ServiceName` dinámico, pero si no se especifica uno, se produce un error de compilación. Puede agregar un valor predeterminado como en este ejemplo.

```powershell
[String]
$ServiceName="Spooler"
```

Sin embargo, en este caso tiene más sentido simplemente obligar al usuario a especificar un valor para el parámetro `$ServiceName`. El atributo `parameter` le permite agregar más compatibilidad con la validación y la canalización para los parámetros de configuración.

Encima de cualquier declaración de parámetro, agregue el bloque de atributos `parameter` como se muestra en el ejemplo siguiente.

```powershell
[parameter()]
[String]
$ServiceName
```

Puede especificar argumentos para cada atributo `parameter`, para controlar los aspectos del parámetro definido. En el ejemplo siguiente se hace de `$ServiceName` un parámetro de tipo obligatorio (**Mandatory**).

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Para el parámetro `$State`, nos gustaría evitar que el usuario especificara los valores fuera de un conjunto predefinido (como Running, Stopped); el atributo `ValidationSet*` evitaría que el usuario especificara los valores fuera de un conjunto predefinido (como Running, Stopped). En el ejemplo siguiente se agrega el atributo `ValidationSet` al parámetro `$State`. Puesto que no deseamos que el parámetro `$State` sea de tipo **Mandatory**, tenemos que agregarle un valor predeterminado.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> No es necesario especificar un atributo `parameter` cuando se usa un atributo `validation`.

Puede leer más sobre `parameter` y los atributos de validación en [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters) (Acerca de los parámetros avanzados de funciones).

## <a name="fully-parameterized-configuration"></a>Configuración totalmente parametrizada

Ahora tenemos una configuración parametrizada que obliga al usuario a especificar un valor `-InstanceName`, `-ServiceName` y valida el parámetro `-State`.

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a>Vea también

- [Escritura de la ayuda de las configuraciones de DSC](configHelp.md)
- [Configuraciones dinámicas](flow-control-in-configurations.md)
- [Uso de datos de configuración en DSC](configData.md)
- [Separación de los datos de entorno y configuración](separatingEnvData.md)
