---
ms.date: 12/12/2018
keywords: DSC, powershell, recursos, la galería, el programa de instalación
title: Agregar parámetros a una configuración
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402554"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="3e19f-103">Agregar parámetros a una configuración</span><span class="sxs-lookup"><span data-stu-id="3e19f-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="3e19f-104">Al igual que las funciones, [configuraciones](configurations.md) se puede parametrizar para permitir que las configuraciones más dinámicas basadas en la entrada del usuario.</span><span class="sxs-lookup"><span data-stu-id="3e19f-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="3e19f-105">Los pasos son similares a las descritas en [funciones con parámetros](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="3e19f-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="3e19f-106">Este ejemplo comienza con una configuración básica que configura el servicio de "Cola" a "Running".</span><span class="sxs-lookup"><span data-stu-id="3e19f-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="3e19f-107">Parámetros de configuración integrados</span><span class="sxs-lookup"><span data-stu-id="3e19f-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="3e19f-108">A diferencia de una función sin embargo, el [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) atributo no agrega ninguna funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="3e19f-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="3e19f-109">Además [parámetros comunes de](/powershell/module/microsoft.powershell.core/about/about_commonparameters), las configuraciones también pueden usar lo siguiente creado en los parámetros, sin tener que definirlas.</span><span class="sxs-lookup"><span data-stu-id="3e19f-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="3e19f-110">Parámetro</span><span class="sxs-lookup"><span data-stu-id="3e19f-110">Parameter</span></span>  |<span data-ttu-id="3e19f-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="3e19f-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="3e19f-112">Usar para definir [configuraciones compuesto](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="3e19f-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="3e19f-113">Usar para definir [configuraciones compuesto](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="3e19f-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="3e19f-114">Usar para definir [configuraciones compuesto](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="3e19f-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="3e19f-115">Usa para pasar estructurado en [datos de configuración](configData.md) para su uso en la configuración.</span><span class="sxs-lookup"><span data-stu-id="3e19f-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="3e19f-116">Se utiliza para especificar dónde su "\<computername\>.mof" se compilará el archivo</span><span class="sxs-lookup"><span data-stu-id="3e19f-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="3e19f-117">Agregar sus propios parámetros a las configuraciones</span><span class="sxs-lookup"><span data-stu-id="3e19f-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="3e19f-118">Además de los parámetros integrados, también puede agregar sus propios parámetros a las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="3e19f-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="3e19f-119">El bloque de parámetros que se pasa directamente dentro de la declaración de la configuración, al igual que una función.</span><span class="sxs-lookup"><span data-stu-id="3e19f-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="3e19f-120">Debe ser un bloque de parámetros de configuración fuera de cualquier **nodo** declaraciones y por encima *importar* instrucciones.</span><span class="sxs-lookup"><span data-stu-id="3e19f-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="3e19f-121">Mediante la adición de parámetros, puede realizar las configuraciones más robusto y dinámico.</span><span class="sxs-lookup"><span data-stu-id="3e19f-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="3e19f-122">Agregar un parámetro ComputerName</span><span class="sxs-lookup"><span data-stu-id="3e19f-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="3e19f-123">Es el primer parámetro puede agregar un `-Computername` parámetro, por lo que puede compilar dinámicamente un archivo ".mof" para cualquier `-Computername` pasa a la configuración.</span><span class="sxs-lookup"><span data-stu-id="3e19f-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="3e19f-124">Como las funciones, también puede definir un valor predeterminado, en caso de que no pasa un valor para el usuario `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="3e19f-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="3e19f-125">Dentro de la configuración, a continuación, puede especificar su `-ComputerName` al definir el bloque del nodo de parámetro.</span><span class="sxs-lookup"><span data-stu-id="3e19f-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="3e19f-126">Llame a su configuración con parámetros</span><span class="sxs-lookup"><span data-stu-id="3e19f-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="3e19f-127">Después de agregar parámetros a la configuración, puede usar tal como lo haría con un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3e19f-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="3e19f-128">Compilar varios archivos .mof</span><span class="sxs-lookup"><span data-stu-id="3e19f-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="3e19f-129">El bloque de nodo también puede aceptar una lista separada por comas de nombres de equipo y generará archivos ".mof" para cada uno.</span><span class="sxs-lookup"><span data-stu-id="3e19f-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="3e19f-130">Puede ejecutar el ejemplo siguiente para generar archivos de "MOF" para todos los equipos que se pasa a la `-ComputerName` parámetro.</span><span class="sxs-lookup"><span data-stu-id="3e19f-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="3e19f-131">Parámetros avanzados en las configuraciones</span><span class="sxs-lookup"><span data-stu-id="3e19f-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="3e19f-132">Además un `-ComputerName` parámetro, podemos agregar parámetros para el nombre del servicio y el estado.</span><span class="sxs-lookup"><span data-stu-id="3e19f-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="3e19f-133">En el ejemplo siguiente se agrega un bloque de parámetros con un `-ServiceName` parámetro y lo usa para definir de forma dinámica el **servicio** bloque de recursos.</span><span class="sxs-lookup"><span data-stu-id="3e19f-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="3e19f-134">También agrega un `-State` parámetro para definir de forma dinámica el **estado** en el **servicio** bloque de recursos.</span><span class="sxs-lookup"><span data-stu-id="3e19f-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
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
> <span data-ttu-id="3e19f-135">En otros escenarios advacned, es posible que más sentido para mover los datos dinámicos en un modo estructurado [datos de configuración](configData.md).</span><span class="sxs-lookup"><span data-stu-id="3e19f-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="3e19f-136">El ejemplo de configuración ahora toma una dinámica `$ServiceName`, pero si no se especifica, se produce un error de compilación.</span><span class="sxs-lookup"><span data-stu-id="3e19f-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="3e19f-137">Puede agregar un valor predeterminado como en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="3e19f-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="3e19f-138">En este caso, tiene más sentido simplemente debe forzar al usuario especificar un valor para el `$ServiceName` parámetro.</span><span class="sxs-lookup"><span data-stu-id="3e19f-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="3e19f-139">El `parameter` atributo le permite agregar validación adicional y la canalización se admiten para los parámetros de la configuración.</span><span class="sxs-lookup"><span data-stu-id="3e19f-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="3e19f-140">Encima de cualquier declaración de parámetro, agregue el `parameter` bloque de atributos como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="3e19f-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="3e19f-141">Puede especificar argumentos para cada uno de ellos `parameter` atributo para controlar los aspectos del parámetro definido.</span><span class="sxs-lookup"><span data-stu-id="3e19f-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="3e19f-142">En el ejemplo siguiente se realiza la `$ServiceName` un **obligatorio** parámetro.</span><span class="sxs-lookup"><span data-stu-id="3e19f-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="3e19f-143">Para el `$State` parámetro, nos gustaría evitar que el usuario especifica los valores fuera de un conjunto predefinido (como en ejecución, detenido) el `ValidationSet*`atributo evitaría que el usuario especifica los valores fuera de un conjunto predefinido (por ejemplo, en ejecución, Detenido).</span><span class="sxs-lookup"><span data-stu-id="3e19f-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="3e19f-144">En el ejemplo siguiente se agrega el `ValidationSet` atributo a la `$State` parámetro.</span><span class="sxs-lookup"><span data-stu-id="3e19f-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="3e19f-145">Puesto que deseamos realizar la `$State` parámetro **obligatorio**, necesitamos agregar un valor predeterminado para ella.</span><span class="sxs-lookup"><span data-stu-id="3e19f-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="3e19f-146">No es necesario especificar un `parameter` atributo cuando se usa un `validation` atributo.</span><span class="sxs-lookup"><span data-stu-id="3e19f-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="3e19f-147">Puede leer más sobre la `parameter` y atributos de validación en [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3e19f-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="3e19f-148">Configuración totalmente parametrizado</span><span class="sxs-lookup"><span data-stu-id="3e19f-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="3e19f-149">Ahora tenemos una configuración parametrizada que obliga al usuario especificar un `-InstanceName`, `-ServiceName`y valida el `-State` parámetro.</span><span class="sxs-lookup"><span data-stu-id="3e19f-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="see-also"></a><span data-ttu-id="3e19f-150">Vea también</span><span class="sxs-lookup"><span data-stu-id="3e19f-150">See also</span></span>

- [<span data-ttu-id="3e19f-151">Escritura de la ayuda de las configuraciones de DSC</span><span class="sxs-lookup"><span data-stu-id="3e19f-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="3e19f-152">Configuración dinámica</span><span class="sxs-lookup"><span data-stu-id="3e19f-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="3e19f-153">Usar datos de configuración en las configuraciones</span><span class="sxs-lookup"><span data-stu-id="3e19f-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="3e19f-154">Datos de configuración y el entorno independiente</span><span class="sxs-lookup"><span data-stu-id="3e19f-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
