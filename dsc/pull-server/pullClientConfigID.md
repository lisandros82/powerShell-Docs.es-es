---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configurar un cliente de incorporación de cambios mediante identificadores de configuración en PowerShell 5.0 y versiones posteriores
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402785"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Configurar un cliente de incorporación de cambios mediante identificadores de configuración en PowerShell 5.0 y versiones posteriores

> Se aplica a: Windows PowerShell 5.0

> [!IMPORTANT]
> El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades. Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).

Antes de configurar un cliente de extracción, debe configurar un servidor de extracción. Aunque este orden no es necesario, ayuda a solucionar problemas y le ayuda a asegurarse de que el registro fue correcto. Para configurar un servidor de extracción, puede usar a las siguientes guías:

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)

Cada nodo de destino puede configurarse para descargar las configuraciones, recursos e incluso notificado su estado. Las secciones siguientes muestran cómo configurar a un cliente de extracción con un recurso compartido de SMB o el servidor de extracción de DSC de HTTP. Cuando se actualiza el LCM del nodo, se comunicará a la ubicación configurada para descargar las configuraciones asignadas. Si todos los recursos necesarios no existen en el nodo, se descargarán automáticamente ellos desde la ubicación configurada. Si el nodo se configura con un [servidor de informes](reportServer.md), a continuación, notificará el estado de la operación.

> **Nota**: En este tema se aplica a PowerShell 5.0. Para obtener información sobre cómo configurar un cliente de incorporación de cambios en PowerShell 4.0, consulte [Configuración de un cliente de incorporación de cambios con el id. de configuración de PowerShell 4.0](pullClientConfigID4.md).

## <a name="configure-the-pull-client-lcm"></a>Configurar el LCM de cliente de incorporación de cambios

Ejecución de cualquiera de los ejemplos siguientes crea una nueva carpeta de salida denominada **PullClientConfigID** y coloca un archivo MOF de metaconfiguración en ella. En este caso, el nombre del archivo MOF de metaconfiguración será `localhost.meta.mof`.

Para aplicar la configuración, llame al cmdlet **Set-DscLocalConfigurationManager**, con el valor de **Path** establecido en la ubicación del archivo MOF de metaconfiguración. Por ejemplo:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Id. de configuración

Los ejemplos siguientes se establece la **ConfigurationID** propiedades del LCM en un **Guid** que había creado anteriormente para este propósito. La propiedad **ConfigurationID** es lo que usa el LCM para buscar la configuración adecuada en el servidor de incorporación de cambios. El archivo MOF de configuración del servidor de incorporación de cambios debe denominarse `ConfigurationID.mof`, donde *ConfigurationID* es el valor de la propiedad **ConfigurationID** del LCM del nodo de destino. Para obtener más información, consulte [publicar las configuraciones a un servidor de extracción (v4/v5)](publishConfigs.md).

Puede crear uno aleatorio **Guid** en el ejemplo a continuación, o mediante el [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Para obtener más información sobre el uso de **GUID** en su entorno, consulte [planear GUID](/powershell/dsc/secureserver#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurar un cliente de extracción para descargar las configuraciones

Cada cliente debe configurarse en **extracción** modo y dada la incorporación de cambios de dirección url del servidor donde se almacena su configuración. Para ello, tendrá que configurar el administrador de configuración local (LCM) con la información necesaria. Para configurar el LCM, debe crear un tipo especial de configuración, decorado con el atributo **DSCLocalConfigurationManager**. Para más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>Servidor de extracción de DSC de HTTP

El script siguiente configura el LCM para que extraiga configuraciones de un servidor denominado "CONTOSO-PullSrv".

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

En el script, el bloque **ConfigurationRepositoryWeb** define el servidor de incorporación de cambios. El **ServerUrl** especifica la dirección url de la extracción de DSC

### <a name="smb-share"></a>Recurso compartido de SMB

El script siguiente configura el LCM para que extraiga configuraciones desde el recurso compartido SMB `\\SMBPullServer\Pull`.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

En el script, el **ConfigurationRepositoryShare** bloque define el servidor de extracción, en este caso, es simplemente un recurso compartido SMB.

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurar un cliente de extracción para descargar los recursos

Si especifica solo el **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** bloquear en su configuración del LCM (como en los ejemplos anteriores), el cliente de extracción extraerá los recursos de la misma recupera sus configuraciones de ubicación. También puede especificar ubicaciones independientes para los recursos. Para especificar una ubicación de recursos como un servidor independiente, use el **ResourceRepositoryWeb** bloque. Para especificar una ubicación de recursos como un recurso compartido SMB, use el **ResourceRepositoryShare** bloque.

> [!NOTE]
> Puede combinar **ConfigurationRepositoryWeb** con **ResourceRepositoryShare** o **ConfigurationRepositoryShare** con **ResourceRepositoryWeb** . Ejemplos de esto no se muestran a continuación.

### <a name="http-dsc-pull-server"></a>Servidor de extracción de DSC de HTTP

La metaconfiguración siguiente configura un cliente de extracción para obtener sus configuraciones de **CONTOSO-PullSrv** y sus recursos de **CONTOSO-ResourceSrv**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>Recurso compartido de SMB

El ejemplo siguiente muestra una metaconfiguration que configura un cliente para que extraiga configuraciones desde el recurso compartido SMB `\\SMBPullServer\Configurations`y los recursos desde el recurso compartido SMB `\\SMBPullServer\Resources`.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a>Descargar automáticamente los recursos en el modo de inserción

A partir de PowerShell 5.0, los clientes de extracción pueden descargar los módulos desde un recurso compartido SMB, incluso cuando están configurados para **Push** modo. Esto es especialmente útil en escenarios donde no desea configurar un servidor de extracción. El **ResourceRepositoryShare** bloque puede usarse sin especificar un **ConfigurationRepositoryShare**. El ejemplo siguiente muestra una metaconfiguration que configura un cliente para obtener recursos desde un recurso compartido SMB `\\SMBPullServer\Resources`. Cuando el nodo está **PUSHED** una configuración, se descargarán automáticamente los recursos necesarios, desde el recurso compartido especificado.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a>Configurar un cliente de incorporación de cambios para informar del estado

De forma predeterminada, los nodos no enviarán informes a un servidor de incorporación de cambios configurado. Puede usar un solo servidor de extracción para configuraciones, recursos e informes, pero debe crear un bloque **ReportRepositoryWeb** para configurar los informes.

### <a name="http-dsc-pull-server"></a>Servidor de extracción de DSC de HTTP

En el siguiente ejemplo se muestra una metaconfiguración que configura un cliente para que envíe informes de datos y extraiga configuraciones y recursos a un único servidor de extracción.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

Para especificar un servidor de informes, utilice un bloque **ReportRepositoryWeb**. Un servidor de informes no puede ser un servidor SMB.
La metaconfiguración siguiente configura un cliente de extracción para que obtenga sus configuraciones de **CONTOSO-PullSrv** y sus recursos de **CONTOSO-ResourceSrv**, y para que envíe los informes a **CONTOSO-ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>Recurso compartido de SMB

Un servidor de informes no puede ser un recurso compartido SMB.

## <a name="next-steps"></a>Pasos a seguir

Una vez que se ha configurado el cliente de extracción, puede usar a las siguientes guías para realizar los pasos siguientes:

- [Publicación de las configuraciones en un servidor de extracción (v4/v5)](publishConfigs.md)
- [Empaquetado y carga de recursos en un servidor de extracción (v4)](package-upload-resources.md)

## <a name="see-also"></a>Véase también

* [Configuración de un cliente de extracción con nombres de configuración](pullClientConfigNames.md)
