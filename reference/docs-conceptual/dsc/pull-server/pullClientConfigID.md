---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configuración de un cliente de extracción mediante ID de configuración en PowerShell 5.0 y versiones posteriores
ms.openlocfilehash: bd173a1079b916c450a0292dca7a595a9bcff985
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417239"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Configuración de un cliente de extracción mediante ID de configuración en PowerShell 5.0 y versiones posteriores

> Se aplica a: Windows PowerShell 5.0

> [!IMPORTANT]
> El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades. Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).

Antes de configurar un cliente de extracción, debe configurar un servidor de extracción. Aunque este orden no es obligatorio, ayuda a solucionar problemas y ayuda a garantizar que el registro sea correcto. Para configurar un servidor de extracción, puede usar a las siguientes guías:

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)

Cada nodo de destino puede configurarse para descargar configuraciones y recursos, e incluso para notificar de su estado. Las secciones siguientes muestran cómo configurar a un cliente de extracción con un recurso compartido SMB o el servidor de extracción de DSC HTTP. Cuando se actualice el LCM del nodo, accederá a la ubicación configurada para descargar las configuraciones asignadas. Si los recursos necesarios no existen en el nodo, se descargarán automáticamente desde la ubicación configurada. Si el nodo se configura con un [servidor de informes](reportServer.md), notificará el estado de la operación.

> [!NOTE]
> Este tema se aplica a PowerShell 5.0. Para obtener información sobre cómo configurar un cliente de incorporación de cambios en PowerShell 4.0, consulte [Configuración de un cliente de incorporación de cambios con el id. de configuración de PowerShell 4.0](pullClientConfigID4.md).

## <a name="configure-the-pull-client-lcm"></a>Configuración del LCM del cliente de extracción

La ejecución de cualquiera de los ejemplos siguientes crea una nueva carpeta de salida denominada **PullClientConfigID** y coloca un archivo MOF de metaconfiguración en ella. En este caso, el nombre del archivo MOF de metaconfiguración será `localhost.meta.mof`.

Para aplicar la configuración, llame al cmdlet **Set-DscLocalConfigurationManager**, con el valor de **Path** establecido en la ubicación del archivo MOF de metaconfiguración. Por ejemplo:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Id. de configuración

Los ejemplos siguientes establecen la propiedad **ConfigurationID** del LCM en un **GUID** que se había creado anteriormente para este fin. La propiedad **ConfigurationID** es lo que usa el LCM para buscar la configuración adecuada en el servidor de incorporación de cambios. El archivo MOF de configuración del servidor de incorporación de cambios debe denominarse `ConfigurationID.mof`, donde *ConfigurationID* es el valor de la propiedad **ConfigurationID** del LCM del nodo de destino. Para obtener más información, vea [Publicación de las configuraciones en un servidor de extracción (v4/v5)](publishConfigs.md).

Puede crear un **GUID** aleatorio mediante el ejemplo siguiente, o mediante el cmdlet [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid).

```powershell
[System.Guid]::NewGuid()
```

Para obtener más información sobre el uso de **GUID** en su entorno, vea el tema sobre la [planificación de GUID](/powershell/scripting/dsc/secureserver#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configuración de un cliente de extracción para descargar configuraciones

Cada cliente debe configurarse en modo **Pull** (de extracción) y se le debe asignar la URL del servidor de extracción donde se almacena su configuración. Para ello, tendrá que configurar el administrador de configuración local (LCM) con la información necesaria. Para configurar el LCM, debe crear un tipo especial de configuración, decorado con el atributo **DSCLocalConfigurationManager**. Para más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>Servidor de extracción de DSC HTTP

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

En el script, el bloque **ConfigurationRepositoryWeb** define el servidor de incorporación de cambios. **ServerUrl** especifica la dirección URL de la extracción de DSC

### <a name="smb-share"></a>Recurso compartido SMB

El script siguiente configura el LCM para que extraiga configuraciones del recurso compartido SMB `\\SMBPullServer\Pull`.

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

En el script, el bloque **ConfigurationRepositoryShare** define el servidor de extracción que, en este caso, es simplemente un recurso compartido SMB.

## <a name="set-up-a-pull-client-to-download-resources"></a>Configuración de un cliente de extracción para descargar recursos

Si solo especifica el bloque **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** en la configuración del LCM (como en el ejemplo anterior), el cliente de extracción extraerá recursos de la misma ubicación donde recupera sus configuraciones. También puede especificar ubicaciones independientes para los recursos. Para especificar una ubicación de recurso como un servidor independiente, use el bloque **ResourceRepositoryWeb**. Para especificar una ubicación de recurso como un recurso compartido SMB, use el bloque **ResourceRepositoryShare**.

> [!NOTE]
> Puede combinar **ConfigurationRepositoryWeb** con **ResourceRepositoryShare** o **ConfigurationRepositoryShare** con **ResourceRepositoryWeb**. A continuación no se muestran ejemplos de esto.

### <a name="http-dsc-pull-server"></a>Servidor de extracción de DSC HTTP

La metaconfiguración siguiente configura un cliente de extracción para que obtenga sus configuraciones de **CONTOSO-PullSrv** y sus recursos de **CONTOSO-ResourceSrv**.

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

### <a name="smb-share"></a>Recurso compartido SMB

En el siguiente ejemplo se muestra una metaconfiguración que configura un cliente para extraer configuraciones del recurso compartido SMB `\\SMBPullServer\Configurations` y recursos del recurso compartido SMB `\\SMBPullServer\Resources`.

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

#### <a name="automatically-download-resources-in-push-mode"></a>Descarga automática de recursos en modo de inserción

A partir de PowerShell 5.0, los clientes de extracción pueden descargar módulos desde un recurso compartido SMB, incluso cuando están configurados para el modo **Push** (de inserción). Esto es especialmente útil en escenarios donde no se quiere configurar un servidor de extracción. El bloque **ResourceRepositoryShare** puede usarse sin especificar un **ConfigurationRepositoryShare**. En el siguiente ejemplo se muestra una metaconfiguración que configura un cliente para extraer de un recurso compartido SMB `\\SMBPullServer\Resources`. Cuando el nodo haya **INSERTADO** una configuración, descargará automáticamente los recursos necesarios, desde el recurso compartido especificado.

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

## <a name="set-up-a-pull-client-to-report-status"></a>Configuración de un cliente de extracción para notificar el estado

De forma predeterminada, los nodos no enviarán informes a un servidor de extracción configurado. Puede usar un solo servidor de extracción para configuraciones, recursos e informes, pero debe crear un bloque **ReportRepositoryWeb** para configurar los informes.

### <a name="http-dsc-pull-server"></a>Servidor de extracción de DSC HTTP

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

### <a name="smb-share"></a>Recurso compartido SMB

Un servidor de informes no puede ser un recurso compartido SMB.

## <a name="next-steps"></a>Pasos a seguir

Una vez que se ha configurado el cliente de extracción, puede usar a las siguientes guías para realizar los pasos siguientes:

- [Publicación de las configuraciones en un servidor de extracción (v4/v5)](publishConfigs.md)
- [Empaquetado y carga de recursos en un servidor de extracción (v4)](package-upload-resources.md)

## <a name="see-also"></a>Véase también

* [Configuración de un cliente de extracción con nombres de configuración](pullClientConfigNames.md)
