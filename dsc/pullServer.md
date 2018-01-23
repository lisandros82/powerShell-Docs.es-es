---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Configuración de un servidor de extracción web de DSC"
ms.openlocfilehash: 9a09804ef0efe3e4c92923910884710187d44ac5
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-dsc-web-pull-server"></a><span data-ttu-id="bc56b-103">Configuración de un servidor de extracción web de DSC</span><span class="sxs-lookup"><span data-stu-id="bc56b-103">Setting up a DSC web pull server</span></span>

> <span data-ttu-id="bc56b-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bc56b-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="bc56b-105">Un servidor de extracción web de DSC es un servicio web en IIS que usa una interfaz de OData para poner a disposición de los nodos de destino los archivos de configuración DSC cuando esos nodos los soliciten.</span><span class="sxs-lookup"><span data-stu-id="bc56b-105">A DSC web pull server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="bc56b-106">Requisitos para usar un servidor de extracción:</span><span class="sxs-lookup"><span data-stu-id="bc56b-106">Requirements for using a pull server:</span></span>

* <span data-ttu-id="bc56b-107">Un servidor que ejecute:</span><span class="sxs-lookup"><span data-stu-id="bc56b-107">A server running:</span></span>
  - <span data-ttu-id="bc56b-108">WMF/PowerShell 5.0 o una versión posterior</span><span class="sxs-lookup"><span data-stu-id="bc56b-108">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="bc56b-109">Rol del servidor IIS</span><span class="sxs-lookup"><span data-stu-id="bc56b-109">IIS server role</span></span>
  - <span data-ttu-id="bc56b-110">Servicio DSC</span><span class="sxs-lookup"><span data-stu-id="bc56b-110">DSC Service</span></span>
* <span data-ttu-id="bc56b-111">Idealmente, algún medio para generar un certificado, para proteger las credenciales que se pasan al administrador de configuración local (LCM) en los nodos de destino</span><span class="sxs-lookup"><span data-stu-id="bc56b-111">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="bc56b-112">Puede agregar el rol del servidor IIS y el servicio DSC con el asistente para agregar roles y características en el administrador del servidor o mediante el uso de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc56b-112">You can add the IIS server role and DSC Service with the Add Roles and Features wizard in Server Manager, or by using PowerShell.</span></span> <span data-ttu-id="bc56b-113">Los scripts de ejemplo incluidos en este tema también controlarán estos dos pasos por usted.</span><span class="sxs-lookup"><span data-stu-id="bc56b-113">The sample scripts included in this topic will handle both of these steps for you as well.</span></span>

## <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="bc56b-114">Uso del recurso xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="bc56b-114">Using the xDSCWebService resource</span></span>
<span data-ttu-id="bc56b-115">La manera más fácil de configurar un servidor de extracción web es usar el recurso xWebService, incluido en el módulo xPSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="bc56b-115">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span> <span data-ttu-id="bc56b-116">En los siguientes pasos se explica cómo usar el recurso en una configuración que configure el servicio web.</span><span class="sxs-lookup"><span data-stu-id="bc56b-116">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="bc56b-117">Llame al cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) para instalar el módulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="bc56b-117">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="bc56b-118">**Nota**: **Install-Module** está incluido en el módulo **PowerShellGet**, que se incluye en PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="bc56b-118">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="bc56b-119">Puede descargar el módulo **PowerShellGet** para PowerShell 3.0 y 4.0 en [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186) (Vista previa de los módulos de PowerShell PackageManagement).</span><span class="sxs-lookup"><span data-stu-id="bc56b-119">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="bc56b-120">Obtenga un certificado SSL para el servidor de extracción de DSC de una entidad de certificación de confianza, ya sea dentro de su organización o de una entidad pública.</span><span class="sxs-lookup"><span data-stu-id="bc56b-120">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="bc56b-121">El certificado recibido de la entidad suele tener el formato PFX.</span><span class="sxs-lookup"><span data-stu-id="bc56b-121">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="bc56b-122">Instale el certificado en el nodo que se convertirá en el servidor de incorporación de cambios de DSC en la ubicación predeterminada que debe ser CERT: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="bc56b-122">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="bc56b-123">Anote la huella digital del certificado.</span><span class="sxs-lookup"><span data-stu-id="bc56b-123">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="bc56b-124">Seleccione un GUID para usarlo como clave de registro.</span><span class="sxs-lookup"><span data-stu-id="bc56b-124">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="bc56b-125">Para generar uno con PowerShell, escriba lo siguiente en el aviso de PS y presione ENTRAR: '``` [guid]::newGuid()```' o '```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="bc56b-125">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="bc56b-126">Esta clave la utilizarán los nodos de cliente como una clave compartida para la autenticación durante el registro.</span><span class="sxs-lookup"><span data-stu-id="bc56b-126">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="bc56b-127">Para más información, consulte la sección Clave de registro más adelante.</span><span class="sxs-lookup"><span data-stu-id="bc56b-127">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="bc56b-128">En PowerShell ISE, inicie (F5) el siguiente script de configuración (incluido en la carpeta Example del módulo **xPSDesiredStateConfiguration** como Sample_xDscWebService.ps1).</span><span class="sxs-lookup"><span data-stu-id="bc56b-128">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="bc56b-129">Este script configura el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="bc56b-129">This script sets up the pull server.</span></span>
  
    ```powershell
    configuration Sample_xDscPullServer
    { 
        param  
        ( 
                [string[]]$NodeName = 'localhost', 

                [ValidateNotNullOrEmpty()] 
                [string] $certificateThumbPrint,

                [Parameter(Mandatory)]
                [ValidateNotNullOrEmpty()]
                [string] $RegistrationKey 
         ) 
         
         Import-DSCResource -ModuleName xPSDesiredStateConfiguration
         Import-DSCResource –ModuleName PSDesiredStateConfiguration

         Node $NodeName 
         { 
             WindowsFeature DSCServiceFeature 
             { 
                 Ensure = 'Present'
                 Name   = 'DSC-Service'             
             } 

             xDscWebService PSDSCPullServer 
             { 
                 Ensure                   = 'Present' 
                 EndpointName             = 'PSDSCPullServer' 
                 Port                     = 8080 
                 PhysicalPath             = "$env:SystemDrive\inetpub\PSDSCPullServer" 
                 CertificateThumbPrint    = $certificateThumbPrint          
                 ModulePath               = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
                 ConfigurationPath        = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration" 
                 State                    = 'Started'
                 DependsOn                = '[WindowsFeature]DSCServiceFeature'     
                 UseSecurityBestPractices = $false
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

1. <span data-ttu-id="bc56b-130">Ejecute la configuración pasando la huella digital del certificado SSL como el parámetro **certificateThumbPrint** y una clave de registro GUID como el parámetro **RegistrationKey**:</span><span class="sxs-lookup"><span data-stu-id="bc56b-130">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

## <a name="registration-key"></a><span data-ttu-id="bc56b-131">Clave de registro</span><span class="sxs-lookup"><span data-stu-id="bc56b-131">Registration Key</span></span>
<span data-ttu-id="bc56b-132">Para permitir que los nodos de cliente se registren con el servidor de forma que puedan usar nombres de configuración en lugar de un identificador de configuración, se guarda una clave de registro creada mediante la configuración anterior en un archivo denominado `RegistrationKeys.txt` en `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="bc56b-132">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="bc56b-133">La clave de registro funciona como un secreto compartido que se usa durante el registro inicial del cliente con el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="bc56b-133">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="bc56b-134">El cliente generará un certificado autofirmado que se utiliza para autenticar el servidor de incorporación de cambios inequívocamente una vez que el registro se complete correctamente.</span><span class="sxs-lookup"><span data-stu-id="bc56b-134">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="bc56b-135">La huella digital del certificado se almacena localmente y se asocia con la dirección URL del servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="bc56b-135">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="bc56b-136">**Nota**: No se admiten claves del registro en PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="bc56b-136">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="bc56b-137">Para configurar un nodo para que se autentique con el servidor de extracción, la clave de registro debe estar en la metaconfiguration de cualquier nodo de destino que se registre con este servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="bc56b-137">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="bc56b-138">Tenga en cuenta que el elemento **RegistrationKey** de la siguiente metaconfiguration se quita una vez que el equipo de destino se ha registrado correctamente, y que el valor '140a952b-b9d6-406b-b416-e0f759c9c0e4' debe coincidir con el valor almacenado en el archivo RegistrationKeys.txt del servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="bc56b-138">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="bc56b-139">Trate siempre el valor de clave de registro de forma segura, porque conocer esta clave conlleva que cualquier máquina de destino se registre al servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="bc56b-139">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }
        
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey    = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }   
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes
```
> <span data-ttu-id="bc56b-140">**Nota**: La sección **ReportServerWeb** permite informar de datos que deben enviarse al servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="bc56b-140">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span> 

<span data-ttu-id="bc56b-141">Si falta la propiedad **ConfigurationID** en el archivo de metaconfiguration, significa implícitamente que el servidor de incorporación de cambios es compatible con la versión V2 del protocolo del servidor de incorporación de cambios, lo que requiere un registro inicial.</span><span class="sxs-lookup"><span data-stu-id="bc56b-141">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="bc56b-142">Por el contrario, si hay una propiedad **ConfigurationID**, significa que se usa la versión V1 del protocolo del servidor de incorporación de cambios y que no hay ningún procesamiento de registro.</span><span class="sxs-lookup"><span data-stu-id="bc56b-142">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="bc56b-143">**Nota**: En un escenario de inserción, hay un error en la versión actual que hace que sea necesario definir una propiedad ConfigurationID en el archivo de metaconfiguration para los nodos que nunca se han registrado en un servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="bc56b-143">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="bc56b-144">De esta manera, se forzará el protocolo del servidor de incorporación de cambios V1 y se evitarán los mensajes de error de registro.</span><span class="sxs-lookup"><span data-stu-id="bc56b-144">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="bc56b-145">Colocación de configuraciones y recursos</span><span class="sxs-lookup"><span data-stu-id="bc56b-145">Placing configurations and resources</span></span>

<span data-ttu-id="bc56b-146">Una vez completada la configuración del servidor de incorporación de cambios, los módulos y las configuraciones que estarán disponibles para la incorporación de cambios de los nodos de destino se colocarán en las carpetas que definan las propiedades **ConfigurationPath** y **ModulePath** de la configuración del servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="bc56b-146">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="bc56b-147">Estos archivos deben estar en un formato concreto para que el servidor de incorporación de cambios los procese correctamente.</span><span class="sxs-lookup"><span data-stu-id="bc56b-147">These files need to be in a specific format in order for the pull server to correctly process them.</span></span> 

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="bc56b-148">Formato del paquete de módulo de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="bc56b-148">DSC resource module package format</span></span>

<span data-ttu-id="bc56b-149">Cada módulo de recursos se debe comprimir, y se le debe asignar un nombre de acuerdo con el siguiente patrón `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="bc56b-149">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="bc56b-150">Por ejemplo, un módulo denominado xWebAdminstration con una versión de módulo de 3.1.2.0 se denominaría 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="bc56b-150">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="bc56b-151">Cada versión de un módulo debe incluirse en un solo archivo ZIP.</span><span class="sxs-lookup"><span data-stu-id="bc56b-151">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="bc56b-152">Dado que solo hay una versión de un recurso en cada archivo ZIP, no se admite el formato de módulo que se agrega en WMF 5.0 con compatibilidad con varias versiones de módulo en un único directorio.</span><span class="sxs-lookup"><span data-stu-id="bc56b-152">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="bc56b-153">Esto significa que antes de empaquetar los módulos de recursos de DSC para su uso con el servidor de incorporación de cambios, deberá realizar un pequeño cambio en la estructura de directorios.</span><span class="sxs-lookup"><span data-stu-id="bc56b-153">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="bc56b-154">El formato predeterminado de los módulos que contienen recursos de DSC en WMF 5.0 es '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span><span class="sxs-lookup"><span data-stu-id="bc56b-154">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="bc56b-155">Antes de empaquetar el servidor de extracción, quite la carpeta **{Module version}** para que la ruta de acceso se convierta en '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span><span class="sxs-lookup"><span data-stu-id="bc56b-155">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="bc56b-156">Con este cambio, comprima la carpeta según lo descrito anteriormente y coloque estos archivos ZIP en la carpeta **ModulePath**.</span><span class="sxs-lookup"><span data-stu-id="bc56b-156">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="bc56b-157">Use `new-dscchecksum {module zip file}` para crear un archivo de suma de comprobación para el módulo que acaba de agregar.</span><span class="sxs-lookup"><span data-stu-id="bc56b-157">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="bc56b-158">Formato de archivo MOF de configuración</span><span class="sxs-lookup"><span data-stu-id="bc56b-158">Configuration MOF format</span></span> 
<span data-ttu-id="bc56b-159">Un archivo de configuración MOF debe emparejarse con un archivo de suma de comprobación para que un LCM de un nodo de destino pueda validar la configuración.</span><span class="sxs-lookup"><span data-stu-id="bc56b-159">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="bc56b-160">Para crear una suma de comprobación, llame al cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx).</span><span class="sxs-lookup"><span data-stu-id="bc56b-160">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="bc56b-161">El cmdlet toma un parámetro **Path** que especifica la carpeta donde se encuentra el MOF de configuración.</span><span class="sxs-lookup"><span data-stu-id="bc56b-161">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="bc56b-162">El cmdlet crea un archivo de suma de comprobación denominado `ConfigurationMOFName.mof.checksum`, donde `ConfigurationMOFName` es el nombre del archivo mof de configuración.</span><span class="sxs-lookup"><span data-stu-id="bc56b-162">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="bc56b-163">Si hay más de un archivo MOF de configuración en la carpeta especificada, se crea una suma de comprobación para cada una de las configuraciones de la carpeta.</span><span class="sxs-lookup"><span data-stu-id="bc56b-163">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="bc56b-164">Coloque los archivos MOF y sus archivos asociados de suma de comprobación en la carpeta **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="bc56b-164">Place the MOF files and their associated checksum files in the the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="bc56b-165">**Nota**: Si cambia el archivo MOF de configuración de cualquier manera, también deberá volver a crear el archivo de suma de comprobación.</span><span class="sxs-lookup"><span data-stu-id="bc56b-165">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="tooling"></a><span data-ttu-id="bc56b-166">Herramientas</span><span class="sxs-lookup"><span data-stu-id="bc56b-166">Tooling</span></span>
<span data-ttu-id="bc56b-167">Con el fin de facilitar la configuración, la validación y la administración del servidor de incorporación de cambios, se incluyen las siguientes herramientas como ejemplos en la versión más reciente del módulo xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="bc56b-167">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>
1. <span data-ttu-id="bc56b-168">Un módulo que le ayudará a empaquetar los archivos de configuración y los módulos de recursos de DSC para su uso en el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="bc56b-168">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="bc56b-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="bc56b-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="bc56b-170">Vea los ejemplos siguientes:</span><span class="sxs-lookup"><span data-stu-id="bc56b-170">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="bc56b-171">Un script que valida que el servidor de incorporación de cambios se configura correctamente.</span><span class="sxs-lookup"><span data-stu-id="bc56b-171">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="bc56b-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="bc56b-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>


## <a name="pull-client-configuration"></a><span data-ttu-id="bc56b-173">Configuración del cliente de incorporación de cambios</span><span class="sxs-lookup"><span data-stu-id="bc56b-173">Pull client configuration</span></span> 
<span data-ttu-id="bc56b-174">En los temas siguientes se describe en detalle cómo configurar los clientes de extracción:</span><span class="sxs-lookup"><span data-stu-id="bc56b-174">The following topics describe setting up pull clients in detail:</span></span>

* [<span data-ttu-id="bc56b-175">Configuración de un cliente de extracción de DSC mediante un id. de configuración</span><span class="sxs-lookup"><span data-stu-id="bc56b-175">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
* [<span data-ttu-id="bc56b-176">Configuración de un cliente de extracción de DSC mediante nombres de configuración</span><span class="sxs-lookup"><span data-stu-id="bc56b-176">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="bc56b-177">Configuraciones parciales</span><span class="sxs-lookup"><span data-stu-id="bc56b-177">Partial configurations</span></span>](partialConfigs.md)


## <a name="see-also"></a><span data-ttu-id="bc56b-178">Vea también</span><span class="sxs-lookup"><span data-stu-id="bc56b-178">See also</span></span>
* [<span data-ttu-id="bc56b-179">Información general sobre la configuración de estado deseado de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc56b-179">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="bc56b-180">Establecer configuraciones</span><span class="sxs-lookup"><span data-stu-id="bc56b-180">Enacting configurations</span></span>](enactingConfigurations.md)
* [<span data-ttu-id="bc56b-181">Uso de un servidor de informes de DSC</span><span class="sxs-lookup"><span data-stu-id="bc56b-181">Using a DSC report server</span></span>](reportServer.md)

