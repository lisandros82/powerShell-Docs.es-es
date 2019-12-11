---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 'Inicio rápido: creación de un sitio web con DSC'
ms.openlocfilehash: d98607939ccd3cc5e660936d8c0a6d54fce7d65f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71955072"
---
> <span data-ttu-id="00391-103">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="00391-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart---create-a-website-with-dsc"></a><span data-ttu-id="00391-104">Inicio rápido: creación de un sitio web con DSC</span><span class="sxs-lookup"><span data-stu-id="00391-104">Quickstart - Create a website with DSC</span></span>

<span data-ttu-id="00391-105">Este ejercicio le guía a través de la creación y aplicación de una especificación de la configuración de estado deseado (DSC) de principio a fin.</span><span class="sxs-lookup"><span data-stu-id="00391-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="00391-106">En el ejemplo, nos aseguraremos de que un servidor tiene habilitada la característica `Web-Server` (IIS) y de que el contenido de un sitio web "Hello World" simple está presente en el directorio `inetpub\wwwroot` de ese servidor.</span><span class="sxs-lookup"><span data-stu-id="00391-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `inetpub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="00391-107">Para información general de lo que es DSC y cómo funciona, consulte [Información general sobre la configuración de estado deseado para responsables de toma de decisiones](../overview/decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="00391-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](../overview/decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="00391-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00391-108">Requirements</span></span>

<span data-ttu-id="00391-109">Para ejecutar este ejemplo, necesitará un equipo con Windows Server 2012 o posterior y PowerShell 4.0 o posterior.</span><span class="sxs-lookup"><span data-stu-id="00391-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="00391-110">Escritura y colocación del archivo index.htm</span><span class="sxs-lookup"><span data-stu-id="00391-110">Write and place the index.htm file</span></span>

<span data-ttu-id="00391-111">En primer lugar, vamos a crear el archivo HTML que se utilizará como el contenido del sitio web.</span><span class="sxs-lookup"><span data-stu-id="00391-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="00391-112">En la carpeta raíz, cree una carpeta denominada `test`.</span><span class="sxs-lookup"><span data-stu-id="00391-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="00391-113">En un editor de texto, escriba el texto siguiente:</span><span class="sxs-lookup"><span data-stu-id="00391-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="00391-114">Guárdelo como `index.htm` en la carpeta `test` que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="00391-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="00391-115">Escritura de la configuración</span><span class="sxs-lookup"><span data-stu-id="00391-115">Write the configuration</span></span>

<span data-ttu-id="00391-116">Una [configuración DSC](../configurations/configurations.md) es una función especial de PowerShell que define cómo desea configurar uno o más equipos de destino (nodos).</span><span class="sxs-lookup"><span data-stu-id="00391-116">A [DSC configuration](../configurations/configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="00391-117">En PowerShell ISE, escriba lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="00391-117">In the PowerShell ISE, type the following:</span></span>

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

<span data-ttu-id="00391-118">Guarde el archivo como `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="00391-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="00391-119">Puede ver que se parece a una función de PowerShell, con la incorporación de la palabra clave **Configuration** utilizada antes del nombre de la función.</span><span class="sxs-lookup"><span data-stu-id="00391-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="00391-120">El bloque **Node** especifica el nodo de destino que va a configurar, en este caso `localhost`.</span><span class="sxs-lookup"><span data-stu-id="00391-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="00391-121">La configuración llama a dos [recursos](../resources/resources.md): **WindowsFeature** y **File**.</span><span class="sxs-lookup"><span data-stu-id="00391-121">The configuration calls two [resources](../resources/resources.md), **WindowsFeature** and **File**.</span></span>
<span data-ttu-id="00391-122">Los recursos se encargan de garantizar que el nodo de destino se encuentra en el estado definido por la configuración.</span><span class="sxs-lookup"><span data-stu-id="00391-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="00391-123">Compilación de la configuración</span><span class="sxs-lookup"><span data-stu-id="00391-123">Compile the configuration</span></span>

<span data-ttu-id="00391-124">Para que una configuración de DSC se aplique a un nodo, debe compilarse primero en un archivo MOF.</span><span class="sxs-lookup"><span data-stu-id="00391-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="00391-125">Para ello, ejecute la configuración como una función.</span><span class="sxs-lookup"><span data-stu-id="00391-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="00391-126">En una consola de PowerShell, vaya a la misma carpeta donde guardó la configuración y ejecute los siguientes comandos para compilar la configuración en un archivo MOF:</span><span class="sxs-lookup"><span data-stu-id="00391-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="00391-127">Esto genera la siguiente salida:</span><span class="sxs-lookup"><span data-stu-id="00391-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="00391-128">La primera línea hace que la función de configuración esté disponible en la consola.</span><span class="sxs-lookup"><span data-stu-id="00391-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="00391-129">La segunda línea ejecuta la configuración.</span><span class="sxs-lookup"><span data-stu-id="00391-129">The second line runs the configuration.</span></span>
<span data-ttu-id="00391-130">El resultado es que se crea una carpeta nueva llamada `WebsiteTest` como una subcarpeta de la carpeta actual.</span><span class="sxs-lookup"><span data-stu-id="00391-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="00391-131">La carpeta `WebsiteTest` contiene un archivo denominado `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="00391-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="00391-132">Este es el archivo que se puede aplicar al nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="00391-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="00391-133">Aplicación de la configuración</span><span class="sxs-lookup"><span data-stu-id="00391-133">Apply the configuration</span></span>

<span data-ttu-id="00391-134">Ahora que ha compilado MOF, puede aplicar la configuración al nodo de destino (en este caso, el equipo local) mediante una llamada al cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="00391-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="00391-135">El cmdlet `Start-DscConfiguration` indica el [administrador de configuración local (LCM)](../managing-nodes/metaConfig.md), que es el motor de DSC, para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="00391-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="00391-136">El LCM se encarga de llamar a los recursos de DSC para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="00391-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="00391-137">En una consola de PowerShell, vaya a la misma carpeta donde guardó la configuración y ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="00391-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="00391-138">Probar la configuración</span><span class="sxs-lookup"><span data-stu-id="00391-138">Test the configuration</span></span>

<span data-ttu-id="00391-139">Puede llamar al cmdlet [DscConfigurationStatus Get](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) para ver si la configuración se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="00391-139">You can call the [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="00391-140">También puede probar los resultados directamente, en este caso examinando `http://localhost/` en un explorador web.</span><span class="sxs-lookup"><span data-stu-id="00391-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="00391-141">Debería ver la página HTML "Hello World" que creó como el primer paso en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="00391-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="00391-142">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="00391-142">Next steps</span></span>

- <span data-ttu-id="00391-143">Conozca más sobre las configuraciones de DSC en [Configuraciones DSC](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="00391-143">Find out more about DSC configurations at [DSC configurations](../configurations/configurations.md).</span></span>
- <span data-ttu-id="00391-144">Vea qué recursos de DSC están disponibles y cómo crear recursos personalizados de DSC en [recursos de DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="00391-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="00391-145">Encuentre las configuraciones y los recursos de DSC en la [Galería de PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="00391-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
