---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configuración de un cliente de extracción mediante nombres de configuración en PowerShell 5.0 y versiones posteriores
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2019
ms.locfileid: "58058202"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Configuración de un cliente de extracción mediante nombres de configuración en PowerShell 5.0 y versiones posteriores

> Se aplica a: Windows PowerShell 5.0

> [!IMPORTANT]
> El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades. Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).

Antes de configurar un cliente de extracción, debe configurar un servidor de extracción. Aunque este orden no es obligatorio, ayuda a solucionar problemas y ayuda a garantizar que el registro sea correcto. Para configurar un servidor de extracción, puede usar a las siguientes guías:

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)

Cada nodo de destino puede configurarse para descargar configuraciones y recursos, e incluso para notificar de su estado. Las secciones siguientes muestran cómo configurar a un cliente de extracción con un recurso compartido SMB o el servidor de extracción de DSC HTTP. Cuando se actualice el LCM del nodo, accederá a la ubicación configurada para descargar las configuraciones asignadas. Si los recursos necesarios no existen en el nodo, se descargarán automáticamente desde la ubicación configurada. Si el nodo se configura con un [servidor de informes](reportServer.md), notificará el estado de la operación.

> [!NOTE]
> Este tema se aplica a PowerShell 5.0.
> Para obtener información sobre cómo configurar un cliente de extracción en PowerShell 4.0, consulte [Configuración de un cliente de extracción con ID de configuración en PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Configuración del LCM del cliente de extracción

La ejecución de cualquiera de los ejemplos siguientes crea una nueva carpeta de salida denominada **PullClientConfigName** y coloca un archivo MOF de metaconfiguración en ella. En este caso, el nombre del archivo MOF de metaconfiguración será `localhost.meta.mof`.

Para aplicar la configuración, llame al cmdlet **Set-DscLocalConfigurationManager**, con el valor de **Path** establecido en la ubicación del archivo MOF de metaconfiguración. Por ejemplo:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Nombre de la configuración

Los ejemplos siguientes establecen la propiedad **ConfigurationName** del LCM en el nombre de una configuración previamente compilada, creada para este propósito. La propiedad **ConfigurationName** es lo que usa el LCM para buscar la configuración adecuada en el servidor de extracción. El archivo MOF de configuración en el servidor de extracción debe denominarse `<ConfigurationName>.mof`, en este caso, "ClientConfig.mof". Para obtener más información, consulte [Publicación de las configuraciones en un servidor de extracción (v4/v5)](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configuración de un cliente de extracción para descargar configuraciones

Cada cliente debe configurarse en modo **Pull** (de extracción) y se le debe asignar la URL del servidor de extracción donde se almacena su configuración. Para ello, tendrá que configurar el administrador de configuración local (LCM) con la información necesaria. Para configurar el LCM, debe crear un tipo especial de configuración, decorado con el atributo **DSCLocalConfigurationManager**. Para más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md).

El script siguiente configura el LCM para que extraiga configuraciones de un servidor denominado "CONTOSO-PullSrv".

- En el script, el bloque **ConfigurationRepositoryWeb** define el servidor de incorporación de cambios. La propiedad **ServerURL** especifica el punto de conexión del servidor de extracción.

- La propiedad **RegistrationKey** es una clave compartida entre todos los nodos de cliente de un servidor de extracción y ese servidor de extracción. El mismo valor se almacena en un archivo en el servidor de extracción.
  > [!NOTE]
  > Las claves de registro solo funcionan con servidores de extracción **web**. Deberá seguir usando el elemento **ConfigurationID** con un servidor de extracción **SMB**.
  > Para obtener información sobre cómo configurar un servidor de extracción mediante **ConfigurationID**, consulte [Configuración de un cliente de extracción con el id. de configuración](pullClientConfigId.md)

- La propiedad **ConfigurationNames** es una matriz que especifica el nombre de la configuración prevista para el nodo de cliente.
  >**Nota:** Si se especifica más de un valor en **ConfigurationNames**, también deberá especificar bloques **PartialConfiguration** en la configuración.
  >Para obtener información sobre las configuraciones parciales, consulte [Configuraciones parciales de la configuración de estado deseado de PowerShell](partialConfigs.md).

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a>Configuración de un cliente de extracción para descargar recursos

Si solo especifica un bloque **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** en la configuración del LCM (como en el ejemplo anterior), el cliente de extracción extraerá recursos de la misma ubicación donde están almacenados sus archivos ".mof". También puede especificar distintas ubicaciones en las cuales los clientes puedan descargar recursos. Para especificar un servidor de recursos, utilice un bloque **ResourceRepositoryWeb** (para un servidor de extracción web) o un bloque **ResourceRepositoryShare** (para un servidor de extracción SMB).

En el siguiente ejemplo se muestra una metaconfiguración que configura un cliente para descargar configuraciones de un servidor de extracción y recursos de un recurso compartido SMB.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a>Configuración de un cliente de extracción para notificar el estado

Puede utilizar un solo servidor de extracción para configuraciones, recursos e informes. Los informes no están configurados para los clientes, de forma predeterminada. Para configurar que un cliente notifique el estado, debe crear un bloque **ReportRepositoryWeb**. En el siguiente ejemplo se muestra una metaconfiguración que configura un cliente para que envíe informes de datos y extraiga configuraciones y recursos a un único servidor de extracción.

> [!NOTE]
> Un servidor de informes no puede ser un recurso compartido SMB.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Véase también

* [Configuración de un cliente de extracción con el id. de configuración](PullClientConfigNames.md)
* [Configuración de un servidor de extracción web de DSC](pullServer.md)
