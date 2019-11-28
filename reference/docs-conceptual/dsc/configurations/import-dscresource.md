---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Uso de Import-DSCResource
ms.openlocfilehash: 4bc269ab1dd4696298b4f33f7661473aae869eba
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417428"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="5a5c4-103">Uso de Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="5a5c4-103">Using Import-DSCResource</span></span>

<span data-ttu-id="5a5c4-104">`Import-DScResource` es una palabra clave dinámica, que solo se puede usar dentro de un bloque de script de configuración.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="5a5c4-105">La palabra clave `Import-DSCResource` para importar los recursos necesarios en la configuración.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="5a5c4-106">Los recursos en `$pshome` se importan automáticamente, pero se sigue considerando recomendable importar de forma explícita todos los recursos utilizados en su [configuración](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="5a5c4-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="5a5c4-107">La sintaxis de `Import-DSCResource` se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="5a5c4-108">Al especificar módulos por nombre, es necesario enumerar cada uno en una nueva línea.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|<span data-ttu-id="5a5c4-109">Parámetro</span><span class="sxs-lookup"><span data-stu-id="5a5c4-109">Parameter</span></span>  |<span data-ttu-id="5a5c4-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="5a5c4-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="5a5c4-111">Los nombres de recursos de DSC que debe importar.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="5a5c4-112">Si se especifica el nombre del módulo, el comando busca estos recursos de DSC en este módulo; en caso contrario, el comando busca los recursos de DSC en todas las rutas de acceso de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="5a5c4-113">Se admiten los caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="5a5c4-114">El nombre del módulo, o especificación de módulo.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-114">The module name, or module specification.</span></span>  <span data-ttu-id="5a5c4-115">Si especifica los recursos para importar desde un módulo, el comando intentará importar solo esos recursos.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="5a5c4-116">Si especifica solo el módulo, el comando importa todos los recursos de DSC en el módulo.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|
|`-ModuleVersion`|<span data-ttu-id="5a5c4-117">A partir de PowerShell 5.0, puede especificar la versión de un módulo que debería usar una configuración.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-117">Beginning in PowerShell 5.0, you can specify which version of a module a configuration should use.</span></span> <span data-ttu-id="5a5c4-118">Para obtener más información, vea [Importación de una versión específica de un recurso instalado](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="5a5c4-118">For more information, see [Import a specific version of an installed resource](sxsresource.md).</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="5a5c4-119">Ejemplo: Uso de Import-DSCResource dentro de una configuración</span><span class="sxs-lookup"><span data-stu-id="5a5c4-119">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    # In PowerShell 5.0 and later, you can specify a ModuleVersion parameter
    Import-DSCResource -ModuleName ComputerManagementDsc -ModuleVersion 6.0.0.0
...
```

> [!NOTE]
> <span data-ttu-id="5a5c4-120">No se admite la especificación de varios valores para los nombres de recursos y los nombres de los módulos en el mismo comando.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-120">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="5a5c4-121">Puede tener un comportamiento no determinista sobre qué recurso se debe cargar desde qué módulo si existe el mismo recurso en varios módulos.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-121">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="5a5c4-122">El comando siguiente producirá error durante la compilación.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-122">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="5a5c4-123">Aspectos para tener en cuenta cuando se usa solo el parámetro de nombre:</span><span class="sxs-lookup"><span data-stu-id="5a5c4-123">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="5a5c4-124">Es una operación que consume muchos recursos, dependiendo del número de módulos instalados en el equipo.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-124">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="5a5c4-125">Cargará el primer recurso que se encuentre con el nombre especificado.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-125">It will load the first resource found with the given name.</span></span> <span data-ttu-id="5a5c4-126">En caso de que haya instalado más de un recurso con el mismo nombre, podría cargarse el recurso incorrecto.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-126">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="5a5c4-127">El uso recomendado consiste en especificar `–ModuleName` con el parámetro `-Name`, tal como se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-127">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="5a5c4-128">Este uso tiene las siguientes ventajas:</span><span class="sxs-lookup"><span data-stu-id="5a5c4-128">This usage has the following benefits:</span></span>

- <span data-ttu-id="5a5c4-129">Reduce el impacto del rendimiento al limitar el ámbito de búsqueda para el recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-129">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="5a5c4-130">Define explícitamente el módulo que define del recurso, garantizando que se carga el recurso correcto.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-130">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="5a5c4-131">En PowerShell 5.0, los recursos de DSC pueden tener varias versiones, y las versiones pueden instalarse en un equipo en paralelo.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-131">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="5a5c4-132">Esto se implementa mediante varias versiones de un módulo de recursos que están contenidas en la misma carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-132">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="5a5c4-133">Para más información, consulte [Uso de recursos con varias versiones](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="5a5c4-133">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="5a5c4-134">IntelliSense con Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="5a5c4-134">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="5a5c4-135">Al crear la configuración de DSC en el ISE, PowerShell proporciona IntelliSence para los recursos y las propiedades de recursos.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-135">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="5a5c4-136">Las definiciones de recursos en la ruta de acceso del módulo `$pshome` se cargan automáticamente.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-136">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="5a5c4-137">Al importar los recursos mediante la palabra clave `Import-DSCResource`, se agregan las definiciones de recursos especificadas e Intellisense se expande para incluir el esquema del recurso importado.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-137">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Intellisense para recursos](../media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="5a5c4-139">A partir de PowerShell 5.0, se agregó la finalización con tabulación al ISE para los recursos de DSC y sus propiedades.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-139">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="5a5c4-140">Para obtener más información, consulte [Recursos](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="5a5c4-140">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="5a5c4-141">Al compilar la configuración, PowerShell usa las definiciones de recursos importados para validar todos los bloques de recursos en la configuración.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-141">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="5a5c4-142">Cada bloque de recursos se valida mediante la definición de esquema de recursos, para las siguientes reglas.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-142">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="5a5c4-143">Se utilizan solo las propiedades definidas en el esquema.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-143">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="5a5c4-144">Los tipos de datos para cada propiedad son correctos.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-144">The data types for each property are correct.</span></span>
- <span data-ttu-id="5a5c4-145">Se especifican las propiedades de las claves.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-145">Keys properties are specified.</span></span>
- <span data-ttu-id="5a5c4-146">No se usa ninguna propiedad de solo lectura.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-146">No read-only property is used.</span></span>
- <span data-ttu-id="5a5c4-147">La validación sobre el valor asigna tipos.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-147">Validation on value maps types.</span></span>

<span data-ttu-id="5a5c4-148">Tenga en cuenta la siguiente configuración:</span><span class="sxs-lookup"><span data-stu-id="5a5c4-148">Consider the following configuration:</span></span>

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = "Telnet-Client"
            Ensure = "Invalid"
        }
    }
}
```

<span data-ttu-id="5a5c4-149">La compilación de esta configuración da como resultado un error.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-149">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="5a5c4-150">IntelliSense y la validación de esquema permiten detectar más errores durante el tiempo de análisis y compilación, evitando las complicaciones en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-150">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="5a5c4-151">Cada recurso de DSC puede tener un nombre y un **FriendlyName** definido por el esquema del recurso.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-151">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="5a5c4-152">A continuación se muestran las dos primeras líneas de "MSFT_ServiceResource.shema.mof".</span><span class="sxs-lookup"><span data-stu-id="5a5c4-152">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="5a5c4-153">Cuando se usa este recurso en una configuración, puede especificar **MSFT_ServiceResource** o **Service**.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-153">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="5a5c4-154">Diferencias de PowerShell v4 y v5</span><span class="sxs-lookup"><span data-stu-id="5a5c4-154">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="5a5c4-155">Hay varias diferencias que verá al crear configuraciones en PowerShell 4.0 en comparación con Windows PowerShell 5.0 y posteriores.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-155">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="5a5c4-156">En esta sección se destacan las diferencias que verá y que son pertinentes para este artículo.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-156">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="5a5c4-157">Varias versiones de recursos</span><span class="sxs-lookup"><span data-stu-id="5a5c4-157">Multiple Resource Versions</span></span>

<span data-ttu-id="5a5c4-158">La instalación y el uso de varias versiones de recursos en paralelo no se admite en PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-158">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="5a5c4-159">Si observa problemas al importar recursos en la configuración, asegúrese de que solo tiene una versión del recurso instalada.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-159">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="5a5c4-160">En la imagen siguiente, se instalan dos versiones del módulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-160">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Corrección de varias versiones de recursos](../media/multiple-resource-versions-broken.png)

<span data-ttu-id="5a5c4-162">Copie el contenido de la versión del módulo deseada en el nivel superior del directorio de módulo.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-162">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Corrección de varias versiones de recursos](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="5a5c4-164">Ubicación de los recursos</span><span class="sxs-lookup"><span data-stu-id="5a5c4-164">Resource location</span></span>

<span data-ttu-id="5a5c4-165">Al crear y compilar configuraciones, los recursos se pueden almacenar en cualquier directorio especificado por su [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="5a5c4-165">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="5a5c4-166">En PowerShell 4.0, LCM requiere que todos los módulos de recursos de DSC se almacenen en "Archivos de programa\WindowsPowerShell\Modules" o `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-166">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="5a5c4-167">A partir de PowerShell 5.0, esto ya no es necesario, y los módulos de recursos se pueden almacenar en cualquier directorio especificado por `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-167">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

### <a name="moduleversion-added"></a><span data-ttu-id="5a5c4-168">Agregado el parámetro ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="5a5c4-168">ModuleVersion added</span></span>

<span data-ttu-id="5a5c4-169">A partir de PowerShell 5.0, el parámetro `-ModuleVersion` le permite especificar la versión de un módulo que va a usar en la configuración.</span><span class="sxs-lookup"><span data-stu-id="5a5c4-169">Beginning in PowerShell 5.0, the `-ModuleVersion` parameter allows you to specify which version of a module to use within your configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a5c4-170">Vea también</span><span class="sxs-lookup"><span data-stu-id="5a5c4-170">See also</span></span>

- [<span data-ttu-id="5a5c4-171">Recursos</span><span class="sxs-lookup"><span data-stu-id="5a5c4-171">Resources</span></span>](../resources/resources.md)
