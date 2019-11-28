---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Procedimientos recomendados del servidor de extracción
ms.openlocfilehash: 5cb47598b11f7884dddf1440cec21afeab49bebb
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417729"
---
# <a name="pull-server-best-practices"></a>Procedimientos recomendados del servidor de extracción

Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades. Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](/powershell/scripting/dsc/pull-server/pullserver#community-solutions-for-pull-service).

Resumen: El objetivo de este documento es incluir el proceso y la extensibilidad para ayudar a los ingenieros que se estén preparando para la solución. En los detalles se deberían ofrecer procedimientos recomendados identificados por los clientes y después validados por el equipo del producto para garantizar que estén orientados al futuro y se consideren estables.

| |Información del documento|
|:---|:---|
Autor | Michael Greene
Revisores | Ben Gelens, Ravikanth Chaganti y Aleksandar Nikolic
Publicado | Abril de 2015

## <a name="abstract"></a>Resumen

Este documento está diseñado para proporcionar orientación oficial a cualquiera que esté planeando una implementación de servidor de extracción de la configuración de estado deseado de Windows PowerShell. Un servidor de extracción es un servicio sencillo cuya implementación solo debería llevar unos minutos. Aunque en este documento se ofrece orientación técnica de procedimientos que se puede usar durante una implementación, su valor es constituir una referencia de procedimientos recomendados y de aspectos que se deben tener en cuenta antes de implementar.
Los lectores deberían tener conocimientos básicos de DSC y de los términos empleados para describir los componentes incluidos en una implementación de DSC. Para más información, vea el tema [Información general sobre la configuración de estado deseado de Windows PowerShell](/powershell/scripting/dsc/overview).
Dado que se espera que DSC evolucione al ritmo de la nube, también se espera que la tecnología subyacente, incluido el servidor de extracción, evolucione e incorpore nuevas características. Este documento incluye una tabla de versiones en el apéndice que proporciona referencias a versiones anteriores y a soluciones futuras para fomentar diseños orientados al futuro.

Las dos secciones principales de este documento son estas:

- Planeamiento de configuración
- Guía de instalación

### <a name="versions-of-the-windows-management-framework"></a>Versiones de Windows Management Framework

La información de este documento se aplica a Windows Management Framework 5.0. Aunque no se necesita WMF 5.0 para implementar ni usar un servidor de extracción, la versión 5.0 es el centro de este documento.

### <a name="windows-powershell-desired-state-configuration"></a>Configuración de estado deseado de Windows PowerShell

Configuración de estado deseado (DSC) es una plataforma de administración que permite implementar y administrar datos de configuración mediante una sintaxis del sector denominada Managed Object Format (MOF) para describir el Modelo de información común (CIM). Existe un proyecto de código abierto, Infraestructura de administración abierta (OMI), para seguir desarrollando estos estándares en plataformas como Linux y sistemas operativos de hardware de red. Para más información, vea la [página de DMTF con los vínculos a las especificaciones de MOF](https://www.dmtf.org/standards/cim) y los [documentos y el código de OMI](https://collaboration.opengroup.org/omi/documents.php).

Windows PowerShell proporciona un conjunto de extensiones de lenguaje para Configuración de estado deseado que puede usar para crear y administrar configuraciones declarativas.

### <a name="pull-server-role"></a>Rol de servidor de extracción

Un servidor de extracción proporciona un servicio centralizado para almacenar configuraciones que sean accesibles a los nodos de destino.

El rol de servidor de extracción puede implementarse como una instancia de servidor web o como un recurso compartido de archivos SMB. La característica de servidor web incluye una interfaz OData y opcionalmente puede incluir capacidades para que los nodos de destino confirmen el éxito o el error a medida que se apliquen las configuraciones. Esta funcionalidad es útil en entornos donde hay muchos nodos de destino.
Después de configurar un nodo de destino (también conocido como cliente) para que apunte al servidor de extracción, se descargan y se aplican los datos de configuración más recientes y los scripts necesarios. Puede ser como una implementación única o como un trabajo recurrente, lo que también convierte al servidor de extracción en un activo importante para administrar el cambio a escala. Para más información, consulte [ Windows PowerShell Desired State Configuration Pull Servers ](/powershell/scripting/dsc/pullServer/pullserver) (Servidores de incorporación de cambios de la configuración de estado deseado de Windows PowerShell) y

[Push and Pull Configuration Modes](/powershell/scripting/dsc/pullServer/pullserver) (Modos de configuración de inserción y extracción).

## <a name="configuration-planning"></a>Planeamiento de configuración

En cualquier implementación de software empresarial hay información que se puede recopilar de antemano para ayudar a planear la arquitectura correcta y a estar preparado para los pasos necesarios de implementación. En las secciones siguientes se proporciona información sobre cómo prepararse y sobre las conexiones organizativas que probablemente tengan que realizarse de antemano.

### <a name="software-requirements"></a>Requisitos de software

La implementación de un servidor de extracción exige la característica Servicio de DSC de Windows Server. Esta característica se presentó en Windows Server 2012 y se ha actualizado en las versiones siguientes de Windows Management Framework (WMF).

### <a name="software-downloads"></a>Descargas de software

Además de instalar el contenido más reciente desde Windows Update, hay dos descargas consideradas procedimientos recomendados para implementar un servidor de extracción de DSC: la versión más reciente de Windows Management Framework y un módulo de DSC para automatizar el aprovisionamiento del servidor de extracción.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 incluye una característica denominada Servicio de DSC. La característica Servicio de DSC proporciona la funcionalidad de servidor de extracción, incluidos los archivos binarios que admiten el punto de conexión de OData.
WMF está incluido en Windows Server y se actualiza a un ritmo ágil entre versiones de Windows Server. [Las nuevas versiones de WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) pueden incluir actualizaciones de la característica Servicio de DSC. Por esta razón, se recomienda descargar la versión más reciente de WMF y revisar las notas de la versión para determinar si incluye una actualización de dicha característica. También debe revisar la sección de notas de la versión que indica si el estado de diseño de un escenario o una actualización es estable o experimental.
Para permitir un ritmo de versiones ágil, hay características individuales que se pueden declarar estables, lo que indica que están listas para usarse en un entorno de producción, aunque WMF se haya publicado en versión preliminar.
Otras características que históricamente se han actualizado con las versiones de WMF (vea las Notas de la versión de WMF para obtener más detalles):

- Entorno de scripting integrado (ISE) de Windows PowerShell
- Servicios web de Windows PowerShell (Extensión IIS Management OData)
- Configuración de estado deseado (DSC) de Windows PowerShell
- Administración remota de Windows (WinRM) Instrumental de administración de Windows (WMI)

### <a name="dsc-resource"></a>Recurso de DSC

Una implementación de servidor de extracción se puede simplificar mediante el aprovisionamiento del servicio con un script de configuración DSC. En este documento se incluyen scripts de configuración que pueden usarse para implementar un nodo de servidor listo para producción. Para usar los scripts de configuración, se necesita un módulo de DSC que no está incluido en Windows Server. El nombre del módulo necesario es **xPSDesiredStateConfiguration**, que incluye el recurso de DSC **xDscWebService**. El módulo xPSDesiredStateConfiguration se puede descargar [aquí](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Use el cmdlet `Install-Module` del módulo **PowerShellGet**.

```powershell
Install-Module xPSDesiredStateConfiguration
```

El módulo **PowerShellGet** descargará el módulo en:

`C:\Program Files\Windows PowerShell\Modules`

Tarea de planeamiento|
---|
¿Tiene acceso a los archivos de instalación de Windows Server 2012 R2?|
¿El entorno de implementación tendrá acceso a Internet para descargar WMF y el módulo desde la galería en línea?|
¿Cómo se instalarán las actualizaciones de seguridad más recientes después de instalar el sistema operativo?|
¿El entorno tendrá acceso a Internet para obtener actualizaciones o tendrá un servidor local de Windows Server Update Services (WSUS)?|
¿Tiene acceso a archivos de instalación de Windows Server que ya incluyen actualizaciones mediante inserción sin conexión?|

### <a name="hardware-requirements"></a>Requisitos de hardware

Las implementaciones de servidor de extracción se admiten tanto en servidores físicos como virtuales. Los requisitos de tamaño del servidor de extracción están en línea con los requisitos de Windows Server 2012 R2.

CPU: procesador de 64 bits a 1,4 GHz Memoria: 512 MB Espacio en disco: 32 GB Red: adaptador Gigabit Ethernet

Tarea de planeamiento|
---|
¿Va a implementar en hardware físico o en una plataforma de virtualización?|
¿Cuál es el proceso para solicitar un nuevo servidor para el entorno de destino?|
¿Cuál es el tiempo de respuesta medio para que un servidor esté disponible?|
¿Qué servidor de tamaño va a solicitar?|

### <a name="accounts"></a>Cuentas

No hay ningún requisito de cuenta de servicio para implementar una instancia de servidor de extracción.
Pero hay escenarios donde el sitio web podría ejecutarse en el contexto de una cuenta de usuario local.
Por ejemplo, si hay que acceder a un recurso compartido de almacenamiento de contenido del sitio web y Windows Server o el dispositivo que hospeda el recurso compartido de almacenamiento no están unidos a dominio.

### <a name="dns-records"></a>Registros DNS

Al configurar clientes para trabajar con un entorno de servidor de extracción, tendrá que usar un nombre de servidor.
En entornos de prueba, normalmente se usa el nombre de host del servidor o, si la resolución de nombres DNS no está disponible, se puede usar la dirección IP del servidor.
En entornos de producción o en un entorno de laboratorio que sirve para representar una implementación de producción, el procedimiento recomendado es crear un registro CNAME DNS.

Un CNAME DNS le permite crear un alias para hacer referencia al registro de host (A).
El objetivo del registro de nombre adicional es aumentar la flexibilidad por si se necesitara un cambio en el futuro.
Un CNAME puede ayudar a aislar la configuración del cliente para que los cambios en el entorno de servidor, como la sustitución de un servidor de extracción o la adición de servidores adicionales de extracción, no exijan un cambio correspondiente en la configuración del cliente.

Al elegir un nombre para el registro DNS, tenga en cuenta la arquitectura de la solución.
Si usa equilibrio de carga, el certificado empleado para proteger el tráfico a través de HTTPS tendrá que llevar el mismo nombre que el registro DNS.

Escenario |Procedimiento recomendado
:---|:---
Entorno de prueba |Si es posible, reproduzca el entorno de producción planeado. Un nombre de host del servidor es adecuado para configuraciones sencillas. Si DNS no está disponible, se puede usar una dirección IP en lugar de un nombre de host.|
Implementación de un solo nodo |Cree un registro CNAME DNS que apunte al nombre de host del servidor.|

Para más información, vea [Configuring DNS Round Robin in Windows Server (Configuración de round robin de DNS en Windows Server)](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).

Tarea de planeamiento|
---|
¿Sabe con quién tiene que ponerse en contacto para crear y cambiar registros DNS?|
¿Cuál es el tiempo de respuesta medio de una solicitud de registro DNS?|
¿Necesita solicitar registros estáticos de nombre de host (A) para servidores?|
¿Qué va a solicitar como CNAME?|
En caso necesario, ¿qué tipo de solución de equilibrio de carga usaría? (vea la sección Equilibrio de carga para obtener detalles)|

### <a name="public-key-infrastructure"></a>Infraestructura de clave pública

Hoy en día la mayoría de las organizaciones exigen que el tráfico de red, especialmente aquel que incluye datos confidenciales tales como la forma en que los servidores están configurados, se valide o se cifre durante el tránsito.
Aunque es posible implementar un servidor de extracción mediante HTTP, que permite las solicitudes de cliente en texto sin cifrar, el procedimiento recomendado es proteger el tráfico mediante HTTPS. El servicio se puede configurar de modo que use HTTPS con un conjunto de parámetros en el recurso de DSC **xPSDesiredStateConfiguration**.

Los requisitos de certificado para proteger el tráfico HTTPS del servidor de extracción no difieren de la protección de cualquier otro sitio web HTTPS. La plantilla **servidor web** de Servicios de servidor de certificados de Windows Server satisface las capacidades necesarias.

Tarea de planeamiento|
---|
Si las solicitudes de certificado no están automatizadas, ¿con quién tiene que ponerse en contacto para solicitar un certificado?|
¿Cuál es el tiempo de respuesta medio de la solicitud?|
¿Cómo se le transferirá el archivo de certificado?|
¿Cómo se le transferirá la clave privada del certificado?|
¿Cuál es el periodo de expiración predeterminado?|
¿Ha decidido un nombre DNS para el entorno de servidor de extracción que pueda usar para el nombre de certificado?|

### <a name="choosing-an-architecture"></a>Elección de una arquitectura

Un servidor de extracción se puede implementar mediante un servicio web hospedado en IIS o un recurso compartido de archivos SMB. En la mayoría de los casos, la opción del servicio web proporcionará mayor flexibilidad. No es raro que el tráfico HTTPS atraviese límites de red, mientras que el tráfico SMB se suele filtrar o bloquear entre redes. El servicio web también ofrece la opción de incluir un servidor de conformidad o un administrador de informes web (ambos temas se tratarán en una versión futura de este documento) que proporcionan un mecanismo para que los clientes informen del estado a un servidor para una visibilidad centralizada.
SMB proporciona una opción para entornos donde la directiva determina que no se debe usar un servidor web y para otros requisitos de entorno que convierten a un rol de servidor web en no deseado.
En cualquier caso, no olvide evaluar los requisitos de firma y cifrado del tráfico. HTTPS, firma SMB y directivas IPSEC son opciones que vale la pena tener en cuenta.

#### <a name="load-balancing"></a>Equilibrio de carga

Los clientes que interactúan con el servicio web realizan una solicitud de información que se devuelve en una sola respuesta. No se necesitan solicitudes secuenciales, por lo que no es necesario que la plataforma de equilibrio de carga garantice el mantenimiento de las sesiones en un único servidor en cualquier momento.

Tarea de planeamiento|
---|
¿Qué solución se usará para equilibrar el tráfico entre servidores?|
Si usa un equilibrador de carga de hardware, ¿quién recibirá la solicitud de agregar una nueva configuración al dispositivo?|
¿Cuál es el tiempo de respuesta medio de una solicitud para configurar un nuevo servicio web de equilibrio de carga?|
¿Qué información será necesaria para la solicitud?|
¿Habrá que solicitar una dirección IP adicional o el equipo responsable del equilibrio de carga se ocupará de eso?|
¿Tiene los registros DNS necesarios y el equipo responsable de configurar la solución de equilibrio de carga los necesitará?|
¿La solución de equilibrio de carga exige que el dispositivo administre la PKI o puede equilibrar la carga de tráfico HTTPS siempre que no haya ningún requisito de sesión?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Preconfiguración de configuraciones y módulos en el servidor de extracción

Como parte del planeamiento de configuración, debe pensar en los módulos y configuraciones de DSC que hospedará el servidor de extracción. A efectos del planeamiento de configuración, es importante tener un conocimiento básico de cómo preparar e implementar contenido en un servidor de extracción.

En el futuro, esta sección se ampliará y se incluirá en una guía de funcionamiento del servidor de extracción de DSC.  En esa guía se hablará del proceso cotidiano de administrar módulos y configuraciones a lo largo del tiempo mediante automatización.

#### <a name="dsc-modules"></a>Módulos de DSC

Los clientes que soliciten una configuración necesitarán los módulos de DSC necesarios. Una funcionalidad del servidor de extracción es automatizar la distribución a petición de módulos de DSC a los clientes. Si está implementando un servidor de extracción por primera vez, quizás como laboratorio o prueba de concepto, es probable que vaya a depender de los módulos de DSC que hay disponibles en repositorios públicos, como la Galería de PowerShell, o los repositorios GitHub de PowerShell.org para los módulos de DSC.

Es fundamental recordar que cualquier módulo descargado de un repositorio público, incluso orígenes en línea de confianza como la Galería de PowerShell, debe ser revisado por alguien con experiencia en PowerShell y conocimiento del entorno donde se van a usar los módulos antes de que estos se empleen en producción. Mientras se realiza esta tarea, es buen momento para buscar cualquier carga adicional en el módulo que pueda quitarse, como scripts de ejemplo y documentación. Esto reducirá el ancho de banda de red por cliente en la primera solicitud, cuando los módulos se descarguen a través de la red desde el servidor al cliente.

Cada módulo se debe empaquetar en un formato concreto, un archivo ZIP denominado NombreMódulo_Versión.zip que contiene la carga del módulo. Una vez que el archivo se ha copiado en el servidor, se debe crear un archivo de suma de comprobación. Cuando los clientes se conectan al servidor, la suma de comprobación se usa para comprobar que el contenido del módulo de DSC no ha cambiado desde que se publicó.

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

Tarea de planeamiento|
---|
Si está planeando un entorno de prueba o laboratorio, ¿qué escenarios es fundamental validar?|
¿Hay módulos disponibles públicamente que contengan recursos para cubrir todo lo que necesita o va a tener que crear sus propios recursos?|
¿El entorno tendrá acceso a Internet para recuperar módulos públicos?|
¿Quién será responsable de revisar los módulos de DSC?|
Si está planeando un entorno de producción, ¿qué usará como repositorio local para almacenar los módulos de DSC?|
¿Habrá un equipo central que acepte los módulos de DSC de los equipos solicitantes? ¿Cuál será el proceso?|
¿Se automatizará el empaquetado, la copia y la creación de una suma de comprobación para los módulos de DSC listos para producción que van al servidor desde el repositorio de origen?|
¿El equipo también será responsable de administrar la plataforma de automatización?|

#### <a name="dsc-configurations"></a>Configuraciones DSC

El fin de un servidor de extracción es proporcionar un mecanismo centralizado para distribuir configuraciones DSC a nodos cliente. Las configuraciones se almacenan en el servidor como documentos MOF.
Cada documento tendrá como nombre un **GUID** único. Cuando se configuran los clientes para conectar con un servidor de extracción, se les da el **GUID** de la configuración que deben solicitar. Este sistema para hacer referencia a las configuraciones por **GUID** garantiza la exclusividad global y es flexible, de modo que una configuración se puede aplicar con granularidad por nodo o como una configuración de rol que abarca varios servidores que deben tener configuraciones idénticas.

#### <a name="guids"></a>GUID

El planeamiento de **GUID** de configuración merece atención adicional cuando se piensa en una implementación de servidor de extracción. No hay ningún requisito específico para cómo administrar **GUID** y el proceso es probable que sea único para cada entorno. El proceso puede ir desde sencillo a complejo: un archivo CSV almacenado centralmente, una tabla SQL simple, una CMDB o una solución compleja que exija integración con otra herramienta o solución de software. Hay dos enfoques generales:

- **Asignar GUID por servidor**: ofrece una forma de garantizar que cada configuración de servidor se controla individualmente. Esto proporciona un nivel de precisión en torno a las actualizaciones y puede funcionar bien en entornos con pocos servidores.
- **Asignar GUID por rol de servidor**: todos los servidores que realizan la misma función, como los servidores web, usan el mismo GUID para hacer referencia a los datos de configuración necesarios.  Tenga en cuenta que si hay muchos servidores que compartan el mismo GUID, todos ellos se actualizarían simultáneamente cuando cambiara la configuración.

  El GUID debería considerarse información confidencial, porque podría ser aprovechado por alguien con malas intenciones para obtener datos sobre cómo están implementados y configurados los servidores en el entorno. Para más información, vea [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/) (Asignación segura de GUID en modo de extracción de la configuración de estado deseado de PowerShell).

Tarea de planeamiento|
---|
¿Quién será responsable de copiar las configuraciones en la carpeta del servidor de extracción cuando estén listas?|
Si un equipo solicitante crea configuraciones, ¿cuál será el proceso para entregarlas?|
¿Aprovechará un repositorio para almacenar las configuraciones a medida que se crean para todos los equipos?|
¿Automatizará el proceso de copiar las configuraciones en el servidor y de crear una suma de comprobación cuando estén listas?|
¿Cómo se asignarán los GUID a los servidores o roles y dónde se almacenarán?|
¿Qué proceso usará para configurar equipos cliente y cómo se integrará con el proceso para crear y almacenar GUID de configuración?|

## <a name="installation-guide"></a>Guía de instalación

*Los scripts de este documento son ejemplos estables. Revise siempre los scripts detenidamente antes de ejecutarlos en un entorno de producción.*

### <a name="prerequisites"></a>Requisitos previos

Para comprobar la versión de PowerShell del servidor, use el siguiente comando.

```powershell
$PSVersionTable.PSVersion
```

Si es posible, actualice a la versión más reciente de Windows Management Framework.
Luego, ejecute el módulo `xPsDesiredStateConfiguration` con el siguiente comando.

```powershell
Install-Module xPSDesiredStateConfiguration
```

El comando le pedirá su aprobación antes de descargar el módulo.

### <a name="installation-and-configuration-scripts"></a>Scripts de instalación y configuración

El mejor método para implementar un servidor de extracción de DSC es usar un script de configuración de DSC. En este documento se presentan los scripts incluyendo tanto la configuración básica que configuraría solo el servicio web de DSC como la configuración avanzada que configuraría un servidor descentralizado de Windows Server, incluido un servicio web de DSC.

Nota:  De momento, el módulo `xPSDesiredStateConfiguration` de DSC exige que la configuración regional del servidor sea EN-US.

### <a name="basic-configuration-for-windows-server-2012"></a>Configuración básica de Windows Server 2012

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>Configuración avanzada de Windows Server 2012 R2

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a>Comprobar funcionalidad de servidor de extracción

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a>Configurar clientes

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a>Referencias, fragmentos de código y ejemplos adicionales

En este ejemplo se muestra cómo iniciar manualmente una conexión de cliente (necesita WMF5) para realizar pruebas.

```powershell
Update-DscConfiguration –Wait -Verbose
```

Se usa el cmdlet [DnsServerResourceRecordName agregar](http://bit.ly/1G1H31L) para agregar un registro CNAME de tipo a una zona DNS.

La función de PowerShell para [crear una suma de comprobación y publicar el MOF de DSC en el servidor de extracción SMB](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) genera automáticamente la suma de comprobación necesaria y, luego, copia los archivos de suma de comprobación y de configuración MOF en el servidor de extracción SMB.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Apéndice - Conceptos básicos de tipos de archivos de datos del servicio ODATA

Se almacena un archivo de datos para crear información durante la implementación de un servidor de extracción que incluye el servicio web OData. El tipo de archivo depende del sistema operativo, como se describe a continuación.

- **Windows Server 2012** El tipo de archivo siempre será .mdb.
- **Windows Server 2012 R2** El tipo de archivo será .edb a menos que se especifique un tipo .mdb en la configuración.

En el [script de ejemplo avanzado](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) para instalar un servidor de extracción, también encontrará un ejemplo de cómo controlar automáticamente la configuración del archivo web.config para evitar cualquier posibilidad de error causado por el tipo de archivo.
