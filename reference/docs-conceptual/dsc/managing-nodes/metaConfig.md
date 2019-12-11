---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configuración del administrador de configuración local
ms.openlocfilehash: 606cf77ddc3865749e900753aba7c41b66424450
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953852"
---
# <a name="configuring-the-local-configuration-manager"></a>Configuración del administrador de configuración local

> Se aplica a: Windows PowerShell 5.0

El administrador de configuración local (LCM) es el motor de Desired State Configuration (DSC).
El LCM se ejecuta en cada nodo de destino y es el responsable de analizar y establecer las configuraciones que se envían al nodo.
También es responsable de diversos otros aspectos de DSC, entre los que se incluyen los siguientes.

- Determinar el modo de actualización (inserción o extracción).
- Especificar la frecuencia con que un nodo extrae y aplica configuraciones.
- Asociar el nodo con el servicio de extracción.
- Especificar configuraciones parciales.

Se utiliza un tipo especial de configuración para configurar el LCM a fin de que especifique cada uno de estos comportamientos.
En las siguientes secciones se describe cómo configurar el LCM.

Con Windows PowerShell 5.0 se incluyeron nuevas configuraciones para administrar el Administrador de configuración local.
Para obtener información sobre cómo configurar el LCM en Windows PowerShell 4.0, consulte [Administrador de configuración local (LCM) de la configuración de estado deseado de Windows PowerShell 4.0](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Escritura y aplicación de una configuración de LCM

Para configurar el LCM, debe crear y ejecutar un tipo especial de configuración que aplique los valores de LCM.
Para especificar una configuración de LCM, utilice el atributo DscLocalConfigurationManager.
A continuación se muestra una configuración sencilla que establece el LCM en el modo de inserción.

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
}
```

El proceso de aplicar los valores al LCM es similar a la aplicación de una configuración DSC.
Creará una configuración de LCM, la compilará en un archivo MOF y la aplicará en el nodo.
A diferencia de las configuraciones DSC, no aplique una configuración LCM con una llamada al cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).
En su lugar, llame al cmdlet [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) y proporcione la ruta de acceso al MOF de configuración de LCM como un parámetro.
Después de establecer la configuración de LCM, podrá ver las propiedades del LCM con una llamada al cmdlet [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).

Una configuración de LCM puede contener bloques solo para un conjunto limitado de recursos.
En el ejemplo anterior, el único recurso al que se llama es **Settings**.
El resto de recursos disponibles son:

* **ConfigurationRepositoryWeb**: especifica un servicio de extracción HTTP para configuraciones.
* **ConfigurationRepositoryShare**: especifica un recurso compartido SMB para configuraciones.
* **ResourceRepositoryWeb**: especifica un servicio de extracción HTTP para módulos.
* **ResourceRepositoryShare**: especifica un recurso compartido SMB para módulos.
* **ReportServerWeb**: especifica un servicio de extracción HTTP al que se envían informes.
* **PartialConfiguration**: proporciona datos para habilitar las configuraciones parciales.

## <a name="basic-settings"></a>Configuración básica

Aparte de especificar puntos de conexión o rutas de acceso del servicio de extracción y configuraciones parciales, todas las propiedades del LCM se configuran en un bloque **Settings**.
Las propiedades siguientes están disponibles en un bloque **Settings**.

|  Propiedad  |  Tipo  |  Descripción   |
|----------- |------- |--------------- |
| ActionAfterReboot| cadena| Especifica lo que ocurre tras un reinicio durante la aplicación de una configuración. Los valores posibles son __"ContinueConfiguration"__ y __"StopConfiguration"__ . <ul><li> __ContinueConfiguration__: continúe aplicando la configuración actual después de reiniciar el equipo. Este es el valor predeterminado</li><li>__StopConfiguration__: detenga la configuración actual después de reiniciar el equipo.</li></ul>|
| AllowModuleOverwrite| bool| __$TRUE__ si se permite que las nuevas configuraciones descargadas desde el servicio de extracción sobrescriban las antiguas en el nodo de destino. En caso contrario, $FALSE.|
| CertificateID| cadena| La huella digital de un certificado usado para proteger las credenciales que se han pasado en una configuración. Para más información, consulte [Want to secure credentials in Windows PowerShell Desired State Configuration?](https://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx) (¿Quiere proteger las credenciales de configuración de estado deseado de Windows PowerShell?). <br> __Nota:__ Se administra automáticamente si se usa el servicio de extracción DSC de Azure Automation.|
| ConfigurationDownloadManagers| CimInstance[]| Obsoleto. Use los bloques __ConfigurationRepositoryWeb__ y __ConfigurationRepositoryShare__ para definir puntos de conexión del servicio de extracción de configuración.|
| ConfigurationID| cadena| Para la compatibilidad con versiones anteriores con versiones anteriores del servicio de extracción. Un GUID que identifica el archivo de configuración que se obtendrá de un servicio de extracción. El nodo extraerá las configuraciones del servicio de extracción si el nombre del MOF de configuración es ConfigurationID.mof.<br> __Nota:__ Si establece esta propiedad, el registro del nodo con un servicio de extracción mediante __RegistrationKey__ no funcionará. Para más información, consulte [Configuración de un cliente de extracción con nombres de configuración](../pull-server/pullClientConfigNames.md).|
| ConfigurationMode| cadena | Especifica la forma en que el LCM aplica realmente la configuración a los nodos de destino. Los valores posibles son __"ApplyOnly"__ , __"ApplyAndMonitor"__ y __"ApplyAndAutoCorrect"__ . <ul><li>__ApplyOnly__: DSC aplica la configuración y no hace nada más, a menos que se inserte una nueva configuración en el nodo de destino o se extraiga una nueva configuración de un servicio. Después de la aplicación inicial de una nueva configuración, DSC no comprueba si hay un desplazamiento con respecto a un estado configurado previamente. Tenga en cuenta que DSC intentará aplicar la configuración hasta que lo consiga antes de que __ApplyOnly__ surta efecto. </li><li> __ApplyAndMonitor__: Este es el valor predeterminado. El LCM aplica las nuevas configuraciones. Después de la aplicación inicial de una nueva configuración, si el nodo de destino se desplaza del estado deseado, DSC notifica la discrepancia en los registros. Tenga en cuenta que DSC intentará aplicar la configuración hasta que lo consiga antes de que __ApplyAndMonitor__ surta efecto.</li><li>__ApplyAndAutoCorrect__: DSC aplica las nuevas configuraciones. Después de la aplicación inicial de una nueva configuración, si el nodo de destino se desplaza del estado deseado, DSC notifica la discrepancia en los registros y después vuelve a aplicar la configuración actual.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| La frecuencia, en minutos, con que se comprueba y aplica la configuración actual. Esta propiedad se omite si la propiedad ConfigurationMode se establece en ApplyOnly. El valor predeterminado es 15.|
| DebugMode| cadena| Los valores posibles son __None__, __ForceModuleImport__ y __All__. <ul><li>Establézcala en __None__ para utilizar los recursos almacenados en caché. Este es el valor predeterminado y debe utilizarse en escenarios de producción.</li><li>Si se establece en __ForceModuleImport__, provocará que el LCM vuelva a cargar los módulos de recursos de DSC, incluso aunque se hayan cargado y almacenado en caché previamente. Esto afecta al rendimiento de las operaciones de DSC, ya que cada módulo se recarga cuando se usa. Normalmente, este valor se usaría durante la depuración de un recurso.</li><li>En esta versión, __All__  es lo mismo que __ForceModuleImport__.</li></ul> |
| RebootNodeIfNeeded| bool| Establezca esta opción en `$true` para permitir que los recursos reinicien el nodo usando la marca `$global:DSCMachineStatus`. De lo contrario, tendrá que reiniciar manualmente el nodo de configuración que lo requiera. El valor predeterminado es `$false`. Para usar esta configuración cuando una instancia distinta de DSC (como Windows Installer) implementa una condición de reinicio, combine la configuración con el recurso __PendingReboot__ del módulo [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc).|
| RefreshMode| cadena| Especifica cómo obtiene el LCM las configuraciones. Los valores posibles son __"Disabled"__ , __"Push"__ y __"Pull"__ . <ul><li>__Disabled__: las configuraciones DSC se deshabilitan para este nodo.</li><li> __Push__: las configuraciones se inician con una llamada al cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration). La configuración se aplica inmediatamente al nodo. Este es el valor predeterminado.</li><li>__Pull:__ el nodo se configura para comprobar con regularidad si existen configuraciones en una ruta de acceso de SMB o un servicio de extracción. Si esta propiedad se establece en __Pull__, se debe especificar una ruta de acceso HTTP (servicio) o SMB (recurso compartido) en un bloque __ConfigurationRepositoryWeb__ o __ConfigurationRepositoryShare__.</li></ul>|
| RefreshFrequencyMins| Uint32| El intervalo de tiempo, en minutos, que emplea el LCM para comprobar un servicio de extracción en busca de configuraciones actualizadas. Este valor se omite si el LCM no está configurado en el modo de extracción. El valor predeterminado es 30.|
| ReportManagers| CimInstance[]| Obsoleto. Use los bloques __ReportServerWeb__ para definir un punto de conexión para enviar datos de informes a un servicio de extracción.|
| ResourceModuleManagers| CimInstance[]| Obsoleto. Use los bloques __ResourceRepositoryWeb__ y __ResourceRepositoryShare__ para definir puntos de conexión HTTP o rutas de acceso SMB del servicio de extracción, respectivamente.|
| PartialConfigurations| CimInstance| Sin implementar. No usar.|
| StatusRetentionTimeInDays | UInt32| El número de días que el LCM mantiene el estado de la configuración actual.|

> [!NOTE]
> El LCM inicia el ciclo **ConfigurationModeFrequencyMins** según lo siguiente:
>
> - Se aplica una metaconfiguración nueva usando `Set-DscLocalConfigurationManager`
> - Un reinicio del equipo
>
> En cualquier condición en la cual el proceso de temporizador experimente un bloqueo, se detectará dentro del plazo de 30 segundos y se reiniciará el ciclo.
> Una operación simultánea puede retrasar el ciclo de inicio; si la duración de esta operación supera la frecuencia del ciclo configurado, el siguiente temporizador no se iniciará.
>
> Por ejemplo, la metaconfiguración se configura con una frecuencia de extracción de 15 minutos y se produce una extracción en T1.  El nodo no finaliza el trabajo en 16 minutos.  Se omite el primer ciclo de 15 minutos y la extracción siguiente se realizará en T1+15+15.

## <a name="pull-service"></a>Servicio de extracción

La configuración de LCM admite la definición de los siguientes puntos de conexión del servicio de extracción:

- **Servidor de configuración**: un repositorio para las configuraciones de DSC. Defina servidores de configuración mediante el uso de bloques **ConfigurationRepositoryWeb** (para servidores basados en web) y **ConfigurationRepositoryShare** (para servidores basados en SMB).
- **Servidor de recursos**: un repositorio para recursos de DSC, empaquetado como módulos de PowerShell. Defina servidores de recursos mediante el uso de bloques **ResourceRepositoryWeb** (para servidores basados en web) y **ResourceRepositoryShare** (para servidores basados en SMB).
- **Servidor de informes**: un servicio al que DSC envía datos de informes. Defina servidores de informes mediante bloques **ReportServerWeb**. Un servidor de informes debe ser un servicio web.

Para ver más detalles sobre el servicio de extracción, consulte [Servicio de extracción de Desired State Configuration](../pull-server/pullServer.md).

## <a name="configuration-server-blocks"></a>Bloques del servidor de configuración

Para definir un servidor de configuración basado en web, cree un bloque **ConfigurationRepositoryWeb**.
Un bloque **ConfigurationRepositoryWeb** define las siguientes propiedades.

|Propiedad|Tipo|Descripción|
|---|---|---|
|AllowUnsecureConnection|bool|Establézcala en **$TRUE** para permitir conexiones desde el nodo al servidor sin autenticación. Establézcala en **$FALSE** para que se requiera autenticación.|
|CertificateID|cadena|La huella digital de un certificado usado para autenticar el servidor.|
|ConfigurationNames|String[]|Una matriz de nombres de configuraciones que el nodo de destino extraerá. Solo se usan si el nodo se registra con el servicio de extracción mediante un elemento **RegistrationKey**. Para más información, consulte [Configuración de un cliente de extracción con nombres de configuración](../pull-server/pullClientConfigNames.md).|
|RegistrationKey|cadena|Un GUID que registra el nodo con el servicio de extracción. Para más información, consulte [Configuración de un cliente de extracción con nombres de configuración](../pull-server/pullClientConfigNames.md).|
|ServerURL|cadena|La dirección URL del servicio de configuración.|
|ProxyURL*|cadena|URL del proxy HTTP que se debe usar al conectar con el servicio de configuración.|
|ProxyCredential*|PSCredential|Credencial que se debe usar para el proxy HTTP.|

> [!NOTE]
> * Se admite en Windows 1809 y versiones posteriores.

Hay disponible un script de ejemplo para simplificar la configuración del valor ConfigurationRepositoryWeb para los nodos locales, consulte el artículo sobre la [configuración de metaconfiguraciones DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Para definir un servidor de configuración basado en SMB, cree un bloque **ConfigurationRepositoryShare**.
Un bloque **ConfigurationRepositoryShare** define las siguientes propiedades.

|Propiedad|Tipo|Descripción|
|---|---|---|
|Credential|MSFT_Credential|La credencial usada para autenticarse en el recurso compartido SMB.|
|SourcePath|cadena|La ruta de acceso del recurso compartido SMB.|

## <a name="resource-server-blocks"></a>Bloques del servidor de recursos

Para definir un servidor de recursos basado en web, cree un bloque **ResourceRepositoryWeb**.
Un bloque **ResourceRepositoryWeb** define las siguientes propiedades.

|Propiedad|Tipo|Descripción|
|---|---|---|
|AllowUnsecureConnection|bool|Establézcala en **$TRUE** para permitir conexiones desde el nodo al servidor sin autenticación. Establézcala en **$FALSE** para que se requiera autenticación.|
|CertificateID|cadena|La huella digital de un certificado usado para autenticar el servidor.|
|RegistrationKey|cadena|Un GUID que identifica el nodo para el servicio de extracción.|
|ServerURL|cadena|La dirección URL del servidor de configuración.|
|ProxyURL*|cadena|URL del proxy HTTP que se debe usar al conectar con el servicio de configuración.|
|ProxyCredential*|PSCredential|Credencial que se debe usar para el proxy HTTP.|

> [!NOTE]
> * Se admite en Windows 1809 y versiones posteriores.

Hay disponible un script de ejemplo para simplificar la configuración del valor ResourceRepositoryWeb para los nodos locales, consulte el artículo sobre la [configuración de metaconfiguraciones DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Para definir un servidor de recursos basado en SMB, cree un bloque **ResourceRepositoryShare**.
**ResourceRepositoryShare** define las siguientes propiedades.

|Propiedad|Tipo|Descripción|
|---|---|---|
|Credential|MSFT_Credential|La credencial usada para autenticarse en el recurso compartido SMB. Para obtener un ejemplo de transferencia de credenciales, consulte [Configuración de un servidor de incorporación de cambios SMB de DSC](../pull-server/pullServerSMB.md)|
|SourcePath|cadena|La ruta de acceso del recurso compartido SMB.|

## <a name="report-server-blocks"></a>Bloques del servidor de informes

Para definir un servidor de informes, cree un bloque **ReportServerWeb**.
El rol del servidor de informes no es compatible con el servicio de extracción basado en SMB.
**ReportServerWeb** define las siguientes propiedades.

|Propiedad|Tipo|Descripción|
|---|---|---|
|AllowUnsecureConnection|bool|Establézcala en **$TRUE** para permitir conexiones desde el nodo al servidor sin autenticación. Establézcala en **$FALSE** para que se requiera autenticación.|
|CertificateID|cadena|La huella digital de un certificado usado para autenticar el servidor.|
|RegistrationKey|cadena|Un GUID que identifica el nodo para el servicio de extracción.|
|ServerURL|cadena|La dirección URL del servidor de configuración.|
|ProxyURL*|cadena|URL del proxy HTTP que se debe usar al conectar con el servicio de configuración.|
|ProxyCredential*|PSCredential|Credencial que se debe usar para el proxy HTTP.|

> [!NOTE]
> * Se admite en Windows 1809 y versiones posteriores.

Hay disponible un script de ejemplo para simplificar la configuración del valor ReportServerWeb para los nodos locales, consulte el artículo sobre la [configuración de metaconfiguraciones DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Configuraciones parciales

Para definir una configuración parcial, cree un bloque **PartialConfiguration**.
Para más información sobre configuraciones parciales, consulte [Configuraciones parciales de DSC](../pull-server/partialConfigs.md).
**PartialConfiguration** define las siguientes propiedades.

|Propiedad|Tipo|Descripción|
|---|---|---|
|ConfigurationSource|string[]|Una matriz de nombres de servidores de configuración, definidos previamente en bloques **ConfigurationRepositoryWeb** y **ConfigurationRepositoryShare**, desde donde se extrae la configuración parcial.|
|DependsOn|string{}|Una lista de nombres de otras configuraciones que se deben completar antes de que se aplique esta configuración parcial.|
|Descripción|cadena|Texto utilizado para describir la configuración parcial.|
|ExclusiveResources|string[]|Una matriz de recursos exclusivos de esta configuración parcial.|
|RefreshMode|cadena|Especifica cómo obtiene el LCM esta configuración parcial. Los valores posibles son __"Disabled"__ , __"Push"__ y __"Pull"__ . <ul><li>__Disabled__: esta configuración parcial está deshabilitada.</li><li> __Push__: la configuración parcial se inserta en el nodo con una llamada al cmdlet [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration). Cuando todas las configuraciones parciales del nodo se han insertado o extraído de un servicio, es posible iniciar la configuración con una llamada a `Start-DscConfiguration –UseExisting`. Este es el valor predeterminado.</li><li>__Pull:__ el nodo se configura para comprobar con regularidad si existe una configuración parcial en un servicio de extracción. Si esta propiedad se establece en __Pull__, debe especificar un servicio de extracción en una propiedad __ConfigurationSource__. Para más información sobre el servicio de extracción de Azure Automation, consulte [Información general de DSC de Azure Automation](https://docs.microsoft.com/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|string[]|Una matriz de los nombres de los servidores de recursos desde los que se descargarán los recursos necesarios para esta configuración parcial. Estos nombres deben hacer referencia a los puntos de conexión del servicio definidos previamente en los bloques **ResourceRepositoryWeb** y **ResourceRepositoryShare**.|

__Note:__ DSC de Azure Automation admite configuraciones parciales, pero solo se puede extraer una configuración de cada cuenta de automatización por nodo.

## <a name="see-also"></a>Véase también

### <a name="concepts"></a>Conceptos
[Información de Desired State Configuration](../overview/overview.md)

[Introducción a DSC de Azure Automation](https://docs.microsoft.com/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Otros recursos

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[Configuración de un cliente de extracción con nombres de configuración](../pull-server/pullClientConfigNames.md)
