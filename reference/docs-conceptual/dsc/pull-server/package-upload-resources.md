---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Empaquetado y carga de recursos en un servidor de extracción
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954382"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Empaquetado y carga de recursos en un servidor de extracción

En las secciones siguientes se supone que ya ha configurado un servidor de extracción. De no ser así, puede usar las siguientes guías:

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)

Cada nodo de destino puede configurarse para descargar configuraciones y recursos, e incluso para notificar de su estado. Este artículo le mostrará cómo cargar recursos para que estén disponibles para su descarga, así como configurar clientes para descargar automáticamente los recursos. Cuando el nodo recibe una configuración asignada, a través de **extracción** o **inserción** (v5), descarga automáticamente todos los recursos requeridos por la configuración de la ubicación especificada en el LCM.

## <a name="package-resource-modules"></a>Módulos del recurso Package

Cada recurso disponible para que un cliente lo descargue debe almacenarse en un archivo ".zip". El siguiente ejemplo mostrará los pasos necesarios utilizando el recurso [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0).

> [!NOTE]
> Si tiene clientes que utilizan PowerShell 4.0, deberá aplanar la estructura de la carpeta de recursos y eliminar las carpetas de la versión. Para obtener más información, consulte [Varias versiones de recursos](../configurations/import-dscresource.md#multiple-resource-versions).

Puede comprimir el directorio de recursos mediante cualquier utilidad, script o método que prefiera. En Windows, puede *hacer clic con el botón derecho* en el directorio "xPSDesiredStateConfiguration" y seleccionar "Enviar a" y luego "Carpeta comprimida".

![Clic con el botón derecho](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>Cambio de nombre del archivo de recursos

El archivo de recursos debe tener un nombre con este formato:

```
{ModuleName}_{Version}.zip
```

En el ejemplo anterior, el nombre "xPSDesiredStateConfiguration.zip" debe cambiarse a "xPSDesiredStateConfiguration_8.4.4.0.zip".

### <a name="create-checksums"></a>Creación de sumas de comprobación

Una vez que el módulo de recursos se ha comprimido y su nombre se ha cambiado, deberá crear una **suma de comprobación**.  La **suma de comprobación** la usa el LCM en el cliente para determinar si el recurso se ha cambiado y debe descargarse de nuevo. Puede crear una **suma de comprobación** con el cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum), como se muestra en el ejemplo siguiente.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

No se mostrará ningún resultado, pero ahora debería ver "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum". También puede ejecutar `New-DSCCheckSum` en un directorio de archivos mediante el parámetro `-Path`. Si ya existe una suma de comprobación, puede forzar que se cree de nuevo con el parámetro `-Force`.

### <a name="where-to-store-resource-archives"></a>Dónde almacenar los archivos de recursos

#### <a name="on-a-dsc-http-pull-server"></a>En un servidor de extracción HTTP de DSC

Al configurar el servidor de extracción HTTP, como se explica en [Configuración de un servidor de extracción HTTP de DSC](pullServer.md), se especifican directorios para las claves **ModulePath** y **ConfigurationPath**. La clave **ConfigurationPath** indica dónde se deben almacenar los archivos ".mof". El parámetro **ModulePath** indica dónde se deben almacenar los módulos de recursos de DSC.

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

Si especificó un valor para **ResourceRepositoryShare**, al configurar el cliente de extracción, almacene los archivos y las sumas de comprobación en el directorio **SourcePath** del bloque **ResourceRepositoryShare**.

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

Si especificó solo un valor **ConfigurationRepositoryShare**, al configurar el cliente de extracción, almacene los archivos y las sumas de comprobación en el directorio **SourcePath** del bloque **ConfigurationRepositoryShare**.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>Actualización de los recursos

Puede forzar que un nodo actualice sus recursos cambiando el número de versión en el nombre del archivo o creando una nueva suma de comprobación. El cliente de extracción buscará las versiones más recientes de los recursos necesarios, así como las sumas de comprobación actualizadas, cuando se actualiza el LCM.

## <a name="see-also"></a>Vea también

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)
