---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 'Recursos compuestos: uso de una configuración DSC como un recurso'
ms.openlocfilehash: 79fe94bd5bab8fa460714e5994d2e2487f302410
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/25/2019
ms.locfileid: "75415889"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="ab38d-103">Recursos compuestos: uso de una configuración DSC como un recurso</span><span class="sxs-lookup"><span data-stu-id="ab38d-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="ab38d-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ab38d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ab38d-105">En situaciones del mundo real, las configuraciones pueden acabar siendo largas y complejas, con llamadas a muchos recursos diferentes y estableciendo una gran cantidad de propiedades.</span><span class="sxs-lookup"><span data-stu-id="ab38d-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="ab38d-106">Para ayudar a abordar esta complejidad, puede utilizar una configuración de estado deseado (DSC) de Windows PowerShell como recurso para otras configuraciones.</span><span class="sxs-lookup"><span data-stu-id="ab38d-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="ab38d-107">Esto se denomina "recurso compuesto".</span><span class="sxs-lookup"><span data-stu-id="ab38d-107">This is called a composite resource.</span></span> <span data-ttu-id="ab38d-108">Un recurso compuesto es una configuración DSC que toma parámetros.</span><span class="sxs-lookup"><span data-stu-id="ab38d-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="ab38d-109">Los parámetros de la configuración actúan como las propiedades del recurso.</span><span class="sxs-lookup"><span data-stu-id="ab38d-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="ab38d-110">La configuración se guarda como un archivo con una extensión `.schema.psm1`.</span><span class="sxs-lookup"><span data-stu-id="ab38d-110">The configuration is saved as a file with a `.schema.psm1` extension.</span></span> <span data-ttu-id="ab38d-111">Toma el lugar del esquema MOF y del script de recurso en un recurso de DSC típico.</span><span class="sxs-lookup"><span data-stu-id="ab38d-111">It takes the place of both the MOF schema, and the resource script in a typical DSC resource.</span></span> <span data-ttu-id="ab38d-112">Para más información sobre los recursos DSC, consulte [Recursos de Desired State Configuration de Windows PowerShell](resources.md).</span><span class="sxs-lookup"><span data-stu-id="ab38d-112">For more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="ab38d-113">Creación del recurso compuesto</span><span class="sxs-lookup"><span data-stu-id="ab38d-113">Creating the composite resource</span></span>

<span data-ttu-id="ab38d-114">En nuestro ejemplo, se creará una configuración que invoca un número de recursos existentes para configurar las máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="ab38d-114">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="ab38d-115">En lugar de especificar los valores que se establecerán en bloques de configuración, la configuración toma parámetros que se utilizan en los bloques de configuración.</span><span class="sxs-lookup"><span data-stu-id="ab38d-115">Instead of specifying the values to be set in configuration blocks, the configuration takes in parameters that are then used in the configuration blocks.</span></span>

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Create VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="ab38d-116">DSC no admite actualmente la colocación de recursos compuestos o configuraciones anidadas dentro de un recurso compuesto.</span><span class="sxs-lookup"><span data-stu-id="ab38d-116">DSC doesn't currently support placing composite resources or nested configurations within a composite resource.</span></span>

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="ab38d-117">Guardar la configuración como un recurso compuesto</span><span class="sxs-lookup"><span data-stu-id="ab38d-117">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="ab38d-118">Para usar la configuración con parámetros como un recurso de DSC, guárdela en una estructura de directorios similar a la de cualquier otro recurso basado en MOF y asígnele un nombre con una extensión `.schema.psm1`.</span><span class="sxs-lookup"><span data-stu-id="ab38d-118">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a `.schema.psm1` extension.</span></span> <span data-ttu-id="ab38d-119">En este ejemplo, usamos el archivo `xVirtualMachine.schema.psm1`.</span><span class="sxs-lookup"><span data-stu-id="ab38d-119">For this example, we'll name the file `xVirtualMachine.schema.psm1`.</span></span> <span data-ttu-id="ab38d-120">También deberá crear un manifiesto llamado `xVirtualMachine.psd1` que contenga la línea siguiente.</span><span class="sxs-lookup"><span data-stu-id="ab38d-120">You also need to create a manifest named `xVirtualMachine.psd1` that contains the following line.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

> [!NOTE]
> <span data-ttu-id="ab38d-121">Esto es además de `MyDscResources.psd1`, el manifiesto del módulo para todos los recursos de la carpeta `MyDscResources`.</span><span class="sxs-lookup"><span data-stu-id="ab38d-121">This is in addition to `MyDscResources.psd1`, the module manifest for all resources under the `MyDscResources` folder.</span></span>

<span data-ttu-id="ab38d-122">Cuando haya terminado, la estructura de carpetas debería ser la siguiente.</span><span class="sxs-lookup"><span data-stu-id="ab38d-122">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
        |- MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="ab38d-123">El recurso ahora es detectable mediante el cmdlet `Get-DscResource` y sus propiedades las puede detectar cualquier cmdlet o mediante la función de autocompletar <kbd>Ctrl</kbd>+<kbd>Espacio</kbd> en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ab38d-123">The resource is now discoverable by using the `Get-DscResource` cmdlet, and its properties are discoverable by either that cmdlet or by using <kbd>Ctrl</kbd>+<kbd>Space</kbd> autocomplete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="ab38d-124">Uso del recurso compuesto</span><span class="sxs-lookup"><span data-stu-id="ab38d-124">Using the composite resource</span></span>

<span data-ttu-id="ab38d-125">A continuación, se crea una configuración que llama al recurso compuesto.</span><span class="sxs-lookup"><span data-stu-id="ab38d-125">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="ab38d-126">Esta configuración llama al recurso compuesto xVirtualMachine para crear una máquina virtual y después llama al recurso **xComputer** para cambiar su nombre.</span><span class="sxs-lookup"><span data-stu-id="ab38d-126">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

```powershell
configuration RenameVM
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

<span data-ttu-id="ab38d-127">También puede usar este recurso para crear varias máquinas virtuales, para lo cual pasará una matriz de nombres de máquina virtual al recurso xVirtualMachine.</span><span class="sxs-lookup"><span data-stu-id="ab38d-127">You can also use this resource to create multiple VMs by passing in an array of VM names to the xVirtualMachine resource.</span></span>

```PowerShell
Configuration MultipleVms
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VMs
        {
            VMName = "IIS01", "SQL01", "SQL02"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="ab38d-128">Compatibilidad con PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ab38d-128">Supporting PsDscRunAsCredential</span></span>

> [!NOTE]
> <span data-ttu-id="ab38d-129">**PsDscRunAsCredential** es compatible con PowerShell 5.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="ab38d-129">**PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="ab38d-130">La propiedad **PsDscRunAsCredential** se puede usar en el bloque de recursos de [configuraciones de DSC](../configurations/configurations.md) para especificar que el recurso se debe ejecutar bajo un conjunto especificado de credenciales.</span><span class="sxs-lookup"><span data-stu-id="ab38d-130">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span> <span data-ttu-id="ab38d-131">Para más información, consulte [DSC de ejecución con las credenciales de usuario](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="ab38d-131">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="ab38d-132">Para tener acceso al contexto de usuario desde un recurso personalizado, puede usar la variable automática `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="ab38d-132">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="ab38d-133">Por ejemplo, el código siguiente podría escribir el contexto de usuario bajo el cual se ejecuta el recurso en el flujo de salida detallado:</span><span class="sxs-lookup"><span data-stu-id="ab38d-133">For example, the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="ab38d-134">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ab38d-134">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="ab38d-135">Conceptos</span><span class="sxs-lookup"><span data-stu-id="ab38d-135">Concepts</span></span>

- [<span data-ttu-id="ab38d-136">Escribir un recurso de DSC personalizado con MOF</span><span class="sxs-lookup"><span data-stu-id="ab38d-136">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="ab38d-137">Introducción a la configuración de estado deseado de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab38d-137">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)
