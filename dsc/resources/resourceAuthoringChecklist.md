---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Lista de comprobación de creación de recursos
ms.openlocfilehash: 7b1a096bba1b729c096b6689178ee022e12e4634
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076589"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="90772-103">Lista de comprobación de creación de recursos</span><span class="sxs-lookup"><span data-stu-id="90772-103">Resource authoring checklist</span></span>

<span data-ttu-id="90772-104">Esta lista de comprobación es una lista de procedimientos recomendados cuando se crea un nuevo recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="90772-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="90772-105">El módulo de recursos contiene los archivos .psd1 y schema.mof para cada recurso</span><span class="sxs-lookup"><span data-stu-id="90772-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>

<span data-ttu-id="90772-106">Compruebe que el recurso tiene la estructura correcta y que contiene todos los archivos requeridos.</span><span class="sxs-lookup"><span data-stu-id="90772-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="90772-107">Cada módulo de recursos debe contener un archivo. psd1 y todos los recursos no compuestos deben tener el archivo schema.mof.</span><span class="sxs-lookup"><span data-stu-id="90772-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="90772-108">No se enumerarán los recursos que no incluyan esquema por `Get-DscResource` y los usuarios no podrán usar Intellisense al escribir código en esos módulos en ISE.</span><span class="sxs-lookup"><span data-stu-id="90772-108">Resources that do not contain schema will not be listed by `Get-DscResource` and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span>
<span data-ttu-id="90772-109">La estructura de directorios del recurso xRemoteFile, que forma parte del [módulo de recursos xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), tiene el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="90772-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="90772-110">El recurso y el esquema son correctos</span><span class="sxs-lookup"><span data-stu-id="90772-110">Resource and schema are correct</span></span>

<span data-ttu-id="90772-111">Compruebe el archivo del esquema del recurso (\*. schema.mof).</span><span class="sxs-lookup"><span data-stu-id="90772-111">Verify the resource schema (\*.schema.mof) file.</span></span> <span data-ttu-id="90772-112">Puede usar el [Diseñador de recursos de DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) como ayuda para desarrollar y probar su esquema.</span><span class="sxs-lookup"><span data-stu-id="90772-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to help develop and test your schema.</span></span>
<span data-ttu-id="90772-113">Asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="90772-113">Make sure that:</span></span>

- <span data-ttu-id="90772-114">Los tipos de propiedad sean correctos (por ejemplo, no use String para propiedades que acepten valores numéricos; debe usar UInt32 u otros tipos numéricos en su lugar).</span><span class="sxs-lookup"><span data-stu-id="90772-114">Property types are correct (e.g. don’t use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="90772-115">Los atributos de propiedad se especifican correctamente como: ([key], [required], [write], [read])</span><span class="sxs-lookup"><span data-stu-id="90772-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="90772-116">Al menos un parámetro del esquema debe estar marcado como [key].</span><span class="sxs-lookup"><span data-stu-id="90772-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="90772-117">La propiedad [read] no coexiste con [required], [key] o [write]</span><span class="sxs-lookup"><span data-stu-id="90772-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="90772-118">Si se especifican varios calificadores excepto [read], [key] tiene prioridad.</span><span class="sxs-lookup"><span data-stu-id="90772-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="90772-119">Si [write] y [required] están especificados, tiene prioridad [required].</span><span class="sxs-lookup"><span data-stu-id="90772-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="90772-120">ValueMap esté especificado cuando sea necesario. Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="90772-120">ValueMap is specified where appropriate Example:</span></span>

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- <span data-ttu-id="90772-121">El nombre descriptivo esté especificado y cumpla con las convenciones de nomenclatura de DSC.</span><span class="sxs-lookup"><span data-stu-id="90772-121">Friendly name is specified and confirms to DSC naming conventions</span></span>

  <span data-ttu-id="90772-122">Ejemplo: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span><span class="sxs-lookup"><span data-stu-id="90772-122">Example: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span></span>

- <span data-ttu-id="90772-123">Cada campo tenga una descripción descriptiva.</span><span class="sxs-lookup"><span data-stu-id="90772-123">Every field has meaningful description.</span></span> <span data-ttu-id="90772-124">El repositorio GitHub de PowerShell tiene buenos ejemplos, como [.schema.mof para xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="90772-124">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="90772-125">Además, debe usar los cmdlets **Test-xDscResource** y **Test-xDscSchema** del [Diseñador de recursos de DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) para comprobar automáticamente el recurso y el esquema:</span><span class="sxs-lookup"><span data-stu-id="90772-125">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to automatically verify the resource and schema:</span></span>

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

<span data-ttu-id="90772-126">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="90772-126">For example:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="90772-127">El recurso se carga sin errores</span><span class="sxs-lookup"><span data-stu-id="90772-127">Resource loads without errors</span></span>

<span data-ttu-id="90772-128">Compruebe si el módulo de recursos se puede cargar correctamente.</span><span class="sxs-lookup"><span data-stu-id="90772-128">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="90772-129">Esta operación se puede realizar manualmente, para lo que hay que ejecutar `Import-Module <resource_module> -force` y confirmar que no se producen errores, o bien escribir la automatización de pruebas.</span><span class="sxs-lookup"><span data-stu-id="90772-129">This can be achieved manually, by running `Import-Module <resource_module> -force` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="90772-130">Si opta por este último método, puede seguir esta estructura en el caso de prueba:</span><span class="sxs-lookup"><span data-stu-id="90772-130">In case of the latter, you can follow this structure in your test case:</span></span>

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="90772-131">El recurso es idempotente en el caso positivo</span><span class="sxs-lookup"><span data-stu-id="90772-131">Resource is idempotent in the positive case</span></span>

<span data-ttu-id="90772-132">Una de las características fundamentales de los recursos de DSC es la idempotencia.</span><span class="sxs-lookup"><span data-stu-id="90772-132">One of the fundamental characteristics of DSC resources is idempotence.</span></span> <span data-ttu-id="90772-133">Esto significa que la aplicación de una configuración de DSC que contenga dicho recurso varias veces siempre logrará el mismo resultado.</span><span class="sxs-lookup"><span data-stu-id="90772-133">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="90772-134">Por ejemplo, si creamos una configuración que contenga el recurso File siguiente:</span><span class="sxs-lookup"><span data-stu-id="90772-134">For example, if we create a configuration which contains the following File resource:</span></span>

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

<span data-ttu-id="90772-135">Después de aplicarlo por primera vez, el archivo test.txt debería aparecer en la carpeta `C:\test`.</span><span class="sxs-lookup"><span data-stu-id="90772-135">After applying it for the first time, file test.txt should appear in `C:\test` folder.</span></span> <span data-ttu-id="90772-136">Sin embargo, las ejecuciones posteriores de la misma configuración no deben cambiar el estado de la máquina (por ejemplo, no deben crearse copias del archivo `test.txt`).</span><span class="sxs-lookup"><span data-stu-id="90772-136">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the `test.txt` file should be created).</span></span>
<span data-ttu-id="90772-137">Para garantizar que un recurso es idempotente, puede llamar a `Set-TargetResource` repetidas veces al probar el recurso directamente, o bien llamar a `Start-DscConfiguration` varias veces al realizar pruebas globales.</span><span class="sxs-lookup"><span data-stu-id="90772-137">To ensure a resource is idempotent you can repeatedly call `Set-TargetResource` when testing the resource directly, or call `Start-DscConfiguration` multiple times when doing end to end testing.</span></span> <span data-ttu-id="90772-138">El resultado debería ser el mismo después de cada ejecución.</span><span class="sxs-lookup"><span data-stu-id="90772-138">The result should be the same after every run.</span></span>

## <a name="test-user-modification-scenario"></a><span data-ttu-id="90772-139">Prueba de un escenario de modificación de un usuario</span><span class="sxs-lookup"><span data-stu-id="90772-139">Test user modification scenario</span></span>

<span data-ttu-id="90772-140">Si cambia el estado de la máquina y vuelve a ejecutar DSC, podrá comprobar que `Set-TargetResource` y `Test-TargetResource` funcionan correctamente.</span><span class="sxs-lookup"><span data-stu-id="90772-140">By changing the state of the machine and then rerunning DSC, you can verify that `Set-TargetResource` and `Test-TargetResource` function properly.</span></span> <span data-ttu-id="90772-141">Estos son los pasos que debe realizar:</span><span class="sxs-lookup"><span data-stu-id="90772-141">Here are steps you should take:</span></span>

1. <span data-ttu-id="90772-142">Comience con el recurso que no está en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="90772-142">Start with the resource not in the desired state.</span></span>
2. <span data-ttu-id="90772-143">Ejecute la configuración con su recurso.</span><span class="sxs-lookup"><span data-stu-id="90772-143">Run configuration with your resource</span></span>
3. <span data-ttu-id="90772-144">Compruebe que `Test-DscConfiguration` devuelve True</span><span class="sxs-lookup"><span data-stu-id="90772-144">Verify `Test-DscConfiguration` returns True</span></span>
4. <span data-ttu-id="90772-145">Modifique el elemento configurado para que no esté en el estado deseado</span><span class="sxs-lookup"><span data-stu-id="90772-145">Modify the configured item to be out of the desired state</span></span>
5. <span data-ttu-id="90772-146">Compruebe que `Test-DscConfiguration` devuelve False</span><span class="sxs-lookup"><span data-stu-id="90772-146">Verify `Test-DscConfiguration` returns false</span></span>

<span data-ttu-id="90772-147">Este es un ejemplo más concreto de uso del recurso Registry:</span><span class="sxs-lookup"><span data-stu-id="90772-147">Here’s a more concrete example using Registry resource:</span></span>

1. <span data-ttu-id="90772-148">Comience con la clave del Registro que no está en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="90772-148">Start with registry key not in the desired state</span></span>
2. <span data-ttu-id="90772-149">Ejecute `Start-DscConfiguration` con una configuración para colocarla en el estado deseado y compruebe si pasa.</span><span class="sxs-lookup"><span data-stu-id="90772-149">Run `Start-DscConfiguration` with a configuration to put it in the desired state and verify it passes.</span></span>
3. <span data-ttu-id="90772-150">Ejecute `Test-DscConfiguration` y compruebe que devuelve True</span><span class="sxs-lookup"><span data-stu-id="90772-150">Run `Test-DscConfiguration` and verify it returns true</span></span>
4. <span data-ttu-id="90772-151">Modifique el valor de la clave para que no esté en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="90772-151">Modify the value of the key so that it is not in the desired state</span></span>
5. <span data-ttu-id="90772-152">Ejecute `Test-DscConfiguration` y compruebe que devuelve False</span><span class="sxs-lookup"><span data-stu-id="90772-152">Run `Test-DscConfiguration` and verify it returns false</span></span>
6. <span data-ttu-id="90772-153">La funcionalidad `Get-TargetResource` se comprobó con `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="90772-153">`Get-TargetResource` functionality was verified using `Get-DscConfiguration`</span></span>

<span data-ttu-id="90772-154">`Get-TargetResource` debe devolver los detalles del estado actual del recurso.</span><span class="sxs-lookup"><span data-stu-id="90772-154">`Get-TargetResource` should return details of the current state of the resource.</span></span> <span data-ttu-id="90772-155">Asegúrese de probarlo, para lo que debe llamar a `Get-DscConfiguration` después de aplicar la configuración y comprobar que el resultado refleja correctamente el estado actual de la máquina.</span><span class="sxs-lookup"><span data-stu-id="90772-155">Make sure to test it by calling `Get-DscConfiguration` after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="90772-156">Es importante probarlo por separado, ya que los problemas de esta área no aparecerán al llamar a `Start-DscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="90772-156">It's important to test it separately, since any issues in this area won't appear when calling `Start-DscConfiguration`.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="90772-157">Llame a las funciones **Get/Set/Test-TargetResource** directamente</span><span class="sxs-lookup"><span data-stu-id="90772-157">Call **Get/Set/Test-TargetResource** functions directly</span></span>

<span data-ttu-id="90772-158">Asegúrese de probar las funciones **Get/Set/Test-TargetResource** implementadas en el recurso. Para ello, llámelas directamente y compruebe que funcionan según lo esperado.</span><span class="sxs-lookup"><span data-stu-id="90772-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="90772-159">Realice la comprobación global mediante **Start-DscConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="90772-159">Verify End to End using **Start-DscConfiguration**</span></span>

<span data-ttu-id="90772-160">Es importante llamar directamente a las funciones **Get/Set/Test-TargetResource** para probarlas, pero no todos los problemas se detectarán de esta forma.</span><span class="sxs-lookup"><span data-stu-id="90772-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="90772-161">Debe centrar una parte importante de las pruebas en el uso de `Start-DscConfiguration` o el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="90772-161">You should focus significant part of your testing on using `Start-DscConfiguration` or the pull server.</span></span> <span data-ttu-id="90772-162">De hecho, así es como los usuarios usarán el recurso, por lo que no subestime la importancia de este tipo de pruebas.</span><span class="sxs-lookup"><span data-stu-id="90772-162">In fact, this is how users will use the resource, so don’t underestimate the significance of this type of tests.</span></span>
<span data-ttu-id="90772-163">Posibles tipos de problemas:</span><span class="sxs-lookup"><span data-stu-id="90772-163">Possible types of issues:</span></span>

- <span data-ttu-id="90772-164">Es posible que Credential/Session se comporten de manera diferente porque el agente DSC se ejecuta como un servicio.</span><span class="sxs-lookup"><span data-stu-id="90772-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="90772-165">Asegúrese de probar todas las características aquí de un extremo a otro.</span><span class="sxs-lookup"><span data-stu-id="90772-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="90772-166">Los errores que produce `Start-DscConfiguration` pueden ser diferentes de los que se muestran al llamar a la función `Set-TargetResource` directamente.</span><span class="sxs-lookup"><span data-stu-id="90772-166">Errors output by `Start-DscConfiguration` may be different than those displayed when calling the `Set-TargetResource` function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="90772-167">Prueba de compatibilidad en todas las plataformas compatibles con DSC</span><span class="sxs-lookup"><span data-stu-id="90772-167">Test compatability on all DSC supported platforms</span></span>

<span data-ttu-id="90772-168">El recurso debería funcionar en todas las plataformas compatibles de DSC (Windows Server 2008 R2 y versiones más recientes).</span><span class="sxs-lookup"><span data-stu-id="90772-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="90772-169">Instalar la versión más reciente de WMF (Windows Management Framework) en el sistema operativo para obtener la versión más reciente de DSC.</span><span class="sxs-lookup"><span data-stu-id="90772-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="90772-170">Si el recurso no funciona en algunas de estas plataformas por diseño, debería devolverse un mensaje de error específico.</span><span class="sxs-lookup"><span data-stu-id="90772-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="90772-171">Asimismo, asegúrese de que el recurso comprueba si los cmdlets que está llamando están presentes en una máquina determinada.</span><span class="sxs-lookup"><span data-stu-id="90772-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="90772-172">En Windows Server 2012 se agregó un gran número de cmdlets nuevos que no están disponibles en Windows Server 2008 R2, incluso con WMF instalado.</span><span class="sxs-lookup"><span data-stu-id="90772-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="90772-173">Compruébelo en el cliente de Windows (si es aplicable)</span><span class="sxs-lookup"><span data-stu-id="90772-173">Verify on Windows Client (if applicable)</span></span>

<span data-ttu-id="90772-174">Una laguna muy común de las pruebas consiste en comprobar el recurso solo en las versiones de servidor de Windows.</span><span class="sxs-lookup"><span data-stu-id="90772-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="90772-175">Muchos recursos también están diseñados para funcionar en las SKU de cliente. Si es su caso, no olvide probarlo también en estas plataformas.</span><span class="sxs-lookup"><span data-stu-id="90772-175">Many resources are also designed to work on Client SKUs, so if that’s true in your case, don’t forget to test it on those platforms as well.</span></span>

## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="90772-176">Get-DSCResource enumera el recurso</span><span class="sxs-lookup"><span data-stu-id="90772-176">Get-DSCResource lists the resource</span></span>

<span data-ttu-id="90772-177">Después de implementar el módulo, una llamada a `Get-DscResource` debería enumerar su recurso, entre otros, como resultado.</span><span class="sxs-lookup"><span data-stu-id="90772-177">After deploying the module, calling `Get-DscResource` should list your resource among others as a result.</span></span> <span data-ttu-id="90772-178">Si no encuentra el recurso en la lista, asegúrese de que el archivo schema.mof de ese recurso existe.</span><span class="sxs-lookup"><span data-stu-id="90772-178">If you can’t find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>

## <a name="resource-module-contains-examples"></a><span data-ttu-id="90772-179">El módulo de recursos contiene ejemplos</span><span class="sxs-lookup"><span data-stu-id="90772-179">Resource module contains examples</span></span>

<span data-ttu-id="90772-180">La creación de ejemplos de calidad ayudará a otros usuarios a aprender a usarlo.</span><span class="sxs-lookup"><span data-stu-id="90772-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="90772-181">Esto es fundamental, sobre todo porque muchos usuarios tratan el código de ejemplo como documentación.</span><span class="sxs-lookup"><span data-stu-id="90772-181">This is crucial, especially since many users treat sample code as documentation.</span></span>

- <span data-ttu-id="90772-182">En primer lugar, debe determinar los ejemplos que se incluirán con el módulo; como mínimo, debe cubrir los casos de uso más importantes para el recurso:</span><span class="sxs-lookup"><span data-stu-id="90772-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="90772-183">Si el módulo contiene varios recursos que deben trabajar conjuntamente para un escenario de un extremo a otro, sería ideal que el ejemplo básico de un extremo a otro fuese primero.</span><span class="sxs-lookup"><span data-stu-id="90772-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="90772-184">Los ejemplos iniciales deben ser muy simples: cómo empezar a trabajar con los recursos en pequeños fragmentos manejables (por ejemplo, crear un nuevo VHD).</span><span class="sxs-lookup"><span data-stu-id="90772-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="90772-185">Los ejemplos siguientes deben basarse en esos ejemplos (por ejemplo, crear una VM a partir de un VHD, quitar la VM o modificarla) y mostrar una funcionalidad avanzada (por ejemplo, crear una VM con memoria dinámica).</span><span class="sxs-lookup"><span data-stu-id="90772-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="90772-186">Las configuraciones de ejemplo deben tener parámetros (todos los valores deben pasarse a la configuración como parámetros y no debería haber ningún valor codificado):</span><span class="sxs-lookup"><span data-stu-id="90772-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>

  ```powershell
  configuration Sample_xRemoteFile_DownloadFile
  {
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
  }
  ```

- <span data-ttu-id="90772-187">Es recomendable incluir un ejemplo (comentado) de cómo llamar a la configuración con los valores reales al final del script de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="90772-187">It’s a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span>
  <span data-ttu-id="90772-188">Por ejemplo, en la configuración anterior no es necesariamente obvio que la mejor forma de especificar UserAgent es:</span><span class="sxs-lookup"><span data-stu-id="90772-188">For example, in the configuration above it isn't necessarily obvious that the best way to specify UserAgent is:</span></span>

  <span data-ttu-id="90772-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` En cuyo caso un comentario puede clarificar la ejecución prevista de la configuración:</span><span class="sxs-lookup"><span data-stu-id="90772-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- <span data-ttu-id="90772-190">Para cada ejemplo, escriba una breve descripción que explique qué hace y el significado de los parámetros.</span><span class="sxs-lookup"><span data-stu-id="90772-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="90772-191">Asegúrese de que los ejemplos tratan la mayoría de los escenarios importantes para el recurso y, si no falta nada, compruebe que todos se ejecutan y coloque la máquina en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="90772-191">Make sure examples cover most the important scenarios for your resource and if there’s nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="90772-192">Los mensajes de error son fáciles de entender y ayudar a los usuarios a solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="90772-192">Error messages are easy to understand and help users solve problems</span></span>

<span data-ttu-id="90772-193">Los mensajes de error correctos deben:</span><span class="sxs-lookup"><span data-stu-id="90772-193">Good error messages should be:</span></span>

- <span data-ttu-id="90772-194">Existir: el principal problema de los mensajes de error es que a menudo no existen, por lo que debe asegurarse de que estén presentes.</span><span class="sxs-lookup"><span data-stu-id="90772-194">There: The biggest problem with error messages is that they often don’t exist, so make sure they are there.</span></span>
- <span data-ttu-id="90772-195">Fáciles de entender: usar lenguaje natural, sin códigos de error ilegibles.</span><span class="sxs-lookup"><span data-stu-id="90772-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="90772-196">Precisos: describir el problema con exactitud.</span><span class="sxs-lookup"><span data-stu-id="90772-196">Precise: Describe what’s exactly the problem</span></span>
- <span data-ttu-id="90772-197">Constructivos: aconsejar cómo corregir el problema.</span><span class="sxs-lookup"><span data-stu-id="90772-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="90772-198">Educados: no culpar al usuario ni hacerle sentir mal.</span><span class="sxs-lookup"><span data-stu-id="90772-198">Polite: Don’t blame user or make them feel bad</span></span>

<span data-ttu-id="90772-199">Asegúrese de comprobar los errores en los escenarios de un extremo a otro (mediante `Start-DscConfiguration`), ya que pueden diferir de los devueltos al ejecutar las funciones de recursos directamente.</span><span class="sxs-lookup"><span data-stu-id="90772-199">Make sure you verify errors in End to End scenarios (using `Start-DscConfiguration`), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="90772-200">Los mensajes de registro son fáciles de entender e informativos (incluidos los registros –verbose, –debug y ETW)</span><span class="sxs-lookup"><span data-stu-id="90772-200">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span>

<span data-ttu-id="90772-201">Asegúrese de que los registros que emite el recurso son fáciles de comprender y proporcionan valor al usuario.</span><span class="sxs-lookup"><span data-stu-id="90772-201">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="90772-202">Los recursos deben generar toda la información que pueda resultar útil para el usuario, pero un mayor número de registros no siempre es mejor.</span><span class="sxs-lookup"><span data-stu-id="90772-202">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="90772-203">Debe evitar la redundancia y la salida de datos que no proporcionen valor adicional: evite que nadie deba consultar cientos de entradas de registro para encontrar lo que busca.</span><span class="sxs-lookup"><span data-stu-id="90772-203">You should avoid redundancy and outputting data which does not provide additional value – don’t make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="90772-204">Por supuesto, la ausencia de registros tampoco es una solución aceptable para este problema.</span><span class="sxs-lookup"><span data-stu-id="90772-204">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="90772-205">Al realizar pruebas, también debe analizar los registros detallados y de depuración (ejecutando `Start-DscConfiguration` con los modificadores `–Verbose` y `–Debug`, respectivamente), así como los registros ETW.</span><span class="sxs-lookup"><span data-stu-id="90772-205">When testing, you should also analyze verbose and debug logs (by running `Start-DscConfiguration` with `–Verbose` and `–Debug` switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="90772-206">Para ver los registros de ETW de DSC, vaya al Visor de eventos y abra la carpeta siguiente: Applications and Services- Microsoft - Windows - Desired State Configuration.</span><span class="sxs-lookup"><span data-stu-id="90772-206">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="90772-207">De forma predeterminada, será Canal operativo, pero asegúrese de habilitar Canal analítico y Canal de depuración antes de ejecutar la configuración.</span><span class="sxs-lookup"><span data-stu-id="90772-207">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span>
<span data-ttu-id="90772-208">Para habilitar los canales analítico o de depuración, puede ejecutar el script siguiente:</span><span class="sxs-lookup"><span data-stu-id="90772-208">To enable Analytic/Debug channels, you can execute script below:</span></span>

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="90772-209">La implementación de recursos no contiene rutas de acceso codificadas</span><span class="sxs-lookup"><span data-stu-id="90772-209">Resource implementation does not contain hardcoded paths</span></span>

<span data-ttu-id="90772-210">Asegúrese de no hay ninguna ruta de codificada en la implementación de recursos, especialmente si adoptan el idioma (en-us) o si hay variables del sistema que se pueden usar.</span><span class="sxs-lookup"><span data-stu-id="90772-210">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="90772-211">Si el recurso necesita acceder a rutas de acceso específicas, use las variables de entorno en lugar de codificar la ruta de acceso, ya que puede diferir en otras máquinas.</span><span class="sxs-lookup"><span data-stu-id="90772-211">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="90772-212">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="90772-212">Example:</span></span>

<span data-ttu-id="90772-213">En lugar de:</span><span class="sxs-lookup"><span data-stu-id="90772-213">Instead of:</span></span>

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

<span data-ttu-id="90772-214">Puede escribir:</span><span class="sxs-lookup"><span data-stu-id="90772-214">You can write:</span></span>

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="90772-215">La implementación de recursos no contiene información de usuario</span><span class="sxs-lookup"><span data-stu-id="90772-215">Resource implementation does not contain user information</span></span>

<span data-ttu-id="90772-216">Asegúrese de que no hay nombres de correo electrónico, información de la cuenta o nombres de personas en el código.</span><span class="sxs-lookup"><span data-stu-id="90772-216">Make sure there are no email names, account information, or names of people in the code.</span></span>

## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="90772-217">El recurso se probó con credenciales válidas o no válidas</span><span class="sxs-lookup"><span data-stu-id="90772-217">Resource was tested with valid/invalid credentials</span></span>

<span data-ttu-id="90772-218">Si el recurso toma una credencial como parámetro:</span><span class="sxs-lookup"><span data-stu-id="90772-218">If your resource takes a credential as parameter:</span></span>

- <span data-ttu-id="90772-219">Compruebe que el recurso funciona cuando Sistema local (o la cuenta de equipo para los recursos remotos) no tiene acceso.</span><span class="sxs-lookup"><span data-stu-id="90772-219">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="90772-220">Compruebe que el recurso funciona con una credencial especificada para Get, Set y Test</span><span class="sxs-lookup"><span data-stu-id="90772-220">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="90772-221">Si el recurso accede a recursos compartidos, pruebe todas las variantes que necesite admitir, como:</span><span class="sxs-lookup"><span data-stu-id="90772-221">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="90772-222">Recursos compartidos de Windows estándar.</span><span class="sxs-lookup"><span data-stu-id="90772-222">Standard windows shares.</span></span>
  - <span data-ttu-id="90772-223">Recursos compartidos de DFS.</span><span class="sxs-lookup"><span data-stu-id="90772-223">DFS shares.</span></span>
  - <span data-ttu-id="90772-224">Recursos compartidos de SAMBA (si desea admitir Linux).</span><span class="sxs-lookup"><span data-stu-id="90772-224">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="90772-225">El recurso no requiere una entrada interactiva</span><span class="sxs-lookup"><span data-stu-id="90772-225">Resource does not require interactive input</span></span>

<span data-ttu-id="90772-226">Las funciones **Get/Set/Test-TargetResource** deben ejecutarse automáticamente y no deben esperar la entrada del usuario en ninguna fase de la ejecución (por ejemplo, no debe usar `Get-Credential`dentro de estas funciones).</span><span class="sxs-lookup"><span data-stu-id="90772-226">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user’s input at any stage of execution (e.g. you should not use `Get-Credential` inside these functions).</span></span> <span data-ttu-id="90772-227">Si la entrada del usuario es necesaria, debe pasarla a la configuración como un parámetro durante la fase de compilación.</span><span class="sxs-lookup"><span data-stu-id="90772-227">If you need to provide user’s input, you should pass it to the configuration as parameter during the compilation phase.</span></span>

## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="90772-228">La funcionalidad del recurso se probó de manera exhaustiva</span><span class="sxs-lookup"><span data-stu-id="90772-228">Resource functionality was thoroughly tested</span></span>

<span data-ttu-id="90772-229">Esta lista de comprobación contiene elementos que es importante probar y/o que suelen omitirse.</span><span class="sxs-lookup"><span data-stu-id="90772-229">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="90772-230">Se realizarán muchas pruebas, principalmente funcionales, que serán específicas para el recurso que se está probando y que no se mencionan aquí.</span><span class="sxs-lookup"><span data-stu-id="90772-230">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="90772-231">No olvide los casos de prueba negativos.</span><span class="sxs-lookup"><span data-stu-id="90772-231">Don’t forget about negative test cases.</span></span>

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="90772-232">Procedimiento recomendado: el módulo de recursos contiene la carpeta Tests con el script ResourceDesignerTests.ps1</span><span class="sxs-lookup"><span data-stu-id="90772-232">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span>

<span data-ttu-id="90772-233">Se recomienda crear la carpeta "Tests" en el módulo de recursos, crear el archivo `ResourceDesignerTests.ps1` y agregar pruebas mediante **Test-xDscResource** y **Test-xDscSchema** para todos los recursos del módulo determinado.</span><span class="sxs-lookup"><span data-stu-id="90772-233">It’s a good practice to create folder “Tests” inside resource module, create `ResourceDesignerTests.ps1` file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span>
<span data-ttu-id="90772-234">De este modo puede validar rápidamente los esquemas de todos los recursos de los módulos determinados y realizar una comprobación de integridad antes de la publicación.</span><span class="sxs-lookup"><span data-stu-id="90772-234">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="90772-235">Para xRemoteFile, `ResourceTests.ps1` podría ser tan simple como:</span><span class="sxs-lookup"><span data-stu-id="90772-235">For xRemoteFile, `ResourceTests.ps1` could look as simple as:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="90772-236">Procedimiento recomendado: la carpeta de recursos contiene el script del Diseñador de recursos para generar el esquema</span><span class="sxs-lookup"><span data-stu-id="90772-236">Best practice: Resource folder contains resource designer script for generating schema</span></span>

<span data-ttu-id="90772-237">Cada recurso debe contener un script del Diseñador de recursos que genere un esquema MOF del recurso.</span><span class="sxs-lookup"><span data-stu-id="90772-237">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="90772-238">Este archivo debe colocarse en `<ResourceName>\ResourceDesignerScripts` y denominarse Generate`<ResourceName>Schema.ps1` Para el recurso xRemoteFile, este archivo se llamaría `GenerateXRemoteFileSchema.ps1` y contendría:</span><span class="sxs-lookup"><span data-stu-id="90772-238">This file should be placed in `<ResourceName>\ResourceDesignerScripts` and be named Generate `<ResourceName>Schema.ps1` For xRemoteFile resource this file would be called `GenerateXRemoteFileSchema.ps1` and contain:</span></span>

```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```

## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="90772-239">Procedimiento recomendado: el recurso admite -whatif</span><span class="sxs-lookup"><span data-stu-id="90772-239">Best practice: Resource supports -WhatIf</span></span>

<span data-ttu-id="90772-240">Si el recurso realiza operaciones "peligrosas", se recomienda implementar la funcionalidad `-WhatIf`.</span><span class="sxs-lookup"><span data-stu-id="90772-240">If your resource is performing “dangerous” operations, it’s a good practice to implement `-WhatIf` functionality.</span></span> <span data-ttu-id="90772-241">Después de hacerlo, asegúrese de que la salida `-WhatIf` describe correctamente las operaciones que se realizarían si se ejecutara el comando sin el modificador `-WhatIf`.</span><span class="sxs-lookup"><span data-stu-id="90772-241">After it’s done, make sure that `-WhatIf` output correctly describes operations which would happen if command was executed without `-WhatIf` switch.</span></span>
<span data-ttu-id="90772-242">Asimismo, compruebe que las operaciones no se ejecutan (no se realiza ningún cambio en el estado del nodo) cuando el modificador`–WhatIf` está presente.</span><span class="sxs-lookup"><span data-stu-id="90772-242">Also, verify that operations does not execute (no changes to the node’s state are made) when `–WhatIf` switch is present.</span></span>
<span data-ttu-id="90772-243">Por ejemplo, supongamos que está probando el recurso File.</span><span class="sxs-lookup"><span data-stu-id="90772-243">For example, let’s assume we are testing File resource.</span></span> <span data-ttu-id="90772-244">A continuación se muestra una configuración sencilla que crea el archivo `test.txt` con contenido "test":</span><span class="sxs-lookup"><span data-stu-id="90772-244">Below is simple configuration which creates file `test.txt` with contents “test”:</span></span>

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

<span data-ttu-id="90772-245">Si compilamos y, después, ejecutamos la configuración con el modificador `-WhatIf`, la salida nos indica qué ocurre exactamente cuando ejecutamos la configuración.</span><span class="sxs-lookup"><span data-stu-id="90772-245">If we compile and then execute the configuration with the `-WhatIf` switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="90772-246">Sin embargo, no se ejecutó la configuración en sí (no se creó el archivo `test.txt`).</span><span class="sxs-lookup"><span data-stu-id="90772-246">The configuration itself however was not executed (`test.txt` file was not created).</span></span>

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="90772-247">Esta lista no es exhaustiva, pero abarca muchos problemas importantes que se pueden detectar durante el diseño, el desarrollo y las pruebas de los recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="90772-247">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>
