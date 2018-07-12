---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configuraciones parciales de la configuración de estado deseado de PowerShell
ms.openlocfilehash: 1f5ec5bd5055ccc3d83a60712aebe635f2548828
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893008"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>Configuraciones parciales de la configuración de estado deseado de PowerShell

> Se aplica a: Windows PowerShell 5.0 y posterior.

En PowerShell 5.0, la configuración de estado deseado (DSC) permite que las configuraciones se entreguen en fragmentos y desde varios orígenes. El administrador de configuración local (LCM) en el nodo de destino reúne los fragmentos antes de aplicarlos como una configuración única. Esta capacidad permite compartir el control de la configuración entre equipos o usuarios.
Por ejemplo, si dos o más equipos de desarrolladores colaboran en un servicio, es posible que cada uno de ellos prefiera crear configuraciones para administrar su parte del servicio. Cada una de estas configuraciones se podría extraer de servidores de extracción diferentes y se podría agregar en diferentes fases del desarrollo. Las configuraciones parciales también permiten que distintas personas o equipos controlen aspectos diferentes de los nodos de configuración, sin tener que coordinar la edición de un documento de configuración único. Por ejemplo, un equipo podría ser responsable de la implementación de una máquina virtual y un sistema operativo, mientras que otro equipo podría implementar otras aplicaciones y servicios en esa máquina virtual. Con las configuraciones parciales, cada equipo puede crear su propia configuración, sin que ninguna de ellas sea innecesariamente complicada.

Puede utilizar las configuraciones parciales en el modo de inserción, el modo de extracción o una combinación de ambos.

## <a name="partial-configurations-in-push-mode"></a>Configuraciones parciales en el modo de inserción

Para utilizar configuraciones parciales en modo de inserción, debe configurar el LCM en el nodo de destino para que reciba las configuraciones parciales. Cada configuración parcial se debe insertar en el destino mediante el cmdlet `Publish-DSCConfiguration`. El nodo de destino combina entonces la configuración parcial en una configuración única, que puede aplicar mediante una llamada al cmdlet [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration).

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>Configurar el LCM para configuraciones parcial del modo de inserción

Para configurar el LCM para configuraciones parciales en el modo de inserción, debe crear una configuración **DSCLocalConfigurationManager** con un bloque **PartialConfiguration** para cada configuración parcial. Para más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local de Windows](/powershell/dsc/metaConfig).
En el ejemplo siguiente se muestra una configuración de LCM que espera dos configuraciones parciales: una que implemente el sistema operativo y otra que implemente y configure SharePoint.

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

El valor **RefreshMode** de cada configuración parcial se establece en "Push". Los nombres de los bloques **PartialConfiguration** (en este caso, "ServiceAccountConfig" y "SharePointConfig") deben coincidir exactamente con los nombres de las configuraciones que se inserten en el nodo de destino.

> [!Note]
> El nombre de cada bloque **PartialConfiguration** debe coincidir con el nombre real de la configuración tal como esté especificado en el script de configuración y no con el nombre del archivo MOF, que debe ser el nombre del nodo de destino o `localhost`.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Publicación e inicialización de las configuraciones parciales del modo de inserción

Después llame a [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) para cada configuración, pasando las carpetas que contengan los documentos de configuración como los parámetros **Path**. `Publish-DSCConfiguration` coloca los archivos MOF de configuración en los nodos de destino. Después de publicar las dos configuraciones, puede llamar a `Start-DSCConfiguration –UseExisting` en el nodo de destino.

Por ejemplo, si ha compilado los siguientes documentos MOF de configuración en el nodo de creación:

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\DscTests\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

Publicaría y ejecutaría las configuraciones de la forma siguiente:

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> El usuario que ejecuta el cmdlet [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) debe tener privilegios de administrador en el nodo de destino.

## <a name="partial-configurations-in-pull-mode"></a>Configuraciones parciales en el modo de extracción

Las configuraciones parciales pueden extraerse de uno o varios servidores de extracción (para más información sobre los servidores de extracción, consulte [Servidores de extracción de la configuración de estado deseado de Windows PowerShell](pullServer.md). Para ello, tendrá que configurar el LCM en el nodo de destino para extraer las configuraciones parciales, especificar un nombre y localizar los documentos de configuración correctamente en los servidores de extracción.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>Configurar el LCM para configuraciones del modo de extracción

Para configurar el LCM para extraer configuraciones parciales de un servidor de extracción, debe definir el servidor de extracción en un bloque **ConfigurationRepositoryWeb** (para un servidor de extracción HTTP) o **ConfigurationRepositoryShare** (para un servidor de extracción SMB). A continuación, cree bloques **PartialConfiguration** que hagan referencia al servidor de extracción mediante la propiedad **ConfigurationSource**. También debe crear un bloque **Settings** para especificar que el LCM usa el modo de extracción y para especificar los valores de **ConfigurationNames** o **ConfigurationID** que el servidor de extracción y el nodo de destino usan para identificar las configuraciones. La metaconfiguración siguiente define un servidor de extracción HTTP denominado CONTOSO-PullSrv y dos configuraciones parciales que usan dicho servidor de extracción.

Para obtener más información sobre cómo configurar el LCM mediante **ConfigurationNames**, consulte [Configuración de un cliente de extracción mediante nombres de configuración](pullClientConfigNames.md).
Para obtener más información sobre cómo configurar el LCM mediante **ConfigurationID**, consulte [Configuración de un cliente de extracción mediante id. de configuración](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>Configurar el LCM para configuraciones de modo de extracción mediante nombres de configuración

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>Configurar el LCM para configuraciones de modo de extracción mediante ConfigurationID

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

Puede extraer configuraciones parciales de más de un servidor de extracción; solo sería necesario definir cada servidor de extracción y, después, hacer referencia al servidor de extracción adecuado en cada bloque **PartialConfiguration**.

Después de crear la metaconfiguración, debe ejecutar para crear un documento de configuración (archivo MOF) y, a continuación, llame a [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) para configurar el LCM.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Nomenclatura y ubicación de los documentos de configuración en el servidor de extracción (ConfigurationNames)

Los documentos de configuración parcial deben ubicarse en la carpeta especificada en el valor **ConfigurationPath** del archivo `web.config` del servidor de extracción (normalmente `C:\Program Files\WindowsPowerShell\DscService\Configuration`).

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Nomenclatura de los documentos de configuración en el servidor de extracción en PowerShell 5.1

Si extrae una sola configuración parcial de un servidor de extracción individual, el documento de configuración puede tener cualquier nombre.
Si está extrayendo los más de una configuración parcial de un servidor de extracción, el documento de configuración podría denominarse `<ConfigurationName>.mof`, donde *ConfigurationName* es el nombre de la configuración parcial, o `<ConfigurationName>.<NodeName>.mof`, donde *ConfigurationName* es el nombre de la configuración parcial y *NodeName* es el nombre del nodo de destino.
Esto le permite extraer las configuraciones del servidor de extracción de DSC de Azure Automation.

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>Nomenclatura de los documentos de configuración en el servidor de extracción en PowerShell 5.0

Los documentos de configuración deben nombrarse del modo siguiente: `ConfigurationName.mof`, donde *ConfigurationName* es el nombre de la configuración parcial. En el ejemplo, los documentos de configuración deben nombrarse del modo siguiente:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Nomenclatura y ubicación de los documentos de configuración en el servidor de extracción (ConfigurationID)

Los documentos de configuración parcial deben ubicarse en la carpeta especificada en el valor **ConfigurationPath** del archivo `web.config` del servidor de extracción (normalmente `C:\Program Files\WindowsPowerShell\DscService\Configuration`). Los documentos de configuración deben tener el siguiente nombre: *ConfigurationName*. *ConfigurationID8`.mof`, donde *ConfigurationName* es el nombre de la configuración parcial y *ConfigurationID* es el identificador de configuración definido en el LCM del nodo de destino. En el ejemplo, los documentos de configuración deben nombrarse del modo siguiente:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a>Ejecución de configuraciones parciales de un servidor de extracción

Cuando se haya configurado el LCM en el nodo de destino y se hayan creado los documentos de configuración con los nombres correctos en el servidor de extracción, el nodo de destino extraerá las configuraciones parciales, las combinará y aplicará la configuración resultante a intervalos regulares, según especifique la propiedad **RefreshFrequencyMins** del LCM. Si quiere forzar una actualización, puede llamar al cmdlet [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) para extraer las configuraciones y luego a `Start-DSCConfiguration –UseExisting` para aplicarlas.

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Configuraciones parciales en los modos de inserción y extracción mixtos

También puede mezclar los modos de inserción y extracción para las configuraciones parciales. Es decir, podría tener una configuración parcial que se haya extraído de un servidor de extracción, mientras que otra configuración parcial se inserta. Especifique el modo de actualización de cada configuración parcial, tal como se describe en las secciones anteriores.
Por ejemplo, la metaconfiguración siguiente describe el mismo ejemplo, con la configuración parcial de la cuenta de `ServiceAccountConfig` en el modo de extracción y la configuración parcial de `SharePointConfig` en el modo de inserción.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>Modos de inserción y extracción mixtos mediante ConfigurationNames

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>Modos de inserción y extracción mixtos mediante ConfigurationID

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

Tenga en cuenta que el valor de **RefreshMode** especificado en el bloque Settings es "Pull", pero el valor de **RefreshMode** para configuración parcial de `SharePointConfig` es "Push".

Asigne un nombre y localice los archivos MOF de configuración tal y como se ha descrito anteriormente para sus modos de actualización correspondientes. Llame a `Publish-DSCConfiguration` para publicar la configuración parcial de `SharePointConfig` y, o bien espere a que se extraiga la configuración `ServiceAccountConfig` del servidor de incorporación de cambios, o bien fuerce una actualización mediante una llamada a [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).

## <a name="example-serviceaccountconfig-partial-configuration"></a>Configuración parcial de ServiceAccountConfig de ejemplo

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration


    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential

        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig

```

## <a name="example-sharepointconfig-partial-configuration"></a>Configuración parcial de SharePointConfig de ejemplo

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a>Véase también

[Servidores de extracción de la configuración de estado deseado de Windows PowerShell](pullServer.md)

[Configuración del administrador de configuración local de Windows](/powershell/dsc/metaConfig)