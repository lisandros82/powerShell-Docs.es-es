---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configuración del Administrador de configuración local en versiones anteriores de Windows PowerShell
ms.openlocfilehash: cea32c9aa8144bc52f3d44f2ad852f577f6a5e6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079615"
---
# <a name="configuring-the-local-configuration-manager-in-previous-versions-of-windows-powershell"></a>Configuración del Administrador de configuración local en versiones anteriores de Windows PowerShell

>Se aplica a: Windows PowerShell 4.0

**Para obtener información relacionada con Windows PowerShell 5.0 y versiones posteriores, consulte [Configuración del administrador de configuración local](metaConfig.md).**

El administrador de configuración local es el motor de la configuración de estado deseado (DSC) de Windows PowerShell.
Se ejecuta en todos los nodos de destino y es el responsable de llamar a los recursos de configuración que se incluyen en un script de configuración DSC.
En este tema se enumeran las propiedades del administrador de configuración local y se describe cómo puede modificar la configuración del administrador de configuración local en un nodo de destino.

## <a name="local-configuration-manager-properties"></a>Propiedades del administrador de configuración local

A continuación se enumeran las propiedades del administrador de configuración local que se pueden establecer o recuperar.

- **AllowModuleOverwrite**: controla si se permite que las nuevas configuraciones descargadas desde el servicio de configuración sobrescriban las antiguas en el nodo de destino. Los valores posibles son True y False.
- **CertificateID**: La huella digital de un certificado usado para proteger las credenciales que se han pasado en una configuración. Para más información, consulte [Want to secure credentials in Windows PowerShell Desired State Configuration?](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/) (¿Quiere proteger las credenciales de configuración de estado deseado de Windows PowerShell?).
- **ConfigurationID**: indica un GUID que se usa para obtener un archivo de configuración determinado de un servicio de extracción. El GUID garantiza que se acceda al archivo de configuración correcto.
- **ConfigurationMode**: especifica cómo aplica realmente el administrador de configuración local la configuración en los nodos de destino. Puede tomar los valores siguientes:
  - **ApplyOnly**: con esta opción, DSC aplica la configuración y no hace nada más, a menos que se detecte una nueva configuración, ya sea porque envíe una configuración nueva directamente al nodo de destino, o bien porque se esté está conectando a un servicio de extracción y DSC detecte una configuración nueva al efectuar una comprobación con el servidor de extracción. Si se desplaza la configuración del nodo de destino, no se realiza ninguna acción.
  - **ApplyAndMonitor**: con esta opción (que es el valor predeterminado), DSC aplica a las nuevas configuraciones, ya sea porque las envía directamente al nodo de destino o porque se detectan en un servicio de extracción. A partir de ahí, si la configuración del nodo de destino se desplaza del archivo de configuración, DSC notifica la discrepancia en los registros. Para conocer más sobre el registro de DSC, consulte [Uso de registros de eventos para diagnosticar errores de la configuración de estado deseado](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect**: con esta opción, DSC aplica a las nuevas configuraciones, ya sea porque las envía directamente al nodo de destino o porque se detectan en un servicio de extracción. A partir de ahí, si la configuración del nodo de destino se desplaza del archivo de configuración, DSC notifica la discrepancia en los registros y luego intenta ajustar la configuración del nodo de destino para que sea conforme con el archivo de configuración.
- **ConfigurationModeFrequencyMins**: Representa la frecuencia (en minutos) con la que la aplicación de fondo de DSC intenta implementar la configuración actual en el nodo de destino. El valor predeterminado es 15. Este valor se puede establecer en combinación con RefreshMode. Cuando el valor de RefreshMode se establece en PULL, el nodo de destino contacta con el servicio de configuración en un intervalo que establece el valor de RefreshFrequencyMins y descarga la configuración actual. Independientemente del valor de RefreshMode, en el intervalo que define ConfigurationModeFrequencyMins, el motor de coherencia aplica la configuración más reciente que se haya descargado en el nodo de destino. El valor de RefreshFrequencyMins debe establecerse en un entero que sea múltiplo del valor de ConfigurationModeFrequencyMins.
- **Credential**: indica las credenciales (como ocurre con Get-Credential) necesarias para acceder a recursos remotos, como para contactar con el servicio de configuración.
- **DownloadManagerCustomData**: representa una matriz que contiene datos personalizados específicos del administrador de descargas.
- **DownloadManagerName**: indica el nombre de la configuración y el administrador de descargas del módulo.
- **RebootNodeIfNeeded**: Establezca esta opción en `$true` para permitir que los recursos reinicien el nodo usando la marca `$global:DSCMachineStatus`. De lo contrario, tendrá que reiniciar manualmente el nodo de configuración que lo requiera. El valor predeterminado es `$false`. Para usar esta configuración cuando una instancia distinta de DSC (como Windows Installer) implementa una condición de reinicio, combine la configuración con el módulo [xPendingReboot](https://github.com/powershell/xpendingreboot).
- **RefreshFrequencyMins**: se usa cuando se ha configurado un servicio de extracción. Representa la frecuencia (en minutos) con que el administrador de configuración local contacta con un servicio de extracción para descargar la configuración actual. Este valor se puede establecer junto con ConfigurationModeFrequencyMins. Cuando el valor de RefreshMode se establece en PULL, el nodo de destino contacta con el servicio de extracción "pull" en un intervalo que establece el valor de RefreshFrequencyMins y descarga la configuración actual. En el intervalo que define ConfigurationModeFrequencyMins, el motor de coherencia aplica la configuración más reciente que se haya descargado en el nodo de destino. Si el valor de RefreshFrequencyMins no se establece en un entero que sea múltiplo del valor de ConfigurationModeFrequencyMins, el sistema lo redondeará al alza. El valor predeterminado es 30.
- **RefreshMode**: los valores posibles son **Push** (el valor predeterminado) y **Pull**. En la configuración "push", debe colocar un archivo de configuración en cada nodo de destino, mediante cualquier equipo cliente. En el modo "pull", debe configurar un servicio de extracción con el que el administrador de configuración local contacte y acceda a los archivos de configuración.

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

### <a name="example-of-updating-local-configuration-manager-settings"></a>Ejemplo de actualización de la configuración del administrador de configuración local

Puede actualizar la configuración del administrador de configuración local de un nodo de destino si incluye un bloque **LocalConfigurationManager** dentro del bloque del nodo en un script de configuración, como se muestra en el ejemplo siguiente.

```powershell
Configuration ExampleConfig
{
    Node “Server001”
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

La ejecución del script del ejemplo anterior genera un archivo MOF que especifica y almacena la configuración deseada.
Para aplicar la configuración, puede usar el cmdlet **Set-DscLocalConfigurationManager**, como se muestra en el ejemplo siguiente.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> [!NOTE]
> Para el parámetro **Path**, debe especificar la misma ruta de acceso que haya especificado para el parámetro **OutputPath** al invocar la configuración del ejemplo anterior.

Para ver la configuración actual del administrador de configuración local, puede utilizar el cmdlet **Get-DscLocalConfigurationManager**.
Si invoca este cmdlet sin parámetros, de forma predeterminada obtendrá la configuración del administrador de configuración local del nodo en el que se ejecuta.
Para especificar otro nodo, use el parámetro **CimSession** con este cmdlet.
