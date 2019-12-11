---
ms.date: 12/12/2018
keywords: dsc,powershell,resource,gallery,setup
title: Agregar parámetros a una configuración
ms.openlocfilehash: 72e6c15593d11ed39d7fe8ea79f794089f410cf8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954202"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="e4c98-103">Agregar parámetros a una configuración</span><span class="sxs-lookup"><span data-stu-id="e4c98-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="e4c98-104">Al igual que las funciones, las [configuraciones](configurations.md) se pueden parametrizar para permitir configuraciones más dinámicas basadas en la entrada del usuario.</span><span class="sxs-lookup"><span data-stu-id="e4c98-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="e4c98-105">Los pasos son similares a las descritos en [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions) (Funciones con parámetros).</span><span class="sxs-lookup"><span data-stu-id="e4c98-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="e4c98-106">Este ejemplo comienza con una configuración básica que configura el servicio "Spooler" para que su estado sea "Running".</span><span class="sxs-lookup"><span data-stu-id="e4c98-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="e4c98-107">Parámetros de configuración integrados</span><span class="sxs-lookup"><span data-stu-id="e4c98-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="e4c98-108">A diferencia de una función, el atributo [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) no agrega ninguna funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="e4c98-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="e4c98-109">Además de los [parámetros comunes](/powershell/module/microsoft.powershell.core/about/about_commonparameters), las configuraciones también pueden usar los siguiente parámetros integrados, sin necesidad que definirlos.</span><span class="sxs-lookup"><span data-stu-id="e4c98-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="e4c98-110">Parámetro</span><span class="sxs-lookup"><span data-stu-id="e4c98-110">Parameter</span></span>  |<span data-ttu-id="e4c98-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4c98-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="e4c98-112">Se utiliza para definir [configuraciones compuestas](compositeconfigs.md).</span><span class="sxs-lookup"><span data-stu-id="e4c98-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="e4c98-113">Se utiliza para definir [configuraciones compuestas](compositeconfigs.md).</span><span class="sxs-lookup"><span data-stu-id="e4c98-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="e4c98-114">Se utiliza para definir [configuraciones compuestas](compositeconfigs.md).</span><span class="sxs-lookup"><span data-stu-id="e4c98-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="e4c98-115">Se utiliza para pasar [datos de configuración](configData.md) estructurados para su uso en la configuración.</span><span class="sxs-lookup"><span data-stu-id="e4c98-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="e4c98-116">Se utiliza para especificar dónde se compilará su archivo "\<computername\>.mof".</span><span class="sxs-lookup"><span data-stu-id="e4c98-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="e4c98-117">Adición de sus propios parámetros a las configuraciones</span><span class="sxs-lookup"><span data-stu-id="e4c98-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="e4c98-118">Además de los parámetros integrados, también puede agregar sus propios parámetros a las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="e4c98-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="e4c98-119">El bloque de parámetros se pasa directamente a la declaración de la configuración, igual que una función.</span><span class="sxs-lookup"><span data-stu-id="e4c98-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="e4c98-120">Un bloque de parámetros de configuración debe estar fuera de cualquier declaración de **nodo** y por encima de cualquier instrucción de *importación*.</span><span class="sxs-lookup"><span data-stu-id="e4c98-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="e4c98-121">Al agregar parámetros, puede hacer que sus configuraciones sean más robustas y dinámicas.</span><span class="sxs-lookup"><span data-stu-id="e4c98-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="e4c98-122">Adición de un parámetro ComputerName</span><span class="sxs-lookup"><span data-stu-id="e4c98-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="e4c98-123">El primer parámetro que podría agregar es un parámetro `-Computername`, de manera que podría compilar un archivo ".mof" para cualquier `-Computername` que pase a la configuración.</span><span class="sxs-lookup"><span data-stu-id="e4c98-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="e4c98-124">Al igual que las funciones, también puede definir un valor predeterminado, en caso de que el usuario no pase un valor para `-ComputerName`.</span><span class="sxs-lookup"><span data-stu-id="e4c98-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="e4c98-125">Dentro de la configuración, puede especificar a continuación su parámetro `-ComputerName` al definir el bloque del nodo.</span><span class="sxs-lookup"><span data-stu-id="e4c98-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="e4c98-126">Llamada a su configuración con parámetros</span><span class="sxs-lookup"><span data-stu-id="e4c98-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="e4c98-127">Después de agregar parámetros a la configuración, puede usarlos tal como lo haría con un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4c98-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="e4c98-128">Compilación de varios archivos .mof</span><span class="sxs-lookup"><span data-stu-id="e4c98-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="e4c98-129">El bloque de nodo también puede aceptar una lista separada por comas de nombres de equipos, y generará archivos ".mof" para cada uno.</span><span class="sxs-lookup"><span data-stu-id="e4c98-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="e4c98-130">Puede ejecutar el ejemplo siguiente para generar archivos ".mof" para todos los equipos que se pasan al parámetro `-ComputerName`.</span><span class="sxs-lookup"><span data-stu-id="e4c98-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="e4c98-131">Parámetros avanzados en las configuraciones</span><span class="sxs-lookup"><span data-stu-id="e4c98-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="e4c98-132">Además un parámetro `-ComputerName`, podemos agregar parámetros para el nombre y el estado del servicio.</span><span class="sxs-lookup"><span data-stu-id="e4c98-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="e4c98-133">En el ejemplo siguiente se agrega un bloque de parámetros con un parámetro `-ServiceName` y se usa para definir de forma dinámica el bloque de recursos **Service**.</span><span class="sxs-lookup"><span data-stu-id="e4c98-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="e4c98-134">También agrega un parámetro `-State` para definir de forma dinámica el **estado** en el bloque de recursos **Service**.</span><span class="sxs-lookup"><span data-stu-id="e4c98-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="e4c98-135">En escenarios más avanzados, es posible que tenga más sentido mover los datos dinámicos en [datos de configuración](configData.md) estructurados.</span><span class="sxs-lookup"><span data-stu-id="e4c98-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="e4c98-136">El ejemplo de configuración ahora toma un `$ServiceName` dinámico, pero si no se especifica uno, se produce un error de compilación.</span><span class="sxs-lookup"><span data-stu-id="e4c98-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="e4c98-137">Puede agregar un valor predeterminado como en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="e4c98-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="e4c98-138">Sin embargo, en este caso tiene más sentido simplemente obligar al usuario a especificar un valor para el parámetro `$ServiceName`.</span><span class="sxs-lookup"><span data-stu-id="e4c98-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="e4c98-139">El atributo `parameter` le permite agregar más compatibilidad con la validación y la canalización para los parámetros de configuración.</span><span class="sxs-lookup"><span data-stu-id="e4c98-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="e4c98-140">Encima de cualquier declaración de parámetro, agregue el bloque de atributos `parameter` como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="e4c98-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="e4c98-141">Puede especificar argumentos para cada atributo `parameter`, para controlar los aspectos del parámetro definido.</span><span class="sxs-lookup"><span data-stu-id="e4c98-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="e4c98-142">En el ejemplo siguiente se hace de `$ServiceName` un parámetro de tipo obligatorio (**Mandatory**).</span><span class="sxs-lookup"><span data-stu-id="e4c98-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="e4c98-143">Para el parámetro `$State`, nos gustaría evitar que el usuario especificara los valores fuera de un conjunto predefinido (como Running, Stopped); el atributo `ValidationSet*` evitaría que el usuario especificara los valores fuera de un conjunto predefinido (como Running, Stopped).</span><span class="sxs-lookup"><span data-stu-id="e4c98-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="e4c98-144">En el ejemplo siguiente se agrega el atributo `ValidationSet` al parámetro `$State`.</span><span class="sxs-lookup"><span data-stu-id="e4c98-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="e4c98-145">Puesto que no deseamos que el parámetro `$State` sea de tipo **Mandatory**, tenemos que agregarle un valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="e4c98-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="e4c98-146">No es necesario especificar un atributo `parameter` cuando se usa un atributo `validation`.</span><span class="sxs-lookup"><span data-stu-id="e4c98-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="e4c98-147">Puede leer más sobre `parameter` y los atributos de validación en [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters) (Acerca de los parámetros avanzados de funciones).</span><span class="sxs-lookup"><span data-stu-id="e4c98-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="e4c98-148">Configuración totalmente parametrizada</span><span class="sxs-lookup"><span data-stu-id="e4c98-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="e4c98-149">Ahora tenemos una configuración parametrizada que obliga al usuario a especificar un valor `-InstanceName`, `-ServiceName` y valida el parámetro `-State`.</span><span class="sxs-lookup"><span data-stu-id="e4c98-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="e4c98-150">Vea también</span><span class="sxs-lookup"><span data-stu-id="e4c98-150">See also</span></span>

- [<span data-ttu-id="e4c98-151">Escritura de la ayuda de las configuraciones de DSC</span><span class="sxs-lookup"><span data-stu-id="e4c98-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="e4c98-152">Configuraciones dinámicas</span><span class="sxs-lookup"><span data-stu-id="e4c98-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="e4c98-153">Uso de datos de configuración en DSC</span><span class="sxs-lookup"><span data-stu-id="e4c98-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="e4c98-154">Separación de los datos de entorno y configuración</span><span class="sxs-lookup"><span data-stu-id="e4c98-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
