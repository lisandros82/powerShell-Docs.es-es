---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Mejoras de la configuración del estado deseado en WMF 5.1
ms.openlocfilehash: 92f82d62550e105a187fd7c0c58b49367c646a7e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679632"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>Mejoras en la configuración de estado deseado (DSC) en WMF 5.1

## <a name="dsc-class-resource-improvements"></a>Mejoras en los recursos de la clase DSC

En WMF 5.1, hemos corregido los siguientes problemas conocidos:

- Get-DscConfiguration puede devolver valores vacíos (NULL) o errores si la función Get() de un recurso de DSC basado en clases devuelve un tipo complejo o de tabla hash.
- Get-DscConfiguration devuelve un error si se usa la credencial RunAs en la configuración de DSC.
- Un recurso basado en clases no se puede usar en una configuración compuesta.
- Start-DscConfiguration se bloquea si el recurso basado en clases tiene una propiedad de un tipo propio.
- Los recursos basados en clases no se pueden utilizar como recursos exclusivos.

## <a name="dsc-resource-debugging-improvements"></a>Mejoras en la depuración de recursos de DSC

En WMF 5.0, el depurador de PowerShell no se detenía directamente en el método de recursos basados en clases (Get/Set/Test).
En WMF 5.1, el depurador se detiene en el método de recursos basados en clases de la misma manera que con los métodos de recursos basados en MOF.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>El cliente de extracción de DSC es compatible con TLS 1.1 y TLS 1.2

Anteriormente, el cliente de extracción de DSC solo era compatible con SSL3.0 y TLS1.0 a través de conexiones HTTPS.
Cuando se le obligaba a usar protocolos más seguros, el cliente de extracción dejaba de funcionar.
En WMF 5.1, el cliente de extracción de DSC ya no es compatible con SSL 3.0 y, en cambio, ya es compatible con los protocolos TLS 1.1 y TLS 1.2 que son más seguros.

## <a name="improved-pull-server-registration"></a>Registro de servidor de extracción mejorado

En las versiones anteriores de WMF, si se realizaban solicitudes de informes y registros concurrentes al servidor de extracción de DSC mientras se usaba la base de datos ESENT, LCM no podía registrarlas ni informar al respecto.
En tales casos, los registros de eventos del servidor de extracción tienen el error "El nombre de instancia ya está en uso".
Esto se debe a que se usa un patrón incorrecto para acceder a la base de datos ESENT en un escenario de varios subprocesos.
En WMF 5.1, este problema se ha corregido.
Los informes o registros simultáneos (que implican la base de datos ESENT) funcionan correctamente en WMF 5.1.
Este problema solo concierne a la base de datos ESENT, no se aplica a la base de datos OLEDB.

## <a name="enable-circular-log-on-esent-database-instance"></a>Habilitación del registro circular en la instancia de base de datos ESENT

En versiones anteriores de DSC-PullServer, los archivos de registro de la base de datos ESENT llenaban el espacio en disco del servidor de extracción, porque la instancia de la base de datos se creó sin el registro circular. En esta versión, tiene la opción de controlar el comportamiento del registro circular de la instancia mediante el archivo web.config del servidor de extracción. De forma predeterminada, CircularLogging se establece en TRUE.

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a>Convención de nomenclatura de configuración parcial de extracción

En la versión anterior, la convención de nomenclatura de una configuración parcial consistía en que el nombre de archivo MOF en el servidor o servicio de extracción debía coincidir con el nombre de configuración parcial especificado en la configuración del administrador de configuración local, que a su vez debe coincidir con el nombre de configuración insertado en el archivo MOF.

Vea las instantáneas siguientes:

- Opciones de configuración local que definen una configuración parcial que puede recibir un nodo.

![Metaconfiguración de ejemplo](../images/MetaConfigPartialOne.png)

- Definición de configuración parcial de ejemplo.

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

- "ConfigurationName" insertado en el archivo MOF generado.

![Archivo MOF de ejemplo generado](../images/PartialGeneratedMof.png)

- FileName en el repositorio de configuración de extracción

![FileName en el repositorio de configuración](../images/PartialInConfigRepository.png)

El nombre del servicio Automatización de Azure generó archivos MOF como `<ConfigurationName>.<NodeName>.mof`.
Por tanto, la configuración siguiente se compila como PartialOne.localhost.mof.

Esto hizo imposible extraer una de las configuraciones parciales del servicio Automatización de Azure.

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

En WMF 5.1, la configuración parcial del servidor o servicio de extracción se puede denominar `<ConfigurationName>.<NodeName>.mof`.
Además, si una máquina extrae una sola configuración del servidor o servicio de extracción, el archivo de configuración del repositorio de configuración del servidor de extracción puede tener cualquier nombre de archivo.
Esta flexibilidad de nomenclatura le permite administrar los nodos parcialmente mediante el servicio Azure Automation, donde cierta configuración del nodo proviene del DSC de Azure Automation y con una configuración parcial que administra de forma local.

La metaconfiguración siguiente configura un nodo que se debe administrar tanto localmente como mediante el servicio Azure Automation.

```powershell
[DscLocalConfigurationManager()]
Configuration RegistrationMetaConfig
{
    Settings
    {
        RefreshFrequencyMins = 30
        RefreshMode = "PULL"
    }

    ConfigurationRepositoryWeb web
    {
        ServerURL =  $endPoint
        RegistrationKey = $registrationKey
        ConfigurationNames = $configurationName
    }

    # Partial configuration managed by Azure Automation service.
    PartialConfiguration PartialConfigurationManagedByAzureAutomation
    {
        ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
    }

    # This partial configuration is managed locally.
    PartialConfiguration OnPremisesConfig
    {
        RefreshMode = "PUSH"
        ExclusiveResources = @("Script")
    }

}

RegistrationMetaConfig
Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
```

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>Uso de PsDscRunAsCredential con recursos compuestos de DSC

Hemos agregado compatibilidad para usar [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) con recursos [compuestos](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) de DSC.

Ahora puede especificar el valor de PsDscRunAsCredential al usar recursos compuestos dentro de las configuraciones.
Si se especifica así, todos los recursos se ejecutarán dentro de un recurso compuesto como un usuario RunAs.
Si el recurso compuesto llama a otro recurso compuesto, todos los recursos se ejecutarán también como usuario RunAs.
Las credenciales de RunAs se propagan a todos los niveles de la jerarquía del recurso compuesto.
Si cualquier recurso de un recurso compuesto especifica su propio valor para PsDscRunAsCredential, aparece un error de combinación durante la compilación de la configuración.

En este ejemplo se muestra el uso con el recurso compuesto [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) que se incluye en el módulo PSDesiredStateConfiguration.

```powershell
Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

InstallWindowsFeature -ConfigurationData $configData
```

## <a name="dsc-module-and-configuration-signing-validations"></a>Validaciones de firmas de configuraciones y módulos de DSC

En DSC, las configuraciones y los módulos se distribuyen a los equipos administrados desde el servidor de extracción.
Si el servidor de extracción está en peligro, un atacante puede modificar las configuraciones y los módulos del servidor de extracción y propagarlos a todos los nodos administrados, poniéndolos todos en peligro.

En WMF 5.1, DSC admite la validación de las firmas digitales en los archivos del catálogo y de configuración (.MOF).
Esta característica evita que los nodos ejecuten archivos de módulos o de configuración que no están firmados por un firmante de confianza o que se han alterado después de que los haya firmado un firmante de confianza.

### <a name="how-to-sign-configuration-and-module"></a>Cómo firmar un módulo y una configuración

***
* Los archivos de configuración (. MOF): El cmdlet de PowerShell existente [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) se amplía para admitir la firma de los archivos MOF.
* Módulos Firma de módulos se realiza mediante la firma del catálogo de módulos correspondiente mediante los siguientes pasos:
    1. Cree un archivo de catálogo: Un archivo de catálogo contiene una colección de algoritmos hash criptográficos o huellas digitales.
       Cada huella digital corresponde a un archivo que se incluye en el módulo.
       Se ha agregado un nuevo cmdlet, [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), para que los usuarios puedan crear un archivo de catálogo para su módulo.
    2. Inicie sesión en el archivo de catálogo: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) para firmar el archivo de catálogo.
    3. Coloque el archivo de catálogo dentro de la carpeta del módulo.
Por convención, el archivo de catálogo del módulo debe colocarse en la carpeta del módulo y debe tener el mismo nombre que este.

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>Configuración de LocalConfigurationManager para habilitar las validaciones de las firmas

#### <a name="pull"></a>Extracción

En un nodo, LocalConfigurationManager realiza la validación de las firmas de módulos y las configuraciones en función de su configuración actual.
De forma predeterminada, la validación de firmas está deshabilitada.
La validación de firmas se puede habilitar agregando un bloque "SignatureValidation" a la definición de metaconfiguración del nodo, tal como se muestra aquí:

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

El establecimiento de la metaconfiguración anterior en un nodo habilita la validación de firmas de los módulos y las configuraciones descargados.
LocalConfigurationManager lleva a cabo los pasos siguientes para comprobar las firmas digitales.

1. Compruebe que la firma de un archivo de configuración (. MOF) es válida.
   Usa el cmdlet de PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), que se amplía en la versión 5.1 para admitir la validación de la firma de MOF.
2. Compruebe que la entidad de certificación que autorizó al firmante es de confianza.
3. Descargue las dependencias de los módulos o recursos de la configuración en una ubicación temporal.
4. Compruebe la firma del catálogo incluida dentro del módulo.
    * Busque un archivo `<moduleName>.cat` y compruebe su firma mediante el cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).
    * Compruebe que la entidad de certificación que autenticó al firmante es de confianza.
    * Compruebe que el contenido de los módulos no se ha alterado, para lo que debe usar el cmdlet nuevo [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).
5. Install-Module en $env:ProgramFiles\WindowsPowerShell\Modules\
6. Configuración de proceso

> Nota: La validación de la firma en el catálogo de módulo y la configuración solo se realizan la primera vez que se aplica la configuración al sistema o cuando el módulo se descarga e instala.
Las ejecuciones de coherencia no validan la firma de Current.mof ni sus dependencias de módulo.
Si se ha producido un error en cualquier etapa de la comprobación, por ejemplo, si la configuración extraída del servidor de extracción no tiene firma, el procesamiento de la configuración termina con el error que se muestra más adelante y se eliminan todos los archivos temporales.

![Configuración de salida de error de ejemplo](../images/PullUnsignedConfigFail.png)

De forma similar, la extracción de un módulo cuyo catálogo no esté firmado provoca el siguiente error:

![Módulo de salida de error de ejemplo](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a>Push

Una configuración entregada mediante inserción puede alterarse en su origen antes de que se entregue al nodo.
El administrador de configuración local lleva a cabo pasos de validación de firmas similares para las configuraciones insertadas o publicadas.
A continuación, se muestra un ejemplo completo de validación de firma para la inserción.

- Habilite la validación de firma en el nodo.

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'
    }
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType =  'Configuration','Module'
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

- Cree un archivo de configuración de ejemplo.

```powershell
# Sample configuration
Configuration Test
{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

- Intente insertar el archivo de configuración sin firmar en el nodo.

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- Firme el archivo configuración mediante el certificado de firma de código.

![SignMofFile](../images/SignMofFile.png)

- Intente insertar el archivo MOF firmado.

![SignMofFile](../images/PushSignedMof.png)
