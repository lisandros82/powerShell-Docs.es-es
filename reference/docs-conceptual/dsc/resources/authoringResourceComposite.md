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
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Recursos compuestos: uso de una configuración DSC como un recurso

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

En situaciones del mundo real, las configuraciones pueden acabar siendo largas y complejas, con llamadas a muchos recursos diferentes y estableciendo una gran cantidad de propiedades. Para ayudar a abordar esta complejidad, puede utilizar una configuración de estado deseado (DSC) de Windows PowerShell como recurso para otras configuraciones. Esto se denomina "recurso compuesto". Un recurso compuesto es una configuración DSC que toma parámetros. Los parámetros de la configuración actúan como las propiedades del recurso. La configuración se guarda como un archivo con una extensión `.schema.psm1`. Toma el lugar del esquema MOF y del script de recurso en un recurso de DSC típico. Para más información sobre los recursos DSC, consulte [Recursos de Desired State Configuration de Windows PowerShell](resources.md).

## <a name="creating-the-composite-resource"></a>Creación del recurso compuesto

En nuestro ejemplo, se creará una configuración que invoca un número de recursos existentes para configurar las máquinas virtuales. En lugar de especificar los valores que se establecerán en bloques de configuración, la configuración toma parámetros que se utilizan en los bloques de configuración.

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
> DSC no admite actualmente la colocación de recursos compuestos o configuraciones anidadas dentro de un recurso compuesto.

### <a name="saving-the-configuration-as-a-composite-resource"></a>Guardar la configuración como un recurso compuesto

Para usar la configuración con parámetros como un recurso de DSC, guárdela en una estructura de directorios similar a la de cualquier otro recurso basado en MOF y asígnele un nombre con una extensión `.schema.psm1`. En este ejemplo, usamos el archivo `xVirtualMachine.schema.psm1`. También deberá crear un manifiesto llamado `xVirtualMachine.psd1` que contenga la línea siguiente.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

> [!NOTE]
> Esto es además de `MyDscResources.psd1`, el manifiesto del módulo para todos los recursos de la carpeta `MyDscResources`.

Cuando haya terminado, la estructura de carpetas debería ser la siguiente.

```
$env: psmodulepath
    |- MyDscResources
        |- MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

El recurso ahora es detectable mediante el cmdlet `Get-DscResource` y sus propiedades las puede detectar cualquier cmdlet o mediante la función de autocompletar <kbd>Ctrl</kbd>+<kbd>Espacio</kbd> en Windows PowerShell ISE.

## <a name="using-the-composite-resource"></a>Uso del recurso compuesto

A continuación, se crea una configuración que llama al recurso compuesto. Esta configuración llama al recurso compuesto xVirtualMachine para crear una máquina virtual y después llama al recurso **xComputer** para cambiar su nombre.

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

También puede usar este recurso para crear varias máquinas virtuales, para lo cual pasará una matriz de nombres de máquina virtual al recurso xVirtualMachine.

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

## <a name="supporting-psdscrunascredential"></a>Compatibilidad con PsDscRunAsCredential

> [!NOTE]
> **PsDscRunAsCredential** es compatible con PowerShell 5.0 y versiones posteriores.

La propiedad **PsDscRunAsCredential** se puede usar en el bloque de recursos de [configuraciones de DSC](../configurations/configurations.md) para especificar que el recurso se debe ejecutar bajo un conjunto especificado de credenciales. Para más información, consulte [DSC de ejecución con las credenciales de usuario](../configurations/runAsUser.md).

Para tener acceso al contexto de usuario desde un recurso personalizado, puede usar la variable automática `$PsDscContext`.

Por ejemplo, el código siguiente podría escribir el contexto de usuario bajo el cual se ejecuta el recurso en el flujo de salida detallado:

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Consulte también

### <a name="concepts"></a>Conceptos

- [Escribir un recurso de DSC personalizado con MOF](authoringResourceMOF.md)
- [Introducción a la configuración de estado deseado de Windows PowerShell](../overview/overview.md)
