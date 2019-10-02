---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configuración de un cliente de extracción mediante ID de configuración en PowerShell 4.0
ms.openlocfilehash: 9259c624c8725f7d76f61e9ad7caa42e1bfa308c
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324879"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>Configuración de un cliente de extracción mediante ID de configuración en PowerShell 4.0

>Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades. Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).

Antes de configurar un cliente de extracción, debe configurar un servidor de extracción. Aunque este orden no es obligatorio, ayuda a solucionar problemas y ayuda a garantizar que el registro sea correcto. Para configurar un servidor de extracción, puede usar a las siguientes guías:

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)

Cada nodo de destino puede configurarse para descargar configuraciones y recursos, e incluso para notificar de su estado. Las secciones siguientes muestran cómo configurar a un cliente de extracción con un recurso compartido SMB o el servidor de extracción de DSC HTTP. Cuando se actualice el LCM del nodo, accederá a la ubicación configurada para descargar las configuraciones asignadas. Si los recursos necesarios no existen en el nodo, se descargarán automáticamente desde la ubicación configurada. Si el nodo se configura con un [servidor de informes](reportServer.md), notificará el estado de la operación.

## <a name="configure-the-pull-client-lcm"></a>Configuración del LCM del cliente de extracción

La ejecución de cualquiera de los ejemplos siguientes crea una nueva carpeta de salida denominada **PullClientConfigID** y coloca un archivo MOF de metaconfiguración en ella. En este caso, el nombre del archivo MOF de metaconfiguración será `localhost.meta.mof`.

Para aplicar la configuración, llame al cmdlet **Set-DscLocalConfigurationManager**, con el valor de **Path** establecido en la ubicación del archivo MOF de metaconfiguración. Por ejemplo:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Id. de configuración

Los ejemplos siguientes establecen la propiedad **ConfigurationID** del LCM en un **GUID** que se había creado anteriormente para este fin. La propiedad **ConfigurationID** es lo que usa el LCM para buscar la configuración adecuada en el servidor de incorporación de cambios. El archivo MOF de configuración del servidor de incorporación de cambios debe denominarse `ConfigurationID.mof`, donde *ConfigurationID* es el valor de la propiedad **ConfigurationID** del LCM del nodo de destino. Para obtener más información, consulte [Publicación de las configuraciones en un servidor de extracción (v4/v5)](publishConfigs.md).

Puede crear un **GUID** aleatorio mediante el ejemplo siguiente.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configuración de un cliente de extracción para descargar configuraciones

Cada cliente debe configurarse en modo **Pull** (de extracción) y se le debe asignar la URL del servidor de extracción donde se almacena su configuración. Para ello, tendrá que configurar el administrador de configuración local (LCM) con la información necesaria. Para configurar el LCM, debe crear un tipo especial de configuración, con un bloque **DSCLocalConfigurationManager**. Para más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](../managing-nodes/metaConfig4.md).

## <a name="http-dsc-pull-server"></a>Servidor de extracción de DSC HTTP

Si el servidor de extracción está configurado como un servicio web, establezca **DownloadManagerName** en **WebDownloadManager**. La propiedad **WebDownloadManager** requiere que especifique un valor **ServerUrl** para la clave **DownloadManagerCustomData**. También puede especificar un valor para **AllowUnsecureConnection**, como en el ejemplo siguiente. El script siguiente configura el LCM para que extraiga configuraciones de un servidor denominado "PullServer".

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = "TRUE"}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>Recurso compartido SMB

Si el servidor de extracción está configurado como un recurso compartido de archivos SMB, en lugar de un servicio web, establezca **DownloadManagerName** en **DscFileDownloadManager** en lugar de en **WebDownLoadManager**. La propiedad **DscFileDownloadManager** requiere que especifique una propiedad **SourcePath** en **DownloadManagerCustomData**. El script siguiente configura LCM para que extraiga las configuraciones de un recurso compartido SMB denominado "SmbDscShare" en un servidor denominado "CONTOSO-SERVER".

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a>Pasos a seguir

Una vez que se ha configurado el cliente de extracción, puede usar a las siguientes guías para realizar los pasos siguientes:

- [Publicación de las configuraciones en un servidor de extracción (v4/v5)](publishConfigs.md)
- [Empaquetado y carga de recursos en un servidor de extracción (v4)](package-upload-resources.md)

## <a name="see-also"></a>Véase también

- [Configuración de un servidor de extracción web de DSC](pullServer.md)
- [Configuración de un servidor de extracción SMB de DSC](pullServerSMB.md)
