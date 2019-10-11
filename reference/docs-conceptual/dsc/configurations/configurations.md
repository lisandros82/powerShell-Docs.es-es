---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configuraciones DSC
ms.openlocfilehash: d7749ec88f9cca3e29c6b38d61fb73776af7ceb4
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954502"
---
# <a name="dsc-configurations"></a><span data-ttu-id="3160d-103">Configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="3160d-103">DSC Configurations</span></span>

> <span data-ttu-id="3160d-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3160d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="3160d-105">Las configuraciones DSC son scripts de PowerShell que definen un tipo especial de función.</span><span class="sxs-lookup"><span data-stu-id="3160d-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="3160d-106">Para definir una configuración, se utiliza la palabra clave de PowerShell **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="3160d-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

<span data-ttu-id="3160d-107">Guarde el script como un archivo `.ps1`.</span><span class="sxs-lookup"><span data-stu-id="3160d-107">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="3160d-108">Sintaxis de la configuración</span><span class="sxs-lookup"><span data-stu-id="3160d-108">Configuration syntax</span></span>

<span data-ttu-id="3160d-109">Un script de configuración consta de las partes siguientes:</span><span class="sxs-lookup"><span data-stu-id="3160d-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="3160d-110">El bloque **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="3160d-110">The **Configuration** block.</span></span> <span data-ttu-id="3160d-111">Este es el bloque del script más externo.</span><span class="sxs-lookup"><span data-stu-id="3160d-111">This is the outermost script block.</span></span> <span data-ttu-id="3160d-112">Para definirlo, se usa la palabra clave **Configuration** y se facilita un nombre.</span><span class="sxs-lookup"><span data-stu-id="3160d-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="3160d-113">En este caso, el nombre de la configuración es "MyDscConfiguration".</span><span class="sxs-lookup"><span data-stu-id="3160d-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="3160d-114">Uno o varios bloques **Node**.</span><span class="sxs-lookup"><span data-stu-id="3160d-114">One or more **Node** blocks.</span></span> <span data-ttu-id="3160d-115">Estos definen los nodos (equipos o máquinas virtuales) que se están configurando.</span><span class="sxs-lookup"><span data-stu-id="3160d-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="3160d-116">En la configuración anterior, hay un bloque **Node** cuyo destino es un equipo denominado "TEST-PC1".</span><span class="sxs-lookup"><span data-stu-id="3160d-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span> <span data-ttu-id="3160d-117">El bloque Node puede aceptar varios nombres de equipo.</span><span class="sxs-lookup"><span data-stu-id="3160d-117">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="3160d-118">Uno o varios bloques de recursos.</span><span class="sxs-lookup"><span data-stu-id="3160d-118">One or more resource blocks.</span></span> <span data-ttu-id="3160d-119">Es aquí donde la configuración establece las propiedades de los recursos que se están configurando.</span><span class="sxs-lookup"><span data-stu-id="3160d-119">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="3160d-120">En este caso, hay dos bloques de recursos, cada uno de los cuales llama al recurso "WindowsFeature".</span><span class="sxs-lookup"><span data-stu-id="3160d-120">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="3160d-121">Dentro de un bloque **Configuration**, puede hacer todo lo que se puede realizar normalmente en una función de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3160d-121">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="3160d-122">Por ejemplo, en el ejemplo anterior, si no quisiera codificar de forma rígida el nombre del equipo de destino en la configuración, podría agregar un parámetro para el nombre del nodo:</span><span class="sxs-lookup"><span data-stu-id="3160d-122">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="3160d-123">En este ejemplo, especifique el nombre del nodo, pasando como parámetro **ComputerName** cuando compile la configuración.</span><span class="sxs-lookup"><span data-stu-id="3160d-123">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="3160d-124">El nombre se establece como el valor predeterminado "localhost".</span><span class="sxs-lookup"><span data-stu-id="3160d-124">The name defaults to "localhost".</span></span>

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

<span data-ttu-id="3160d-125">El bloque **Node** también puede aceptar varios nombres de equipo.</span><span class="sxs-lookup"><span data-stu-id="3160d-125">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="3160d-126">En el ejemplo anterior, puede usar el parámetro `-ComputerName` o pasar una lista de equipos separados por comas directamente al bloque **Node**.</span><span class="sxs-lookup"><span data-stu-id="3160d-126">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="3160d-127">Al especificar una lista de equipos para el bloque **Node** desde una configuración, debe utilizar la notación de matriz.</span><span class="sxs-lookup"><span data-stu-id="3160d-127">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a><span data-ttu-id="3160d-128">Compilación de la configuración</span><span class="sxs-lookup"><span data-stu-id="3160d-128">Compiling the configuration</span></span>

<span data-ttu-id="3160d-129">Antes de que se pueda establecer una configuración, debe compilarla en un documento MOF.</span><span class="sxs-lookup"><span data-stu-id="3160d-129">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="3160d-130">Para ello, llame a la configuración, como lo haría con una función de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3160d-130">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="3160d-131">La última línea del ejemplo que contiene sólo el nombre de la configuración llama a la configuración.</span><span class="sxs-lookup"><span data-stu-id="3160d-131">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="3160d-132">Para llamar a una configuración, la función debe estar en el ámbito global (como ocurre con cualquier otra función de PowerShell).</span><span class="sxs-lookup"><span data-stu-id="3160d-132">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="3160d-133">Puede conseguirlo si precede el script con el operador punto ".", o si ejecuta el script de configuración presionando F5 o haciendo clic en el botón **Ejecutar Script** del ISE.</span><span class="sxs-lookup"><span data-stu-id="3160d-133">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="3160d-134">Para anteponer el operador punto al script, ejecute el comando `. .\myConfig.ps1`, donde `myConfig.ps1` es el nombre del archivo de script que contiene la configuración.</span><span class="sxs-lookup"><span data-stu-id="3160d-134">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="3160d-135">Cuando llama a la configuración:</span><span class="sxs-lookup"><span data-stu-id="3160d-135">When you call the configuration, it:</span></span>

- <span data-ttu-id="3160d-136">Resuelve todas las variables</span><span class="sxs-lookup"><span data-stu-id="3160d-136">Resolves all variables</span></span>
- <span data-ttu-id="3160d-137">Crea una carpeta en el directorio actual con el mismo nombre que la configuración.</span><span class="sxs-lookup"><span data-stu-id="3160d-137">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="3160d-138">Crea un archivo denominado _NodeName_.mof en el directorio nuevo, donde _NodeName_ es el nombre del nodo de destino de la configuración.</span><span class="sxs-lookup"><span data-stu-id="3160d-138">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="3160d-139">Si hay más de un nodo, se creará un archivo MOF para cada nodo.</span><span class="sxs-lookup"><span data-stu-id="3160d-139">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="3160d-140">El archivo MOF contiene toda la información de configuración del nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="3160d-140">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="3160d-141">Por este motivo, es importante protegerlo adecuadamente.</span><span class="sxs-lookup"><span data-stu-id="3160d-141">Because of this, it's important to keep it secure.</span></span>
> <span data-ttu-id="3160d-142">Para obtener más información, consulte [Proteger el archivo MOF](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="3160d-142">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="3160d-143">Cuando se compila la primera configuración anterior, el resultado es la estructura de carpetas siguiente:</span><span class="sxs-lookup"><span data-stu-id="3160d-143">Compiling the first configuration above results in the following folder structure:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

<span data-ttu-id="3160d-144">Si la configuración toma un parámetro, como en el segundo ejemplo, se debe proporcionar en tiempo de compilación.</span><span class="sxs-lookup"><span data-stu-id="3160d-144">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="3160d-145">Este sería su aspecto:</span><span class="sxs-lookup"><span data-stu-id="3160d-145">Here's how that would look:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="3160d-146">Uso de nuevos recursos en la configuración</span><span class="sxs-lookup"><span data-stu-id="3160d-146">Using new resources in Your configuration</span></span>

<span data-ttu-id="3160d-147">Si ha ejecutado los ejemplos anteriores, habrá observado que se le mostró una advertencia respecto a que se estaba utilizando un recurso sin importarlo explícitamente.</span><span class="sxs-lookup"><span data-stu-id="3160d-147">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="3160d-148">En la actualidad, DSC incluye 12 recursos como parte del módulo PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="3160d-148">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="3160d-149">El cmdlet ([Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)) puede utilizarse para determinar qué recursos están instalados en el sistema y disponibles para que el LCM los use.</span><span class="sxs-lookup"><span data-stu-id="3160d-149">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="3160d-150">Cuando estos módulos se hayan colocado en `$env:PSModulePath` y [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) los reconozca correctamente, es necesario que se carguen en la configuración.</span><span class="sxs-lookup"><span data-stu-id="3160d-150">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="3160d-151">**Import-DscResource** es una palabra clave dinámica que solo puede reconocerse dentro de un bloque **Configuration**, no es un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3160d-151">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span>
<span data-ttu-id="3160d-152">**Import-DscResource** admite dos parámetros:</span><span class="sxs-lookup"><span data-stu-id="3160d-152">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="3160d-153">**ModuleName** es la manera recomendada de usar **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="3160d-153">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="3160d-154">Acepta el nombre del módulo que contiene los recursos que se importarán (así como una matriz de cadenas de nombres de módulo).</span><span class="sxs-lookup"><span data-stu-id="3160d-154">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="3160d-155">**Name** es el nombre del recurso que se importará.</span><span class="sxs-lookup"><span data-stu-id="3160d-155">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="3160d-156">Este no es el nombre descriptivo que [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) devuelve como "Name", sino el nombre de clase que se usa al definir el esquema del recurso (que [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) devuelve como **ResourceType**).</span><span class="sxs-lookup"><span data-stu-id="3160d-156">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="3160d-157">Para obtener más información sobre el uso de `Import-DSCResource`, consulte [Uso de Import-DSCResource](import-dscresource.md)</span><span class="sxs-lookup"><span data-stu-id="3160d-157">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="3160d-158">Diferencias de PowerShell v4 y v5</span><span class="sxs-lookup"><span data-stu-id="3160d-158">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="3160d-159">Hay diferencias en cuanto a dónde se deben almacenar los recursos de DSC en PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="3160d-159">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="3160d-160">Para obtener más información, consulte [Ubicación de los recursos](import-dscresource.md#resource-location).</span><span class="sxs-lookup"><span data-stu-id="3160d-160">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="3160d-161">Véase también</span><span class="sxs-lookup"><span data-stu-id="3160d-161">See Also</span></span>

- [<span data-ttu-id="3160d-162">Información general sobre la configuración de estado deseado de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3160d-162">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="3160d-163">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="3160d-163">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="3160d-164">Configuración del administrador de configuración local</span><span class="sxs-lookup"><span data-stu-id="3160d-164">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
