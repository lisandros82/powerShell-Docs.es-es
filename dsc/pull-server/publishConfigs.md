---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Publicar en un servidor de extracción mediante identificadores de configuración (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402401"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Publicar en un servidor de extracción mediante identificadores de configuración (v4/v5)

Las secciones siguientes se suponen que ya ha configurado un servidor de extracción. Si no ha configurado el servidor de incorporación de cambios, puede usar a las siguientes guías:

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)

Cada nodo de destino puede configurarse para descargar las configuraciones, recursos e incluso notificado su estado. En este artículo le mostrará cómo cargar recursos para que estén disponibles para descargarse y configurar clientes para descargar automáticamente los recursos. Cuando el nodo recibe una configuración asignada, a través de **extraer** o **Push** (v5), se descarga automáticamente todos los recursos requeridos por la configuración de la ubicación especificada en el LCM.

## <a name="compile-configurations"></a>Compilar las configuraciones

El primer paso para almacenar [configuraciones](../configurations/configurations.md) en un servidor de incorporación de cambios, es compilarlos en archivos ".mof". Para realizar una configuración genérica y es aplicable a más clientes, use `localhost` en el bloque de nodo. El ejemplo siguiente muestra un shell de configuración que usa `localhost` en lugar de un nombre de cliente específico.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Una vez que ha compilado su configuración genérico, debe tener un archivo "localhost.mof".

## <a name="renaming-the-mof-file"></a>Cambiar el nombre del archivo MOF

Puede almacenar archivos de configuración "MOF" en un servidor de extracción por **ConfigurationName** o **ConfigurationID**. Dependiendo de cómo se va a configurar los clientes de incorporación de cambios, puede elegir una sección a continuación para cambiar correctamente el nombre de los archivos compilados ".mof".

### <a name="configuration-ids-guid"></a>Identificadores de configuración (GUID)

Tendrá que cambiar el nombre de su archivo de "localhost.mof" a "<GUID>.mof" archivo. Puede crear uno aleatorio **Guid** en el ejemplo a continuación, o mediante el [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Salida de muestra

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

A continuación, puede cambiar el nombre de su archivo de ".mof" mediante cualquier método aceptable. El ejemplo siguiente, se usa el [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Para obtener más información sobre el uso de **GUID** en su entorno, consulte [planear GUID](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Nombres de la configuración

Tendrá que cambiar el nombre de su archivo de "localhost.mof" a "<Configuration Name>.mof" archivo. En el ejemplo siguiente, se usa el nombre de configuración de la sección anterior. A continuación, puede cambiar el nombre de su archivo de ".mof" mediante cualquier método aceptable. El ejemplo siguiente, se usa el [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Creación de la suma de comprobación

Cada archivo de "MOF" almacena en un recurso compartido SMB o servidor de extracción debe tener un archivo asociado ".checksum". Este archivo permite que los clientes saber cuándo el archivo asociado ".mof" ha cambiado y debe descargarse de nuevo.

Puede crear un **suma de comprobación** con el [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet. También puede ejecutar `New-DSCCheckSum` frente a un directorio de archivos mediante el `-Path` parámetro. Si ya existe una suma de comprobación, puede forzarlo a volver a crearse con el `-Force` parámetro. En el ejemplo siguiente se especifica un directorio que contiene el archivo "MOF" de la sección anterior y usa el `-Force` parámetro.

```powershell
New-DscChecksum -Path '.\' -Force
```

No se mostrará ningún resultado, pero ahora debería ver un "<GUID or Configuration Name>. mof.checksum" archivo.

## <a name="where-to-store-mof-files-and-checksums"></a>Dónde almacenar los archivos MOF y las sumas de comprobación

### <a name="on-a-dsc-http-pull-server"></a>En un servidor de extracción de DSC

Al configurar el servidor de extracción HTTP, como se explica en [configurar un servidor de extracción de DSC HTTP](pullServer.md), especificar directorios de la **ModulePath** y **ConfigurationPath** claves. El **ConfigurationPath** clave indica dónde se deben almacenar los archivos "MOF". El **ConfigurationPath** indica dónde se deben almacenar los archivos de "MOF" y ".checksum" archivos.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>En un recurso compartido SMB

Al configurar un cliente de extracción para usar un recurso compartido SMB, especifique un **ConfigurationRepositoryShare**. Todos los archivos "MOF" y ".checksum", a continuación, se deben almacenar en el **SourcePath** directorio desde el **ConfigurationRepositoryShare** bloque.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Pasos a seguir

A continuación, querrá configurar los clientes de extracción para extraer la configuración especificada. Para obtener más información, consulte una de las siguientes guías:

- [Configurar un cliente de incorporación de cambios mediante identificadores de configuración (v4)](pullClientConfigId4.md)
- [Configurar un cliente de incorporación de cambios mediante identificadores de configuración (v5)](pullClientConfigId.md)
- [Configurar un cliente de extracción mediante nombres de configuración (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>Vea también

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)
- [Paquete y los recursos de carga para un servidor de extracción](package-upload-resources.md)
