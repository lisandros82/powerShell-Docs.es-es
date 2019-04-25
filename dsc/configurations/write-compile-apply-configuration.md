---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,service,setup
title: Escritura, compilación y aplicación de una configuración
ms.openlocfilehash: 947308efa165543571801c88a922daf44fa88be0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080023"
---
> <span data-ttu-id="3c899-103">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3c899-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="3c899-104">Escritura, compilación y aplicación de una configuración</span><span class="sxs-lookup"><span data-stu-id="3c899-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="3c899-105">Este ejercicio le guía a través de la creación y aplicación de una especificación de la configuración de estado deseado (DSC) de principio a fin.</span><span class="sxs-lookup"><span data-stu-id="3c899-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="3c899-106">En el ejemplo siguiente, obtendrá información sobre cómo escribir y aplicar una configuración muy sencilla.</span><span class="sxs-lookup"><span data-stu-id="3c899-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="3c899-107">La configuración garantizará la existencia de un archivo "HelloWorld.txt" en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="3c899-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="3c899-108">Si elimina el archivo, DSC volverá a crearlo la próxima vez que realice una actualización.</span><span class="sxs-lookup"><span data-stu-id="3c899-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="3c899-109">Para obtener información general de lo que es DSC y cómo funciona, consulte [Información general sobre Desired State Configuration para desarrolladores](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="3c899-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="3c899-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c899-110">Requirements</span></span>

<span data-ttu-id="3c899-111">Para ejecutar este ejemplo, necesitará un equipo con PowerShell 4.0 o posterior.</span><span class="sxs-lookup"><span data-stu-id="3c899-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="3c899-112">Escritura de la configuración</span><span class="sxs-lookup"><span data-stu-id="3c899-112">Write the configuration</span></span>

<span data-ttu-id="3c899-113">Una [configuración](configurations.md) de DSC es una función especial de PowerShell que define cómo quiere configurar uno o más equipos de destino (nodos).</span><span class="sxs-lookup"><span data-stu-id="3c899-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="3c899-114">En PowerShell ISE, o en otro editor de PowerShell, escriba lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="3c899-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

<span data-ttu-id="3c899-115">Guarde el archivo como "HelloWorld.ps1".</span><span class="sxs-lookup"><span data-stu-id="3c899-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="3c899-116">Definir una configuración es parecido a definir una función.</span><span class="sxs-lookup"><span data-stu-id="3c899-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="3c899-117">El bloque **Node** especifica el nodo de destino que va a configurar, en este caso `localhost`.</span><span class="sxs-lookup"><span data-stu-id="3c899-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="3c899-118">La configuración llama a uno de los [recursos](../resources/resources.md), el recurso `File`.</span><span class="sxs-lookup"><span data-stu-id="3c899-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="3c899-119">Los recursos se encargan de garantizar que el nodo de destino se encuentra en el estado definido por la configuración.</span><span class="sxs-lookup"><span data-stu-id="3c899-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="3c899-120">Compilación de la configuración</span><span class="sxs-lookup"><span data-stu-id="3c899-120">Compile the configuration</span></span>

<span data-ttu-id="3c899-121">Para que una configuración de DSC se aplique a un nodo, debe compilarse primero en un archivo MOF.</span><span class="sxs-lookup"><span data-stu-id="3c899-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="3c899-122">Al ejecutarse la configuración, como en el caso de una función, se compilará un archivo ".mof" para cada nodo definido por el bloque `Node`.</span><span class="sxs-lookup"><span data-stu-id="3c899-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="3c899-123">Para ejecutar la configuración, deberá *usar el operador punto* en el script "HelloWorld.ps1" en el ámbito actual.</span><span class="sxs-lookup"><span data-stu-id="3c899-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="3c899-124">Para obtener más información, vea [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing) (Acerca de los scripts).</span><span class="sxs-lookup"><span data-stu-id="3c899-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="3c899-125">*Use el operador punto* en el script "HelloWorld.ps1" escribiendo la ruta de acceso donde la almacenó, después de `. ` (punto, espacio).</span><span class="sxs-lookup"><span data-stu-id="3c899-125">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="3c899-126">A continuación, puede ejecutar la configuración llamándola igual que una función.</span><span class="sxs-lookup"><span data-stu-id="3c899-126">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="3c899-127">Esto genera la siguiente salida:</span><span class="sxs-lookup"><span data-stu-id="3c899-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="3c899-128">Aplicación de la configuración</span><span class="sxs-lookup"><span data-stu-id="3c899-128">Apply the configuration</span></span>

<span data-ttu-id="3c899-129">Ahora que ha compilado MOF, puede aplicar la configuración al nodo de destino (en este caso, el equipo local) mediante una llamada al cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="3c899-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="3c899-130">El cmdlet `Start-DscConfiguration` indica el [administrador de configuración local (LCM)](../managing-nodes/metaConfig.md), el motor de DSC, para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="3c899-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="3c899-131">El LCM se encarga de llamar a los recursos de DSC para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="3c899-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="3c899-132">Use el código siguiente para ejecutar el cmdlet `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="3c899-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="3c899-133">Especifique la ruta de acceso del directorio donde se almacena "localhost.mof" en el parámetro `-Path`.</span><span class="sxs-lookup"><span data-stu-id="3c899-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="3c899-134">El cmdlet `Start-DSCConfiguration` busca en el directorio especificado todos los archivos "\<nombrearchivo\>.mof".</span><span class="sxs-lookup"><span data-stu-id="3c899-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="3c899-135">El cmdlet `Start-DSCConfiguration` intenta aplicar cada archivo ".mof" que encuentra con el nombre del equipo especificado por el nombre de archivo ("localhost", "servidor01", "dc-02", etc.).</span><span class="sxs-lookup"><span data-stu-id="3c899-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="3c899-136">Si no se especifica el parámetro `-Wait`, `Start-DSCConfiguration` crea un trabajo en segundo plano para llevar a cabo la operación.</span><span class="sxs-lookup"><span data-stu-id="3c899-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="3c899-137">La especificación del parámetro `-Verbose` permite ver el resultado **detallado** de la operación.</span><span class="sxs-lookup"><span data-stu-id="3c899-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="3c899-138">`-Wait` y `-Verbose` son parámetros opcionales, ambos.</span><span class="sxs-lookup"><span data-stu-id="3c899-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="3c899-139">Probar la configuración</span><span class="sxs-lookup"><span data-stu-id="3c899-139">Test the configuration</span></span>

<span data-ttu-id="3c899-140">Cuando el cmdlet `Start-DSCConfiguration` se haya completado, debe ver un archivo "HelloWorld.txt" en la ubicación especificada.</span><span class="sxs-lookup"><span data-stu-id="3c899-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="3c899-141">Puede comprobar el contenido con el cmdlet [Get-Content](/powershell/module/microsoft.powershell.management/get-content).</span><span class="sxs-lookup"><span data-stu-id="3c899-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="3c899-142">También puede *probar* el estado actual con [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="3c899-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="3c899-143">El resultado debe ser "True" si el nodo es compatible actualmente con la configuración aplicada.</span><span class="sxs-lookup"><span data-stu-id="3c899-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="3c899-144">Nueva aplicación de la configuración</span><span class="sxs-lookup"><span data-stu-id="3c899-144">Re-applying the configuration</span></span>

<span data-ttu-id="3c899-145">Para que la configuración se aplique de nuevo, puede quitar el archivo de texto creado por la configuración.</span><span class="sxs-lookup"><span data-stu-id="3c899-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="3c899-146">El uso del cmdlet `Start-DSCConfiguration` con el parámetro `-UseExisting`.</span><span class="sxs-lookup"><span data-stu-id="3c899-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="3c899-147">El parámetro `-UseExisting` indica a `Start-DSCConfiguration` que vuelva a aplicar el archivo "current.mof", que representa la última configuración aplicada correctamente.</span><span class="sxs-lookup"><span data-stu-id="3c899-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="3c899-148">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="3c899-148">Next steps</span></span>

- <span data-ttu-id="3c899-149">Conozca más sobre las configuraciones de DSC en [Configuraciones DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="3c899-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="3c899-150">Vea qué recursos de DSC están disponibles y cómo crear recursos personalizados de DSC en [recursos de DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="3c899-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="3c899-151">Encuentre las configuraciones y los recursos de DSC en la [Galería de PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="3c899-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
