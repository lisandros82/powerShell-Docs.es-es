---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Escribir un recurso de DSC personalizado con clases de PowerShell
ms.openlocfilehash: 34356f65bcb83153e7395a16d2a4a5cf2e507332
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952832"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="b839a-103">Escribir un recurso de DSC personalizado con clases de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b839a-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="b839a-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b839a-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="b839a-105">Con la introducción de las clases de PowerShell en Windows PowerShell 5.0, ahora puede definir un recurso de DSC mediante la creación de una clase.</span><span class="sxs-lookup"><span data-stu-id="b839a-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="b839a-106">La clase define el esquema y la implementación del recurso, así que no hay necesidad de crear un archivo MOF independiente.</span><span class="sxs-lookup"><span data-stu-id="b839a-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="b839a-107">La estructura de carpetas de un recurso basado en clases también es más sencilla, porque no es necesaria una carpeta **DSCResources**.</span><span class="sxs-lookup"><span data-stu-id="b839a-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="b839a-108">En un recurso de DSC basados en clases, el esquema se define como propiedades de la clase que se pueden modificar con atributos para especificar el tipo de propiedad.</span><span class="sxs-lookup"><span data-stu-id="b839a-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="b839a-109">El recurso se implementa con los métodos **Get()** , **Set()** y **Test()** (equivalentes a las funciones **Get-TargetResource**, **Set-TargetResource** y **Test-TargetResource** en un recurso de script).</span><span class="sxs-lookup"><span data-stu-id="b839a-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="b839a-110">En este tema, se creará un recurso simple denominado **FileResource** que administra un archivo en una ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="b839a-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="b839a-111">Para más información sobre los recursos DSC, consulte [Crear recursos de configuración de estado deseado de Windows PowerShell personalizados](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="b839a-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="b839a-112">**Nota:** Los recursos basados en clases no admiten colecciones genéricas.</span><span class="sxs-lookup"><span data-stu-id="b839a-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="b839a-113">Estructura de carpetas de un recurso de clase</span><span class="sxs-lookup"><span data-stu-id="b839a-113">Folder structure for a class resource</span></span>

<span data-ttu-id="b839a-114">Para implementar un recurso de DSC personalizado con una clase de PowerShell, cree la siguiente estructura de carpetas.</span><span class="sxs-lookup"><span data-stu-id="b839a-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="b839a-115">La clase se define en **MyDscResource.psm1** y el manifiesto del módulo se define en **MyDscResource.psd1**.</span><span class="sxs-lookup"><span data-stu-id="b839a-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="b839a-116">Crear la clase</span><span class="sxs-lookup"><span data-stu-id="b839a-116">Create the class</span></span>

<span data-ttu-id="b839a-117">Utilice la palabra clave class para crear una clase de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b839a-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="b839a-118">Para especificar que una clase es un recurso de DSC, use el atributo **DscResource()** .</span><span class="sxs-lookup"><span data-stu-id="b839a-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="b839a-119">El nombre de la clase es el nombre del recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="b839a-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="b839a-120">Declarar propiedades</span><span class="sxs-lookup"><span data-stu-id="b839a-120">Declare properties</span></span>

<span data-ttu-id="b839a-121">El esquema de recursos de DSC se define como propiedades de la clase.</span><span class="sxs-lookup"><span data-stu-id="b839a-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="b839a-122">Se declaran tres propiedades como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="b839a-122">We declare three properties as follows.</span></span>

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

<span data-ttu-id="b839a-123">Observe que las propiedades se modifican mediante atributos.</span><span class="sxs-lookup"><span data-stu-id="b839a-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="b839a-124">El significado de los atributos es el que se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="b839a-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="b839a-125">**DscProperty(Key)** : La propiedad es obligatoria.</span><span class="sxs-lookup"><span data-stu-id="b839a-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="b839a-126">Se trata de una clave.</span><span class="sxs-lookup"><span data-stu-id="b839a-126">The property is a key.</span></span> <span data-ttu-id="b839a-127">Los valores de todas las propiedades marcadas como claves deben combinarse para identificar de forma única la instancia de un recurso dentro de una configuración.</span><span class="sxs-lookup"><span data-stu-id="b839a-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="b839a-128">**DscProperty(Mandatory)** : La propiedad es obligatoria.</span><span class="sxs-lookup"><span data-stu-id="b839a-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="b839a-129">**DscProperty(NotConfigurable)** : La propiedad es de solo lectura.</span><span class="sxs-lookup"><span data-stu-id="b839a-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="b839a-130">Las propiedades marcadas con este atributo no se pueden establecer mediante una configuración, pero se rellenan con el método **Get()** cuando existe.</span><span class="sxs-lookup"><span data-stu-id="b839a-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="b839a-131">**DscProperty()** : La propiedad se puede configurar, pero no es obligatoria.</span><span class="sxs-lookup"><span data-stu-id="b839a-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="b839a-132">Las propiedades **$Path** y **$SourcePath** son cadenas.</span><span class="sxs-lookup"><span data-stu-id="b839a-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="b839a-133">**$CreationTime** es una propiedad [DateTime](/dotnet/api/system.datetime).</span><span class="sxs-lookup"><span data-stu-id="b839a-133">The **$CreationTime** is a [DateTime](/dotnet/api/system.datetime) property.</span></span> <span data-ttu-id="b839a-134">La propiedad **$Ensure** es un tipo de enumeración, que se define como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="b839a-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="b839a-135">Implementar los métodos</span><span class="sxs-lookup"><span data-stu-id="b839a-135">Implementing the methods</span></span>

<span data-ttu-id="b839a-136">Los métodos **Get()** , **Set()** y **Test()** son análogos a las funciones **Get-TargetResource**, **Set-TargetResource** y **Test-TargetResource** de un recurso de script.</span><span class="sxs-lookup"><span data-stu-id="b839a-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="b839a-137">Este código también incluye la función CopyFile(), una función del asistente que copia el archivo de **$SourcePath** a **$Path**.</span><span class="sxs-lookup"><span data-stu-id="b839a-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span>

```powershell
    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### <a name="the-complete-file"></a><span data-ttu-id="b839a-138">El archivo completo</span><span class="sxs-lookup"><span data-stu-id="b839a-138">The complete file</span></span>

<span data-ttu-id="b839a-139">A continuación se muestra el archivo de clases completo.</span><span class="sxs-lookup"><span data-stu-id="b839a-139">The complete class file follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```

## <a name="create-a-manifest"></a><span data-ttu-id="b839a-140">Crear un manifiesto</span><span class="sxs-lookup"><span data-stu-id="b839a-140">Create a manifest</span></span>

<span data-ttu-id="b839a-141">Para que un recurso basado en clases esté disponible para el motor de DSC, debe incluir una instrucción **DscResourcesToExport** en el archivo de manifiesto que indique al módulo que se exporten los recursos.</span><span class="sxs-lookup"><span data-stu-id="b839a-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="b839a-142">El manifiesto tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="b839a-142">Our manifest looks like this:</span></span>

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
}
```

## <a name="test-the-resource"></a><span data-ttu-id="b839a-143">Probar el recurso</span><span class="sxs-lookup"><span data-stu-id="b839a-143">Test the resource</span></span>

<span data-ttu-id="b839a-144">Después de guardar la clase y los archivos de manifiesto en la estructura de carpetas tal y como se describió anteriormente, puede crear una configuración que utilice el nuevo recurso.</span><span class="sxs-lookup"><span data-stu-id="b839a-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="b839a-145">Para obtener información sobre cómo ejecutar una configuración DSC, consulte [Establecer configuraciones](../pull-server/enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="b839a-145">For information about how to run a DSC configuration, see [Enacting configurations](../pull-server/enactingConfigurations.md).</span></span> <span data-ttu-id="b839a-146">La configuración siguiente comprobará si existe el archivo en `c:\test\test.txt` y, si no es así, copia el archivo desde `c:\test.txt` (debe crear `c:\test.txt` antes de ejecutar la configuración).</span><span class="sxs-lookup"><span data-stu-id="b839a-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="b839a-147">Compatibilidad con PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="b839a-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="b839a-148">**Nota:** **PsDscRunAsCredential** es compatible con PowerShell 5.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b839a-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="b839a-149">La propiedad **PsDscRunAsCredential** se puede usar en el bloque de recursos de [configuraciones de DSC](../configurations/configurations.md) para especificar que el recurso se debe ejecutar bajo un conjunto especificado de credenciales.</span><span class="sxs-lookup"><span data-stu-id="b839a-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="b839a-150">Para más información, consulte [DSC de ejecución con las credenciales de usuario](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="b839a-150">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="b839a-151">Exigir o impedir PsDscRunAsCredential para el recurso</span><span class="sxs-lookup"><span data-stu-id="b839a-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="b839a-152">El atributo **DscResource()** toma un parámetro opcional **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="b839a-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="b839a-153">Este parámetro toma uno de estos tres valores:</span><span class="sxs-lookup"><span data-stu-id="b839a-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="b839a-154">`Optional` **PsDscRunAsCredential** es opcional para las configuraciones que llaman a este recurso.</span><span class="sxs-lookup"><span data-stu-id="b839a-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="b839a-155">Este es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="b839a-155">This is the default value.</span></span>
- <span data-ttu-id="b839a-156">`Mandatory` **PsDscRunAsCredential** se debe usar para cada configuración que llama a este recurso.</span><span class="sxs-lookup"><span data-stu-id="b839a-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="b839a-157">`NotSupported` Las configuraciones que llaman a este recurso no pueden usar **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="b839a-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="b839a-158">`Default` Igual que `Optional`.</span><span class="sxs-lookup"><span data-stu-id="b839a-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="b839a-159">Por ejemplo, use el atributo siguiente para especificar que el recurso personalizado no admite el uso de **PsDscRunAsCredential**:</span><span class="sxs-lookup"><span data-stu-id="b839a-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a><span data-ttu-id="b839a-160">Declaración de varios recursos de clase en un módulo</span><span class="sxs-lookup"><span data-stu-id="b839a-160">Declaring multiple class resources in a module</span></span>

<span data-ttu-id="b839a-161">Un módulo puede definir varios recursos de DSC basados en clases.</span><span class="sxs-lookup"><span data-stu-id="b839a-161">A module can define multiple class based DSC resources.</span></span> <span data-ttu-id="b839a-162">Puede crear la estructura de carpetas de las maneras siguientes:</span><span class="sxs-lookup"><span data-stu-id="b839a-162">You can create the folder structure in the following ways:</span></span>

1. <span data-ttu-id="b839a-163">Defina el primer recurso en el archivo "<ModuleName>.psm1" y los recursos siguientes en la carpeta **DSCResources**.</span><span class="sxs-lookup"><span data-stu-id="b839a-163">Define the first resource in the "<ModuleName>.psm1" file and subsequent resources under the **DSCResources** folder.</span></span>

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

2. <span data-ttu-id="b839a-164">Defina todos los recursos en la carpeta **DSCResources**.</span><span class="sxs-lookup"><span data-stu-id="b839a-164">Define all resources under the **DSCResources** folder.</span></span>

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- FirstResource.psm1
              SecondResource.psm1
   ```

> [!NOTE]
> <span data-ttu-id="b839a-165">En los ejemplos anteriores, agregue cualquier archivo PSM1 bajo **DSCResources** a la clave **NestedModules** en su archivo PSD1.</span><span class="sxs-lookup"><span data-stu-id="b839a-165">In the examples above, add any PSM1 files under the **DSCResources** to the **NestedModules** key in your PSD1 file.</span></span>

### <a name="access-the-user-context"></a><span data-ttu-id="b839a-166">Acceso al contexto de usuario</span><span class="sxs-lookup"><span data-stu-id="b839a-166">Access the user context</span></span>

<span data-ttu-id="b839a-167">Para tener acceso al contexto de usuario desde un recurso personalizado, puede usar la variable automática `$global:PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="b839a-167">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="b839a-168">Por ejemplo, el código siguiente podría escribir el contexto de usuario bajo el cual se ejecuta el recurso en el flujo de salida detallado:</span><span class="sxs-lookup"><span data-stu-id="b839a-168">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="b839a-169">Véase también</span><span class="sxs-lookup"><span data-stu-id="b839a-169">See Also</span></span>

[<span data-ttu-id="b839a-170">Crear recursos de configuración de estado deseado de Windows PowerShell personalizados</span><span class="sxs-lookup"><span data-stu-id="b839a-170">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)
