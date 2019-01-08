---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configurar un cliente de incorporación de cambios con identificadores de configuración de PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402993"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>Configurar un cliente de incorporación de cambios con identificadores de configuración de PowerShell 4.0

>Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades. Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).

Antes de configurar un cliente de extracción, debe configurar un servidor de extracción. Aunque este orden no es necesario, ayuda a solucionar problemas y le ayuda a asegurarse de que el registro fue correcto. Para configurar un servidor de extracción, puede usar a las siguientes guías:

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)

Cada nodo de destino puede configurarse para descargar las configuraciones, recursos e incluso notificado su estado. Las secciones siguientes muestran cómo configurar a un cliente de extracción con un recurso compartido de SMB o el servidor de extracción de DSC de HTTP. Cuando se actualiza el LCM del nodo, se comunicará a la ubicación configurada para descargar las configuraciones asignadas. Si todos los recursos necesarios no existen en el nodo, se descargarán automáticamente ellos desde la ubicación configurada. Si el nodo se configura con un [servidor de informes](reportServer.md), a continuación, notificará el estado de la operación.

## <a name="configure-the-pull-client-lcm"></a>Configurar el LCM de cliente de incorporación de cambios

Ejecución de cualquiera de los ejemplos siguientes crea una nueva carpeta de salida denominada **PullClientConfigID** y coloca un archivo MOF de metaconfiguración en ella. En este caso, el nombre del archivo MOF de metaconfiguración será `localhost.meta.mof`.

Para aplicar la configuración, llame al cmdlet **Set-DscLocalConfigurationManager**, con el valor de **Path** establecido en la ubicación del archivo MOF de metaconfiguración. Por ejemplo:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Id. de configuración

Los ejemplos siguientes conjunto el **ConfigurationID** propiedades del LCM en un **Guid** que había creado anteriormente para este propósito. La propiedad **ConfigurationID** es lo que usa el LCM para buscar la configuración adecuada en el servidor de incorporación de cambios. El archivo MOF de configuración del servidor de incorporación de cambios debe denominarse `ConfigurationID.mof`, donde *ConfigurationID* es el valor de la propiedad **ConfigurationID** del LCM del nodo de destino. Para obtener más información, consulte [publicar las configuraciones a un servidor de extracción (v4/v5)](publishConfigs.md).

Puede crear uno aleatorio **Guid** mediante el ejemplo siguiente.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurar un cliente de extracción para descargar las configuraciones

Cada cliente debe configurarse en **extracción** modo y dada la incorporación de cambios de dirección url del servidor donde se almacena su configuración. Para ello, tendrá que configurar el administrador de configuración local (LCM) con la información necesaria. Para configurar el LCM, debe crear un tipo especial de configuración, con un **LocalConfigurationManager** bloque. Para más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](../managing-nodes/metaConfig4.md).

## <a name="http-dsc-pull-server"></a>Servidor de extracción de DSC de HTTP

Si el servidor de extracción está configurado como un servicio web, establezca el **DownloadManagerName** a **WebDownloadManager**. El **WebDownloadManager** requiere que especifique un **ServerUrl** a la **DownloadManagerCustomData** clave. También puede especificar un valor para **AllowUnsecureConnection**, como en el ejemplo siguiente. El script siguiente configura el LCM para que extraiga configuraciones de un servidor denominado "PullServer".

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
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>Recurso compartido de SMB

Si el servidor de extracción está configurado como un recurso compartido de archivos SMB, en lugar de un servicio web, establezca el **DownloadManagerName** a **DscFileDownloadManager** en lugar de **WebDownLoadManager**. El **DscFileDownloadManager** requiere que especifique un **SourcePath** propiedad en el **DownloadManagerCustomData**. El script siguiente configura LCM para que extraiga las configuraciones de un recurso compartido SMB denominado "SmbDscShare" en un servidor denominado "CONTOSO-SERVER".

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

- [Configurar un servidor de extracción web de DSC](pullServer.md)
- [Configuración de un servidor de extracción SMB de DSC](pullServerSMB.md)
