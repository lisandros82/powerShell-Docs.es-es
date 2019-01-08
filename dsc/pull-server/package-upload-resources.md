---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Paquete y los recursos de carga para un servidor de extracción
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402298"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Paquete y los recursos de carga para un servidor de extracción

Las secciones siguientes se suponen que ya ha configurado un servidor de extracción. Si no ha configurado el servidor de incorporación de cambios, puede usar a las siguientes guías:

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)

Cada nodo de destino puede configurarse para descargar las configuraciones, recursos e incluso notificado su estado. En este artículo le mostrará cómo cargar recursos para que estén disponibles para descargarse y configurar clientes para descargar automáticamente los recursos. Cuando el nodo recibe una configuración asignada, a través de **extraer** o **Push** (v5), se descarga automáticamente todos los recursos requeridos por la configuración de la ubicación especificada en el LCM.

## <a name="package-resource-modules"></a>Módulos de recursos del paquete

Cada recurso disponible para el cliente descargue debe almacenarse en un archivo "zip". El ejemplo siguiente mostrará los pasos necesarios mediante el [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) recursos.

> [!NOTE]
> Si tiene cualquier cliente que emplee PowerShell 4.0, se deberá flaten la estructura de carpetas de recursos y quite las carpetas de versión. Para obtener más información, consulte [varias versiones de recursos](../configurations/import-dscresource.md#multiple-resource-versions).

Puede comprimir el directorio de recursos mediante cualquier utilidad, un script o un método que prefiera. En Windows, puede *haga* en el directorio "xPSDesiredStateConfiguration" y seleccione "Enviar a" y "Carpeta comprimida".

![Clic con el botón derecho](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>El archivo de recursos de nomenclatura

El archivo de recursos debe llamarse con el formato siguiente:

```
{ModuleName}_{Version}.zip
```

En el ejemplo anterior, "xPSDesiredStateConfiguration.zip" debe ser "xPSDesiredStateConfiguration_8.4.4.0.zip" cuyo nombre ha cambiado.

### <a name="create-checksums"></a>Cree sumas de comprobación

Una vez que el módulo de recursos se ha comprimido y se ha cambiado el nombre, deberá crear un **suma de comprobación**.  El **suma de comprobación** se usa el LCM en el cliente, para determinar si el recurso se ha cambiado y debe descargarse de nuevo. Puede crear un **suma de comprobación** con el [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, como se muestra en el ejemplo siguiente.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

No se mostrará ningún resultado, pero ahora debería ver un "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum". También puede ejecutar `New-DSCCheckSum` frente a un directorio de archivos mediante el `-Path` parámetro. Si ya existe una suma de comprobación, puede forzarlo a volver a crearse con el `-Force` parámetro.

### <a name="where-to-store-resource-archives"></a>Dónde almacenar los archivos de recursos

#### <a name="on-a-dsc-http-pull-server"></a>En un servidor de extracción de DSC

Al configurar el servidor de extracción HTTP, como se explica en [configurar un servidor de extracción de DSC HTTP](pullServer.md), especificar directorios de la **ModulePath** y **ConfigurationPath** claves. El **ConfigurationPath** clave indica dónde se deben almacenar los archivos "MOF". El **ModulePath** indica dónde se deben almacenar los módulos de recursos de DSC.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>En un recurso compartido SMB

Si ha especificado un **ResourceRepositoryShare**, al configurar el cliente de extracción, el almacén de archivos y las sumas de comprobación en el **SourcePath** directorio desde el **ResourceRepositoryShare** bloque.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

Si sólo especifica una **ConfigurationRepositoryShare**, al configurar el cliente de extracción, el almacén de archivos y las sumas de comprobación en el **SourcePath** directorio desde el  **ConfigurationRepositoryShare** bloque.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>Actualización de los recursos

Puede forzar un nodo para actualizar sus recursos cambiando el número de versión en el nombre del archivo, o mediante la creación de una nueva suma de comprobación. El cliente de incorporación de cambios buscará las versiones más recientes de los recursos necesarios, así como actualizar las sumas de comprobación, cuando se actualiza el LCM.

## <a name="see-also"></a>Vea también

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)
