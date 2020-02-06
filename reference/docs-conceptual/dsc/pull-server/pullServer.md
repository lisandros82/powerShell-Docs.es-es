---
ms.date: 01/08/2020
keywords: dsc,powershell,configuration,setup
title: Servicio de extracción de DSC
ms.openlocfilehash: f171c3dc579dfb24a8c9fb87fbb50dccae619091
ms.sourcegitcommit: aaf1284dfec2e4c698009d6dc27ff103aaafd581
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76885394"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="20a5b-103">Servicio de extracción de Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="20a5b-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20a5b-104">El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="20a5b-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="20a5b-105">Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="20a5b-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="20a5b-106">El Administrador de configuración local (LCM) puede administrarse de forma central con una solución de servicio de extracción.</span><span class="sxs-lookup"><span data-stu-id="20a5b-106">Local Configuration Manager (LCM) can be centrally managed by a Pull Service solution.</span></span> <span data-ttu-id="20a5b-107">Cuando se usa este enfoque, el nodo que se está administrando se registra en un servicio y se le asigna una configuración en las opciones del LCM.</span><span class="sxs-lookup"><span data-stu-id="20a5b-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span> <span data-ttu-id="20a5b-108">La configuración y todos los recursos de DSC necesarios como dependencias para la configuración se descargan en la máquina y el LCM las usa para administrar la configuración.</span><span class="sxs-lookup"><span data-stu-id="20a5b-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span> <span data-ttu-id="20a5b-109">La información sobre el estado de la máquina que se está administrando se carga al servicio para crear un informe.</span><span class="sxs-lookup"><span data-stu-id="20a5b-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span> <span data-ttu-id="20a5b-110">Este concepto se conoce como "servicio de extracción".</span><span class="sxs-lookup"><span data-stu-id="20a5b-110">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="20a5b-111">Las opciones actuales del servicio de extracción incluyen:</span><span class="sxs-lookup"><span data-stu-id="20a5b-111">The current options for pull service include:</span></span>

- <span data-ttu-id="20a5b-112">Servicio Desired State Configuration de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="20a5b-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="20a5b-113">Un servicio de extracción que se ejecuta en Windows Server</span><span class="sxs-lookup"><span data-stu-id="20a5b-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="20a5b-114">Soluciones de código abierto mantenidas por la comunidad</span><span class="sxs-lookup"><span data-stu-id="20a5b-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="20a5b-115">Un recurso compartido SMB</span><span class="sxs-lookup"><span data-stu-id="20a5b-115">An SMB share</span></span>

<span data-ttu-id="20a5b-116">La escala recomendada para cada solución es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="20a5b-116">The recommended scale for each solution is as follows:</span></span>

|                   <span data-ttu-id="20a5b-117">Solución</span><span class="sxs-lookup"><span data-stu-id="20a5b-117">Solution</span></span>                   |              <span data-ttu-id="20a5b-118">Nodos de cliente</span><span class="sxs-lookup"><span data-stu-id="20a5b-118">Client nodes</span></span>              |
| -------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="20a5b-119">Servidor de extracción de Windows mediante la base de datos MDB/ESENT</span><span class="sxs-lookup"><span data-stu-id="20a5b-119">Windows Pull Server using MDB/ESENT database</span></span> | <span data-ttu-id="20a5b-120">Hasta 500 nodos</span><span class="sxs-lookup"><span data-stu-id="20a5b-120">Up to 500 nodes</span></span>                        |
| <span data-ttu-id="20a5b-121">Servidor de extracción de Windows mediante la base de datos SQL</span><span class="sxs-lookup"><span data-stu-id="20a5b-121">Windows Pull Server using SQL database</span></span>       | <span data-ttu-id="20a5b-122">Hasta 1000 nodos</span><span class="sxs-lookup"><span data-stu-id="20a5b-122">Up to 1000 nodes</span></span>                       |
| <span data-ttu-id="20a5b-123">DSC de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="20a5b-123">Azure Automation DSC</span></span>                         | <span data-ttu-id="20a5b-124">Escenarios con más de 1000 nodos</span><span class="sxs-lookup"><span data-stu-id="20a5b-124">Scenarios with greater than 1000 nodes</span></span> |

<span data-ttu-id="20a5b-125">**La solución recomendada**, y la opción que tiene la mayor cantidad de características disponibles, es [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="20a5b-125">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="20a5b-126">El servicio de Azure puede administrar nodos locales en centros de datos privados, o bien en nubes públicas como Azure y AWS.</span><span class="sxs-lookup"><span data-stu-id="20a5b-126">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span> <span data-ttu-id="20a5b-127">En el caso de entornos privados donde los servidores no se pueden conectar directamente a Internet, considere limitar el tráfico de salida solo al intervalo IP de Azure (consulte los [intervalos IP del centro de datos de Azure](https://www.microsoft.com/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="20a5b-127">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="20a5b-128">Las características del servicio en línea que no están disponibles actualmente en el servicio de extracción de Windows Server incluyen las siguientes:</span><span class="sxs-lookup"><span data-stu-id="20a5b-128">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="20a5b-129">Se cifran todos los datos, ya sea que estén en tránsito o en reposo</span><span class="sxs-lookup"><span data-stu-id="20a5b-129">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="20a5b-130">Los certificados de cliente se crean y administran de manera automática</span><span class="sxs-lookup"><span data-stu-id="20a5b-130">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="20a5b-131">Almacén de secretos para administrar de manera centralizada las [contraseñas/credenciales](/azure/automation/automation-credentials) o las [variables](/azure/automation/automation-variables), como nombres de servidor o cadenas de conexión</span><span class="sxs-lookup"><span data-stu-id="20a5b-131">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="20a5b-132">Administración centralizada de la [configuración de LCM](../managing-nodes/metaConfig.md#basic-settings) del nodo</span><span class="sxs-lookup"><span data-stu-id="20a5b-132">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="20a5b-133">Asignación centralizada de las configuraciones a los nodos cliente</span><span class="sxs-lookup"><span data-stu-id="20a5b-133">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="20a5b-134">Publicación de los cambios de configuración en "grupos de valor controlado" para pruebas antes de llegar a producción</span><span class="sxs-lookup"><span data-stu-id="20a5b-134">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="20a5b-135">Informes gráficos</span><span class="sxs-lookup"><span data-stu-id="20a5b-135">Graphical reporting</span></span>
  - <span data-ttu-id="20a5b-136">Detalle de estado en el nivel de recurso DSC de granularidad</span><span class="sxs-lookup"><span data-stu-id="20a5b-136">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="20a5b-137">Mensajes detallados de error de equipos cliente para la solución de problemas</span><span class="sxs-lookup"><span data-stu-id="20a5b-137">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="20a5b-138">[Integración de Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) para alertas, tareas automatizadas, aplicación Android/iOS para informes y alertas</span><span class="sxs-lookup"><span data-stu-id="20a5b-138">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="20a5b-139">Servicio de extracción de DSC en Windows Server</span><span class="sxs-lookup"><span data-stu-id="20a5b-139">DSC pull service in Windows Server</span></span>

<span data-ttu-id="20a5b-140">Es posible configurar un servicio de extracción para que se ejecute en Windows Server.</span><span class="sxs-lookup"><span data-stu-id="20a5b-140">It is possible to configure a pull service to run on Windows Server.</span></span> <span data-ttu-id="20a5b-141">Tenga en cuenta que la solución de servicio de extracción incluida en Windows Server solo tiene funcionalidades de almacenamiento de configuraciones y módulos para descargar y capturar datos de informes en una base de datos.</span><span class="sxs-lookup"><span data-stu-id="20a5b-141">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data into a database.</span></span> <span data-ttu-id="20a5b-142">No se incluyen muchas de las funcionalidades que ofrece el servicio en Azure y, por lo tanto, no es una herramienta lo suficientemente eficaz como para evaluar el uso del servicio.</span><span class="sxs-lookup"><span data-stu-id="20a5b-142">It does not include many of the capabilities offered by the service in Azure and so, is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="20a5b-143">El servicio de extracción que se ofrece en Windows Server es un servicio web en IIS que usa una interfaz de OData para poner a disposición de los nodos de destino los archivos de configuración DSC cuando esos nodos los soliciten.</span><span class="sxs-lookup"><span data-stu-id="20a5b-143">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="20a5b-144">Requisitos para usar un servidor de extracción:</span><span class="sxs-lookup"><span data-stu-id="20a5b-144">Requirements for using a pull server:</span></span>

- <span data-ttu-id="20a5b-145">Un servidor que ejecute:</span><span class="sxs-lookup"><span data-stu-id="20a5b-145">A server running:</span></span>
  - <span data-ttu-id="20a5b-146">WMF/PowerShell 4.0 o una versión superior</span><span class="sxs-lookup"><span data-stu-id="20a5b-146">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="20a5b-147">Rol del servidor IIS</span><span class="sxs-lookup"><span data-stu-id="20a5b-147">IIS server role</span></span>
  - <span data-ttu-id="20a5b-148">Servicio DSC</span><span class="sxs-lookup"><span data-stu-id="20a5b-148">DSC Service</span></span>
- <span data-ttu-id="20a5b-149">Idealmente, algún medio para generar un certificado, para proteger las credenciales que se pasan al administrador de configuración local (LCM) en los nodos de destino</span><span class="sxs-lookup"><span data-stu-id="20a5b-149">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="20a5b-150">La mejor manera para configurar Windows Server para hospedar un servicio de extracción es usar una configuración de DSC.</span><span class="sxs-lookup"><span data-stu-id="20a5b-150">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span> <span data-ttu-id="20a5b-151">A continuación se muestra un script de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="20a5b-151">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="20a5b-152">Sistemas de base de datos admitidos</span><span class="sxs-lookup"><span data-stu-id="20a5b-152">Supported database systems</span></span>

| <span data-ttu-id="20a5b-153">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="20a5b-153">WMF 4.0</span></span> |       <span data-ttu-id="20a5b-154">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="20a5b-154">WMF 5.0</span></span>        |       <span data-ttu-id="20a5b-155">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="20a5b-155">WMF 5.1</span></span>        | <span data-ttu-id="20a5b-156">WMF 5.1 (Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="20a5b-156">WMF 5.1 (Windows Server Insider Preview 17090)</span></span> |
| ------- | -------------------- | -------------------- | ---------------------------------------------- |
| <span data-ttu-id="20a5b-157">MDB</span><span class="sxs-lookup"><span data-stu-id="20a5b-157">MDB</span></span>     | <span data-ttu-id="20a5b-158">ESENT (predeterminado), MDB</span><span class="sxs-lookup"><span data-stu-id="20a5b-158">ESENT (Default), MDB</span></span> | <span data-ttu-id="20a5b-159">ESENT (predeterminado), MDB</span><span class="sxs-lookup"><span data-stu-id="20a5b-159">ESENT (Default), MDB</span></span> | <span data-ttu-id="20a5b-160">ESENT (predeterminado), SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="20a5b-160">ESENT (Default), SQL Server, MDB</span></span>               |

<span data-ttu-id="20a5b-161">A partir de la versión 17090 de [Windows Server Insider Preview](https://www.microsoft.com/software-download/windowsinsiderpreviewserver), SQL Server es una opción admitida en el servicio de extracción (característica de Windows *DSC-Service*).</span><span class="sxs-lookup"><span data-stu-id="20a5b-161">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="20a5b-162">Esto constituye una nueva opción para ajustar la escala de entornos de DSC de gran envergadura que no se han migrado a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="20a5b-162">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> [!NOTE]
> <span data-ttu-id="20a5b-163">La compatibilidad con SQL Server no se incluirá en WMF 5.1 ni en versiones anteriores, y solo estará disponible en versiones de Windows Server posteriores a la 17090.</span><span class="sxs-lookup"><span data-stu-id="20a5b-163">SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="20a5b-164">Para configurar el servidor de extracción de forma que use SQL Server, establezca **SqlProvider** en `$true` y **SqlConnectionString** en una cadena de conexión de SQL Server válida.</span><span class="sxs-lookup"><span data-stu-id="20a5b-164">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="20a5b-165">Para más información, vea [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings) (Cadenas de conexión de SqlClient).</span><span class="sxs-lookup"><span data-stu-id="20a5b-165">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="20a5b-166">Para ver un ejemplo de configuración de SQL Server con **xDscWebService**, lea primero [Uso del recurso xDSCWebService](#using-the-xdscwebservice-resource) y, después, revise [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 en GitHub](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="20a5b-166">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="20a5b-167">Uso del recurso xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="20a5b-167">Using the xDscWebService resource</span></span>

<span data-ttu-id="20a5b-168">La manera más fácil de configurar un servidor de extracción web es usando el recurso **xDscWebService**, incluido en el módulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="20a5b-168">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="20a5b-169">En los siguientes pasos se explica cómo usar el recurso en `Configuration` que configure el servicio web.</span><span class="sxs-lookup"><span data-stu-id="20a5b-169">The following steps explain how to use the resource in a `Configuration` that sets up the web service.</span></span>

1. <span data-ttu-id="20a5b-170">Llame al cmdlet [Install-Module](/reference/6/PowerShellGet/Install-Module.md) para instalar el módulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="20a5b-170">Call the [Install-Module](/reference/6/PowerShellGet/Install-Module.md) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>

   > [!NOTE]
   > <span data-ttu-id="20a5b-171">`Install-Module` está incluido en el módulo **PowerShellGet**, que se incluye en PowerShell 5.0 y superior.</span><span class="sxs-lookup"><span data-stu-id="20a5b-171">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0 and higher.</span></span>

1. <span data-ttu-id="20a5b-172">Obtenga un certificado SSL para el servidor de extracción de DSC de una entidad de certificación de confianza, ya sea dentro de su organización o de una entidad pública.</span><span class="sxs-lookup"><span data-stu-id="20a5b-172">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="20a5b-173">El certificado recibido de la entidad suele tener el formato PFX.</span><span class="sxs-lookup"><span data-stu-id="20a5b-173">The certificate received from the authority is usually in the PFX format.</span></span>
1. <span data-ttu-id="20a5b-174">Instale el certificado en el nodo que se convertirá en el servidor de extracción de DSC en la ubicación predeterminada que debe ser `CERT:\LocalMachine\My`.</span><span class="sxs-lookup"><span data-stu-id="20a5b-174">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="20a5b-175">Anote la huella digital del certificado.</span><span class="sxs-lookup"><span data-stu-id="20a5b-175">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="20a5b-176">Seleccione un GUID para usarlo como clave de registro.</span><span class="sxs-lookup"><span data-stu-id="20a5b-176">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="20a5b-177">Para generar uno con PowerShell, escriba lo siguiente en el aviso de PS y pulse la tecla ENTRAR: `[guid]::newGuid()` o `New-Guid`.</span><span class="sxs-lookup"><span data-stu-id="20a5b-177">To generate one using PowerShell enter the following at the PS prompt and press enter: `[guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="20a5b-178">Esta clave la utilizarán los nodos de cliente como una clave compartida para la autenticación durante el registro.</span><span class="sxs-lookup"><span data-stu-id="20a5b-178">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="20a5b-179">Para más información, vea la sección Clave de registro más adelante.</span><span class="sxs-lookup"><span data-stu-id="20a5b-179">For more information, see the Registration Key section below.</span></span>
1. <span data-ttu-id="20a5b-180">En PowerShell ISE, inicie (<kbd>F5</kbd>) el siguiente script de configuración (incluido en la carpeta del módulo **xPSDesiredStateConfiguration** como `Sample_xDscWebServiceRegistration.ps1`).</span><span class="sxs-lookup"><span data-stu-id="20a5b-180">In the PowerShell ISE, start (<kbd>F5</kbd>) the following configuration script (included in the folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`) .</span></span> <span data-ttu-id="20a5b-181">Este script configura el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="20a5b-181">This script sets up the pull server.</span></span>

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

1. <span data-ttu-id="20a5b-182">Ejecute la configuración pasando la huella digital del certificado SSL como el parámetro **certificateThumbPrint** y una clave de registro GUID como el parámetro **RegistrationKey**:</span><span class="sxs-lookup"><span data-stu-id="20a5b-182">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="20a5b-183">Clave de registro</span><span class="sxs-lookup"><span data-stu-id="20a5b-183">Registration Key</span></span>

<span data-ttu-id="20a5b-184">Para permitir que los nodos de cliente se registren con el servidor de forma que puedan usar nombres de configuración en lugar de un identificador de configuración, se guarda una clave de registro creada por medio de la configuración anterior en un archivo denominado `RegistrationKeys.txt` en `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="20a5b-184">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="20a5b-185">La clave de registro funciona como un secreto compartido que se usa durante el registro inicial del cliente con el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="20a5b-185">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="20a5b-186">El cliente generará un certificado autofirmado que se usa para autenticar el servidor de incorporación de cambios inequívocamente una vez que el registro se complete correctamente.</span><span class="sxs-lookup"><span data-stu-id="20a5b-186">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="20a5b-187">La huella digital del certificado se almacena localmente y se asocia con la dirección URL del servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="20a5b-187">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="20a5b-188">No se admiten claves del registro en PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="20a5b-188">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="20a5b-189">Para configurar un nodo para que se autentique con el servidor de extracción, la clave de registro debe estar en la metaconfiguration de cualquier nodo de destino que se registre con este servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="20a5b-189">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="20a5b-190">Tenga en cuenta que el elemento **RegistrationKey** de la siguiente metaconfiguración se quita una vez que el equipo de destino se ha registrado correctamente y que el valor debe coincidir con el valor almacenado en el archivo `RegistrationKeys.txt` en el servidor de extracción ("140a952b-b9d6-406b-b416-e0f759c9c0e4" para este ejemplo).</span><span class="sxs-lookup"><span data-stu-id="20a5b-190">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="20a5b-191">Trate siempre el valor de clave de registro de forma segura, porque conocer esta clave conlleva que cualquier máquina de destino se registre al servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="20a5b-191">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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
> <span data-ttu-id="20a5b-192">La sección **ReportServerWeb** permite informar de datos que deben enviarse al servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="20a5b-192">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="20a5b-193">Si falta la propiedad **ConfigurationID** en el archivo de metaconfiguration, significa implícitamente que el servidor de incorporación de cambios es compatible con la versión V2 del protocolo del servidor de incorporación de cambios, lo que requiere un registro inicial.</span><span class="sxs-lookup"><span data-stu-id="20a5b-193">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="20a5b-194">Por el contrario, si hay una propiedad **ConfigurationID**, significa que se usa la versión V1 del protocolo del servidor de incorporación de cambios y que no hay ningún procesamiento de registro.</span><span class="sxs-lookup"><span data-stu-id="20a5b-194">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="20a5b-195">En un escenario de inserción, hay un error en la versión actual que hace que sea necesario definir una propiedad ConfigurationID en el archivo de metaconfiguration para los nodos que nunca se hayan registrado en un servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="20a5b-195">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="20a5b-196">De esta manera, se forzará el protocolo del servidor de incorporación de cambios V1 y se evitarán los mensajes de error de registro.</span><span class="sxs-lookup"><span data-stu-id="20a5b-196">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="20a5b-197">Colocación de configuraciones y recursos</span><span class="sxs-lookup"><span data-stu-id="20a5b-197">Placing configurations and resources</span></span>

<span data-ttu-id="20a5b-198">Una vez completada la configuración del servidor de incorporación de cambios, los módulos y las configuraciones que estarán disponibles para la incorporación de cambios de los nodos de destino se colocarán en las carpetas que definan las propiedades **ConfigurationPath** y **ModulePath** de la configuración del servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="20a5b-198">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="20a5b-199">Estos archivos deben estar en un formato concreto para que el servidor de incorporación de cambios los procese correctamente.</span><span class="sxs-lookup"><span data-stu-id="20a5b-199">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="20a5b-200">Formato del paquete de módulo de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="20a5b-200">DSC resource module package format</span></span>

<span data-ttu-id="20a5b-201">Cada módulo de recursos se debe comprimir y se le debe asignar un nombre de acuerdo con el patrón `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="20a5b-201">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="20a5b-202">Por ejemplo, un módulo denominado **xWebAdminstration** con una versión de módulo de 3.1.2.0 se denominaría `xWebAdministration_3.1.2.0.zip`.</span><span class="sxs-lookup"><span data-stu-id="20a5b-202">For example, a module named **xWebAdminstration** with a module version of 3.1.2.0 would be named `xWebAdministration_3.1.2.0.zip`.</span></span> <span data-ttu-id="20a5b-203">Cada versión de un módulo debe incluirse en un solo archivo ZIP.</span><span class="sxs-lookup"><span data-stu-id="20a5b-203">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="20a5b-204">Dado que solo hay una versión de un recurso en cada archivo ZIP, no se admite el formato de módulo que se agrega en WMF 5.0 con compatibilidad con varias versiones de módulo en un único directorio.</span><span class="sxs-lookup"><span data-stu-id="20a5b-204">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="20a5b-205">Esto significa que antes de empaquetar los módulos de recursos de DSC para su uso con el servidor de incorporación de cambios, deberá realizar un pequeño cambio en la estructura de directorios.</span><span class="sxs-lookup"><span data-stu-id="20a5b-205">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="20a5b-206">El formato predeterminado de los módulos que contienen recursos de DSC en WMF 5.0 es `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="20a5b-206">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="20a5b-207">Antes de empaquetar para el servidor de extracción, quite la carpeta **{Versión del módulo}** para que la ruta se quede en `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="20a5b-207">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="20a5b-208">Con este cambio, comprima la carpeta según lo descrito anteriormente y coloque estos archivos ZIP en la carpeta **ModulePath**.</span><span class="sxs-lookup"><span data-stu-id="20a5b-208">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="20a5b-209">Use `New-DscChecksum {module zip file}` para crear un archivo de suma de comprobación para el módulo que acaba de agregar.</span><span class="sxs-lookup"><span data-stu-id="20a5b-209">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="20a5b-210">Formato de archivo MOF de configuración</span><span class="sxs-lookup"><span data-stu-id="20a5b-210">Configuration MOF format</span></span>

<span data-ttu-id="20a5b-211">Un archivo de configuración MOF debe emparejarse con un archivo de suma de comprobación para que un LCM de un nodo de destino pueda validar la configuración.</span><span class="sxs-lookup"><span data-stu-id="20a5b-211">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="20a5b-212">Para crear una suma de comprobación, llame al cmdlet [New-DscChecksum](/reference/6/PSDesiredStateConfiguration/New-DSCCheckSum.md).</span><span class="sxs-lookup"><span data-stu-id="20a5b-212">To create a checksum, call the [New-DscChecksum](/reference/6/PSDesiredStateConfiguration/New-DSCCheckSum.md) cmdlet.</span></span> <span data-ttu-id="20a5b-213">El cmdlet toma un parámetro **Path** que especifica la carpeta donde se encuentra el MOF de configuración.</span><span class="sxs-lookup"><span data-stu-id="20a5b-213">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="20a5b-214">El cmdlet crea un archivo de suma de comprobación denominado `ConfigurationMOFName.mof.checksum`, donde `ConfigurationMOFName` es el nombre del archivo mof de configuración.</span><span class="sxs-lookup"><span data-stu-id="20a5b-214">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="20a5b-215">Si hay más de un archivo MOF de configuración en la carpeta especificada, se crea una suma de comprobación para cada una de las configuraciones de la carpeta.</span><span class="sxs-lookup"><span data-stu-id="20a5b-215">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="20a5b-216">Coloque los archivos MOF y sus archivos asociados de suma de comprobación en la carpeta **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="20a5b-216">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="20a5b-217">Si cambia el archivo MOF de configuración de cualquier manera, también deberá volver a crear el archivo de suma de comprobación.</span><span class="sxs-lookup"><span data-stu-id="20a5b-217">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="20a5b-218">Tooling</span><span class="sxs-lookup"><span data-stu-id="20a5b-218">Tooling</span></span>

<span data-ttu-id="20a5b-219">Con el fin de facilitar la configuración, la validación y la administración del servidor de incorporación de cambios, se incluyen las siguientes herramientas como ejemplos en la versión más reciente del módulo xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="20a5b-219">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="20a5b-220">Un módulo que le ayudará a empaquetar los archivos de configuración y los módulos de recursos de DSC para su uso en el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="20a5b-220">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="20a5b-221">[PublishModulesAndMofsToPullServer.psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).</span><span class="sxs-lookup"><span data-stu-id="20a5b-221">[PublishModulesAndMofsToPullServer.psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).</span></span>
   <span data-ttu-id="20a5b-222">Vea los ejemplos siguientes:</span><span class="sxs-lookup"><span data-stu-id="20a5b-222">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="20a5b-223">Un script que valida que el servidor de incorporación de cambios se configura correctamente.</span><span class="sxs-lookup"><span data-stu-id="20a5b-223">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="20a5b-224">[PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).</span><span class="sxs-lookup"><span data-stu-id="20a5b-224">[PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="20a5b-225">Soluciones comunitarias para el servicio de extracción</span><span class="sxs-lookup"><span data-stu-id="20a5b-225">Community Solutions for Pull Service</span></span>

<span data-ttu-id="20a5b-226">La comunidad de DSC ha creado varias soluciones para implementar el protocolo del servicio de extracción.</span><span class="sxs-lookup"><span data-stu-id="20a5b-226">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span> <span data-ttu-id="20a5b-227">En entornos locales, estas ofrecen funcionalidades de servicios de extracción y una oportunidad para contribuir con la comunidad con mejoras.</span><span class="sxs-lookup"><span data-stu-id="20a5b-227">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="20a5b-228">Tug</span><span class="sxs-lookup"><span data-stu-id="20a5b-228">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="20a5b-229">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="20a5b-229">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="20a5b-230">Configuración del cliente de incorporación de cambios</span><span class="sxs-lookup"><span data-stu-id="20a5b-230">Pull client configuration</span></span>

<span data-ttu-id="20a5b-231">En los temas siguientes se describe en detalle cómo configurar los clientes de extracción:</span><span class="sxs-lookup"><span data-stu-id="20a5b-231">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="20a5b-232">Configuración de un cliente de extracción de DSC mediante un ID de configuración</span><span class="sxs-lookup"><span data-stu-id="20a5b-232">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="20a5b-233">Configuración de un cliente de extracción de DSC mediante nombres de configuración</span><span class="sxs-lookup"><span data-stu-id="20a5b-233">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="20a5b-234">Configuraciones parciales</span><span class="sxs-lookup"><span data-stu-id="20a5b-234">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="20a5b-235">Consulte también</span><span class="sxs-lookup"><span data-stu-id="20a5b-235">See also</span></span>

- [<span data-ttu-id="20a5b-236">Información general sobre la configuración de estado deseado de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="20a5b-236">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="20a5b-237">Establecer configuraciones</span><span class="sxs-lookup"><span data-stu-id="20a5b-237">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="20a5b-238">Uso de un servidor de informes de DSC</span><span class="sxs-lookup"><span data-stu-id="20a5b-238">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="20a5b-239">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9) (Protocolo del modelo de extracción de configuración de estado deseado)</span><span class="sxs-lookup"><span data-stu-id="20a5b-239">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)</span></span>
- <span data-ttu-id="20a5b-240">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5) (Error del protocolo del modelo de extracción de Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="20a5b-240">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)</span></span>
