---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954252"
---
# <a name="dsc-resources"></a><span data-ttu-id="a8bc3-103">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="a8bc3-103">DSC Resources</span></span>

><span data-ttu-id="a8bc3-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a8bc3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a8bc3-105">Los recursos de la configuración de estado deseado (DSC) ofrecen los bloques de creación para una configuración DSC.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="a8bc3-106">Un recurso expone las propiedades que se pueden configurar (el esquema) y contiene las funciones de script de PowerShell a las que el administrador de configuración local (LCM) llama para "que sea así".</span><span class="sxs-lookup"><span data-stu-id="a8bc3-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="a8bc3-107">Un recurso puede modelar algo tan genérico como un archivo o tan específico como una configuración de servidor IIS.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="a8bc3-108">Grupos de recursos similares se combinan en un módulo de DSC, que organiza todos los archivos necesarios en una estructura portátil que incluye los metadatos para identificar cómo están diseñados para usarse los recursos.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="a8bc3-109">Cada recurso tiene un \*esquema que determina la sintaxis necesaria para usar el recurso en una [configuración](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="a8bc3-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="a8bc3-110">El esquema de un recurso se puede definir de las siguientes maneras:</span><span class="sxs-lookup"><span data-stu-id="a8bc3-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="a8bc3-111">Archivo **"Schema.Mof"** : La mayoría de los recursos definen su *esquema* en un archivo "schema.mof", utilizando [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="a8bc3-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="a8bc3-112">Archivo **"\<Nombre de recurso\>.schema.psm1"** : Los [recursos compuestos](../configurations/compositeConfigs.md) definen su *esquema* en un archivo "<ResourceName>.schema.psm1" usando un [bloque de parámetros](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="a8bc3-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="a8bc3-113">Archivo **"\<Nombre de recurso\>.psm1"** : Los recursos DSC basados en clase definen su *esquema* en la definición de clase.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="a8bc3-114">Los elementos de sintaxis se denotan como propiedades de la clase.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="a8bc3-115">Para más información, consulte [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc) (Acerca de las clases).</span><span class="sxs-lookup"><span data-stu-id="a8bc3-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="a8bc3-116">Para recuperar la sintaxis de un recurso DSC, use el cmdlet [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) con el parámetro `-Syntax`.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="a8bc3-117">Este uso es similar al uso de [Get-Command](/powershell/module/microsoft.powershell.core/get-command) con el parámetro `-Syntax` para obtener la sintaxis del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="a8bc3-118">La salida que ve mostrará la plantilla utilizada para un bloque de recursos para el recurso que especifique.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="a8bc3-119">La salida que ve debe ser similar a la salida siguiente, aunque la sintaxis de este recurso podría cambiar en el futuro.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="a8bc3-120">Al igual que la sintaxis del cmdlet, las *claves* que aparecen entre corchetes son opcionales.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="a8bc3-121">Los tipos especifican el tipo de datos que espera cada clave.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="a8bc3-122">La clave **Ensure** es opcional porque el valor predeterminado es "Present".</span><span class="sxs-lookup"><span data-stu-id="a8bc3-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="a8bc3-123">Dentro de una configuración, un bloque de recursos **Service** podría parecerse a esto para aplicar **Ensure** en relación con la ejecución del servicio Spooler.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="a8bc3-124">Antes de usar un recurso en una configuración, debe importarlo mediante [Import-DSCResource](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="a8bc3-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="a8bc3-125">Las configuraciones pueden contener varias instancias del mismo tipo de recurso.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="a8bc3-126">Cada instancia debe tener un nombre exclusivo.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="a8bc3-127">En el siguiente ejemplo, se agrega un segundo bloque de recursos **Service** para configurar el servicio "DHCP".</span><span class="sxs-lookup"><span data-stu-id="a8bc3-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="a8bc3-128">A partir de PowerShell 5.0, se agregó Intellisense para DSC.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="a8bc3-129">Esta nueva característica permite usar \<TAB\> y \<Ctrl+barra espaciadora\> para completar automáticamente los nombres de clave.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Finalización con tabulación de recursos](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="a8bc3-131">Recursos integrados</span><span class="sxs-lookup"><span data-stu-id="a8bc3-131">Built-in resources</span></span>

<span data-ttu-id="a8bc3-132">Además de los recursos de la comunidad, hay recursos incorporados para Windows, para Linux y para la dependencia entre nodos.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="a8bc3-133">Puede usar los pasos anteriores para determinar la sintaxis de estos recursos y cómo usarlos.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="a8bc3-134">Las páginas relativas a estos recursos se han almacenado en **Referencia**.</span><span class="sxs-lookup"><span data-stu-id="a8bc3-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="a8bc3-135">Recursos integrados de Windows</span><span class="sxs-lookup"><span data-stu-id="a8bc3-135">Windows built-in resources</span></span>

* [<span data-ttu-id="a8bc3-136">Recurso Archive</span><span class="sxs-lookup"><span data-stu-id="a8bc3-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="a8bc3-137">Recurso Environment</span><span class="sxs-lookup"><span data-stu-id="a8bc3-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="a8bc3-138">Recurso File</span><span class="sxs-lookup"><span data-stu-id="a8bc3-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="a8bc3-139">Recurso Group</span><span class="sxs-lookup"><span data-stu-id="a8bc3-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="a8bc3-140">Recurso GroupSet</span><span class="sxs-lookup"><span data-stu-id="a8bc3-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="a8bc3-141">Recurso Log</span><span class="sxs-lookup"><span data-stu-id="a8bc3-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="a8bc3-142">Recurso Package</span><span class="sxs-lookup"><span data-stu-id="a8bc3-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="a8bc3-143">Recurso ProcessSet</span><span class="sxs-lookup"><span data-stu-id="a8bc3-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="a8bc3-144">Recurso Registry</span><span class="sxs-lookup"><span data-stu-id="a8bc3-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="a8bc3-145">Recurso Script</span><span class="sxs-lookup"><span data-stu-id="a8bc3-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="a8bc3-146">Recurso Service</span><span class="sxs-lookup"><span data-stu-id="a8bc3-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="a8bc3-147">Recurso ServiceSet</span><span class="sxs-lookup"><span data-stu-id="a8bc3-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="a8bc3-148">Recurso User</span><span class="sxs-lookup"><span data-stu-id="a8bc3-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="a8bc3-149">Recurso WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="a8bc3-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="a8bc3-150">Recurso WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="a8bc3-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="a8bc3-151">Recurso WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="a8bc3-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="a8bc3-152">Recurso WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="a8bc3-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="a8bc3-153">Recurso WindowsPackageCabResource</span><span class="sxs-lookup"><span data-stu-id="a8bc3-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="a8bc3-154">Recurso WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="a8bc3-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="a8bc3-155">Recursos de [dependencias entre nodos](../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="a8bc3-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="a8bc3-156">Recurso WaitForAll</span><span class="sxs-lookup"><span data-stu-id="a8bc3-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="a8bc3-157">Recurso WaitForSome</span><span class="sxs-lookup"><span data-stu-id="a8bc3-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="a8bc3-158">Recurso WaitForAny</span><span class="sxs-lookup"><span data-stu-id="a8bc3-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="a8bc3-159">Recursos de Administración de paquetes</span><span class="sxs-lookup"><span data-stu-id="a8bc3-159">Package Management resources</span></span>

* [<span data-ttu-id="a8bc3-160">Recurso PackageManagement</span><span class="sxs-lookup"><span data-stu-id="a8bc3-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="a8bc3-161">Recurso PackageManagementSource</span><span class="sxs-lookup"><span data-stu-id="a8bc3-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="a8bc3-162">Recursos de Linux</span><span class="sxs-lookup"><span data-stu-id="a8bc3-162">Linux resources</span></span>

* [<span data-ttu-id="a8bc3-163">Recurso Archive para Linux</span><span class="sxs-lookup"><span data-stu-id="a8bc3-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="a8bc3-164">Recurso Environment para Linux</span><span class="sxs-lookup"><span data-stu-id="a8bc3-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="a8bc3-165">Recurso FileLine para Linux</span><span class="sxs-lookup"><span data-stu-id="a8bc3-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="a8bc3-166">Recurso File para Linux</span><span class="sxs-lookup"><span data-stu-id="a8bc3-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="a8bc3-167">Recurso Group para Linux</span><span class="sxs-lookup"><span data-stu-id="a8bc3-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="a8bc3-168">Recurso Package para Linux</span><span class="sxs-lookup"><span data-stu-id="a8bc3-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="a8bc3-169">Recurso Script para Linux</span><span class="sxs-lookup"><span data-stu-id="a8bc3-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="a8bc3-170">Recurso Service para Linux</span><span class="sxs-lookup"><span data-stu-id="a8bc3-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="a8bc3-171">Recurso SshAuthorizedKeys para Linux</span><span class="sxs-lookup"><span data-stu-id="a8bc3-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="a8bc3-172">Recurso User para Linux</span><span class="sxs-lookup"><span data-stu-id="a8bc3-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
