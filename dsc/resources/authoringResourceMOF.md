---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Escribir un recurso de DSC personalizado con MOF
ms.openlocfilehash: f243c3e3297711e6f6346a0f813a9c017fe227c3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2019
ms.locfileid: "58059735"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="bc044-103">Escribir un recurso de DSC personalizado con MOF</span><span class="sxs-lookup"><span data-stu-id="bc044-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="bc044-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bc044-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="bc044-105">En este tema se define el esquema de un recurso personalizado de configuración de estado deseado (DSC) de Windows PowerShell en un archivo MOF y se implementa el recurso en un archivo de script de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc044-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="bc044-106">Este recurso personalizado es para la creación y el mantenimiento de un sitio web.</span><span class="sxs-lookup"><span data-stu-id="bc044-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="bc044-107">Crear el esquema MOF</span><span class="sxs-lookup"><span data-stu-id="bc044-107">Creating the MOF schema</span></span>

<span data-ttu-id="bc044-108">El esquema define las propiedades del recurso que se pueden configurar mediante un script de configuración DSC.</span><span class="sxs-lookup"><span data-stu-id="bc044-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="bc044-109">Estructura de carpetas de un recurso MOF</span><span class="sxs-lookup"><span data-stu-id="bc044-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="bc044-110">Para implementar un recurso de DSC personalizado con un esquema MOF, cree la siguiente estructura de carpetas.</span><span class="sxs-lookup"><span data-stu-id="bc044-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="bc044-111">El esquema MOF se define en el archivo Demo_IISWebsite.schema.mof y el script del recurso se define en Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="bc044-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="bc044-112">Opcionalmente, puede crear un archivo de manifiesto del módulo (psd1).</span><span class="sxs-lookup"><span data-stu-id="bc044-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="bc044-113">Tenga en cuenta que es necesario crear una carpeta denominada DSCResources en la carpeta de nivel superior y que la carpeta de cada recurso debe tener el mismo nombre que el recurso.</span><span class="sxs-lookup"><span data-stu-id="bc044-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="bc044-114">Contenido del archivo MOF</span><span class="sxs-lookup"><span data-stu-id="bc044-114">The contents of the MOF file</span></span>

<span data-ttu-id="bc044-115">A continuación se muestra un ejemplo de un archivo MOF que se puede utilizar para un recurso de sitio web personalizado.</span><span class="sxs-lookup"><span data-stu-id="bc044-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="bc044-116">Para seguir este ejemplo, guarde este esquema en un archivo y asigne como nombre del archivo *Demo_IISWebsite.schema.mof*.</span><span class="sxs-lookup"><span data-stu-id="bc044-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

<span data-ttu-id="bc044-117">Tenga en cuenta lo siguiente sobre el código anterior:</span><span class="sxs-lookup"><span data-stu-id="bc044-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="bc044-118">`FriendlyName` define el nombre que se puede utilizar para hacer referencia a este recurso personalizado en los scripts de configuración DSC.</span><span class="sxs-lookup"><span data-stu-id="bc044-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="bc044-119">En este ejemplo, `Website` equivale al nombre descriptivo `Archive` para el recurso integrado Archive.</span><span class="sxs-lookup"><span data-stu-id="bc044-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="bc044-120">La clase que defina para el recurso personalizado debe derivarse de `OMI_BaseResource`.</span><span class="sxs-lookup"><span data-stu-id="bc044-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="bc044-121">El calificador de tipo, `[Key]`, en una propiedad indica que esta propiedad identificará de forma única la instancia del recurso.</span><span class="sxs-lookup"><span data-stu-id="bc044-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="bc044-122">Se necesita al menos una propiedad `[Key]`.</span><span class="sxs-lookup"><span data-stu-id="bc044-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="bc044-123">El calificador `[Required]` indica que la propiedad es obligatoria (debe especificarse un valor en cualquier script de configuración que use este recurso).</span><span class="sxs-lookup"><span data-stu-id="bc044-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="bc044-124">El calificador `[write]` indica que esta propiedad es opcional cuando se utiliza el recurso personalizado en un script de configuración.</span><span class="sxs-lookup"><span data-stu-id="bc044-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="bc044-125">El calificador `[read]` indica que una propiedad no se puede establecer mediante una configuración y es solo con fines informativos.</span><span class="sxs-lookup"><span data-stu-id="bc044-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="bc044-126">`Values` restringe los valores que se pueden asignar a la propiedad a la lista de valores definidos en `ValueMap`.</span><span class="sxs-lookup"><span data-stu-id="bc044-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="bc044-127">Para más información, consulte [Calificadores Value y ValueMap](/windows/desktop/WmiSdk/value-map).</span><span class="sxs-lookup"><span data-stu-id="bc044-127">For more information, see [ValueMap and Value Qualifiers](/windows/desktop/WmiSdk/value-map).</span></span>
* <span data-ttu-id="bc044-128">Se recomienda incluir una propiedad denominada `Ensure` con los valores `Present` y `Absent` en el recurso como una forma de mantener un estilo coherente con los recursos integrados de DSC.</span><span class="sxs-lookup"><span data-stu-id="bc044-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="bc044-129">Asigne el nombre del archivo de esquema para el recurso personalizado de la siguiente forma: `classname.schema.mof`, donde `classname` es el identificador que sigue a la palabra clave `class` en la definición del esquema.</span><span class="sxs-lookup"><span data-stu-id="bc044-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="bc044-130">Escribir el script del recurso</span><span class="sxs-lookup"><span data-stu-id="bc044-130">Writing the resource script</span></span>

<span data-ttu-id="bc044-131">El script del recurso implementa la lógica del recurso.</span><span class="sxs-lookup"><span data-stu-id="bc044-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="bc044-132">En este módulo, debe incluir tres funciones llamadas **Get-TargetResource**, **Set-TargetResource** y **Test-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="bc044-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="bc044-133">Las tres funciones deben tomar un conjunto de parámetros que sea idéntico al conjunto de propiedades definidas en el esquema MOF que creó para el recurso.</span><span class="sxs-lookup"><span data-stu-id="bc044-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="bc044-134">En este documento, este conjunto de propiedades se conoce como "propiedades del recurso".</span><span class="sxs-lookup"><span data-stu-id="bc044-134">In this document, this set of properties is referred to as the “resource properties.”</span></span> <span data-ttu-id="bc044-135">Almacene estas tres funciones en un archivo denominado <ResourceName>.psm1.</span><span class="sxs-lookup"><span data-stu-id="bc044-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="bc044-136">En el ejemplo siguiente, las funciones se almacenan en un archivo denominado Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="bc044-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> [!NOTE]
> <span data-ttu-id="bc044-137">Al ejecutar el mismo script de configuración en el recurso más de una vez, no se deberían obtener errores. Asimismo, el recurso debería permanecer en el mismo estado que si se hubiera ejecutado el script una vez.</span><span class="sxs-lookup"><span data-stu-id="bc044-137">When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="bc044-138">Para lograrlo, asegúrese de que las funciones **Get-TargetResource** y **Test-TargetResource** no modifiquen el recurso y de que la invocación de la función **Set-TargetResource** más de una vez en una secuencia con los mismos valores de los parámetros sea siempre equivalente a invocarla una vez.</span><span class="sxs-lookup"><span data-stu-id="bc044-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="bc044-139">En la implementación de la función **Get-TargetResource**, utilice los valores de propiedades clave del recurso que se proporcionan como parámetros para comprobar el estado de la instancia del recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="bc044-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="bc044-140">Esta función debe devolver una tabla hash que enumere todas las propiedades del recurso como claves y los valores reales de estas propiedades como los valores correspondientes.</span><span class="sxs-lookup"><span data-stu-id="bc044-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="bc044-141">En el código siguiente se muestra un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="bc044-141">The following code provides an example.</span></span>

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }

        $getTargetResourceResult;
}
```

<span data-ttu-id="bc044-142">Según los valores especificados para las propiedades del recurso en el script de configuración, la función **Set-TargetResource** debe realizar una de las siguientes acciones:</span><span class="sxs-lookup"><span data-stu-id="bc044-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="bc044-143">Crear un sitio web.</span><span class="sxs-lookup"><span data-stu-id="bc044-143">Create a new website</span></span>
* <span data-ttu-id="bc044-144">Actualizar un sitio web existente.</span><span class="sxs-lookup"><span data-stu-id="bc044-144">Update an existing website</span></span>
* <span data-ttu-id="bc044-145">Eliminar un sitio web existente.</span><span class="sxs-lookup"><span data-stu-id="bc044-145">Delete an existing website</span></span>

<span data-ttu-id="bc044-146">En el ejemplo siguiente se ilustra esto.</span><span class="sxs-lookup"><span data-stu-id="bc044-146">The following example illustrates this.</span></span>

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

<span data-ttu-id="bc044-147">Por último, la función **Test-TargetResource** debe tomar el mismo parámetro establecido que **Get-TargetResource** y **Set-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="bc044-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="bc044-148">En la implementación de **Test-TargetResource**, compruebe el estado de la instancia del recurso que se especifica en los parámetros clave.</span><span class="sxs-lookup"><span data-stu-id="bc044-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="bc044-149">Si el estado real de la instancia del recurso no coincide con los valores especificados en el conjunto de parámetros, devuelva **$false**.</span><span class="sxs-lookup"><span data-stu-id="bc044-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="bc044-150">De lo contrario, devuelva **$true**.</span><span class="sxs-lookup"><span data-stu-id="bc044-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="bc044-151">El código siguiente implementa la función **Test-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="bc044-151">The following code implements the **Test-TargetResource** function.</span></span>

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

<span data-ttu-id="bc044-152">**Nota**: Para una depuración más sencilla, utilice el cmdlet **Write-Verbose** en la implementación de las tres funciones anteriores.</span><span class="sxs-lookup"><span data-stu-id="bc044-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span>
><span data-ttu-id="bc044-153">Este cmdlet escribe texto en la secuencia de mensajes detallados.</span><span class="sxs-lookup"><span data-stu-id="bc044-153">This cmdlet writes text to the verbose message stream.</span></span>
><span data-ttu-id="bc044-154">De forma predeterminada, la secuencia de mensajes detallados no se muestra, pero se puede mostrar si se cambia el valor de la variable **$VerbosePreference** o se usa el parámetro **Verbose** en los cmdlets de DSC = new.</span><span class="sxs-lookup"><span data-stu-id="bc044-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="bc044-155">Crear el manifiesto del módulo</span><span class="sxs-lookup"><span data-stu-id="bc044-155">Creating the module manifest</span></span>

<span data-ttu-id="bc044-156">Por último, utilice el cmdlet **New-ModuleManifest** para definir un archivo <ResourceName>.psd1 para el módulo de recursos personalizados.</span><span class="sxs-lookup"><span data-stu-id="bc044-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="bc044-157">Al invocar este cmdlet, haga referencia al archivo del módulo de script (.psm1) que se describe en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="bc044-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="bc044-158">Incluya **Get-TargetResource**, **Set-TargetResource** y **Test-TargetResource** en la lista de funciones que se deben exportar.</span><span class="sxs-lookup"><span data-stu-id="bc044-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="bc044-159">A continuación se muestra un archivo de manifiesto de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="bc044-159">Following is an example manifest file.</span></span>

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="bc044-160">Compatibilidad con PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="bc044-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="bc044-161">**Nota:** **PsDscRunAsCredential** es compatible con PowerShell 5.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="bc044-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="bc044-162">La propiedad **PsDscRunAsCredential** se puede usar en el bloque de recursos de [configuraciones de DSC](../configurations/configurations.md) para especificar que el recurso se debe ejecutar bajo un conjunto especificado de credenciales.</span><span class="sxs-lookup"><span data-stu-id="bc044-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="bc044-163">Para más información, consulte [DSC de ejecución con las credenciales de usuario](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="bc044-163">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="bc044-164">Para tener acceso al contexto de usuario desde un recurso personalizado, puede usar la variable automática `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="bc044-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="bc044-165">Por ejemplo, el código siguiente podría escribir el contexto de usuario bajo el cual se ejecuta el recurso en el flujo de salida detallado:</span><span class="sxs-lookup"><span data-stu-id="bc044-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a><span data-ttu-id="bc044-166">Reinicio del nodo</span><span class="sxs-lookup"><span data-stu-id="bc044-166">Rebooting the Node</span></span>

<span data-ttu-id="bc044-167">Si las acciones realizadas en la función `Set-TargetResource` requieren un reinicio, puede usar una marca global para indicar al LCM que reinicie el nodo.</span><span class="sxs-lookup"><span data-stu-id="bc044-167">If the actions taken in your `Set-TargetResource` function require a reboot, you can use a global flag to tell the LCM to reboot the Node.</span></span> <span data-ttu-id="bc044-168">Este reinicio se produce inmediatamente después de completarse la función `Set-TargetResource`.</span><span class="sxs-lookup"><span data-stu-id="bc044-168">This reboot occurs directly after the `Set-TargetResource` function completes.</span></span>

<span data-ttu-id="bc044-169">Dentro de la función `Set-TargetResource`, agregue la siguiente línea de código.</span><span class="sxs-lookup"><span data-stu-id="bc044-169">Inside your `Set-TargetResource` function, add the following line of code.</span></span>

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

<span data-ttu-id="bc044-170">Para que el LCM reinicie el nodo, la marca **RebootNodeIfNeeded** debe establecerse en `$true`.</span><span class="sxs-lookup"><span data-stu-id="bc044-170">In order for the LCM to reboot the Node, the **RebootNodeIfNeeded** flag needs to be set to `$true`.</span></span> <span data-ttu-id="bc044-171">El ajuste **ActionAfterReboot** debe establecerse también en **ContinueConfiguration**, que es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="bc044-171">The **ActionAfterReboot** setting should also be set to **ContinueConfiguration**, which is the default.</span></span> <span data-ttu-id="bc044-172">Para obtener más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md) o [Configuración del administrador de configuración local (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="bc044-172">For more information on configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configuring the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>
