---
ms.date: 04/11/2018
keywords: dsc,powershell,configuration,setup
title: Servicio de extracción de DSC
ms.openlocfilehash: 2ef48b88cc9e14da452e0d19e5a0f43fc8a95ab2
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619167"
---
# <a name="desired-state-configuration-pull-service"></a>Servicio de extracción de Desired State Configuration

> Se aplica a: Windows PowerShell 5.0

> [!IMPORTANT]
> El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades. Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).

El Administrador de configuración local puede administrarse de forma central con una solución de servicio de extracción.
Cuando se usa este enfoque, el nodo que se está administrando se registra en un servicio y se le asigna una configuración en las opciones del LCM.
La configuración y todos los recursos de DSC necesarios como dependencias para la configuración se descargan en la máquina y el LCM las usa para administrar la configuración.
La información sobre el estado de la máquina que se está administrando se carga al servicio para crear un informe.
Este concepto se conoce como "servicio de extracción".

Las opciones actuales del servicio de extracción incluyen:

- Servicio Desired State Configuration de Azure Automation
- Un servicio de extracción que se ejecuta en Windows Server
- Soluciones de código abierto mantenidas por la comunidad
- Un recurso compartido SMB

**La solución recomendada**, y la opción que tiene la mayor cantidad de características disponibles, es [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started).

El servicio de Azure puede administrar nodos locales en centros de datos privados, o bien en nubes públicas como Azure y AWS.
En el caso de entornos privados donde los servidores no se pueden conectar directamente a Internet, considere limitar el tráfico de salida solo al intervalo IP de Azure (consulte los [intervalos IP del centro de datos de Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Las características del servicio en línea que no están disponibles actualmente en el servicio de extracción de Windows Server incluyen las siguientes:
- Se cifran todos los datos, ya sea que estén en tránsito o en reposo
- Los certificados de cliente se crean y administran de manera automática
- Almacén de secretos para administrar de manera centralizada las [contraseñas/credenciales](/azure/automation/automation-credentials) o las [variables](/azure/automation/automation-variables), como nombres de servidor o cadenas de conexión
- Administración centralizada de la [configuración de LCM](metaConfig.md#basic-settings) del nodo
- Asignación centralizada de las configuraciones a los nodos cliente
- Publicación de los cambios de configuración en "grupos de valor controlado" para pruebas antes de llegar a producción
- Informes gráficos
  - Detalle de estado en el nivel de recurso DSC de granularidad
  - Mensajes detallados de error de equipos cliente para la solución de problemas
- [Integración de Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) para alertas, tareas automatizadas, aplicación Android/iOS para informes y alertas

## <a name="dsc-pull-service-in-windows-server"></a>Servicio de extracción de DSC en Windows Server

Es posible configurar un servicio de extracción para que se ejecute en Windows Server.
Tenga en cuenta que la solución de servicio de extracción incluida en Windows Server solo tiene funcionalidades de almacenamiento de configuraciones y módulos para descargar y capturar datos de informes en una base de datos.
No se incluyen muchas de las funcionalidades que ofrece el servicio en Azure y, por lo tanto, no es una herramienta lo suficientemente eficaz como para evaluar el uso del servicio.

El servicio de extracción que se ofrece en Windows Server es un servicio web en IIS que usa una interfaz de OData para poner a disposición de los nodos de destino los archivos de configuración DSC cuando esos nodos los soliciten.

Requisitos para usar un servidor de extracción:

- Un servidor que ejecute:
  - WMF/PowerShell 5.0 o una versión posterior
  - Rol del servidor IIS
  - Servicio DSC
- Idealmente, algún medio para generar un certificado, para proteger las credenciales que se pasan al administrador de configuración local (LCM) en los nodos de destino

La mejor manera para configurar Windows Server para hospedar un servicio de extracción es usar una configuración de DSC.
A continuación se muestra un script de ejemplo.

### <a name="supported-database-systems"></a>Sistemas de base de datos admitidos

|WMF 4.0   |WMF 5.0  |WMF 5.1 |WMF 5.1 (Windows Server Insider Preview 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT (predeterminado), MDB |ESENT (predeterminado), MDB|ESENT (predeterminado), SQL Server, MDB

A partir de la versión 17090 de [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server es una opción admitida en el servicio de extracción (característica de Windows *DSC-Service*).  Esto constituye una nueva opción para ajustar la escala de entornos de DSC de gran envergadura que no se han migrado a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started).

> **Nota**: La compatibilidad con SQL Server no se incluirá en WMF 5.1 ni versiones anteriores y solo estará disponible en versiones de Windows Server a partir de 17090.

Para configurar el servidor de extracción de forma que use SQL Server, establezca **SqlProvider** en `$true` y **SqlConnectionString** en una cadena de conexión de SQL Server válida.  Para más información, vea [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings) (Cadenas de conexión de SqlClient).
Para ver un ejemplo de configuración de SQL Server con **xDscWebService**, lea primero [Uso del recurso xDSCWebService](#using-the-xdscwebservice-resource) y, después, revise [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 en GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>Uso del recurso xDSCWebService

La manera más fácil de configurar un servidor de extracción web es usando el recurso **xDscWebService**, incluido en el módulo **xPSDesiredStateConfiguration**.
En los siguientes pasos se explica cómo usar el recurso en una configuración que configure el servicio web.

1. Llame al cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) para instalar el módulo **xPSDesiredStateConfiguration**. **Nota**: **Install-Module** está incluido en el módulo **PowerShellGet**, que se incluye en PowerShell 5.0. Puede descargar el módulo **PowerShellGet** para PowerShell 3.0 y 4.0 en [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186) (Vista previa de los módulos de PowerShell PackageManagement).
1. Obtenga un certificado SSL para el servidor de extracción de DSC de una entidad de certificación de confianza, ya sea dentro de su organización o de una entidad pública. El certificado recibido de la entidad suele tener el formato PFX. Instale el certificado en el nodo que se convertirá en el servidor de incorporación de cambios de DSC en la ubicación predeterminada que debe ser CERT: \LocalMachine\My. Anote la huella digital del certificado.
1. Seleccione un GUID para usarlo como clave de registro. Para generar uno con PowerShell, escriba lo siguiente en el aviso de PS y presione ENTRAR: '``` [guid]::newGuid()```' o '```New-Guid```'. Esta clave la utilizarán los nodos de cliente como una clave compartida para la autenticación durante el registro. Para más información, vea la sección Clave de registro más adelante.
1. En PowerShell ISE, inicie (F5) el siguiente script de configuración (incluido en la carpeta Example del módulo **xPSDesiredStateConfiguration** como Sample_xDscWebServiceRegistration.ps1). Este script configura el servidor de incorporación de cambios.

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                Enable32BitAppOnWin64   = $false
            }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }
    ```

1. Ejecute la configuración pasando la huella digital del certificado SSL como el parámetro **certificateThumbPrint** y una clave de registro GUID como el parámetro **RegistrationKey**:

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a>Clave de registro

Para permitir que los nodos de cliente se registren con el servidor de forma que puedan usar nombres de configuración en lugar de un identificador de configuración, se guarda una clave de registro creada por medio de la configuración anterior en un archivo denominado `RegistrationKeys.txt` en `C:\Program Files\WindowsPowerShell\DscService`. La clave de registro funciona como un secreto compartido que se usa durante el registro inicial del cliente con el servidor de incorporación de cambios. El cliente generará un certificado autofirmado que se usa para autenticar el servidor de incorporación de cambios inequívocamente una vez que el registro se complete correctamente. La huella digital del certificado se almacena localmente y se asocia con la dirección URL del servidor de extracción.
> **Nota**: No se admiten claves del registro en PowerShell 4.0.

Para configurar un nodo para que se autentique con el servidor de extracción, la clave de registro debe estar en la metaconfiguration de cualquier nodo de destino que se registre con este servidor de extracción. Tenga en cuenta que el elemento **RegistrationKey** de la siguiente metaconfiguration se quita una vez que el equipo de destino se ha registrado correctamente, y que el valor '140a952b-b9d6-406b-b416-e0f759c9c0e4' debe coincidir con el valor almacenado en el archivo RegistrationKeys.txt del servidor de incorporación de cambios. Trate siempre el valor de clave de registro de forma segura, porque conocer esta clave conlleva que cualquier máquina de destino se registre al servidor de incorporación de cambios.

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to setup pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> **Nota**: La sección **ReportServerWeb** permite informar de datos que deben enviarse al servidor de incorporación de cambios.

Si falta la propiedad **ConfigurationID** en el archivo de metaconfiguration, significa implícitamente que el servidor de incorporación de cambios es compatible con la versión V2 del protocolo del servidor de incorporación de cambios, lo que requiere un registro inicial.
Por el contrario, si hay una propiedad **ConfigurationID**, significa que se usa la versión V1 del protocolo del servidor de incorporación de cambios y que no hay ningún procesamiento de registro.

>**Nota**: En un escenario de inserción, hay un error en la versión actual que hace que sea necesario definir una propiedad ConfigurationID en el archivo de metaconfiguration para los nodos que nunca se han registrado en un servidor de incorporación de cambios. De esta manera, se forzará el protocolo del servidor de incorporación de cambios V1 y se evitarán los mensajes de error de registro.

## <a name="placing-configurations-and-resources"></a>Colocación de configuraciones y recursos

Una vez completada la configuración del servidor de incorporación de cambios, los módulos y las configuraciones que estarán disponibles para la incorporación de cambios de los nodos de destino se colocarán en las carpetas que definan las propiedades **ConfigurationPath** y **ModulePath** de la configuración del servidor de incorporación de cambios.
Estos archivos deben estar en un formato concreto para que el servidor de incorporación de cambios los procese correctamente.

### <a name="dsc-resource-module-package-format"></a>Formato del paquete de módulo de recursos de DSC

Cada módulo de recursos se debe comprimir y se le debe asignar un nombre de acuerdo con el patrón `{Module Name}_{Module Version}.zip`.
Por ejemplo, un módulo denominado xWebAdminstration con una versión de módulo de 3.1.2.0 se denominaría 'xWebAdministration_3.2.1.0.zip'.
Cada versión de un módulo debe incluirse en un solo archivo ZIP.
Dado que solo hay una versión de un recurso en cada archivo ZIP, no se admite el formato de módulo que se agrega en WMF 5.0 con compatibilidad con varias versiones de módulo en un único directorio.
Esto significa que antes de empaquetar los módulos de recursos de DSC para su uso con el servidor de incorporación de cambios, deberá realizar un pequeño cambio en la estructura de directorios.
El formato predeterminado de los módulos que contienen recursos de DSC en WMF 5.0 es '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.
Antes de empaquetar el servidor de extracción, quite la carpeta **{Module version}** para que la ruta de acceso se convierta en '{Module Folder}\DscResources\{DSC Resource Folder}\'.
Con este cambio, comprima la carpeta según lo descrito anteriormente y coloque estos archivos ZIP en la carpeta **ModulePath**.

Use `New-DscChecksum {module zip file}` para crear un archivo de suma de comprobación para el módulo que acaba de agregar.

### <a name="configuration-mof-format"></a>Formato de archivo MOF de configuración

Un archivo de configuración MOF debe emparejarse con un archivo de suma de comprobación para que un LCM de un nodo de destino pueda validar la configuración.
Para crear una suma de comprobación, llame al cmdlet [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum).
El cmdlet toma un parámetro **Path** que especifica la carpeta donde se encuentra el MOF de configuración.
El cmdlet crea un archivo de suma de comprobación denominado `ConfigurationMOFName.mof.checksum`, donde `ConfigurationMOFName` es el nombre del archivo mof de configuración.
Si hay más de un archivo MOF de configuración en la carpeta especificada, se crea una suma de comprobación para cada una de las configuraciones de la carpeta.
Coloque los archivos MOF y sus archivos asociados de suma de comprobación en la carpeta **ConfigurationPath**.

>**Nota**: Si cambia el archivo MOF de configuración de cualquier manera, también deberá volver a crear el archivo de suma de comprobación.

### <a name="tooling"></a>Herramientas

Con el fin de facilitar la configuración, la validación y la administración del servidor de incorporación de cambios, se incluyen las siguientes herramientas como ejemplos en la versión más reciente del módulo xPSDesiredStateConfiguration:

1. Un módulo que le ayudará a empaquetar los archivos de configuración y los módulos de recursos de DSC para su uso en el servidor de incorporación de cambios. [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). Vea los ejemplos siguientes:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Un script que valida que el servidor de incorporación de cambios se configura correctamente. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Soluciones comunitarias para el servicio de extracción

La comunidad de DSC ha creado varias soluciones para implementar el protocolo del servicio de extracción.
En entornos locales, estas ofrecen funcionalidades de servicios de extracción y una oportunidad para contribuir con la comunidad con mejoras.

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Configuración del cliente de incorporación de cambios

En los temas siguientes se describe en detalle cómo configurar los clientes de extracción:

- [Configuración de un cliente de extracción de DSC mediante un id. de configuración](pullClientConfigID.md)
- [Configuración de un cliente de extracción de DSC mediante nombres de configuración](pullClientConfigNames.md)
- [Configuraciones parciales](partialConfigs.md)

## <a name="see-also"></a>Vea también

- [Información general sobre la configuración de estado deseado de Windows PowerShell](overview.md)
- [Establecer configuraciones](enactingConfigurations.md)
- [Uso de un servidor de informes de DSC](reportServer.md)
- [[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx) (Protocolo del modelo de extracción de configuración de estado deseado)
- [[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx) (Errata del protocolo del modelo de extracción de configuración de estado deseado)
