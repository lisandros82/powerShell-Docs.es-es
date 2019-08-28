---
ms.date: 03/04/2019
keywords: dsc,powershell,configuration,setup
title: Servicio de extracción de DSC
ms.openlocfilehash: 865eae5813e0c7b656a4158f0b1350e60f1e3291
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986537"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="ba8cf-103">Servicio de extracción de Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="ba8cf-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba8cf-104">El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="ba8cf-105">Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="ba8cf-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="ba8cf-106">El Administrador de configuración local puede administrarse de forma central con una solución de servicio de extracción.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-106">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="ba8cf-107">Cuando se usa este enfoque, el nodo que se está administrando se registra en un servicio y se le asigna una configuración en las opciones del LCM.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="ba8cf-108">La configuración y todos los recursos de DSC necesarios como dependencias para la configuración se descargan en la máquina y el LCM las usa para administrar la configuración.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="ba8cf-109">La información sobre el estado de la máquina que se está administrando se carga al servicio para crear un informe.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="ba8cf-110">Este concepto se conoce como "servicio de extracción".</span><span class="sxs-lookup"><span data-stu-id="ba8cf-110">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="ba8cf-111">Las opciones actuales del servicio de extracción incluyen:</span><span class="sxs-lookup"><span data-stu-id="ba8cf-111">The current options for pull service include:</span></span>

- <span data-ttu-id="ba8cf-112">Servicio Desired State Configuration de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="ba8cf-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="ba8cf-113">Un servicio de extracción que se ejecuta en Windows Server</span><span class="sxs-lookup"><span data-stu-id="ba8cf-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="ba8cf-114">Soluciones de código abierto mantenidas por la comunidad</span><span class="sxs-lookup"><span data-stu-id="ba8cf-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="ba8cf-115">Un recurso compartido SMB</span><span class="sxs-lookup"><span data-stu-id="ba8cf-115">An SMB share</span></span>

<span data-ttu-id="ba8cf-116">**La solución recomendada**, y la opción que tiene la mayor cantidad de características disponibles, es [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="ba8cf-116">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="ba8cf-117">El servicio de Azure puede administrar nodos locales en centros de datos privados, o bien en nubes públicas como Azure y AWS.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-117">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="ba8cf-118">En el caso de entornos privados donde los servidores no se pueden conectar directamente a Internet, considere limitar el tráfico de salida solo al intervalo IP de Azure (consulte los [intervalos IP del centro de datos de Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="ba8cf-118">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="ba8cf-119">Las características del servicio en línea que no están disponibles actualmente en el servicio de extracción de Windows Server incluyen las siguientes:</span><span class="sxs-lookup"><span data-stu-id="ba8cf-119">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="ba8cf-120">Se cifran todos los datos, ya sea que estén en tránsito o en reposo</span><span class="sxs-lookup"><span data-stu-id="ba8cf-120">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="ba8cf-121">Los certificados de cliente se crean y administran de manera automática</span><span class="sxs-lookup"><span data-stu-id="ba8cf-121">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="ba8cf-122">Almacén de secretos para administrar de manera centralizada las [contraseñas/credenciales](/azure/automation/automation-credentials) o las [variables](/azure/automation/automation-variables), como nombres de servidor o cadenas de conexión</span><span class="sxs-lookup"><span data-stu-id="ba8cf-122">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="ba8cf-123">Administración centralizada de la [configuración de LCM](../managing-nodes/metaConfig.md#basic-settings) del nodo</span><span class="sxs-lookup"><span data-stu-id="ba8cf-123">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="ba8cf-124">Asignación centralizada de las configuraciones a los nodos cliente</span><span class="sxs-lookup"><span data-stu-id="ba8cf-124">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="ba8cf-125">Publicación de los cambios de configuración en "grupos de valor controlado" para pruebas antes de llegar a producción</span><span class="sxs-lookup"><span data-stu-id="ba8cf-125">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="ba8cf-126">Informes gráficos</span><span class="sxs-lookup"><span data-stu-id="ba8cf-126">Graphical reporting</span></span>
  - <span data-ttu-id="ba8cf-127">Detalle de estado en el nivel de recurso DSC de granularidad</span><span class="sxs-lookup"><span data-stu-id="ba8cf-127">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="ba8cf-128">Mensajes detallados de error de equipos cliente para la solución de problemas</span><span class="sxs-lookup"><span data-stu-id="ba8cf-128">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="ba8cf-129">[Integración de Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) para alertas, tareas automatizadas, aplicación Android/iOS para informes y alertas</span><span class="sxs-lookup"><span data-stu-id="ba8cf-129">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="ba8cf-130">Servicio de extracción de DSC en Windows Server</span><span class="sxs-lookup"><span data-stu-id="ba8cf-130">DSC pull service in Windows Server</span></span>

<span data-ttu-id="ba8cf-131">Es posible configurar un servicio de extracción para que se ejecute en Windows Server.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-131">It is possible to configure a pull service to run on Windows Server.</span></span>
<span data-ttu-id="ba8cf-132">Tenga en cuenta que la solución de servicio de extracción incluida en Windows Server solo tiene funcionalidades de almacenamiento de configuraciones y módulos para descargar y capturar datos de informes en una base de datos.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-132">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="ba8cf-133">No se incluyen muchas de las funcionalidades que ofrece el servicio en Azure y, por lo tanto, no es una herramienta lo suficientemente eficaz como para evaluar el uso del servicio.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-133">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="ba8cf-134">El servicio de extracción que se ofrece en Windows Server es un servicio web en IIS que usa una interfaz de OData para poner a disposición de los nodos de destino los archivos de configuración DSC cuando esos nodos los soliciten.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-134">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="ba8cf-135">Requisitos para usar un servidor de extracción:</span><span class="sxs-lookup"><span data-stu-id="ba8cf-135">Requirements for using a pull server:</span></span>

- <span data-ttu-id="ba8cf-136">Un servidor que ejecute:</span><span class="sxs-lookup"><span data-stu-id="ba8cf-136">A server running:</span></span>
  - <span data-ttu-id="ba8cf-137">WMF/PowerShell 4.0 o una versión superior</span><span class="sxs-lookup"><span data-stu-id="ba8cf-137">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="ba8cf-138">Rol del servidor IIS</span><span class="sxs-lookup"><span data-stu-id="ba8cf-138">IIS server role</span></span>
  - <span data-ttu-id="ba8cf-139">Servicio DSC</span><span class="sxs-lookup"><span data-stu-id="ba8cf-139">DSC Service</span></span>
- <span data-ttu-id="ba8cf-140">Idealmente, algún medio para generar un certificado, para proteger las credenciales que se pasan al administrador de configuración local (LCM) en los nodos de destino</span><span class="sxs-lookup"><span data-stu-id="ba8cf-140">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="ba8cf-141">La mejor manera para configurar Windows Server para hospedar un servicio de extracción es usar una configuración de DSC.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-141">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="ba8cf-142">A continuación se muestra un script de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-142">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="ba8cf-143">Sistemas de base de datos admitidos</span><span class="sxs-lookup"><span data-stu-id="ba8cf-143">Supported database systems</span></span>

|<span data-ttu-id="ba8cf-144">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="ba8cf-144">WMF 4.0</span></span>   |<span data-ttu-id="ba8cf-145">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="ba8cf-145">WMF 5.0</span></span>  |<span data-ttu-id="ba8cf-146">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="ba8cf-146">WMF 5.1</span></span> |<span data-ttu-id="ba8cf-147">WMF 5.1 (Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="ba8cf-147">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="ba8cf-148">MDB</span><span class="sxs-lookup"><span data-stu-id="ba8cf-148">MDB</span></span>     |<span data-ttu-id="ba8cf-149">ESENT (predeterminado), MDB</span><span class="sxs-lookup"><span data-stu-id="ba8cf-149">ESENT (Default), MDB</span></span> |<span data-ttu-id="ba8cf-150">ESENT (predeterminado), MDB</span><span class="sxs-lookup"><span data-stu-id="ba8cf-150">ESENT (Default), MDB</span></span>|<span data-ttu-id="ba8cf-151">ESENT (predeterminado), SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="ba8cf-151">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="ba8cf-152">A partir de la versión 17090 de [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server es una opción admitida en el servicio de extracción (característica de Windows *DSC-Service*).</span><span class="sxs-lookup"><span data-stu-id="ba8cf-152">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="ba8cf-153">Esto constituye una nueva opción para ajustar la escala de entornos de DSC de gran envergadura que no se han migrado a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="ba8cf-153">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> [!NOTE]
> <span data-ttu-id="ba8cf-154">La compatibilidad con SQL Server no se incluirá en WMF 5.1 ni en versiones anteriores, y solo estará disponible en versiones de Windows Server posteriores a la 17090.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-154">SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="ba8cf-155">Para configurar el servidor de extracción de forma que use SQL Server, establezca **SqlProvider** en `$true` y **SqlConnectionString** en una cadena de conexión de SQL Server válida.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-155">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="ba8cf-156">Para más información, vea [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings) (Cadenas de conexión de SqlClient).</span><span class="sxs-lookup"><span data-stu-id="ba8cf-156">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="ba8cf-157">Para ver un ejemplo de configuración de SQL Server con **xDscWebService**, lea primero [Uso del recurso xDSCWebService](#using-the-xdscwebservice-resource) y, después, revise [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 en GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="ba8cf-157">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="ba8cf-158">Uso del recurso xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="ba8cf-158">Using the xDscWebService resource</span></span>

<span data-ttu-id="ba8cf-159">La manera más fácil de configurar un servidor de extracción web es usando el recurso **xDscWebService**, incluido en el módulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-159">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="ba8cf-160">En los siguientes pasos se explica cómo usar el recurso en una configuración que configure el servicio web.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-160">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="ba8cf-161">Llame al cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) para instalar el módulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-161">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>
   > [!NOTE]
   > <span data-ttu-id="ba8cf-162">**Install-Module** está incluido en el módulo **PowerShellGet**, que se incluye en PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-162">**Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="ba8cf-163">Puede descargar el módulo **PowerShellGet** para PowerShell 3.0 y 4.0 en [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186) (Vista previa de los módulos de PowerShell PackageManagement).</span><span class="sxs-lookup"><span data-stu-id="ba8cf-163">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
2. <span data-ttu-id="ba8cf-164">Obtenga un certificado SSL para el servidor de extracción de DSC de una entidad de certificación de confianza, ya sea dentro de su organización o de una entidad pública.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-164">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="ba8cf-165">El certificado recibido de la entidad suele tener el formato PFX.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-165">The certificate received from the authority is usually in the PFX format.</span></span>
3. <span data-ttu-id="ba8cf-166">Instale el certificado en el nodo que se convertirá en el servidor de extracción de DSC en la ubicación predeterminada que debe ser `CERT:\LocalMachine\My`.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-166">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="ba8cf-167">Anote la huella digital del certificado.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-167">Make a note of the certificate thumbprint.</span></span>
4. <span data-ttu-id="ba8cf-168">Seleccione un GUID para usarlo como clave de registro.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-168">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="ba8cf-169">Para generar uno con PowerShell, escriba lo siguiente en el aviso de PS y pulse la tecla ENTRAR: `[guid]::newGuid()` o `New-Guid`.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-169">To generate one using PowerShell enter the following at the PS prompt and press enter: `[guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="ba8cf-170">Esta clave la utilizarán los nodos de cliente como una clave compartida para la autenticación durante el registro.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-170">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="ba8cf-171">Para más información, vea la sección Clave de registro más adelante.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-171">For more information, see the Registration Key section below.</span></span>
5. <span data-ttu-id="ba8cf-172">En PowerShell ISE, inicie (F5) el siguiente script de configuración (incluido en la carpeta Examples del módulo **xPSDesiredStateConfiguration** como `Sample_xDscWebServiceRegistration.ps1`).</span><span class="sxs-lookup"><span data-stu-id="ba8cf-172">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`).</span></span> <span data-ttu-id="ba8cf-173">Este script configura el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-173">This script sets up the pull server.</span></span>

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

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
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
                UseSecurityBestPractices     = $true
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

6. <span data-ttu-id="ba8cf-174">Ejecute la configuración pasando la huella digital del certificado SSL como el parámetro **certificateThumbPrint** y una clave de registro GUID como el parámetro **RegistrationKey**:</span><span class="sxs-lookup"><span data-stu-id="ba8cf-174">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="ba8cf-175">Clave de registro</span><span class="sxs-lookup"><span data-stu-id="ba8cf-175">Registration Key</span></span>

<span data-ttu-id="ba8cf-176">Para permitir que los nodos de cliente se registren con el servidor de forma que puedan usar nombres de configuración en lugar de un identificador de configuración, se guarda una clave de registro creada por medio de la configuración anterior en un archivo denominado `RegistrationKeys.txt` en `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-176">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="ba8cf-177">La clave de registro funciona como un secreto compartido que se usa durante el registro inicial del cliente con el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-177">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="ba8cf-178">El cliente generará un certificado autofirmado que se usa para autenticar el servidor de incorporación de cambios inequívocamente una vez que el registro se complete correctamente.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-178">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="ba8cf-179">La huella digital del certificado se almacena localmente y se asocia con la dirección URL del servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-179">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="ba8cf-180">No se admiten claves del registro en PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-180">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="ba8cf-181">Para configurar un nodo para que se autentique con el servidor de extracción, la clave de registro debe estar en la metaconfiguration de cualquier nodo de destino que se registre con este servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-181">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="ba8cf-182">Tenga en cuenta que el elemento **RegistrationKey** de la siguiente metaconfiguración se quita una vez que el equipo de destino se ha registrado correctamente y que el valor debe coincidir con el valor almacenado en el archivo `RegistrationKeys.txt` en el servidor de extracción ("140a952b-b9d6-406b-b416-e0f759c9c0e4" para este ejemplo).</span><span class="sxs-lookup"><span data-stu-id="ba8cf-182">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="ba8cf-183">Trate siempre el valor de clave de registro de forma segura, porque conocer esta clave conlleva que cualquier máquina de destino se registre al servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-183">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

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

> [!NOTE]
> <span data-ttu-id="ba8cf-184">La sección **ReportServerWeb** permite informar de datos que deben enviarse al servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-184">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="ba8cf-185">Si falta la propiedad **ConfigurationID** en el archivo de metaconfiguration, significa implícitamente que el servidor de incorporación de cambios es compatible con la versión V2 del protocolo del servidor de incorporación de cambios, lo que requiere un registro inicial.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-185">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="ba8cf-186">Por el contrario, si hay una propiedad **ConfigurationID**, significa que se usa la versión V1 del protocolo del servidor de incorporación de cambios y que no hay ningún procesamiento de registro.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-186">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="ba8cf-187">En un escenario de inserción, hay un error en la versión actual que hace que sea necesario definir una propiedad ConfigurationID en el archivo de metaconfiguration para los nodos que nunca se hayan registrado en un servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-187">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="ba8cf-188">De esta manera, se forzará el protocolo del servidor de incorporación de cambios V1 y se evitarán los mensajes de error de registro.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-188">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="ba8cf-189">Colocación de configuraciones y recursos</span><span class="sxs-lookup"><span data-stu-id="ba8cf-189">Placing configurations and resources</span></span>

<span data-ttu-id="ba8cf-190">Una vez completada la configuración del servidor de incorporación de cambios, los módulos y las configuraciones que estarán disponibles para la incorporación de cambios de los nodos de destino se colocarán en las carpetas que definan las propiedades **ConfigurationPath** y **ModulePath** de la configuración del servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-190">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="ba8cf-191">Estos archivos deben estar en un formato concreto para que el servidor de incorporación de cambios los procese correctamente.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-191">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="ba8cf-192">Formato del paquete de módulo de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="ba8cf-192">DSC resource module package format</span></span>

<span data-ttu-id="ba8cf-193">Cada módulo de recursos se debe comprimir y se le debe asignar un nombre de acuerdo con el patrón `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-193">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="ba8cf-194">Por ejemplo, un módulo denominado xWebAdminstration con una versión de módulo de 3.1.2.0 se denominaría `xWebAdministration_3.1.2.0.zip`.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-194">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named `xWebAdministration_3.1.2.0.zip`.</span></span>
<span data-ttu-id="ba8cf-195">Cada versión de un módulo debe incluirse en un solo archivo ZIP.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-195">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="ba8cf-196">Dado que solo hay una versión de un recurso en cada archivo ZIP, no se admite el formato de módulo que se agrega en WMF 5.0 con compatibilidad con varias versiones de módulo en un único directorio.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-196">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="ba8cf-197">Esto significa que antes de empaquetar los módulos de recursos de DSC para su uso con el servidor de incorporación de cambios, deberá realizar un pequeño cambio en la estructura de directorios.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-197">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="ba8cf-198">El formato predeterminado de los módulos que contienen recursos de DSC en WMF 5.0 es `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-198">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="ba8cf-199">Antes de empaquetar para el servidor de extracción, quite la carpeta **{Versión del módulo}** para que la ruta se quede en `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-199">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="ba8cf-200">Con este cambio, comprima la carpeta según lo descrito anteriormente y coloque estos archivos ZIP en la carpeta **ModulePath**.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-200">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="ba8cf-201">Use `New-DscChecksum {module zip file}` para crear un archivo de suma de comprobación para el módulo que acaba de agregar.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-201">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="ba8cf-202">Formato de archivo MOF de configuración</span><span class="sxs-lookup"><span data-stu-id="ba8cf-202">Configuration MOF format</span></span>

<span data-ttu-id="ba8cf-203">Un archivo de configuración MOF debe emparejarse con un archivo de suma de comprobación para que un LCM de un nodo de destino pueda validar la configuración.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-203">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="ba8cf-204">Para crear una suma de comprobación, llame al cmdlet [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum).</span><span class="sxs-lookup"><span data-stu-id="ba8cf-204">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="ba8cf-205">El cmdlet toma un parámetro **Path** que especifica la carpeta donde se encuentra el MOF de configuración.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-205">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="ba8cf-206">El cmdlet crea un archivo de suma de comprobación denominado `ConfigurationMOFName.mof.checksum`, donde `ConfigurationMOFName` es el nombre del archivo mof de configuración.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-206">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="ba8cf-207">Si hay más de un archivo MOF de configuración en la carpeta especificada, se crea una suma de comprobación para cada una de las configuraciones de la carpeta.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-207">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="ba8cf-208">Coloque los archivos MOF y sus archivos asociados de suma de comprobación en la carpeta **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-208">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="ba8cf-209">Si cambia el archivo MOF de configuración de cualquier manera, también deberá volver a crear el archivo de suma de comprobación.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-209">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="ba8cf-210">Herramientas</span><span class="sxs-lookup"><span data-stu-id="ba8cf-210">Tooling</span></span>

<span data-ttu-id="ba8cf-211">Con el fin de facilitar la configuración, la validación y la administración del servidor de incorporación de cambios, se incluyen las siguientes herramientas como ejemplos en la versión más reciente del módulo xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="ba8cf-211">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="ba8cf-212">Un módulo que le ayudará a empaquetar los archivos de configuración y los módulos de recursos de DSC para su uso en el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-212">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="ba8cf-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="ba8cf-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span>
   <span data-ttu-id="ba8cf-214">Vea los ejemplos siguientes:</span><span class="sxs-lookup"><span data-stu-id="ba8cf-214">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="ba8cf-215">Un script que valida que el servidor de incorporación de cambios se configura correctamente.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-215">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="ba8cf-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="ba8cf-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="ba8cf-217">Soluciones comunitarias para el servicio de extracción</span><span class="sxs-lookup"><span data-stu-id="ba8cf-217">Community Solutions for Pull Service</span></span>

<span data-ttu-id="ba8cf-218">La comunidad de DSC ha creado varias soluciones para implementar el protocolo del servicio de extracción.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-218">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="ba8cf-219">En entornos locales, estas ofrecen funcionalidades de servicios de extracción y una oportunidad para contribuir con la comunidad con mejoras.</span><span class="sxs-lookup"><span data-stu-id="ba8cf-219">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="ba8cf-220">Tug</span><span class="sxs-lookup"><span data-stu-id="ba8cf-220">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="ba8cf-221">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="ba8cf-221">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="ba8cf-222">Configuración del cliente de incorporación de cambios</span><span class="sxs-lookup"><span data-stu-id="ba8cf-222">Pull client configuration</span></span>

<span data-ttu-id="ba8cf-223">En los temas siguientes se describe en detalle cómo configurar los clientes de extracción:</span><span class="sxs-lookup"><span data-stu-id="ba8cf-223">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="ba8cf-224">Configuración de un cliente de extracción de DSC mediante un ID de configuración</span><span class="sxs-lookup"><span data-stu-id="ba8cf-224">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="ba8cf-225">Configuración de un cliente de extracción de DSC mediante nombres de configuración</span><span class="sxs-lookup"><span data-stu-id="ba8cf-225">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="ba8cf-226">Configuraciones parciales</span><span class="sxs-lookup"><span data-stu-id="ba8cf-226">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="ba8cf-227">Vea también</span><span class="sxs-lookup"><span data-stu-id="ba8cf-227">See also</span></span>

- [<span data-ttu-id="ba8cf-228">Información general sobre la configuración de estado deseado de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba8cf-228">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="ba8cf-229">Establecer configuraciones</span><span class="sxs-lookup"><span data-stu-id="ba8cf-229">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="ba8cf-230">Uso de un servidor de informes de DSC</span><span class="sxs-lookup"><span data-stu-id="ba8cf-230">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="ba8cf-231">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx) (Protocolo del modelo de extracción de configuración de estado deseado)</span><span class="sxs-lookup"><span data-stu-id="ba8cf-231">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="ba8cf-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx) (Error del protocolo del modelo de extracción de Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="ba8cf-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>
