---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Mejoras de la configuración del estado deseado en WMF 5.1
ms.openlocfilehash: 92f82d62550e105a187fd7c0c58b49367c646a7e
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523062"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="5a456-103">Mejoras en la configuración de estado deseado (DSC) en WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="5a456-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="5a456-104">Mejoras en los recursos de la clase DSC</span><span class="sxs-lookup"><span data-stu-id="5a456-104">DSC class resource improvements</span></span>

<span data-ttu-id="5a456-105">En WMF 5.1, hemos corregido los siguientes problemas conocidos:</span><span class="sxs-lookup"><span data-stu-id="5a456-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="5a456-106">Get-DscConfiguration puede devolver valores vacíos (NULL) o errores si la función Get() de un recurso de DSC basado en clases devuelve un tipo complejo o de tabla hash.</span><span class="sxs-lookup"><span data-stu-id="5a456-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="5a456-107">Get-DscConfiguration devuelve un error si se usa la credencial RunAs en la configuración de DSC.</span><span class="sxs-lookup"><span data-stu-id="5a456-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="5a456-108">Un recurso basado en clases no se puede usar en una configuración compuesta.</span><span class="sxs-lookup"><span data-stu-id="5a456-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="5a456-109">Start-DscConfiguration se bloquea si el recurso basado en clases tiene una propiedad de un tipo propio.</span><span class="sxs-lookup"><span data-stu-id="5a456-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="5a456-110">Los recursos basados en clases no se pueden utilizar como recursos exclusivos.</span><span class="sxs-lookup"><span data-stu-id="5a456-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="5a456-111">Mejoras en la depuración de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="5a456-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="5a456-112">En WMF 5.0, el depurador de PowerShell no se detenía directamente en el método de recursos basados en clases (Get/Set/Test).</span><span class="sxs-lookup"><span data-stu-id="5a456-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="5a456-113">En WMF 5.1, el depurador se detiene en el método de recursos basados en clases de la misma manera que con los métodos de recursos basados en MOF.</span><span class="sxs-lookup"><span data-stu-id="5a456-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="5a456-114">El cliente de extracción de DSC es compatible con TLS 1.1 y TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="5a456-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="5a456-115">Anteriormente, el cliente de extracción de DSC solo era compatible con SSL3.0 y TLS1.0 a través de conexiones HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a456-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span>
<span data-ttu-id="5a456-116">Cuando se le obligaba a usar protocolos más seguros, el cliente de extracción dejaba de funcionar.</span><span class="sxs-lookup"><span data-stu-id="5a456-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span>
<span data-ttu-id="5a456-117">En WMF 5.1, el cliente de extracción de DSC ya no es compatible con SSL 3.0 y, en cambio, ya es compatible con los protocolos TLS 1.1 y TLS 1.2 que son más seguros.</span><span class="sxs-lookup"><span data-stu-id="5a456-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="5a456-118">Registro de servidor de extracción mejorado</span><span class="sxs-lookup"><span data-stu-id="5a456-118">Improved pull server registration</span></span>

<span data-ttu-id="5a456-119">En las versiones anteriores de WMF, si se realizaban solicitudes de informes y registros concurrentes al servidor de extracción de DSC mientras se usaba la base de datos ESENT, LCM no podía registrarlas ni informar al respecto.</span><span class="sxs-lookup"><span data-stu-id="5a456-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span>
<span data-ttu-id="5a456-120">En tales casos, los registros de eventos del servidor de extracción tienen el error "El nombre de instancia ya está en uso".</span><span class="sxs-lookup"><span data-stu-id="5a456-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="5a456-121">Esto se debe a que se usa un patrón incorrecto para acceder a la base de datos ESENT en un escenario de varios subprocesos.</span><span class="sxs-lookup"><span data-stu-id="5a456-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span>
<span data-ttu-id="5a456-122">En WMF 5.1, este problema se ha corregido.</span><span class="sxs-lookup"><span data-stu-id="5a456-122">In WMF 5.1, this issue has been fixed.</span></span>
<span data-ttu-id="5a456-123">Los informes o registros simultáneos (que implican la base de datos ESENT) funcionan correctamente en WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="5a456-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span>
<span data-ttu-id="5a456-124">Este problema solo concierne a la base de datos ESENT, no se aplica a la base de datos OLEDB.</span><span class="sxs-lookup"><span data-stu-id="5a456-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="5a456-125">Habilitación del registro circular en la instancia de base de datos ESENT</span><span class="sxs-lookup"><span data-stu-id="5a456-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="5a456-126">En versiones anteriores de DSC-PullServer, los archivos de registro de la base de datos ESENT llenaban el espacio en disco del servidor de extracción, porque la instancia de la base de datos se creó sin el registro circular.</span><span class="sxs-lookup"><span data-stu-id="5a456-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="5a456-127">En esta versión, tiene la opción de controlar el comportamiento del registro circular de la instancia mediante el archivo web.config del servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="5a456-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="5a456-128">De forma predeterminada, CircularLogging se establece en TRUE.</span><span class="sxs-lookup"><span data-stu-id="5a456-128">By default CircularLogging is set to TRUE.</span></span>

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="5a456-129">Convención de nomenclatura de configuración parcial de extracción</span><span class="sxs-lookup"><span data-stu-id="5a456-129">Pull partial configuration naming convention</span></span>

<span data-ttu-id="5a456-130">En la versión anterior, la convención de nomenclatura de una configuración parcial consistía en que el nombre de archivo MOF en el servidor o servicio de extracción debía coincidir con el nombre de configuración parcial especificado en la configuración del administrador de configuración local, que a su vez debe coincidir con el nombre de configuración insertado en el archivo MOF.</span><span class="sxs-lookup"><span data-stu-id="5a456-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="5a456-131">Vea las instantáneas siguientes:</span><span class="sxs-lookup"><span data-stu-id="5a456-131">See the snapshots below:</span></span>

- <span data-ttu-id="5a456-132">Opciones de configuración local que definen una configuración parcial que puede recibir un nodo.</span><span class="sxs-lookup"><span data-stu-id="5a456-132">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![Metaconfiguración de ejemplo](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="5a456-134">Definición de configuración parcial de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="5a456-134">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="5a456-135">"ConfigurationName" insertado en el archivo MOF generado.</span><span class="sxs-lookup"><span data-stu-id="5a456-135">'ConfigurationName' embedded in the generated MOF file.</span></span>

![Archivo MOF de ejemplo generado](../images/PartialGeneratedMof.png)

- <span data-ttu-id="5a456-137">FileName en el repositorio de configuración de extracción</span><span class="sxs-lookup"><span data-stu-id="5a456-137">FileName in the pull configuration repository</span></span>

![FileName en el repositorio de configuración](../images/PartialInConfigRepository.png)

<span data-ttu-id="5a456-139">El nombre del servicio Automatización de Azure generó archivos MOF como `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="5a456-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="5a456-140">Por tanto, la configuración siguiente se compila como PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="5a456-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="5a456-141">Esto hizo imposible extraer una de las configuraciones parciales del servicio Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="5a456-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

<span data-ttu-id="5a456-142">En WMF 5.1, la configuración parcial del servidor o servicio de extracción se puede denominar `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="5a456-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="5a456-143">Además, si una máquina extrae una sola configuración del servidor o servicio de extracción, el archivo de configuración del repositorio de configuración del servidor de extracción puede tener cualquier nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="5a456-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span>
<span data-ttu-id="5a456-144">Esta flexibilidad de nomenclatura le permite administrar los nodos parcialmente mediante el servicio Azure Automation, donde cierta configuración del nodo proviene del DSC de Azure Automation y con una configuración parcial que administra de forma local.</span><span class="sxs-lookup"><span data-stu-id="5a456-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="5a456-145">La metaconfiguración siguiente configura un nodo que se debe administrar tanto localmente como mediante el servicio Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="5a456-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="5a456-146">Uso de PsDscRunAsCredential con recursos compuestos de DSC</span><span class="sxs-lookup"><span data-stu-id="5a456-146">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="5a456-147">Hemos agregado compatibilidad para usar [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) con recursos [compuestos](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) de DSC.</span><span class="sxs-lookup"><span data-stu-id="5a456-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="5a456-148">Ahora puede especificar el valor de PsDscRunAsCredential al usar recursos compuestos dentro de las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="5a456-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span>
<span data-ttu-id="5a456-149">Si se especifica así, todos los recursos se ejecutarán dentro de un recurso compuesto como un usuario RunAs.</span><span class="sxs-lookup"><span data-stu-id="5a456-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span>
<span data-ttu-id="5a456-150">Si el recurso compuesto llama a otro recurso compuesto, todos los recursos se ejecutarán también como usuario RunAs.</span><span class="sxs-lookup"><span data-stu-id="5a456-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span>
<span data-ttu-id="5a456-151">Las credenciales de RunAs se propagan a todos los niveles de la jerarquía del recurso compuesto.</span><span class="sxs-lookup"><span data-stu-id="5a456-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span>
<span data-ttu-id="5a456-152">Si cualquier recurso de un recurso compuesto especifica su propio valor para PsDscRunAsCredential, aparece un error de combinación durante la compilación de la configuración.</span><span class="sxs-lookup"><span data-stu-id="5a456-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="5a456-153">En este ejemplo se muestra el uso con el recurso compuesto [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) que se incluye en el módulo PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="5a456-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="5a456-154">Validaciones de firmas de configuraciones y módulos de DSC</span><span class="sxs-lookup"><span data-stu-id="5a456-154">DSC module and configuration signing validations</span></span>

<span data-ttu-id="5a456-155">En DSC, las configuraciones y los módulos se distribuyen a los equipos administrados desde el servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="5a456-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span>
<span data-ttu-id="5a456-156">Si el servidor de extracción está en peligro, un atacante puede modificar las configuraciones y los módulos del servidor de extracción y propagarlos a todos los nodos administrados, poniéndolos todos en peligro.</span><span class="sxs-lookup"><span data-stu-id="5a456-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span>

<span data-ttu-id="5a456-157">En WMF 5.1, DSC admite la validación de las firmas digitales en los archivos del catálogo y de configuración (.MOF).</span><span class="sxs-lookup"><span data-stu-id="5a456-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span>
<span data-ttu-id="5a456-158">Esta característica evita que los nodos ejecuten archivos de módulos o de configuración que no están firmados por un firmante de confianza o que se han alterado después de que los haya firmado un firmante de confianza.</span><span class="sxs-lookup"><span data-stu-id="5a456-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="5a456-159">Cómo firmar un módulo y una configuración</span><span class="sxs-lookup"><span data-stu-id="5a456-159">How to sign configuration and module</span></span>

***
* <span data-ttu-id="5a456-160">Archivos de configuración (.MOF): el cmdlet de PowerShell existente [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) se amplía para admitir la firma de archivos MOF.</span><span class="sxs-lookup"><span data-stu-id="5a456-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>
* <span data-ttu-id="5a456-161">Módulos: la firma de módulos se realiza mediante la firma del catálogo de módulos correspondiente mediante los siguientes pasos:</span><span class="sxs-lookup"><span data-stu-id="5a456-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
    1. <span data-ttu-id="5a456-162">Creación de un archivo de catálogo: un archivo de catálogo contiene una colección de algoritmos hash criptográficos o huellas digitales.</span><span class="sxs-lookup"><span data-stu-id="5a456-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span>
       <span data-ttu-id="5a456-163">Cada huella digital corresponde a un archivo que se incluye en el módulo.</span><span class="sxs-lookup"><span data-stu-id="5a456-163">Each thumbprint corresponds to a file that is included in the module.</span></span>
       <span data-ttu-id="5a456-164">Se ha agregado un nuevo cmdlet, [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), para que los usuarios puedan crear un archivo de catálogo para su módulo.</span><span class="sxs-lookup"><span data-stu-id="5a456-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="5a456-165">Firma del archivo de catálogo: use el cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) para firmar el archivo de catálogo.</span><span class="sxs-lookup"><span data-stu-id="5a456-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="5a456-166">Coloque el archivo de catálogo dentro de la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="5a456-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="5a456-167">Por convención, el archivo de catálogo del módulo debe colocarse en la carpeta del módulo y debe tener el mismo nombre que este.</span><span class="sxs-lookup"><span data-stu-id="5a456-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="5a456-168">Configuración de LocalConfigurationManager para habilitar las validaciones de las firmas</span><span class="sxs-lookup"><span data-stu-id="5a456-168">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="5a456-169">Extracción</span><span class="sxs-lookup"><span data-stu-id="5a456-169">Pull</span></span>

<span data-ttu-id="5a456-170">En un nodo, LocalConfigurationManager realiza la validación de las firmas de módulos y las configuraciones en función de su configuración actual.</span><span class="sxs-lookup"><span data-stu-id="5a456-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span>
<span data-ttu-id="5a456-171">De forma predeterminada, la validación de firmas está deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="5a456-171">By default, signature validation is disabled.</span></span>
<span data-ttu-id="5a456-172">La validación de firmas se puede habilitar agregando un bloque "SignatureValidation" a la definición de metaconfiguración del nodo, tal como se muestra aquí:</span><span class="sxs-lookup"><span data-stu-id="5a456-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="5a456-173">El establecimiento de la metaconfiguración anterior en un nodo habilita la validación de firmas de los módulos y las configuraciones descargados.</span><span class="sxs-lookup"><span data-stu-id="5a456-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span>
<span data-ttu-id="5a456-174">LocalConfigurationManager lleva a cabo los pasos siguientes para comprobar las firmas digitales.</span><span class="sxs-lookup"><span data-stu-id="5a456-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="5a456-175">Compruebe que la firma de un archivo de configuración (. MOF) es válida.</span><span class="sxs-lookup"><span data-stu-id="5a456-175">Verify the signature on a configuration file (.MOF) is valid.</span></span>
   <span data-ttu-id="5a456-176">Usa el cmdlet de PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), que se amplía en la versión 5.1 para admitir la validación de la firma de MOF.</span><span class="sxs-lookup"><span data-stu-id="5a456-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="5a456-177">Compruebe que la entidad de certificación que autorizó al firmante es de confianza.</span><span class="sxs-lookup"><span data-stu-id="5a456-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="5a456-178">Descargue las dependencias de los módulos o recursos de la configuración en una ubicación temporal.</span><span class="sxs-lookup"><span data-stu-id="5a456-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="5a456-179">Compruebe la firma del catálogo incluida dentro del módulo.</span><span class="sxs-lookup"><span data-stu-id="5a456-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="5a456-180">Busque un archivo `<moduleName>.cat` y compruebe su firma mediante el cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span><span class="sxs-lookup"><span data-stu-id="5a456-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="5a456-181">Compruebe que la entidad de certificación que autenticó al firmante es de confianza.</span><span class="sxs-lookup"><span data-stu-id="5a456-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="5a456-182">Compruebe que el contenido de los módulos no se ha alterado, para lo que debe usar el cmdlet nuevo [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="5a456-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="5a456-183">Install-Module en $env:ProgramFiles\WindowsPowerShell\Modules\\</span><span class="sxs-lookup"><span data-stu-id="5a456-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="5a456-184">Configuración de proceso</span><span class="sxs-lookup"><span data-stu-id="5a456-184">Process configuration</span></span>

> <span data-ttu-id="5a456-185">Nota: La validación de la firma en el catálogo de módulo y la configuración solo se realizan la primera vez que se aplica la configuración al sistema o cuando el módulo se descarga e instala.</span><span class="sxs-lookup"><span data-stu-id="5a456-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
<span data-ttu-id="5a456-186">Las ejecuciones de coherencia no validan la firma de Current.mof ni sus dependencias de módulo.</span><span class="sxs-lookup"><span data-stu-id="5a456-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="5a456-187">Si se ha producido un error en cualquier etapa de la comprobación, por ejemplo, si la configuración extraída del servidor de extracción no tiene firma, el procesamiento de la configuración termina con el error que se muestra más adelante y se eliminan todos los archivos temporales.</span><span class="sxs-lookup"><span data-stu-id="5a456-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Configuración de salida de error de ejemplo](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="5a456-189">De forma similar, la extracción de un módulo cuyo catálogo no esté firmado provoca el siguiente error:</span><span class="sxs-lookup"><span data-stu-id="5a456-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Módulo de salida de error de ejemplo](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="5a456-191">Push</span><span class="sxs-lookup"><span data-stu-id="5a456-191">Push</span></span>

<span data-ttu-id="5a456-192">Una configuración entregada mediante inserción puede alterarse en su origen antes de que se entregue al nodo.</span><span class="sxs-lookup"><span data-stu-id="5a456-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span>
<span data-ttu-id="5a456-193">El administrador de configuración local lleva a cabo pasos de validación de firmas similares para las configuraciones insertadas o publicadas.</span><span class="sxs-lookup"><span data-stu-id="5a456-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="5a456-194">A continuación, se muestra un ejemplo completo de validación de firma para la inserción.</span><span class="sxs-lookup"><span data-stu-id="5a456-194">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="5a456-195">Habilite la validación de firma en el nodo.</span><span class="sxs-lookup"><span data-stu-id="5a456-195">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="5a456-196">Cree un archivo de configuración de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="5a456-196">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="5a456-197">Intente insertar el archivo de configuración sin firmar en el nodo.</span><span class="sxs-lookup"><span data-stu-id="5a456-197">Try pushing the unsigned configuration file in to the node.</span></span>

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="5a456-199">Firme el archivo configuración mediante el certificado de firma de código.</span><span class="sxs-lookup"><span data-stu-id="5a456-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="5a456-201">Intente insertar el archivo MOF firmado.</span><span class="sxs-lookup"><span data-stu-id="5a456-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)
