---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Uso de Import-DSCResource
ms.openlocfilehash: 6bc3c1aa1d34a05e3188666da825322235c0672e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402770"
---
# <a name="using-import-dscresource"></a>Uso de Import-DSCResource

`Import-DScResource` es una palabra clave dinámica, que solo se puede usar dentro de un bloque de script de configuración. El `Import-DSCResource` palabra clave para importar todos los recursos necesarios en la configuración. Recursos en `$phsome` se importan automáticamente, pero todavía se considera una práctica recomendada para importar de forma explícita todos los recursos utilizados en su [configuración](Configurations.md).

La sintaxis de `Import-DSCResource` se muestra a continuación.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>]
```

|Parámetro  |Descripción  |
|---------|---------|
|`-Name`|Los nombres de recursos de DSC que se deben importar. Si se especifica el nombre del módulo, el comando busca estos recursos de DSC en este módulo; en caso contrario, el comando busca los recursos de DSC en todas las rutas de acceso de recursos de DSC. Se admiten los caracteres comodín.|
|`-ModuleName`|Los nombres de módulo contenedor o especificaciones del módulo.  Si especifica los recursos para importar desde un módulo, el comando intentará importar sólo esos recursos. Si especifica solo el módulo, el comando importa todos los recursos de DSC en el módulo.|

Puede usar caracteres comodín con el `-Name` al usar `Import-DSCResource`.

```powershell
Import-DscResource -Name * -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Ejemplo: Usar Import-DSCResource dentro de una configuración

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName MS_DSC1 -name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    Import-DSCResource -Name File, TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
...
```

> [!NOTE]
> No se admite especificar varios valores para los nombres de recursos y los nombres de los módulos en el mismo comando. Puede tener un comportamiento no determinista sobre qué recursos se deben cargar desde qué módulo del mismo recurso si existe en varios módulos. A continuación el comando producirá error durante la compilación.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Cosas a tener en cuenta cuando se usa solo el parámetro de nombre:

- Es una operación que consume muchos recursos según el número de módulos instalados en el equipo.
- Cargará el primer recurso que se encuentra con el nombre especificado. En el caso donde hay más de un recurso con el mismo nombre que se instala, se pudo cargar el recurso incorrecto.

El uso recomendado consiste en especificar `–ModuleName` con el `-Name` parámetro, tal como se describe a continuación.

Este uso tiene las siguientes ventajas:

- Reduce el impacto del rendimiento al limitar el ámbito de búsqueda para el recurso especificado.
- Define explícitamente el módulo de definición del recurso, asegurarse de que se carga el recurso correcto.

> [!NOTE]
> En PowerShell 5.0, los recursos de DSC pueden tener varias versiones, y las versiones pueden instalarse en un equipo en paralelo. Esto se implementa mediante varias versiones de un módulo de recursos que están contenidas en la misma carpeta del módulo.
> Para más información, consulte [Uso de recursos con varias versiones](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense con Import-DSCResource

Al crear la configuración de DSC en el ISE, PowerShell proporciona IntelliSence para los recursos y las propiedades de recursos. Las definiciones de recursos en el `$pshome` ruta de acceso del módulo se cargan automáticamente. Al importar los recursos mediante el `Import-DSCResource` palabra clave, se agregan las definiciones de recursos especificado y Intellisense se expande para incluir el esquema del recurso importado.

![Intellisense de recursos](/media/resource-intellisense.png)

> [!NOTE]
> A partir de PowerShell 5.0, finalización con tabulación se ha agregado al ISE para los recursos de DSC y sus propiedades. Para obtener más información, consulte [recursos](../resources/resources.md).

Al compilar la configuración, PowerShell usa las definiciones de recursos importados para validar todos los bloques de recursos en la configuración.
Se valida cada bloque de recursos, mediante la definición de esquema del recurso, para las siguientes reglas.

- Se utilizan solo las propiedades definidas en el esquema.
- Los tipos de datos para cada propiedad son correctos.
- Propiedades de las claves se especifican.
- No se usa ninguna propiedad de solo lectura.
- Asigna los tipos de validación en el valor.

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
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

Compilar esta configuración da como resultado un error.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

IntelliSense y validación de esquema permiten detectar más errores durante el tiempo de análisis y compilación, evitar las complicaciones en tiempo de ejecución.

> [!NOTE]
> Cada recurso de DSC puede tener un nombre y un **FriendlyName** definido por el esquema del recurso. A continuación se muestran las dos primeras líneas de "MSFT_ServiceResource.shema.mof".
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Cuando se usa este recurso en una configuración, puede especificar **MSFT_ServiceResource** o **servicio**.

## <a name="powershell-v4-and-v5-differences"></a>Diferencias de PowerShell v4 y v5

Hay varias diferencias que verá cuando se crean configuraciones en PowerShell 4.0 vs. PowerShell 5.0 y versiones posterior. En esta sección se resaltan las diferencias que ve correspondientes a este artículo.

### <a name="multiple-resource-versions"></a>Varias versiones de recursos

Instalación y uso de varias versiones de los recursos en paralelo no se admiten en PowerShell 4.0. Si observa problemas al importar recursos en la configuración, asegúrese de que solo tiene una versión del recurso instalado.

En la imagen siguiente, dos versiones de la **xPSDesiredStateConfiguration** módulo se instalan.

![Se ha corregido varias versiones de recursos](/media/multiple-resource-versions-broken.md)

Copie el contenido de la versión del módulo deseado en el nivel superior del directorio de módulo.

![Se ha corregido varias versiones de recursos](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Ubicación de los recursos

Hora de crear y compilar configuraciones, los recursos se pueden almacenar en cualquier directorio especificado por su [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). El LCM en PowerShell 4.0, requiere que todos los módulos de recursos de DSC que se almacenará en "Programa Files\WindowsPowerShell\Modules" o `$pshome\Modules`. A partir de PowerShell 5.0, se ha quitado este requisito, y los módulos de recursos se pueden almacenar en cualquier directorio especificado por `PSModulePath`.

## <a name="see-also"></a>Vea también

- [Recursos](../resources/resources.md)
