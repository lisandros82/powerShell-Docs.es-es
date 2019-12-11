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
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a>Escribir un recurso de DSC personalizado con clases de PowerShell

> Se aplica a: Windows PowerShell 5.0

Con la introducción de las clases de PowerShell en Windows PowerShell 5.0, ahora puede definir un recurso de DSC mediante la creación de una clase. La clase define el esquema y la implementación del recurso, así que no hay necesidad de crear un archivo MOF independiente. La estructura de carpetas de un recurso basado en clases también es más sencilla, porque no es necesaria una carpeta **DSCResources**.

En un recurso de DSC basados en clases, el esquema se define como propiedades de la clase que se pueden modificar con atributos para especificar el tipo de propiedad. El recurso se implementa con los métodos **Get()** , **Set()** y **Test()** (equivalentes a las funciones **Get-TargetResource**, **Set-TargetResource** y **Test-TargetResource** en un recurso de script).

En este tema, se creará un recurso simple denominado **FileResource** que administra un archivo en una ruta de acceso especificada.

Para más información sobre los recursos DSC, consulte [Crear recursos de configuración de estado deseado de Windows PowerShell personalizados](authoringResource.md).

>**Nota:** Los recursos basados en clases no admiten colecciones genéricas.

## <a name="folder-structure-for-a-class-resource"></a>Estructura de carpetas de un recurso de clase

Para implementar un recurso de DSC personalizado con una clase de PowerShell, cree la siguiente estructura de carpetas. La clase se define en **MyDscResource.psm1** y el manifiesto del módulo se define en **MyDscResource.psd1**.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a>Crear la clase

Utilice la palabra clave class para crear una clase de PowerShell. Para especificar que una clase es un recurso de DSC, use el atributo **DscResource()** . El nombre de la clase es el nombre del recurso de DSC.

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a>Declarar propiedades

El esquema de recursos de DSC se define como propiedades de la clase. Se declaran tres propiedades como se indica a continuación.

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

Observe que las propiedades se modifican mediante atributos. El significado de los atributos es el que se muestra a continuación:

- **DscProperty(Key)** : La propiedad es obligatoria. Se trata de una clave. Los valores de todas las propiedades marcadas como claves deben combinarse para identificar de forma única la instancia de un recurso dentro de una configuración.
- **DscProperty(Mandatory)** : La propiedad es obligatoria.
- **DscProperty(NotConfigurable)** : La propiedad es de solo lectura. Las propiedades marcadas con este atributo no se pueden establecer mediante una configuración, pero se rellenan con el método **Get()** cuando existe.
- **DscProperty()** : La propiedad se puede configurar, pero no es obligatoria.

Las propiedades **$Path** y **$SourcePath** son cadenas. **$CreationTime** es una propiedad [DateTime](/dotnet/api/system.datetime). La propiedad **$Ensure** es un tipo de enumeración, que se define como se indica a continuación.

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a>Implementar los métodos

Los métodos **Get()** , **Set()** y **Test()** son análogos a las funciones **Get-TargetResource**, **Set-TargetResource** y **Test-TargetResource** de un recurso de script.

Este código también incluye la función CopyFile(), una función del asistente que copia el archivo de **$SourcePath** a **$Path**.

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

### <a name="the-complete-file"></a>El archivo completo

A continuación se muestra el archivo de clases completo.

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

## <a name="create-a-manifest"></a>Crear un manifiesto

Para que un recurso basado en clases esté disponible para el motor de DSC, debe incluir una instrucción **DscResourcesToExport** en el archivo de manifiesto que indique al módulo que se exporten los recursos. El manifiesto tiene este aspecto:

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

## <a name="test-the-resource"></a>Probar el recurso

Después de guardar la clase y los archivos de manifiesto en la estructura de carpetas tal y como se describió anteriormente, puede crear una configuración que utilice el nuevo recurso. Para obtener información sobre cómo ejecutar una configuración DSC, consulte [Establecer configuraciones](../pull-server/enactingConfigurations.md). La configuración siguiente comprobará si existe el archivo en `c:\test\test.txt` y, si no es así, copia el archivo desde `c:\test.txt` (debe crear `c:\test.txt` antes de ejecutar la configuración).

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

## <a name="supporting-psdscrunascredential"></a>Compatibilidad con PsDscRunAsCredential

>**Nota:** **PsDscRunAsCredential** es compatible con PowerShell 5.0 y versiones posteriores.

La propiedad **PsDscRunAsCredential** se puede usar en el bloque de recursos de [configuraciones de DSC](../configurations/configurations.md) para especificar que el recurso se debe ejecutar bajo un conjunto especificado de credenciales.
Para más información, consulte [DSC de ejecución con las credenciales de usuario](../configurations/runAsUser.md).

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a>Exigir o impedir PsDscRunAsCredential para el recurso

El atributo **DscResource()** toma un parámetro opcional **RunAsCredential**.
Este parámetro toma uno de estos tres valores:

- `Optional` **PsDscRunAsCredential** es opcional para las configuraciones que llaman a este recurso. Este es el valor predeterminado.
- `Mandatory` **PsDscRunAsCredential** se debe usar para cada configuración que llama a este recurso.
- `NotSupported` Las configuraciones que llaman a este recurso no pueden usar **PsDscRunAsCredential**.
- `Default` Igual que `Optional`.

Por ejemplo, use el atributo siguiente para especificar que el recurso personalizado no admite el uso de **PsDscRunAsCredential**:

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a>Declaración de varios recursos de clase en un módulo

Un módulo puede definir varios recursos de DSC basados en clases. Puede crear la estructura de carpetas de las maneras siguientes:

1. Defina el primer recurso en el archivo "<ModuleName>.psm1" y los recursos siguientes en la carpeta **DSCResources**.

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

2. Defina todos los recursos en la carpeta **DSCResources**.

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
> En los ejemplos anteriores, agregue cualquier archivo PSM1 bajo **DSCResources** a la clave **NestedModules** en su archivo PSD1.

### <a name="access-the-user-context"></a>Acceso al contexto de usuario

Para tener acceso al contexto de usuario desde un recurso personalizado, puede usar la variable automática `$global:PsDscContext`.

Por ejemplo, el código siguiente podría escribir el contexto de usuario bajo el cual se ejecuta el recurso en el flujo de salida detallado:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Véase también

[Crear recursos de configuración de estado deseado de Windows PowerShell personalizados](authoringResource.md)
