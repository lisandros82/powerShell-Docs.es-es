---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Configuraciones DSC
ms.openlocfilehash: c0cf0e7aa1d18898c50a0662e4fc76ab02932f08
ms.sourcegitcommit: 7bb75bfb8d12aaa6b6071dcb2ca639d4ecceef26
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2017
---
# <a name="dsc-configurations"></a><span data-ttu-id="2612f-103">Configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="2612f-103">DSC Configurations</span></span>

><span data-ttu-id="2612f-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2612f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2612f-105">Las configuraciones DSC son scripts de PowerShell que definen un tipo especial de función.</span><span class="sxs-lookup"><span data-stu-id="2612f-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span> <span data-ttu-id="2612f-106">Para definir una configuración, se utiliza la palabra clave de PowerShell **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="2612f-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

<span data-ttu-id="2612f-107">Guarde el script como un archivo .ps1.</span><span class="sxs-lookup"><span data-stu-id="2612f-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="2612f-108">Sintaxis de la configuración</span><span class="sxs-lookup"><span data-stu-id="2612f-108">Configuration syntax</span></span>

<span data-ttu-id="2612f-109">Un script de configuración consta de las partes siguientes:</span><span class="sxs-lookup"><span data-stu-id="2612f-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="2612f-110">El bloque **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="2612f-110">The **Configuration** block.</span></span> <span data-ttu-id="2612f-111">Este es el bloque del script más externo.</span><span class="sxs-lookup"><span data-stu-id="2612f-111">This is the outermost script block.</span></span> <span data-ttu-id="2612f-112">Para definirlo, se usa la palabra clave **Configuration** y se facilita un nombre.</span><span class="sxs-lookup"><span data-stu-id="2612f-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="2612f-113">En este caso, el nombre de la configuración es "MyDscConfiguration".</span><span class="sxs-lookup"><span data-stu-id="2612f-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="2612f-114">Uno o varios bloques **Node**.</span><span class="sxs-lookup"><span data-stu-id="2612f-114">One or more **Node** blocks.</span></span> <span data-ttu-id="2612f-115">Estos definen los nodos (equipos o máquinas virtuales) que se están configurando.</span><span class="sxs-lookup"><span data-stu-id="2612f-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="2612f-116">En la configuración anterior, hay un bloque **Node** cuyo destino es un equipo denominado "TEST-PC1".</span><span class="sxs-lookup"><span data-stu-id="2612f-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="2612f-117">Uno o varios bloques de recursos.</span><span class="sxs-lookup"><span data-stu-id="2612f-117">One or more resource blocks.</span></span> <span data-ttu-id="2612f-118">Es aquí donde la configuración establece las propiedades de los recursos que se están configurando.</span><span class="sxs-lookup"><span data-stu-id="2612f-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="2612f-119">En este caso, hay dos bloques de recursos, cada uno de los cuales llama al recurso "WindowsFeature".</span><span class="sxs-lookup"><span data-stu-id="2612f-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="2612f-120">Dentro de un bloque **Configuration**, puede hacer todo lo que se puede realizar normalmente en una función de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2612f-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="2612f-121">Por ejemplo, en el ejemplo anterior, si no quisiera codificar de forma rígida el nombre del equipo de destino en la configuración, podría agregar un parámetro para el nombre del nodo:</span><span class="sxs-lookup"><span data-stu-id="2612f-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

<span data-ttu-id="2612f-122">En este ejemplo, especifique el nombre del nodo, pasando como parámetro **ComputerName** cuando compile la configuración.</span><span class="sxs-lookup"><span data-stu-id="2612f-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuraton.</span></span> <span data-ttu-id="2612f-123">El nombre se establece como el valor predeterminado "localhost".</span><span class="sxs-lookup"><span data-stu-id="2612f-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="2612f-124">Compilación de la configuración</span><span class="sxs-lookup"><span data-stu-id="2612f-124">Compiling the configuration</span></span>

<span data-ttu-id="2612f-125">Antes de que se pueda establecer una configuración, debe compilarla en un documento MOF.</span><span class="sxs-lookup"><span data-stu-id="2612f-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span> <span data-ttu-id="2612f-126">Para ello, llame a la configuración, como lo haría con una función de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2612f-126">You do this by calling the configuration like you would a PowerShell function.</span></span>  
<span data-ttu-id="2612f-127">La última línea del ejemplo que contiene sólo el nombre de la configuración llama a la configuración.</span><span class="sxs-lookup"><span data-stu-id="2612f-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

><span data-ttu-id="2612f-128">**Nota:** Para llamar a una configuración, la función debe estar en el ámbito global (como ocurre con cualquier otra función de PowerShell).</span><span class="sxs-lookup"><span data-stu-id="2612f-128">**Note:** To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span> 
><span data-ttu-id="2612f-129">Puede conseguirlo si precede el script con el operador punto ".", o si ejecuta el script de configuración presionando F5 o haciendo clic en el botón **Ejecutar Script** del ISE.</span><span class="sxs-lookup"><span data-stu-id="2612f-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span> 
><span data-ttu-id="2612f-130">Para anteponer el operador punto al script, ejecute el comando `. .\myConfig.ps1`, donde `myConfig.ps1` es el nombre del archivo de script que contiene la configuración.</span><span class="sxs-lookup"><span data-stu-id="2612f-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="2612f-131">Cuando llama a la configuración:</span><span class="sxs-lookup"><span data-stu-id="2612f-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="2612f-132">Resuelve todas las variables</span><span class="sxs-lookup"><span data-stu-id="2612f-132">Resolves all variables</span></span> 
- <span data-ttu-id="2612f-133">Crea una carpeta en el directorio actual con el mismo nombre que la configuración.</span><span class="sxs-lookup"><span data-stu-id="2612f-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="2612f-134">Crea un archivo denominado _NodeName_.mof en el directorio nuevo, donde _NodeName_ es el nombre del nodo de destino de la configuración.</span><span class="sxs-lookup"><span data-stu-id="2612f-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span> 
    <span data-ttu-id="2612f-135">Si hay más de un nodo, se creará un archivo MOF por cada nodo.</span><span class="sxs-lookup"><span data-stu-id="2612f-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

><span data-ttu-id="2612f-136">**Nota**: El archivo MOF contiene toda la información de configuración del nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="2612f-136">**Note**: The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="2612f-137">Por este motivo, es importante protegerlo adecuadamente.</span><span class="sxs-lookup"><span data-stu-id="2612f-137">Because of this, it’s important to keep it secure.</span></span> 
><span data-ttu-id="2612f-138">Para obtener más información, consulte [Proteger el archivo MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="2612f-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="2612f-139">Cuando se compila la primera configuración anterior, el resultado es la estructura de carpetas siguiente:</span><span class="sxs-lookup"><span data-stu-id="2612f-139">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="2612f-140">Si la configuración toma un parámetro, como en el segundo ejemplo, se debe proporcionar en tiempo de compilación.</span><span class="sxs-lookup"><span data-stu-id="2612f-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="2612f-141">Este sería su aspecto:</span><span class="sxs-lookup"><span data-stu-id="2612f-141">Here's how that would look:</span></span>

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

## <a name="using-dependson"></a><span data-ttu-id="2612f-142">Uso de DependsOn</span><span class="sxs-lookup"><span data-stu-id="2612f-142">Using DependsOn</span></span>

<span data-ttu-id="2612f-143">Una palabra clave de DSC bastante útil es **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="2612f-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="2612f-144">Normalmente (aunque no necesariamente siempre), DSC aplica a los recursos en el orden en que aparecen en la configuración.</span><span class="sxs-lookup"><span data-stu-id="2612f-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span> <span data-ttu-id="2612f-145">Sin embargo, **DependsOn** especifica qué recursos dependen de otros recursos y el LCM se asegura de que se apliquen en el orden correcto, independientemente del orden en que se definan las instancias de los recursos.</span><span class="sxs-lookup"><span data-stu-id="2612f-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span> <span data-ttu-id="2612f-146">Por ejemplo, una configuración puede especificar que una instancia del recurso **User** depende de la existencia de una instancia de **Group**:</span><span class="sxs-lookup"><span data-stu-id="2612f-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="2612f-147">Uso de nuevos recursos en la configuración</span><span class="sxs-lookup"><span data-stu-id="2612f-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="2612f-148">Si ha ejecutado los ejemplos anteriores, habrá observado que se le mostró una advertencia respecto a que se estaba utilizando un recurso sin importarlo explícitamente.</span><span class="sxs-lookup"><span data-stu-id="2612f-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="2612f-149">En la actualidad, DSC incluye 12 recursos como parte del módulo PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="2612f-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span> <span data-ttu-id="2612f-150">Otros recursos de los módulos externos deben colocarse en `$env:PSModulePath` para que el LCM los reconozca.</span><span class="sxs-lookup"><span data-stu-id="2612f-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span> <span data-ttu-id="2612f-151">Un cmdlet nuevo, [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), puede utilizarse para determinar qué recursos están instalados en el sistema y están disponibles para que el LCM los use.</span><span class="sxs-lookup"><span data-stu-id="2612f-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span> <span data-ttu-id="2612f-152">Cuando estos módulos se hayan colocado en `$env:PSModulePath` y [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) los reconozca correctamente, es necesario que se carguen en la configuración.</span><span class="sxs-lookup"><span data-stu-id="2612f-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span> 
<span data-ttu-id="2612f-153">**Import-DscResource** es una palabra clave dinámica que solo puede reconocerse dentro de un bloque **Configuration** (es decir, no es un cmdlet).</span><span class="sxs-lookup"><span data-stu-id="2612f-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span> 
<span data-ttu-id="2612f-154">**Import-DscResource** admite dos parámetros:</span><span class="sxs-lookup"><span data-stu-id="2612f-154">**Import-DscResource** supports two parameters:</span></span>
- <span data-ttu-id="2612f-155">**ModuleName** es la manera recomendada de usar **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="2612f-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="2612f-156">Acepta el nombre del módulo que contiene los recursos que se importarán (así como una matriz de cadenas de nombres de módulo).</span><span class="sxs-lookup"><span data-stu-id="2612f-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span> 
- <span data-ttu-id="2612f-157">**Name** es el nombre del recurso que se importará.</span><span class="sxs-lookup"><span data-stu-id="2612f-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="2612f-158">Este no es el nombre descriptivo que [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) devuelve como "Name", sino el nombre de clase que se usa al definir el esquema del recurso (que [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) devuelve como **ResourceType**).</span><span class="sxs-lookup"><span data-stu-id="2612f-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)).</span></span> 

## <a name="see-also"></a><span data-ttu-id="2612f-159">Véase también</span><span class="sxs-lookup"><span data-stu-id="2612f-159">See Also</span></span>
* [<span data-ttu-id="2612f-160">Información general sobre la configuración de estado deseado de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2612f-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="2612f-161">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="2612f-161">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="2612f-162">Configuración del administrador de configuración local</span><span class="sxs-lookup"><span data-stu-id="2612f-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

