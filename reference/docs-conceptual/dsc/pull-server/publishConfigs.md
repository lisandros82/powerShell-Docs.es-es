---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Publicación en un servidor de extracción mediante identificadores de configuración (v4/v5)
ms.openlocfilehash: 3b094308338e62c783b19f4d3bb41634feee63f6
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417255"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Publicación en un servidor de extracción mediante identificadores de configuración (v4/v5)

En las secciones siguientes se supone que ya ha configurado un servidor de extracción. De no ser así, puede usar las siguientes guías:

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)

Cada nodo de destino puede configurarse para descargar configuraciones y recursos, e incluso para notificar de su estado. Este artículo le muestra cómo cargar recursos para que estén disponibles para su descarga, así como configurar clientes para descargar automáticamente los recursos. Cuando el nodo recibe una configuración asignada, a través de **extracción** o **inserción** (v5), descarga automáticamente todos los recursos requeridos por la configuración de la ubicación especificada en el Administrador de configuración local (LCM).

## <a name="compile-configurations"></a>Compilación de configuraciones

El primer paso para almacenar [configuraciones](../configurations/configurations.md) en un servidor de extracción es compilarlas en archivos `.mof`. Para realizar una configuración genérica y aplicable a más clientes, use `localhost` en el bloque Node. El ejemplo siguiente muestra un shell de configuración que usa `localhost` en lugar de un nombre de cliente específico.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Una vez que haya compilado su configuración genérica, debe tener un archivo `localhost.mof`.

## <a name="renaming-the-mof-file"></a>Cambio de nombre del archivo MOF

Puede almacenar archivos de configuración `.mof` en un servidor de extracción por **ConfigurationName** o **ConfigurationID**. Dependiendo de cómo planee configurar sus clientes de extracción, puede elegir una sección a continuación para cambiar adecuadamente el nombre de los archivos `.mof` compilados.

### <a name="configuration-ids-guid"></a>Identificadores de configuración (GUID)

Deberá cambiar el nombre de su archivo `localhost.mof` a `<GUID>.mof`. Puede crear un **GUID** aleatorio mediante el ejemplo siguiente, o mediante el cmdlet [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid).

```powershell
[System.Guid]::NewGuid()
```

Salida de muestra

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

A continuación, puede cambiar el nombre de su archivo `.mof` mediante cualquier método aceptable. En el ejemplo siguiente, se usa el cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Para obtener más información sobre el uso de **GUID** en su entorno, vea el tema sobre la [planificación de GUID](/powershell/scripting/dsc/secureserver#guids).

### <a name="configuration-names"></a>Nombres de la configuración

Deberá cambiar el nombre de su archivo `localhost.mof` a `<Configuration Name>.mof`. En el ejemplo siguiente, se usa el nombre de configuración de la sección anterior. A continuación, puede cambiar el nombre de su archivo `.mof` mediante cualquier método aceptable. En el ejemplo siguiente, se usa el cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Creación de la suma de comprobación

Cada archivo `.mof` almacenado en un servidor de extracción o recurso compartido SMB necesita un archivo `.checksum` asociado.
Este archivo permite a los clientes saber cuándo ha cambiado el archivo `.mof` asociado y debe descargarse nuevamente.

Puede crear una **suma de comprobación** con el cmdlet [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum). También puede ejecutar `New-DSCCheckSum` en un directorio de archivos mediante el parámetro `-Path`.
Si ya existe una suma de comprobación, puede forzar que se cree de nuevo con el parámetro `-Force`. En el ejemplo siguiente se especifica un directorio que contiene el archivo `.mof` de la sección anterior y usa el parámetro `-Force`.

```powershell
New-DscChecksum -Path '.\' -Force
```

No se mostrará ningún resultado, pero ahora debería ver un archivo `<GUID or Configuration Name>.mof.checksum`.

## <a name="where-to-store-mof-files-and-checksums"></a>Dónde almacenar los archivos MOF y las sumas de comprobación

### <a name="on-a-dsc-http-pull-server"></a>En un servidor de extracción HTTP de DSC

Al configurar el servidor de extracción HTTP, como se explica en [Configuración de un servidor de extracción HTTP de DSC](pullServer.md), se especifican directorios para las claves **ModulePath** y **ConfigurationPath**. La clave **ModulePath** indica dónde deben almacenarse los archivos `.zip` empaquetados de un módulo. **ConfigurationPath** indica dónde se deben almacenar los archivos `.mof` y `.checksum`.

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

Al configurar un cliente de extracción para usar un recurso compartido de SMB, especifique un valor para **ConfigurationRepositoryShare**.
Todos los archivos `.mof` y `.checksum` deben almacenarse en el directorio **SourcePath** del bloque **ConfigurationRepositoryShare**.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Pasos siguientes

A continuación, querrá configurar los clientes de extracción para extraer la configuración especificada. Para obtener más información, consulte una de las guías siguientes:

- [Configuración de un cliente de extracción mediante id. de configuración (v4)](pullClientConfigId4.md)
- [Configuración de un cliente de extracción mediante id. de configuración (v5)](pullClientConfigId.md)
- [Configuración de un cliente de extracción mediante nombres de configuración (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>Vea también

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)
- [Empaquetado y carga de recursos en un servidor de extracción](package-upload-resources.md)
