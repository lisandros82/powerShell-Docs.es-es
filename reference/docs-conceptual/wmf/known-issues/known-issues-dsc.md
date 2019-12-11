---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Problemas y limitaciones conocidos de la configuración de estado deseado (DSC)
ms.openlocfilehash: a76c5bb336804c5b384e6b6ba6a705c6049ef7fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416607"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="63382-103">Problemas y limitaciones conocidos de la configuración de estado deseado (DSC)</span><span class="sxs-lookup"><span data-stu-id="63382-103">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="63382-104">Cambio de última hora: los certificados usados para cifrar o descifrar contraseñas en configuraciones de DSC no funcionan después de instalar WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="63382-104">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="63382-105">En las versiones WMF 4.0 y WMF 5.0 Preview, DSC no permitía que las contraseñas de la configuración tuvieran más de 121 caracteres de longitud.</span><span class="sxs-lookup"><span data-stu-id="63382-105">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="63382-106">DSC obligaba a usar contraseñas cortas, aunque se deseasen contraseñas largas y seguras.</span><span class="sxs-lookup"><span data-stu-id="63382-106">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="63382-107">Este cambio de última hora permite que las contraseñas tengan una longitud arbitraria en la configuración de DSC.</span><span class="sxs-lookup"><span data-stu-id="63382-107">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="63382-108">**Resolución:** vuelva a crear el certificado mediante el cifrado de datos o el cifrado de clave, así como con el uso mejorado de claves de cifrado de documentos (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="63382-108">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="63382-109">Para más información, consulte [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span><span class="sxs-lookup"><span data-stu-id="63382-109">For more information, see [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="63382-110">Los cmdlets de DSC puede producir un error después de instalar WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="63382-110">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="63382-111">`Start-DscConfiguration` y otros cmdlets de DSC pueden generar el siguiente error después de instalar WMF 5.0 RTM:</span><span class="sxs-lookup"><span data-stu-id="63382-111">`Start-DscConfiguration` and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

<span data-ttu-id="63382-112">**Resolución:** elimine DSCEngineCache.mof. Para ello, ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados (Ejecutar como administrador):</span><span class="sxs-lookup"><span data-stu-id="63382-112">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="63382-113">Es posible que los Cmdlets de DSC no funcionen si WMF 5.0 RTM se instala encima de WMF 5.0 Production Preview</span><span class="sxs-lookup"><span data-stu-id="63382-113">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="63382-114">**Resolución:** ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados (Ejecutar como administrador):</span><span class="sxs-lookup"><span data-stu-id="63382-114">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="63382-115">LCM puede entrar en un estado inestable al usar Get-DscConfiguration en DebugMode</span><span class="sxs-lookup"><span data-stu-id="63382-115">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="63382-116">Si LCM está en DebugMode, al presionar CTRL+C para detener el procesamiento de `Get-DscConfiguration` puede causar que LCM entre en un estado inestable que impida funcionar a la mayoría de los cmdlets de DSC.</span><span class="sxs-lookup"><span data-stu-id="63382-116">If LCM is in DebugMode, pressing CTRL+C to stop the processing of `Get-DscConfiguration` can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="63382-117">**Resolución:** No presione CTRL+C mientras depura el cmdlet `Get-DscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="63382-117">**Resolution:** Don’t press CTRL+C while debugging `Get-DscConfiguration` cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="63382-118">Stop-DscConfiguration puede no responder en DebugMode</span><span class="sxs-lookup"><span data-stu-id="63382-118">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="63382-119">Si LCM está en DebugMode, es posible que `Stop-DscConfiguration` no responde mientras se intenta detener una operación iniciada por `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="63382-119">If LCM is in DebugMode, `Stop-DscConfiguration` may not respond while trying to stop an operation started by `Get-DscConfiguration`</span></span>

<span data-ttu-id="63382-120">**Resolución:** Finalice la depuración de la operación iniciada por `Get-DscConfiguration` como se describe en [Depuración de recursos de DSC](/powershell/scripting/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="63382-120">**Resolution:** Finish the debugging of the operation started by `Get-DscConfiguration` as outlined in [Debugging DSC resources](/powershell/scripting/dsc/troubleshooting/debugResource).</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="63382-121">No se muestran mensajes de error detallados en DebugMode</span><span class="sxs-lookup"><span data-stu-id="63382-121">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="63382-122">Si LCM está en **DebugMode**, no se muestra ningún mensaje de error detallado de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="63382-122">If LCM is in **DebugMode**, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="63382-123">**Resolución:** deshabilite **DebugMode** para ver mensajes detallados del recurso</span><span class="sxs-lookup"><span data-stu-id="63382-123">**Resolution:** Disable **DebugMode** to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="63382-124">Las operaciones Invoke-DscResource no se pueden recuperar mediante el cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="63382-124">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="63382-125">Después de usar el cmdlet `Invoke-DscResource` para invocar directamente los métodos de cualquier recurso, los registros de dicha operación no se pueden recuperar a través de `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="63382-125">After using `Invoke-DscResource` cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through `Get-DscConfigurationStatus`.</span></span>

<span data-ttu-id="63382-126">**Resolución:** Ninguna.</span><span class="sxs-lookup"><span data-stu-id="63382-126">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="63382-127">Get-DscConfigurationStatus devuelve operaciones de ciclo de extracción como de tipo **Consistency**</span><span class="sxs-lookup"><span data-stu-id="63382-127">Get-DscConfigurationStatus returns pull cycle operations as type **Consistency**</span></span>

<span data-ttu-id="63382-128">Cuando un nodo se establece en modo de actualización de extracción, para cada operación de extracción realizada, el cmdlet `Get-DscConfigurationStatus` indica el tipo de operación como **Consistency** en lugar de *Initial*</span><span class="sxs-lookup"><span data-stu-id="63382-128">When a node is set to PULL refresh mode, for each pull operation performed, `Get-DscConfigurationStatus` cmdlet reports the operation type as **Consistency** instead of *Initial*</span></span>

<span data-ttu-id="63382-129">**Resolución:** Ninguna.</span><span class="sxs-lookup"><span data-stu-id="63382-129">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="63382-130">El cmdlet Invoke-DscResource no devuelve los mensajes en el orden en que se producen</span><span class="sxs-lookup"><span data-stu-id="63382-130">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="63382-131">El cmdlet `Invoke-DscResource` no devuelve los mensajes detallados, de advertencia ni de error en el orden en que los producen LCM o el recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="63382-131">The `Invoke-DscResource` cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="63382-132">**Resolución:** Ninguna.</span><span class="sxs-lookup"><span data-stu-id="63382-132">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="63382-133">Los recursos de DSC no se pueden depurar fácilmente cuando se usan con Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="63382-133">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="63382-134">Cuando LCM se ejecuta en modo de depuración, el cmdlet `Invoke-DscResource` no brinda información sobre el espacio de ejecución al cual conectarse para la depuración.</span><span class="sxs-lookup"><span data-stu-id="63382-134">When LCM is running in debug mode, `Invoke-DscResource` cmdlet does not give information about runspace to connect to for debugging.</span></span> <span data-ttu-id="63382-135">Para más información, consulte [Depuración de recursos de DSC](/powershell/scripting/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="63382-135">For more information, see [Debugging DSC resources](/powershell/scripting/dsc/troubleshooting/debugResource).</span></span>

<span data-ttu-id="63382-136">**Resolución:** Descubra el espacio de ejecución y conéctese a él mediante los cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` y `Debug-Runspace` para depurar el recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="63382-136">**Resolution:** Discover and attach to the runspace using cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` and `Debug-Runspace` to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="63382-137">Varios documentos de configuración parcial para el mismo nodo no pueden tener nombres de recurso idénticos</span><span class="sxs-lookup"><span data-stu-id="63382-137">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="63382-138">Para varias configuraciones parciales implementadas en un mismo nodo, los nombres idénticos de recursos causan un error en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="63382-138">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="63382-139">**Resolución:** use nombres diferentes para la mismos recursos en distintas configuraciones parciales.</span><span class="sxs-lookup"><span data-stu-id="63382-139">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="63382-140">Start-DscConfiguration –UseExisting no funciona con -Credential</span><span class="sxs-lookup"><span data-stu-id="63382-140">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="63382-141">Si se usa `Start-DscConfiguration` con el parámetro **UseExisting**, se omite el parámetro **Credential**.</span><span class="sxs-lookup"><span data-stu-id="63382-141">When using `Start-DscConfiguration` with **UseExisting** parameter, the **Credential** parameter is ignored.</span></span> <span data-ttu-id="63382-142">DSC usa la identidad de proceso predeterminada para continuar la operación.</span><span class="sxs-lookup"><span data-stu-id="63382-142">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="63382-143">Esto provoca un error cuando se necesita una credencial distinta para continuar en el nodo remoto.</span><span class="sxs-lookup"><span data-stu-id="63382-143">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="63382-144">**Resolución:** use una sesión CIM para las operaciones remotas de DSC:</span><span class="sxs-lookup"><span data-stu-id="63382-144">**Resolution:** Use CIM session for remote DSC operations:</span></span>

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="63382-145">Direcciones IPv6 como nombres de nodo en configuraciones de DSC</span><span class="sxs-lookup"><span data-stu-id="63382-145">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="63382-146">No se admiten direcciones IPv6 como nombres de nodo en los scripts de configuración de DSC en esta versión.</span><span class="sxs-lookup"><span data-stu-id="63382-146">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="63382-147">**Resolución:** Ninguna.</span><span class="sxs-lookup"><span data-stu-id="63382-147">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="63382-148">Depuración de recursos de DSC `Class-Based`</span><span class="sxs-lookup"><span data-stu-id="63382-148">Debugging of `Class-Based` DSC Resources</span></span>

<span data-ttu-id="63382-149">En esta versión no se admite la depuración de los recursos de DSC basado en clases.</span><span class="sxs-lookup"><span data-stu-id="63382-149">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="63382-150">**Resolución:** Ninguna.</span><span class="sxs-lookup"><span data-stu-id="63382-150">**Resolution:** None.</span></span>

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="63382-151">Las variables y las funciones que se definen en el ámbito de $script en el recurso basado en clases de DSC no se conservan en varias llamadas a un recurso de DSC</span><span class="sxs-lookup"><span data-stu-id="63382-151">Variables and functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="63382-152">Varias llamadas consecutivas a `Start-DSCConfiguration` producirán un error si la configuración usa cualquier recurso basado en clases que tenga variables o funciones definidas en el ámbito de `$script`.</span><span class="sxs-lookup"><span data-stu-id="63382-152">Multiple consecutive calls to `Start-DSCConfiguration` fails if the configuration is using any class-based resource which has variables or functions defined in `$script` scope.</span></span>

<span data-ttu-id="63382-153">**Resolución:** defina todas las variables y funciones de la propia clase de recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="63382-153">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="63382-154">No usar funciones o variables de ámbito `$script`.</span><span class="sxs-lookup"><span data-stu-id="63382-154">No `$script` scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="63382-155">Depuración de recursos de DSC cuando un recurso usa PSDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="63382-155">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="63382-156">La depuración de recursos de DSC cuando un recurso usa la propiedad **PSDscRunAsCredential** en la configuración no se admite en esta versión.</span><span class="sxs-lookup"><span data-stu-id="63382-156">DSC Resource debugging when a resource is using the **PSDscRunAsCredential** property in the configuration is not supported in this release.</span></span>

<span data-ttu-id="63382-157">**Resolución:** Ninguna.</span><span class="sxs-lookup"><span data-stu-id="63382-157">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="63382-158">PsDscRunAsCredential no se admite para los recursos compuestos de DSC</span><span class="sxs-lookup"><span data-stu-id="63382-158">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="63382-159">**Resolución:** use la propiedad Credential si está disponible.</span><span class="sxs-lookup"><span data-stu-id="63382-159">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="63382-160">ServiceSet y WindowsFeatureSet de ejemplo</span><span class="sxs-lookup"><span data-stu-id="63382-160">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="63382-161">Get-DscResource -Syntax no refleja PsDscRunAsCredential correctamente</span><span class="sxs-lookup"><span data-stu-id="63382-161">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="63382-162">El parámetro **Syntax** no refleja correctamente la propiedad **PsDscRunAsCredential** cuando el recurso la marca como obligatoria o no la admite.</span><span class="sxs-lookup"><span data-stu-id="63382-162">The **Syntax** parameter does not reflect **PsDscRunAsCredential** correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="63382-163">**Resolución:** Ninguna.</span><span class="sxs-lookup"><span data-stu-id="63382-163">**Resolution:** None.</span></span> <span data-ttu-id="63382-164">Sin embargo, la configuración de creación en ISE refleja los metadatos correctos acerca de la propiedad **PsDscRunAsCredential** al usar IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="63382-164">However, authoring configuration in ISE reflects correct metadata about **PsDscRunAsCredential** property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="63382-165">WindowsOptionalFeature no está disponible en Windows 7</span><span class="sxs-lookup"><span data-stu-id="63382-165">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="63382-166">El recurso de DSC **WindowsOptionalFeature** no está disponible en Windows 7.</span><span class="sxs-lookup"><span data-stu-id="63382-166">The **WindowsOptionalFeature** DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="63382-167">Este recurso requiere el módulo DISM, así como los cmdlets DISM que están disponibles a partir de Windows 8 y versiones más recientes del sistema operativo Windows.</span><span class="sxs-lookup"><span data-stu-id="63382-167">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="63382-168">En el caso de los recursos de DSC basados en clases, puede que Import-DscResource -ModuleVersion no funcione según lo previsto</span><span class="sxs-lookup"><span data-stu-id="63382-168">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="63382-169">Si el nodo de compilación tiene varias versiones de un módulo de recursos de DSC basados en clases, `Import-DscResource -ModuleVersion` no podrá seleccionar la versión especificada y genera el siguiente error de compilación.</span><span class="sxs-lookup"><span data-stu-id="63382-169">If the compilation node has multiple versions of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="63382-170">**Resolución:** importe la versión necesaria mediante la defición del objeto **ModuleSpecification** al parámetro **ModuleName** con la clave **RequiredVersion** especificada como sigue:</span><span class="sxs-lookup"><span data-stu-id="63382-170">**Resolution:** Import the required version by defining the **ModuleSpecification** object to the **ModuleName** parameter with **RequiredVersion** key specified as follows:</span></span>

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="63382-171">Algunos recursos de DSC, como el recurso de registro, pueden comenzar a tardar mucho tiempo en procesar la solicitud.</span><span class="sxs-lookup"><span data-stu-id="63382-171">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="63382-172">**Resolución 1:** cree una tarea de programación que limpie periódicamente la siguiente carpeta.</span><span class="sxs-lookup"><span data-stu-id="63382-172">**Resolution 1:** Create a schedule task that cleans up the following folder periodically.</span></span>

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="63382-173">**Resolución 2:** cambie la configuración de DSC para limpiar la carpeta *CommandAnalysis* al final de la configuración.</span><span class="sxs-lookup"><span data-stu-id="63382-173">**Resolution 2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

```powershell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
