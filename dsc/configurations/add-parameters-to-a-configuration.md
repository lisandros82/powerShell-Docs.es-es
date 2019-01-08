---
ms.date: 12/12/2018
keywords: DSC, powershell, recursos, la galería, el programa de instalación
title: Agregar parámetros a una configuración
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402554"
---
# <a name="add-parameters-to-a-configuration"></a>Agregar parámetros a una configuración

Al igual que las funciones, [configuraciones](configurations.md) se puede parametrizar para permitir que las configuraciones más dinámicas basadas en la entrada del usuario. Los pasos son similares a las descritas en [funciones con parámetros](/powershell/module/microsoft.powershell.core/about/about_functions).

Este ejemplo comienza con una configuración básica que configura el servicio de "Cola" a "Running".

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

A diferencia de una función sin embargo, el [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) atributo no agrega ninguna funcionalidad. Además [parámetros comunes de](/powershell/module/microsoft.powershell.core/about/about_commonparameters), las configuraciones también pueden usar lo siguiente creado en los parámetros, sin tener que definirlas.

|Parámetro  |Descripción  |
|---------|---------|
|`-InstanceName`|Usar para definir [configuraciones compuesto](compositeconfigs.md)|
|`-DependsOn`|Usar para definir [configuraciones compuesto](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Usar para definir [configuraciones compuesto](compositeconfigs.md)|
|`-ConfigurationData`|Usa para pasar estructurado en [datos de configuración](configData.md) para su uso en la configuración.|
|`-OutputPath`|Se utiliza para especificar dónde su "\<computername\>.mof" se compilará el archivo|

## <a name="adding-your-own-parameters-to-configurations"></a>Agregar sus propios parámetros a las configuraciones

Además de los parámetros integrados, también puede agregar sus propios parámetros a las configuraciones. El bloque de parámetros que se pasa directamente dentro de la declaración de la configuración, al igual que una función. Debe ser un bloque de parámetros de configuración fuera de cualquier **nodo** declaraciones y por encima *importar* instrucciones. Mediante la adición de parámetros, puede realizar las configuraciones más robusto y dinámico.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Agregar un parámetro ComputerName

Es el primer parámetro puede agregar un `-Computername` parámetro, por lo que puede compilar dinámicamente un archivo ".mof" para cualquier `-Computername` pasa a la configuración. Como las funciones, también puede definir un valor predeterminado, en caso de que no pasa un valor para el usuario `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

Dentro de la configuración, a continuación, puede especificar su `-ComputerName` al definir el bloque del nodo de parámetro.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Llame a su configuración con parámetros

Después de agregar parámetros a la configuración, puede usar tal como lo haría con un cmdlet.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Compilar varios archivos .mof

El bloque de nodo también puede aceptar una lista separada por comas de nombres de equipo y generará archivos ".mof" para cada uno. Puede ejecutar el ejemplo siguiente para generar archivos de "MOF" para todos los equipos que se pasa a la `-ComputerName` parámetro.

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

Además un `-ComputerName` parámetro, podemos agregar parámetros para el nombre del servicio y el estado. En el ejemplo siguiente se agrega un bloque de parámetros con un `-ServiceName` parámetro y lo usa para definir de forma dinámica el **servicio** bloque de recursos. También agrega un `-State` parámetro para definir de forma dinámica el **estado** en el **servicio** bloque de recursos.

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
> En otros escenarios advacned, es posible que más sentido para mover los datos dinámicos en un modo estructurado [datos de configuración](configData.md).

El ejemplo de configuración ahora toma una dinámica `$ServiceName`, pero si no se especifica, se produce un error de compilación. Puede agregar un valor predeterminado como en este ejemplo.

```powershell
[String]
$ServiceName="Spooler"
```

En este caso, tiene más sentido simplemente debe forzar al usuario especificar un valor para el `$ServiceName` parámetro. El `parameter` atributo le permite agregar validación adicional y la canalización se admiten para los parámetros de la configuración.

Encima de cualquier declaración de parámetro, agregue el `parameter` bloque de atributos como se muestra en el ejemplo siguiente.

```powershell
[parameter()]
[String]
$ServiceName
```

Puede especificar argumentos para cada uno de ellos `parameter` atributo para controlar los aspectos del parámetro definido. En el ejemplo siguiente se realiza la `$ServiceName` un **obligatorio** parámetro.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Para el `$State` parámetro, nos gustaría evitar que el usuario especifica los valores fuera de un conjunto predefinido (como en ejecución, detenido) el `ValidationSet*`atributo evitaría que el usuario especifica los valores fuera de un conjunto predefinido (por ejemplo, en ejecución, Detenido). En el ejemplo siguiente se agrega el `ValidationSet` atributo a la `$State` parámetro. Puesto que deseamos realizar la `$State` parámetro **obligatorio**, necesitamos agregar un valor predeterminado para ella.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> No es necesario especificar un `parameter` atributo cuando se usa un `validation` atributo.

Puede leer más sobre la `parameter` y atributos de validación en [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).

## <a name="fully-parameterized-configuration"></a>Configuración totalmente parametrizado

Ahora tenemos una configuración parametrizada que obliga al usuario especificar un `-InstanceName`, `-ServiceName`y valida el `-State` parámetro.

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
- [Configuración dinámica](flow-control-in-configurations.md)
- [Usar datos de configuración en las configuraciones](configData.md)
- [Datos de configuración y el entorno independiente](separatingEnvData.md)
