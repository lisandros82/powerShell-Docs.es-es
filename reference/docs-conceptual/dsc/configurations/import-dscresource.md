---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Uso de Import-DSCResource
ms.openlocfilehash: f6c1260bac7d4c545f5a6bc4c098ca90ebb186b5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954062"
---
# <a name="using-import-dscresource"></a>Uso de Import-DSCResource

`Import-DScResource` es una palabra clave dinámica, que solo se puede usar dentro de un bloque de script de configuración. La palabra clave `Import-DSCResource` para importar los recursos necesarios en la configuración. Los recursos en `$pshome` se importan automáticamente, pero se sigue considerando recomendable importar de forma explícita todos los recursos utilizados en su [configuración](Configurations.md).

La sintaxis de `Import-DSCResource` se muestra a continuación.  Al especificar módulos por nombre, es necesario enumerar cada uno en una nueva línea.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|Parámetro  |Descripción  |
|---------|---------|
|`-Name`|Los nombres de recursos de DSC que debe importar. Si se especifica el nombre del módulo, el comando busca estos recursos de DSC en este módulo; en caso contrario, el comando busca los recursos de DSC en todas las rutas de acceso de recursos de DSC. Se admiten los caracteres comodín.|
|`-ModuleName`|El nombre del módulo, o especificación de módulo.  Si especifica los recursos para importar desde un módulo, el comando intentará importar solo esos recursos. Si especifica solo el módulo, el comando importa todos los recursos de DSC en el módulo.|
|`-ModuleVersion`|A partir de PowerShell 5.0, puede especificar la versión de un módulo que debería usar una configuración. Para obtener más información, vea [Importación de una versión específica de un recurso instalado](sxsresource.md).|

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Ejemplo: Uso de Import-DSCResource dentro de una configuración

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    # In PowerShell 5.0 and later, you can specify a ModuleVersion parameter
    Import-DSCResource -ModuleName ComputerManagementDsc -ModuleVersion 6.0.0.0
...
```

> [!NOTE]
> No se admite la especificación de varios valores para los nombres de recursos y los nombres de los módulos en el mismo comando. Puede tener un comportamiento no determinista sobre qué recurso se debe cargar desde qué módulo si existe el mismo recurso en varios módulos. El comando siguiente producirá error durante la compilación.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Aspectos para tener en cuenta cuando se usa solo el parámetro de nombre:

- Es una operación que consume muchos recursos, dependiendo del número de módulos instalados en el equipo.
- Cargará el primer recurso que se encuentre con el nombre especificado. En caso de que haya instalado más de un recurso con el mismo nombre, podría cargarse el recurso incorrecto.

El uso recomendado consiste en especificar `–ModuleName` con el parámetro `-Name`, tal como se describe a continuación.

Este uso tiene las siguientes ventajas:

- Reduce el impacto del rendimiento al limitar el ámbito de búsqueda para el recurso especificado.
- Define explícitamente el módulo que define del recurso, garantizando que se carga el recurso correcto.

> [!NOTE]
> En PowerShell 5.0, los recursos de DSC pueden tener varias versiones, y las versiones pueden instalarse en un equipo en paralelo. Esto se implementa mediante varias versiones de un módulo de recursos que están contenidas en la misma carpeta del módulo.
> Para más información, consulte [Uso de recursos con varias versiones](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense con Import-DSCResource

Al crear la configuración de DSC en el ISE, PowerShell proporciona IntelliSence para los recursos y las propiedades de recursos. Las definiciones de recursos en la ruta de acceso del módulo `$pshome` se cargan automáticamente. Al importar los recursos mediante la palabra clave `Import-DSCResource`, se agregan las definiciones de recursos especificadas e Intellisense se expande para incluir el esquema del recurso importado.

![Intellisense para recursos](../media/resource-intellisense.png)

> [!NOTE]
> A partir de PowerShell 5.0, se agregó la finalización con tabulación al ISE para los recursos de DSC y sus propiedades. Para obtener más información, consulte [Recursos](../resources/resources.md).

Al compilar la configuración, PowerShell usa las definiciones de recursos importados para validar todos los bloques de recursos en la configuración.
Cada bloque de recursos se valida mediante la definición de esquema de recursos, para las siguientes reglas.

- Se utilizan solo las propiedades definidas en el esquema.
- Los tipos de datos para cada propiedad son correctos.
- Se especifican las propiedades de las claves.
- No se usa ninguna propiedad de solo lectura.
- La validación sobre el valor asigna tipos.

Tenga en cuenta la siguiente configuración:

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = "Telnet-Client"
            Ensure = "Invalid"
        }
    }
}
```

La compilación de esta configuración da como resultado un error.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values: Present, Absent.
```

IntelliSense y la validación de esquema permiten detectar más errores durante el tiempo de análisis y compilación, evitando las complicaciones en tiempo de ejecución.

> [!NOTE]
> Cada recurso de DSC puede tener un nombre y un **FriendlyName** definido por el esquema del recurso. A continuación se muestran las dos primeras líneas de "MSFT_ServiceResource.shema.mof".
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Cuando se usa este recurso en una configuración, puede especificar **MSFT_ServiceResource** o **Service**.

## <a name="powershell-v4-and-v5-differences"></a>Diferencias de PowerShell v4 y v5

Hay varias diferencias que verá al crear configuraciones en PowerShell 4.0 en comparación con Windows PowerShell 5.0 y posteriores. En esta sección se destacan las diferencias que verá y que son pertinentes para este artículo.

### <a name="multiple-resource-versions"></a>Varias versiones de recursos

La instalación y el uso de varias versiones de recursos en paralelo no se admite en PowerShell 4.0. Si observa problemas al importar recursos en la configuración, asegúrese de que solo tiene una versión del recurso instalada.

En la imagen siguiente, se instalan dos versiones del módulo **xPSDesiredStateConfiguration**.

![Corrección de varias versiones de recursos](../media/multiple-resource-versions-broken.png)

Copie el contenido de la versión del módulo deseada en el nivel superior del directorio de módulo.

![Corrección de varias versiones de recursos](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a>Ubicación de los recursos

Al crear y compilar configuraciones, los recursos se pueden almacenar en cualquier directorio especificado por su [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). En PowerShell 4.0, LCM requiere que todos los módulos de recursos de DSC se almacenen en "Archivos de programa\WindowsPowerShell\Modules" o `$pshome\Modules`. A partir de PowerShell 5.0, esto ya no es necesario, y los módulos de recursos se pueden almacenar en cualquier directorio especificado por `PSModulePath`.

### <a name="moduleversion-added"></a>Agregado el parámetro ModuleVersion

A partir de PowerShell 5.0, el parámetro `-ModuleVersion` le permite especificar la versión de un módulo que va a usar en la configuración.

## <a name="see-also"></a>Vea también

- [Recursos](../resources/resources.md)
