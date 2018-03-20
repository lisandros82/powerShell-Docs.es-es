---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Uso de DSC on Nano Server
ms.openlocfilehash: c8f3669ee9c2ed6107c14ba9f4460d82276e1932
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="f8baa-103">Uso de DSC on Nano Server</span><span class="sxs-lookup"><span data-stu-id="f8baa-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="f8baa-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f8baa-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="f8baa-105">**DSC on Nano Server** es un paquete opcional de la carpeta `NanoServer\Packages` de los medios de Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="f8baa-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="f8baa-106">Se puede instalar el paquete cuando se crea un VHD para un Nano Server mediante la especificación de **Microsoft-NanoServer-DSC-Package** como valor del parámetro **Packages** de la función **New-NanoServerImage**.</span><span class="sxs-lookup"><span data-stu-id="f8baa-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="f8baa-107">Por ejemplo, si está creando un VHD para una máquina virtual, el comando sería similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="f8baa-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="f8baa-108">Para obtener más información sobre cómo instalar y usar Nano Server, y también cómo administrar Nano Server con comunicación remota de PowerShell, vea [Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx) (Introducción a Nano Server).</span><span class="sxs-lookup"><span data-stu-id="f8baa-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx).</span></span>


## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="f8baa-109">Características de DSC disponibles en Nano Server</span><span class="sxs-lookup"><span data-stu-id="f8baa-109">DSC features available on Nano Server</span></span>

 <span data-ttu-id="f8baa-110">Dado que Nano Server solo admite un conjunto limitado de API en comparación con una versión completa de Windows Server; por el momento, DSC on Nano Server no tiene paridad completa funcional con DSC cuando se ejecuta en SKU completas.</span><span class="sxs-lookup"><span data-stu-id="f8baa-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="f8baa-111">DSC on Nano Server está en desarrollo activo y todavía no es una característica completa.</span><span class="sxs-lookup"><span data-stu-id="f8baa-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>
 
 <span data-ttu-id="f8baa-112">Las siguientes características de DSC están disponibles actualmente en Nano Server:</span><span class="sxs-lookup"><span data-stu-id="f8baa-112">The following DSC features are currently available on Nano Server:</span></span> 


* <span data-ttu-id="f8baa-113">Modos de inserción y extracción</span><span class="sxs-lookup"><span data-stu-id="f8baa-113">Both push and pull modes</span></span>

* <span data-ttu-id="f8baa-114">Todos los cmdlets de DSC que existen en una versión completa de Windows Server, incluidos los siguientes:</span><span class="sxs-lookup"><span data-stu-id="f8baa-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span> 
  * [<span data-ttu-id="f8baa-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f8baa-115">Get-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn407378.aspx)
  * [<span data-ttu-id="f8baa-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f8baa-116">Set-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn521621.aspx)     
  * [<span data-ttu-id="f8baa-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="f8baa-117">Enable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [<span data-ttu-id="f8baa-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="f8baa-118">Disable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517872.aspx)       
  * [<span data-ttu-id="f8baa-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="f8baa-119">Start-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [<span data-ttu-id="f8baa-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="f8baa-120">Stop-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [<span data-ttu-id="f8baa-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="f8baa-121">Get-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [<span data-ttu-id="f8baa-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="f8baa-122">Test-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407382.aspx)      
  * [<span data-ttu-id="f8baa-123">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="f8baa-123">Publish-DscConfiguraiton</span></span>](https://technet.microsoft.com/en-us/library/mt517875.aspx) 
  * [<span data-ttu-id="f8baa-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="f8baa-124">Update-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [<span data-ttu-id="f8baa-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="f8baa-125">Restore-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [<span data-ttu-id="f8baa-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="f8baa-126">Remove-DscConfigurationDocument</span></span>](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [<span data-ttu-id="f8baa-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="f8baa-127">Get-DscConfigurationStatus</span></span>](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [<span data-ttu-id="f8baa-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="f8baa-128">Invoke-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [<span data-ttu-id="f8baa-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="f8baa-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [<span data-ttu-id="f8baa-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="f8baa-130">Get-DscResource</span></span>](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [<span data-ttu-id="f8baa-131">New-DSCCheckSum</span><span class="sxs-lookup"><span data-stu-id="f8baa-131">New-DscChecksum</span></span>](https://technet.microsoft.com/en-us/library/dn521622.aspx)    

* <span data-ttu-id="f8baa-132">Compilación de configuraciones (vea [Configuraciones DSC](configurations.md))</span><span class="sxs-lookup"><span data-stu-id="f8baa-132">Compiling configurations (see [DSC configurations](configurations.md))</span></span>

  <span data-ttu-id="f8baa-133">**Problema:** no funciona el cifrado de contraseña (vea [Proteger el archivo MOF](securemof.md)) durante la compilación de la configuración.</span><span class="sxs-lookup"><span data-stu-id="f8baa-133">**Issue:** Password encryption (see [Securing the MOF File](securemof.md)) during configuration compilation doesn't work.</span></span>

* <span data-ttu-id="f8baa-134">Compilación de metaconfiguraciones (vea [Configuración del administrador de configuración local](metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="f8baa-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](metaConfig.md))</span></span>

* <span data-ttu-id="f8baa-135">Ejecutar un recurso en el contexto de usuario (vea [DSC de ejecución con las credenciales de usuario (RunAs)](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="f8baa-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](runAsUser.md))</span></span>

* <span data-ttu-id="f8baa-136">Recursos basados en clases (vea [Escribir un recurso de DSC personalizado con clases de PowerShell](authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="f8baa-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](authoringResourceClass.md))</span></span>

* <span data-ttu-id="f8baa-137">Depuración de recursos de DSC (vea [Depuración de recursos de DSC](debugresource.md))</span><span class="sxs-lookup"><span data-stu-id="f8baa-137">Debugging of DSC resources (see [Debugging DSC resources](debugresource.md))</span></span>
  
  <span data-ttu-id="f8baa-138">**Problema:** no funciona si un recurso usa PsDscRunAsCredential (vea [DSC de ejecución con las credenciales de usuario](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="f8baa-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](runAsUser.md))</span></span>

* [<span data-ttu-id="f8baa-139">Especificación de las dependencias entre nodos</span><span class="sxs-lookup"><span data-stu-id="f8baa-139">Specifying cross-node dependencies</span></span>](crossNodeDependencies.md) 

* [<span data-ttu-id="f8baa-140">Control de versiones de recursos</span><span class="sxs-lookup"><span data-stu-id="f8baa-140">Resource versioning</span></span>](sxsResource.md)

* <span data-ttu-id="f8baa-141">Cliente de extracción (configuraciones y recursos) (vea [Configuración de un cliente de extracción mediante nombres de configuración](pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="f8baa-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](pullClientConfigNames.md))</span></span>

* [<span data-ttu-id="f8baa-142">Configuraciones parciales (extracción e incorporación de cambios)</span><span class="sxs-lookup"><span data-stu-id="f8baa-142">Partial configurations (pull & push)</span></span>](partialConfigs.md)

* [<span data-ttu-id="f8baa-143">Generación de informes en el servidor de extracción</span><span class="sxs-lookup"><span data-stu-id="f8baa-143">Reporting to pull server</span></span>](reportServer.md) 

* <span data-ttu-id="f8baa-144">Cifrado de MOF</span><span class="sxs-lookup"><span data-stu-id="f8baa-144">MOF encryption</span></span>

* <span data-ttu-id="f8baa-145">Registro de eventos</span><span class="sxs-lookup"><span data-stu-id="f8baa-145">Event logging</span></span>

* <span data-ttu-id="f8baa-146">Informes de DSC de automatización de Azure</span><span class="sxs-lookup"><span data-stu-id="f8baa-146">Azure Automation DSC reporting</span></span>

* <span data-ttu-id="f8baa-147">Recursos que son totalmente funcionales</span><span class="sxs-lookup"><span data-stu-id="f8baa-147">Resources that are fully functional</span></span>
  * [<span data-ttu-id="f8baa-148">Archive</span><span class="sxs-lookup"><span data-stu-id="f8baa-148">Archive</span></span>](archiveResource.md)
  * [<span data-ttu-id="f8baa-149">Environment</span><span class="sxs-lookup"><span data-stu-id="f8baa-149">Environment</span></span>](environmentResource.md)
  * [<span data-ttu-id="f8baa-150">File</span><span class="sxs-lookup"><span data-stu-id="f8baa-150">File</span></span>](fileResource.md)
  * [<span data-ttu-id="f8baa-151">Log</span><span class="sxs-lookup"><span data-stu-id="f8baa-151">Log</span></span>](logResource.md)
  * <span data-ttu-id="f8baa-152">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="f8baa-152">ProcessSet</span></span>
  * [<span data-ttu-id="f8baa-153">Registry</span><span class="sxs-lookup"><span data-stu-id="f8baa-153">Registry</span></span>](registryResource.md)
  * [<span data-ttu-id="f8baa-154">Script</span><span class="sxs-lookup"><span data-stu-id="f8baa-154">Script</span></span>](scriptResource.md)
  * <span data-ttu-id="f8baa-155">WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="f8baa-155">WindowsPackageCab</span></span>
  * [<span data-ttu-id="f8baa-156">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="f8baa-156">WindowsProcess</span></span>](windowsProcessResource.md)
  * <span data-ttu-id="f8baa-157">WaitForAll (vea [Especificación de dependencias entre nodos](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="f8baa-157">WaitForAll (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="f8baa-158">WaitForAny (vea [Especificación de dependencias entre nodos](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="f8baa-158">WaitForAny (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="f8baa-159">WaitForSome (vea [Especificación de dependencias entre nodos](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="f8baa-159">WaitForSome (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>

* <span data-ttu-id="f8baa-160">Recursos que son parcialmente funcionales</span><span class="sxs-lookup"><span data-stu-id="f8baa-160">Resources that are partially functional</span></span>
  * [<span data-ttu-id="f8baa-161">Grupo</span><span class="sxs-lookup"><span data-stu-id="f8baa-161">Group</span></span>](groupResource.md)
  * <span data-ttu-id="f8baa-162">GroupSet</span><span class="sxs-lookup"><span data-stu-id="f8baa-162">GroupSet</span></span>
  
  <span data-ttu-id="f8baa-163">**Problema:** los recursos anteriores producirán un error si se llama dos veces a una instancia específica (ejecutando dos veces la misma configuración)</span><span class="sxs-lookup"><span data-stu-id="f8baa-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>
  
  * [<span data-ttu-id="f8baa-164">Service</span><span class="sxs-lookup"><span data-stu-id="f8baa-164">Service</span></span>](serviceResource.md)
  * <span data-ttu-id="f8baa-165">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="f8baa-165">ServiceSet</span></span>
  
  <span data-ttu-id="f8baa-166">**Problema:** solo funciona para iniciar y detener el servicio (estado).</span><span class="sxs-lookup"><span data-stu-id="f8baa-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="f8baa-167">Produce un error si intenta cambiar otros atributos del servicio, como startuptype, credenciales, descripción, etc.</span><span class="sxs-lookup"><span data-stu-id="f8baa-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="f8baa-168">El error que se produce es similar a:</span><span class="sxs-lookup"><span data-stu-id="f8baa-168">The error thrown is similar to:</span></span>
  
  <span data-ttu-id="f8baa-169">*No se puede encontrar el tipo [management.managementobject]. Compruebe que está cargado el ensamblado que lo contiene.*</span><span class="sxs-lookup"><span data-stu-id="f8baa-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>
  
* <span data-ttu-id="f8baa-170">Recursos que no son funcionales</span><span class="sxs-lookup"><span data-stu-id="f8baa-170">Resources that are not functional</span></span>
  * [<span data-ttu-id="f8baa-171">Usuario</span><span class="sxs-lookup"><span data-stu-id="f8baa-171">User</span></span>](userResource.md)
  

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="f8baa-172">Características de DSC no disponibles en Nano Server</span><span class="sxs-lookup"><span data-stu-id="f8baa-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="f8baa-173">Las siguientes características de DSC no están disponibles actualmente en Nano Server:</span><span class="sxs-lookup"><span data-stu-id="f8baa-173">The following DSC features are not currently available on Nano Server:</span></span>

* <span data-ttu-id="f8baa-174">Descifrar el documento MOF con contraseñas cifradas</span><span class="sxs-lookup"><span data-stu-id="f8baa-174">Decrypting MOF document with encrypted password(s)</span></span> 
* <span data-ttu-id="f8baa-175">Servidor de extracción: actualmente no se puede establecer un servidor de extracción en Nano Server</span><span class="sxs-lookup"><span data-stu-id="f8baa-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
* <span data-ttu-id="f8baa-176">Todo lo que no está en la lista de trabajos funciona</span><span class="sxs-lookup"><span data-stu-id="f8baa-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="f8baa-177">Uso de recursos personalizados de DSC en Nano Server</span><span class="sxs-lookup"><span data-stu-id="f8baa-177">Using custom DSC resources on Nano Server</span></span>
 
<span data-ttu-id="f8baa-178">Debido a un conjunto limitado de bibliotecas CLR y API de Windows disponibles en Nano Server, los recursos de DSC que funcionan en la versión CLR completa de Windows no funcionan necesariamente en Nano Server.</span><span class="sxs-lookup"><span data-stu-id="f8baa-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span> <span data-ttu-id="f8baa-179">Pruebas de un extremo a otro antes de implementar los recursos personalizados de DSC en un entorno de producción.</span><span class="sxs-lookup"><span data-stu-id="f8baa-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8baa-180">Véase también</span><span class="sxs-lookup"><span data-stu-id="f8baa-180">See Also</span></span>
- <span data-ttu-id="f8baa-181">[Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx) (Introducción a Nano Server)</span><span class="sxs-lookup"><span data-stu-id="f8baa-181">[Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx)</span></span>

