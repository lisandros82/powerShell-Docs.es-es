---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Uso de Import-DSCResource
ms.openlocfilehash: f22c741969b1429074e7307a00a5c014cf563089
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265508"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="f070a-103">Uso de Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="f070a-103">Using Import-DSCResource</span></span>

<span data-ttu-id="f070a-104">`Import-DScResource` es una palabra clave dinámica, que solo se puede usar dentro de un bloque de script de configuración.</span><span class="sxs-lookup"><span data-stu-id="f070a-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="f070a-105">El `Import-DSCResource` palabra clave para importar todos los recursos necesarios en la configuración.</span><span class="sxs-lookup"><span data-stu-id="f070a-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="f070a-106">Recursos en `$phsome` se importan automáticamente, pero todavía se considera una práctica recomendada para importar de forma explícita todos los recursos utilizados en su [configuración](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="f070a-106">Resources under `$phsome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="f070a-107">La sintaxis de `Import-DSCResource` se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="f070a-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="f070a-108">Al especificar módulos por nombre, es un requisito para enumerar cada una en una nueva línea.</span><span class="sxs-lookup"><span data-stu-id="f070a-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|<span data-ttu-id="f070a-109">Parámetro</span><span class="sxs-lookup"><span data-stu-id="f070a-109">Parameter</span></span>  |<span data-ttu-id="f070a-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="f070a-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="f070a-111">Los nombres de recursos de DSC que se deben importar.</span><span class="sxs-lookup"><span data-stu-id="f070a-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="f070a-112">Si se especifica el nombre del módulo, el comando busca estos recursos de DSC en este módulo; en caso contrario, el comando busca los recursos de DSC en todas las rutas de acceso de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="f070a-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="f070a-113">Se admiten los caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="f070a-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="f070a-114">El nombre del módulo o especificación de módulo.</span><span class="sxs-lookup"><span data-stu-id="f070a-114">The module name, or module specification.</span></span>  <span data-ttu-id="f070a-115">Si especifica los recursos para importar desde un módulo, el comando intentará importar sólo esos recursos.</span><span class="sxs-lookup"><span data-stu-id="f070a-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="f070a-116">Si especifica solo el módulo, el comando importa todos los recursos de DSC en el módulo.</span><span class="sxs-lookup"><span data-stu-id="f070a-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="f070a-117">Ejemplo: Usar Import-DSCResource dentro de una configuración</span><span class="sxs-lookup"><span data-stu-id="f070a-117">Example: Use Import-DSCResource within a configuration</span></span>

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
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> <span data-ttu-id="f070a-118">No se admite especificar varios valores para los nombres de recursos y los nombres de los módulos en el mismo comando.</span><span class="sxs-lookup"><span data-stu-id="f070a-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="f070a-119">Puede tener un comportamiento no determinista sobre qué recursos se deben cargar desde qué módulo del mismo recurso si existe en varios módulos.</span><span class="sxs-lookup"><span data-stu-id="f070a-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="f070a-120">A continuación el comando producirá error durante la compilación.</span><span class="sxs-lookup"><span data-stu-id="f070a-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="f070a-121">Cosas a tener en cuenta cuando se usa solo el parámetro de nombre:</span><span class="sxs-lookup"><span data-stu-id="f070a-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="f070a-122">Es una operación que consume muchos recursos según el número de módulos instalados en el equipo.</span><span class="sxs-lookup"><span data-stu-id="f070a-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="f070a-123">Cargará el primer recurso que se encuentra con el nombre especificado.</span><span class="sxs-lookup"><span data-stu-id="f070a-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="f070a-124">En el caso donde hay más de un recurso con el mismo nombre que se instala, se pudo cargar el recurso incorrecto.</span><span class="sxs-lookup"><span data-stu-id="f070a-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="f070a-125">El uso recomendado consiste en especificar `–ModuleName` con el `-Name` parámetro, tal como se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="f070a-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="f070a-126">Este uso tiene las siguientes ventajas:</span><span class="sxs-lookup"><span data-stu-id="f070a-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="f070a-127">Reduce el impacto del rendimiento al limitar el ámbito de búsqueda para el recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="f070a-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="f070a-128">Define explícitamente el módulo de definición del recurso, asegurarse de que se carga el recurso correcto.</span><span class="sxs-lookup"><span data-stu-id="f070a-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="f070a-129">En PowerShell 5.0, los recursos de DSC pueden tener varias versiones, y las versiones pueden instalarse en un equipo en paralelo.</span><span class="sxs-lookup"><span data-stu-id="f070a-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="f070a-130">Esto se implementa mediante varias versiones de un módulo de recursos que están contenidas en la misma carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="f070a-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="f070a-131">Para más información, consulte [Uso de recursos con varias versiones](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="f070a-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="f070a-132">IntelliSense con Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="f070a-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="f070a-133">Al crear la configuración de DSC en el ISE, PowerShell proporciona IntelliSence para los recursos y las propiedades de recursos.</span><span class="sxs-lookup"><span data-stu-id="f070a-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="f070a-134">Las definiciones de recursos en el `$pshome` ruta de acceso del módulo se cargan automáticamente.</span><span class="sxs-lookup"><span data-stu-id="f070a-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="f070a-135">Al importar los recursos mediante el `Import-DSCResource` palabra clave, se agregan las definiciones de recursos especificado y Intellisense se expande para incluir el esquema del recurso importado.</span><span class="sxs-lookup"><span data-stu-id="f070a-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Intellisense de recursos](/media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="f070a-137">A partir de PowerShell 5.0, finalización con tabulación se ha agregado al ISE para los recursos de DSC y sus propiedades.</span><span class="sxs-lookup"><span data-stu-id="f070a-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="f070a-138">Para obtener más información, consulte [recursos](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="f070a-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="f070a-139">Al compilar la configuración, PowerShell usa las definiciones de recursos importados para validar todos los bloques de recursos en la configuración.</span><span class="sxs-lookup"><span data-stu-id="f070a-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="f070a-140">Se valida cada bloque de recursos, mediante la definición de esquema del recurso, para las siguientes reglas.</span><span class="sxs-lookup"><span data-stu-id="f070a-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="f070a-141">Se utilizan solo las propiedades definidas en el esquema.</span><span class="sxs-lookup"><span data-stu-id="f070a-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="f070a-142">Los tipos de datos para cada propiedad son correctos.</span><span class="sxs-lookup"><span data-stu-id="f070a-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="f070a-143">Propiedades de las claves se especifican.</span><span class="sxs-lookup"><span data-stu-id="f070a-143">Keys properties are specified.</span></span>
- <span data-ttu-id="f070a-144">No se usa ninguna propiedad de solo lectura.</span><span class="sxs-lookup"><span data-stu-id="f070a-144">No read-only property is used.</span></span>
- <span data-ttu-id="f070a-145">Asigna los tipos de validación en el valor.</span><span class="sxs-lookup"><span data-stu-id="f070a-145">Validation on value maps types.</span></span>

<span data-ttu-id="f070a-146">Tenga en cuenta la siguiente configuración:</span><span class="sxs-lookup"><span data-stu-id="f070a-146">Consider the following configuration:</span></span>

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
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

<span data-ttu-id="f070a-147">Compilar esta configuración da como resultado un error.</span><span class="sxs-lookup"><span data-stu-id="f070a-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="f070a-148">IntelliSense y validación de esquema permiten detectar más errores durante el tiempo de análisis y compilación, evitar las complicaciones en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="f070a-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="f070a-149">Cada recurso de DSC puede tener un nombre y un **FriendlyName** definido por el esquema del recurso.</span><span class="sxs-lookup"><span data-stu-id="f070a-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="f070a-150">A continuación se muestran las dos primeras líneas de "MSFT_ServiceResource.shema.mof".</span><span class="sxs-lookup"><span data-stu-id="f070a-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="f070a-151">Cuando se usa este recurso en una configuración, puede especificar **MSFT_ServiceResource** o **servicio**.</span><span class="sxs-lookup"><span data-stu-id="f070a-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="f070a-152">Diferencias de PowerShell v4 y v5</span><span class="sxs-lookup"><span data-stu-id="f070a-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="f070a-153">Hay varias diferencias que verá cuando se crean configuraciones en PowerShell 4.0 vs. PowerShell 5.0 y versiones posterior.</span><span class="sxs-lookup"><span data-stu-id="f070a-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="f070a-154">En esta sección se resaltan las diferencias que ve correspondientes a este artículo.</span><span class="sxs-lookup"><span data-stu-id="f070a-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="f070a-155">Varias versiones de recursos</span><span class="sxs-lookup"><span data-stu-id="f070a-155">Multiple Resource Versions</span></span>

<span data-ttu-id="f070a-156">Instalación y uso de varias versiones de los recursos en paralelo no se admiten en PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="f070a-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="f070a-157">Si observa problemas al importar recursos en la configuración, asegúrese de que solo tiene una versión del recurso instalado.</span><span class="sxs-lookup"><span data-stu-id="f070a-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="f070a-158">En la imagen siguiente, dos versiones de la **xPSDesiredStateConfiguration** módulo se instalan.</span><span class="sxs-lookup"><span data-stu-id="f070a-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Se ha corregido varias versiones de recursos](/media/multiple-resource-versions-broken.md)

<span data-ttu-id="f070a-160">Copie el contenido de la versión del módulo deseado en el nivel superior del directorio de módulo.</span><span class="sxs-lookup"><span data-stu-id="f070a-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Se ha corregido varias versiones de recursos](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a><span data-ttu-id="f070a-162">Ubicación de los recursos</span><span class="sxs-lookup"><span data-stu-id="f070a-162">Resource location</span></span>

<span data-ttu-id="f070a-163">Hora de crear y compilar configuraciones, los recursos se pueden almacenar en cualquier directorio especificado por su [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="f070a-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="f070a-164">El LCM en PowerShell 4.0, requiere que todos los módulos de recursos de DSC que se almacenará en "Programa Files\WindowsPowerShell\Modules" o `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="f070a-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="f070a-165">A partir de PowerShell 5.0, se ha quitado este requisito, y los módulos de recursos se pueden almacenar en cualquier directorio especificado por `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="f070a-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f070a-166">Vea también</span><span class="sxs-lookup"><span data-stu-id="f070a-166">See also</span></span>

- [<span data-ttu-id="f070a-167">Recursos</span><span class="sxs-lookup"><span data-stu-id="f070a-167">Resources</span></span>](../resources/resources.md)
