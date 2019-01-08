---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configurar un cliente de extracción mediante nombres de configuración en PowerShell 5.0 y versiones posteriores
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403033"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Configurar un cliente de extracción mediante nombres de configuración en PowerShell 5.0 y versiones posteriores

> Se aplica a: Windows PowerShell 5.0

> [!IMPORTANT]
> El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades. Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).

Antes de configurar un cliente de extracción, debe configurar un servidor de extracción. Aunque este orden no es necesario, ayuda a solucionar problemas y le ayuda a asegurarse de que el registro fue correcto. Para configurar un servidor de extracción, puede usar a las siguientes guías:

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)

Cada nodo de destino puede configurarse para descargar las configuraciones, recursos e incluso notificado su estado. Las secciones siguientes muestran cómo configurar a un cliente de extracción con un recurso compartido de SMB o el servidor de extracción de DSC de HTTP. Cuando se actualiza el LCM del nodo, se comunicará a la ubicación configurada para descargar las configuraciones asignadas. Si todos los recursos necesarios no existen en el nodo, se descargarán automáticamente ellos desde la ubicación configurada. Si el nodo se configura con un [servidor de informes](reportServer.md), a continuación, notificará el estado de la operación.

> **Nota**: En este tema se aplica a PowerShell 5.0.
Para obtener información acerca de cómo configurar un cliente de extracción en PowerShell 4.0, consulte [configurar un cliente de extracción mediante Id. de configuración en PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Configurar el LCM de cliente de incorporación de cambios

Ejecución de cualquiera de los ejemplos siguientes crea una nueva carpeta de salida denominada **PullClientConfigName** y coloca un archivo MOF de metaconfiguración en ella. En este caso, el nombre del archivo MOF de metaconfiguración será `localhost.meta.mof`.

Para aplicar la configuración, llame al cmdlet **Set-DscLocalConfigurationManager**, con el valor de **Path** establecido en la ubicación del archivo MOF de metaconfiguración. Por ejemplo:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Nombre de la configuración

Los ejemplos siguientes se establece la **ConfigurationName** propiedades del LCM en el nombre de una configuración previamente compilado, creado para este propósito. El **ConfigurationName** es lo que usa el LCM para buscar la configuración adecuada en el servidor de extracción. El archivo MOF de configuración en el servidor de incorporación de cambios debe denominarse `<ConfigurationName>.mof`, en este caso, "ClientConfig.mof". Para obtener más información, consulte [publicar las configuraciones a un servidor de extracción (v4/v5)](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurar un cliente de extracción para descargar las configuraciones

Cada cliente debe configurarse en **extracción** modo y dada la incorporación de cambios de dirección url del servidor donde se almacena su configuración. Para ello, tendrá que configurar el administrador de configuración local (LCM) con la información necesaria. Para configurar el LCM, debe crear un tipo especial de configuración, decorado con el atributo **DSCLocalConfigurationManager**. Para más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md).

El script siguiente configura el LCM para que extraiga configuraciones de un servidor denominado "CONTOSO-PullSrv".

- En el script, el bloque **ConfigurationRepositoryWeb** define el servidor de incorporación de cambios. La propiedad **ServerURL** especifica el punto de conexión del servidor de extracción.

- La propiedad **RegistrationKey** es una clave compartida entre todos los nodos de cliente de un servidor de extracción y ese servidor de extracción. El mismo valor se almacena en un archivo en el servidor de extracción.
  > **Nota**: Las claves de registro solo funcionan con **web** servidores de extracción. Deberá seguir usando el elemento **ConfigurationID** con un servidor de extracción **SMB**.
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

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurar un cliente de extracción para descargar los recursos

Si solo especifica un **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** bloquear en su configuración del LCM (como se muestra en el ejemplo anterior), el cliente de extracción extraerá recursos del mismo ubicación donde se almacenan los archivos ".mof". También puede especificar distintas ubicaciones donde los clientes puedan descargar los recursos. Para especificar un servidor de recursos, utilice un bloque **ResourceRepositoryWeb** (para un servidor de extracción web) o un bloque **ResourceRepositoryShare** (para un servidor de extracción SMB).

El ejemplo siguiente muestra una metaconfiguration que configura un cliente para descargar las configuraciones de un servidor de extracción y recursos desde un recurso compartido SMB.

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

## <a name="set-up-a-pull-client-to-report-status"></a>Configurar un cliente de incorporación de cambios para informar del estado

Puede usar un único servidor de extracción para configuraciones, recursos e informes. Informes no están configurados para los clientes de forma predeterminada. Para configurar un cliente para informar del estado, tendrá que crear un **ReportRepositoryWeb** bloque. En el siguiente ejemplo se muestra una metaconfiguración que configura un cliente para que envíe informes de datos y extraiga configuraciones y recursos a un único servidor de extracción.

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
