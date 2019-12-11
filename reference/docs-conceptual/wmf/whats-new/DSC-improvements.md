---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Mejoras de la configuración del estado deseado en WMF 5.1
ms.openlocfilehash: a5efa38ce791a893580316bad7b61a6689153a86
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416673"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="1849f-103">Mejoras en la configuración de estado deseado (DSC) en WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="1849f-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="1849f-104">Mejoras en los recursos de la clase DSC</span><span class="sxs-lookup"><span data-stu-id="1849f-104">DSC class resource improvements</span></span>

<span data-ttu-id="1849f-105">En WMF 5.1, hemos corregido los siguientes problemas conocidos:</span><span class="sxs-lookup"><span data-stu-id="1849f-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="1849f-106">Get-DscConfiguration puede devolver valores vacíos (NULL) o errores si la función Get() de un recurso de DSC basado en clases devuelve un tipo complejo o de tabla hash.</span><span class="sxs-lookup"><span data-stu-id="1849f-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="1849f-107">Get-DscConfiguration devuelve un error si se usa la credencial RunAs en la configuración de DSC.</span><span class="sxs-lookup"><span data-stu-id="1849f-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="1849f-108">Un recurso basado en clases no se puede usar en una configuración compuesta.</span><span class="sxs-lookup"><span data-stu-id="1849f-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="1849f-109">Start-DscConfiguration se bloquea si el recurso basado en clases tiene una propiedad de un tipo propio.</span><span class="sxs-lookup"><span data-stu-id="1849f-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="1849f-110">Los recursos basados en clases no se pueden utilizar como recursos exclusivos.</span><span class="sxs-lookup"><span data-stu-id="1849f-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="1849f-111">Mejoras en la depuración de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="1849f-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="1849f-112">En WMF 5.0, el depurador de PowerShell no se detenía directamente en el método de recursos basados en clases (Get/Set/Test).</span><span class="sxs-lookup"><span data-stu-id="1849f-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span> <span data-ttu-id="1849f-113">En WMF 5.1, el depurador se detiene en el método de recursos basados en clases de la misma manera que con los métodos de recursos basados en MOF.</span><span class="sxs-lookup"><span data-stu-id="1849f-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="1849f-114">El cliente de extracción de DSC es compatible con TLS 1.1 y TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="1849f-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="1849f-115">Anteriormente, el cliente de extracción de DSC solo era compatible con SSL3.0 y TLS1.0 a través de conexiones HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1849f-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="1849f-116">Cuando se le obligaba a usar protocolos más seguros, el cliente de extracción dejaba de funcionar.</span><span class="sxs-lookup"><span data-stu-id="1849f-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="1849f-117">En WMF 5.1, el cliente de extracción de DSC ya no es compatible con SSL 3.0 y, en cambio, ya es compatible con los protocolos TLS 1.1 y TLS 1.2 que son más seguros.</span><span class="sxs-lookup"><span data-stu-id="1849f-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="1849f-118">Registro de servidor de extracción mejorado</span><span class="sxs-lookup"><span data-stu-id="1849f-118">Improved pull server registration</span></span>

<span data-ttu-id="1849f-119">En las versiones anteriores de WMF, si se realizaban solicitudes de informes y registros concurrentes al servidor de extracción de DSC mientras se usaba la base de datos ESENT, LCM no podía registrarlas ni informar al respecto.</span><span class="sxs-lookup"><span data-stu-id="1849f-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="1849f-120">En tales casos, los registros de eventos del servidor de extracción tienen el error "El nombre de instancia ya está en uso".</span><span class="sxs-lookup"><span data-stu-id="1849f-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span> <span data-ttu-id="1849f-121">Esto se debe a que se usa un patrón incorrecto para acceder a la base de datos ESENT en un escenario de varios subprocesos.</span><span class="sxs-lookup"><span data-stu-id="1849f-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="1849f-122">En WMF 5.1, este problema se ha corregido.</span><span class="sxs-lookup"><span data-stu-id="1849f-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="1849f-123">Los informes o registros simultáneos (que implican la base de datos ESENT) funcionan correctamente en WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="1849f-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="1849f-124">Este problema solo concierne a la base de datos ESENT, no se aplica a la base de datos OLEDB.</span><span class="sxs-lookup"><span data-stu-id="1849f-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="1849f-125">Habilitación del registro circular en la instancia de base de datos ESENT</span><span class="sxs-lookup"><span data-stu-id="1849f-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="1849f-126">En versiones anteriores de DSC-PullServer, los archivos de registro de la base de datos ESENT llenaban el espacio en disco del servidor de extracción, porque la instancia de la base de datos se creó sin el registro circular.</span><span class="sxs-lookup"><span data-stu-id="1849f-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="1849f-127">En esta versión, tiene la opción de controlar el comportamiento del registro circular de la instancia mediante el archivo web.config del servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="1849f-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="1849f-128">De forma predeterminada, CircularLogging se establece en TRUE.</span><span class="sxs-lookup"><span data-stu-id="1849f-128">By default CircularLogging is set to TRUE.</span></span>

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a><span data-ttu-id="1849f-129">Compatibilidad de WOW64 con la palabra clave Configuration</span><span class="sxs-lookup"><span data-stu-id="1849f-129">WOW64 support for Configuration Keyword</span></span>

<span data-ttu-id="1849f-130">La palabra clave `Configuration` se admite ahora en WOW64 en un equipo de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="1849f-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span></span> <span data-ttu-id="1849f-131">Esto significa que una configuración de DSC puede definirse y compilarse en un proceso de 32 bits como Windows PowerShell ISE (x 86) ejecutándose en un equipo de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="1849f-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span></span>

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="1849f-132">Convención de nomenclatura de configuración parcial de extracción</span><span class="sxs-lookup"><span data-stu-id="1849f-132">Pull partial configuration naming convention</span></span>

<span data-ttu-id="1849f-133">En la versión anterior, la convención de nomenclatura de una configuración parcial consistía en que el nombre de archivo MOF en el servidor o servicio de extracción debía coincidir con el nombre de configuración parcial especificado en la configuración del administrador de configuración local, que a su vez debe coincidir con el nombre de configuración insertado en el archivo MOF.</span><span class="sxs-lookup"><span data-stu-id="1849f-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="1849f-134">Vea las instantáneas siguientes:</span><span class="sxs-lookup"><span data-stu-id="1849f-134">See the snapshots below:</span></span>

- <span data-ttu-id="1849f-135">Opciones de configuración local que definen una configuración parcial que puede recibir un nodo.</span><span class="sxs-lookup"><span data-stu-id="1849f-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

  ![Metaconfiguración de ejemplo](../images/DSC-improvements/MetaConfigPartialOne.png)

- <span data-ttu-id="1849f-137">Definición de configuración parcial de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="1849f-137">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="1849f-138">"ConfigurationName" insertado en el archivo MOF generado.</span><span class="sxs-lookup"><span data-stu-id="1849f-138">'ConfigurationName' embedded in the generated MOF file.</span></span>

  ![Archivo MOF de ejemplo generado](../images/DSC-improvements/PartialGeneratedMof.png)

- <span data-ttu-id="1849f-140">FileName en el repositorio de configuración de extracción</span><span class="sxs-lookup"><span data-stu-id="1849f-140">FileName in the pull configuration repository</span></span>

  ![FileName en el repositorio de configuración](../images/DSC-improvements/PartialInConfigRepository.png)

  <span data-ttu-id="1849f-142">El nombre del servicio Automatización de Azure generó archivos MOF como `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="1849f-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="1849f-143">Por tanto, la configuración siguiente se compila como PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="1849f-143">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

  <span data-ttu-id="1849f-144">Esto hizo imposible extraer una de las configuraciones parciales del servicio Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="1849f-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

  <span data-ttu-id="1849f-145">En WMF 5.1, la configuración parcial del servidor o servicio de extracción se puede denominar `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="1849f-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="1849f-146">Además, si una máquina extrae una sola configuración del servidor o servicio de extracción, el archivo de configuración del repositorio de configuración del servidor de extracción puede tener cualquier nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="1849f-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="1849f-147">Esta flexibilidad de nomenclatura le permite administrar los nodos parcialmente mediante el servicio Azure Automation, donde cierta configuración del nodo proviene del DSC de Azure Automation y con una configuración parcial que administra de forma local.</span><span class="sxs-lookup"><span data-stu-id="1849f-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

  <span data-ttu-id="1849f-148">La metaconfiguración siguiente configura un nodo que se debe administrar tanto localmente como mediante el servicio Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="1849f-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="1849f-149">Uso de PsDscRunAsCredential con recursos compuestos de DSC</span><span class="sxs-lookup"><span data-stu-id="1849f-149">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="1849f-150">Hemos agregado compatibilidad para usar [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) con recursos [compuestos](/powershell/scripting/dsc/authoringresourcecomposite) de DSC.</span><span class="sxs-lookup"><span data-stu-id="1849f-150">We have added support for using [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) with DSC [Composite](/powershell/scripting/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="1849f-151">Ahora puede especificar el valor de **PsDscRunAsCredential** al usar recursos compuestos dentro de las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="1849f-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span></span> <span data-ttu-id="1849f-152">Si se especifica así, todos los recursos se ejecutarán dentro de un recurso compuesto como un usuario RunAs.</span><span class="sxs-lookup"><span data-stu-id="1849f-152">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="1849f-153">Si el recurso compuesto llama a otro recurso compuesto, todos esos recursos se ejecutarán también como usuario RunAs.</span><span class="sxs-lookup"><span data-stu-id="1849f-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span></span> <span data-ttu-id="1849f-154">Las credenciales de RunAs se propagan a todos los niveles de la jerarquía del recurso compuesto.</span><span class="sxs-lookup"><span data-stu-id="1849f-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="1849f-155">Si cualquier recurso de un recurso compuesto especifica su propio valor para **PsDscRunAsCredential**, aparece un error de combinación durante la compilación de la configuración.</span><span class="sxs-lookup"><span data-stu-id="1849f-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="1849f-156">En este ejemplo se muestra el uso con el recurso compuesto [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) que se incluye en el módulo PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="1849f-156">This example shows usage with the [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="1849f-157">Permitir recursos duplicados idénticos en una configuración</span><span class="sxs-lookup"><span data-stu-id="1849f-157">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="1849f-158">DSC no permite ni administra las definiciones de recursos en conflicto dentro de una configuración.</span><span class="sxs-lookup"><span data-stu-id="1849f-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="1849f-159">En lugar de intentar resolver el conflicto, simplemente no funciona.</span><span class="sxs-lookup"><span data-stu-id="1849f-159">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="1849f-160">Dado que la reutilización de la configuración se usa más en los recursos compuestos, etc., se producirán conflictos más a menudo.</span><span class="sxs-lookup"><span data-stu-id="1849f-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="1849f-161">Cuando las definiciones de recursos en conflicto son idénticas, DSC debe ser inteligente y permitirlo.</span><span class="sxs-lookup"><span data-stu-id="1849f-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="1849f-162">En esta versión, se admite tener varias instancias de recursos con definiciones idénticas:</span><span class="sxs-lookup"><span data-stu-id="1849f-162">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="1849f-163">En versiones anteriores, el resultado sería un error de compilación debido a un conflicto entre las instancias de WindowsFeature FE_IIS y WindowsFeature Worker_IIS al intentar comprobar la instalación del rol "Servidor web".</span><span class="sxs-lookup"><span data-stu-id="1849f-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="1849f-164">Observe que *todas* las propiedades que se están configurando son idénticas en estas dos configuraciones.</span><span class="sxs-lookup"><span data-stu-id="1849f-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="1849f-165">Puesto que *todas* las propiedades de estos dos recursos son idénticas, el resultado será una compilación correcta.</span><span class="sxs-lookup"><span data-stu-id="1849f-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="1849f-166">Si cualquiera de las propiedades difiere entre los dos recursos, no se considerarán idénticas y se producirá un error de compilación.</span><span class="sxs-lookup"><span data-stu-id="1849f-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span></span>

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="1849f-167">Validaciones de firmas de configuraciones y módulos de DSC</span><span class="sxs-lookup"><span data-stu-id="1849f-167">DSC module and configuration signing validations</span></span>

<span data-ttu-id="1849f-168">En DSC, las configuraciones y los módulos se distribuyen a los equipos administrados desde el servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="1849f-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="1849f-169">Si el servidor de extracción está en peligro, un atacante puede modificar las configuraciones y los módulos en el servidor de extracción y distribuirlo a todos los nodos administrados.</span><span class="sxs-lookup"><span data-stu-id="1849f-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span></span>

<span data-ttu-id="1849f-170">En WMF 5.1, DSC admite la validación de las firmas digitales en los archivos del catálogo y de configuración (.MOF).</span><span class="sxs-lookup"><span data-stu-id="1849f-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="1849f-171">Esta característica evita que los nodos ejecuten archivos de módulos o de configuración que no están firmados por un firmante de confianza o que se han alterado después de que los haya firmado un firmante de confianza.</span><span class="sxs-lookup"><span data-stu-id="1849f-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="1849f-172">Cómo firmar un módulo y una configuración</span><span class="sxs-lookup"><span data-stu-id="1849f-172">How to sign configuration and module</span></span>

- <span data-ttu-id="1849f-173">Archivos de configuración (.MOF): el cmdlet de PowerShell existente [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) se amplía para admitir la firma de archivos MOF.</span><span class="sxs-lookup"><span data-stu-id="1849f-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span></span>
- <span data-ttu-id="1849f-174">Módulos: la firma de módulos se realiza mediante la firma del catálogo de módulos correspondiente mediante los siguientes pasos:</span><span class="sxs-lookup"><span data-stu-id="1849f-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
  1. <span data-ttu-id="1849f-175">Creación de un archivo de catálogo: un archivo de catálogo contiene una colección de algoritmos hash criptográficos o huellas digitales.</span><span class="sxs-lookup"><span data-stu-id="1849f-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> <span data-ttu-id="1849f-176">Cada huella digital corresponde a un archivo que se incluye en el módulo.</span><span class="sxs-lookup"><span data-stu-id="1849f-176">Each thumbprint corresponds to a file that is included in the module.</span></span> <span data-ttu-id="1849f-177">Se ha agregado un nuevo cmdlet, [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), para que los usuarios puedan crear un archivo de catálogo para su módulo.</span><span class="sxs-lookup"><span data-stu-id="1849f-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span></span>
  2. <span data-ttu-id="1849f-178">Firma del archivo de catálogo: use el cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) para firmar el archivo de catálogo.</span><span class="sxs-lookup"><span data-stu-id="1849f-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span></span>
  3. <span data-ttu-id="1849f-179">Coloque el archivo de catálogo dentro de la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="1849f-179">Place the catalog file inside the module folder.</span></span> <span data-ttu-id="1849f-180">Por convención, el archivo de catálogo del módulo debe colocarse en la carpeta del módulo y debe tener el mismo nombre que este.</span><span class="sxs-lookup"><span data-stu-id="1849f-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="1849f-181">Configuración de LocalConfigurationManager para habilitar las validaciones de las firmas</span><span class="sxs-lookup"><span data-stu-id="1849f-181">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="1849f-182">Extracción</span><span class="sxs-lookup"><span data-stu-id="1849f-182">Pull</span></span>

<span data-ttu-id="1849f-183">En un nodo, LocalConfigurationManager realiza la validación de las firmas de módulos y las configuraciones en función de su configuración actual.</span><span class="sxs-lookup"><span data-stu-id="1849f-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="1849f-184">De forma predeterminada, la validación de firmas está deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="1849f-184">By default, signature validation is disabled.</span></span> <span data-ttu-id="1849f-185">La validación de firmas se puede habilitar agregando un bloque "SignatureValidation" a la definición de metaconfiguración del nodo, tal como se muestra aquí:</span><span class="sxs-lookup"><span data-stu-id="1849f-185">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="1849f-186">El establecimiento de la metaconfiguración anterior en un nodo habilita la validación de firmas de los módulos y las configuraciones descargados.</span><span class="sxs-lookup"><span data-stu-id="1849f-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="1849f-187">LocalConfigurationManager lleva a cabo los pasos siguientes para comprobar las firmas digitales.</span><span class="sxs-lookup"><span data-stu-id="1849f-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="1849f-188">Compruebe que la firma de un archivo de configuración (. MOF) es válida con el cmdlet `Get-AuthenticodeSignature`.</span><span class="sxs-lookup"><span data-stu-id="1849f-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span></span>
2. <span data-ttu-id="1849f-189">Compruebe que la entidad de certificación que autorizó al firmante es de confianza.</span><span class="sxs-lookup"><span data-stu-id="1849f-189">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="1849f-190">Descargue las dependencias de los módulos o recursos de la configuración en una ubicación temporal.</span><span class="sxs-lookup"><span data-stu-id="1849f-190">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="1849f-191">Compruebe la firma del catálogo incluida dentro del módulo.</span><span class="sxs-lookup"><span data-stu-id="1849f-191">Verify the signature of the catalog included inside the module.</span></span>
   - <span data-ttu-id="1849f-192">Busque un archivo `<moduleName>.cat` y compruebe su firma con `Get-AuthenticodeSignature`.</span><span class="sxs-lookup"><span data-stu-id="1849f-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span></span>
   - <span data-ttu-id="1849f-193">Compruebe que la entidad de certificación que autenticó al firmante es de confianza.</span><span class="sxs-lookup"><span data-stu-id="1849f-193">Verify the certification authority that authenticated the signer is trusted.</span></span>
   - <span data-ttu-id="1849f-194">Compruebe que el contenido de los módulos no se ha alterado, para lo que debe usar el cmdlet nuevo `Test-FileCatalog`.</span><span class="sxs-lookup"><span data-stu-id="1849f-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span></span>
5. <span data-ttu-id="1849f-195">`Install-Module` a `$env:ProgramFiles\WindowsPowerShell\Modules\`</span><span class="sxs-lookup"><span data-stu-id="1849f-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span></span>
6. <span data-ttu-id="1849f-196">Configuración de proceso</span><span class="sxs-lookup"><span data-stu-id="1849f-196">Process configuration</span></span>

> [!NOTE]
> <span data-ttu-id="1849f-197">La validación de la firma en el catálogo de módulo y la configuración solo se realizan la primera vez que se aplica la configuración al sistema o cuando el módulo se descarga e instala.</span><span class="sxs-lookup"><span data-stu-id="1849f-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
> <span data-ttu-id="1849f-198">Las ejecuciones de coherencia no validan la firma de Current.mof ni sus dependencias de módulo.</span><span class="sxs-lookup"><span data-stu-id="1849f-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span> <span data-ttu-id="1849f-199">Si se ha producido un error en cualquier etapa de la comprobación, por ejemplo, si la configuración extraída del servidor de extracción no tiene firma, el procesamiento de la configuración termina con el error que se muestra más adelante y se eliminan todos los archivos temporales.</span><span class="sxs-lookup"><span data-stu-id="1849f-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Configuración de salida de error de ejemplo](../images/DSC-improvements/PullUnsignedConfigFail.png)

<span data-ttu-id="1849f-201">De forma similar, la extracción de un módulo cuyo catálogo no esté firmado provoca el siguiente error:</span><span class="sxs-lookup"><span data-stu-id="1849f-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Módulo de salida de error de ejemplo](../images/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="1849f-203">Push</span><span class="sxs-lookup"><span data-stu-id="1849f-203">Push</span></span>

<span data-ttu-id="1849f-204">Una configuración entregada mediante inserción puede alterarse en su origen antes de que se entregue al nodo.</span><span class="sxs-lookup"><span data-stu-id="1849f-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="1849f-205">El administrador de configuración local lleva a cabo pasos de validación de firmas similares para las configuraciones insertadas o publicadas.</span><span class="sxs-lookup"><span data-stu-id="1849f-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span> <span data-ttu-id="1849f-206">A continuación, se muestra un ejemplo completo de validación de firma para la inserción.</span><span class="sxs-lookup"><span data-stu-id="1849f-206">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="1849f-207">Habilite la validación de firma en el nodo.</span><span class="sxs-lookup"><span data-stu-id="1849f-207">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="1849f-208">Cree un archivo de configuración de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="1849f-208">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="1849f-209">Intente insertar el archivo de configuración sin firmar en el nodo.</span><span class="sxs-lookup"><span data-stu-id="1849f-209">Try pushing the unsigned configuration file in to the node.</span></span>

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/DSC-improvements/PushUnsignedMof.png)

- <span data-ttu-id="1849f-211">Firme el archivo configuración mediante el certificado de firma de código.</span><span class="sxs-lookup"><span data-stu-id="1849f-211">Sign the configuration file using code-signing certificate.</span></span>

  ![SignMofFile](../images/DSC-improvements/SignMofFile.png)

- <span data-ttu-id="1849f-213">Intente insertar el archivo MOF firmado.</span><span class="sxs-lookup"><span data-stu-id="1849f-213">Try pushing the signed MOF file.</span></span>

  ![PushSignedMofFile](../images/DSC-improvements/PushSignedMof.png)
