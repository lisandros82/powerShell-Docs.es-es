---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Update-Module
ms.openlocfilehash: 66535cd5b1f44e108c2bc47fa343c77c86bb21dc
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2017
---
# <a name="update-module"></a><span data-ttu-id="1bfe2-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="1bfe2-103">Update-Module</span></span>

<span data-ttu-id="1bfe2-104">Descarga e instala la versión más reciente de los módulos especificados desde una galería en línea en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="1bfe2-104">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="1bfe2-105">Descripción</span><span class="sxs-lookup"><span data-stu-id="1bfe2-105">Description</span></span>

<span data-ttu-id="1bfe2-106">El cmdlet Update-Module instala una versión más reciente de un módulo de Windows PowerShell instalado desde la galería en línea mediante la ejecución de Install-Module en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="1bfe2-106">The Update-Module cmdlet installs a newer version of a Windows PowerShell module that was installed from the online gallery by running Install-Module on the local computer.</span></span>

<span data-ttu-id="1bfe2-107">De forma predeterminada, se instala la versión más reciente del módulo especificado que esté disponible en la galería en línea, a menos que especifique la versión requerida.</span><span class="sxs-lookup"><span data-stu-id="1bfe2-107">By default, the newest version of the specified module available in online gallery is installed, unless you specify a required version.</span></span> <span data-ttu-id="1bfe2-108">Puede actualizar un módulo instalado especificando el nombre del módulo. Update-Module busca $env:PSModulePath para el módulo que quiere actualizar.</span><span class="sxs-lookup"><span data-stu-id="1bfe2-108">You can update an existing, installed module by specifying the name of the module; Update-Module searches $env:PSModulePath for the module that you want to update.</span></span>

<span data-ttu-id="1bfe2-109">Si ejecuta Update-Module sin el parámetro Name, se actualizan todos los módulos que se pueden actualizar en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="1bfe2-109">Running Update-Module without the Name parameter updates all modules that can be updated on the local computer.</span></span>

### <a name="notes"></a><span data-ttu-id="1bfe2-110">Notas</span><span class="sxs-lookup"><span data-stu-id="1bfe2-110">Notes</span></span>

- <span data-ttu-id="1bfe2-111">Este cmdlet se ejecuta en Windows PowerShell 3.0 o versiones posteriores de Windows PowerShell, en Windows 7 o Windows 2008 R2 y versiones posteriores de Windows.</span><span class="sxs-lookup"><span data-stu-id="1bfe2-111">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>
- <span data-ttu-id="1bfe2-112">Si el módulo que se especifica con el parámetro Name no se instaló mediante Install-Module, se produce un error.</span><span class="sxs-lookup"><span data-stu-id="1bfe2-112">If the module that you specify with the Name parameter was not installed by using Install-Module, an error occurs.</span></span> <span data-ttu-id="1bfe2-113">Update-Module solo se puede ejecutar en los módulos instalados desde la galería en línea mediante la ejecución de Install-Module.</span><span class="sxs-lookup"><span data-stu-id="1bfe2-113">You can only run Update-Module on modules that you installed from the online gallery by running Install-Module.</span></span>
- <span data-ttu-id="1bfe2-114">Si Update-Module intenta actualizar archivos binarios que están en uso, Update-Module devuelve un error que identifica los procesos con problemas e informa al usuario de que vuelva a intentar ejecutar Update-Module después de detener los procesos.</span><span class="sxs-lookup"><span data-stu-id="1bfe2-114">If Update-Module attempts to update binaries that are in use, Update-Module returns an error that identifies the problem processes, and informs the user to retry Update-Module after stopping the processes.</span></span>
- <span data-ttu-id="1bfe2-115">En PowerShell 5.0 o versiones más recientes, cuando Update-Module actualiza un módulo, agrega la versión más reciente (o especificada) del módulo, por lo que las versiones anterior y reciente se encuentran ahora en paralelo en el mismo directorio.</span><span class="sxs-lookup"><span data-stu-id="1bfe2-115">On PowerShell 5.0 or newer versions, when Update-Module updates a module, it adds the latest (or specified) version of the module, so the older and newer versions are now side-by-side in the same directory.</span></span> <span data-ttu-id="1bfe2-116">Sería útil indicarlo y mostrar un ejemplo de la salida de estos comandos.</span><span class="sxs-lookup"><span data-stu-id="1bfe2-116">It would be useful to say so and to show an example of the output from these commands.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="1bfe2-117">Sintaxis de cmdlet</span><span class="sxs-lookup"><span data-stu-id="1bfe2-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="1bfe2-118">Referencia de la ayuda en línea de cmdlet</span><span class="sxs-lookup"><span data-stu-id="1bfe2-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="1bfe2-119">Update-Module</span><span class="sxs-lookup"><span data-stu-id="1bfe2-119">Update-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a><span data-ttu-id="1bfe2-120">Comandos de ejemplo</span><span class="sxs-lookup"><span data-stu-id="1bfe2-120">Example commands</span></span>

```powershell
PS C:\windows\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\windows\system32> Update-Module -Name ContosoServer
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```

### <a name="update-the-module-with-a-prerelease-version-requires--allowprerelease-flag"></a><span data-ttu-id="1bfe2-121">Para actualizar el módulo con una versión preliminar, se necesita la marca -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="1bfe2-121">Update the module with a prerelease version, requires -AllowPrerelease flag</span></span>
```powershell
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module

PS C:\windows\system32> Find-Module ContosoServer -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
3.0.0-alpha    ConstosoServer                      MSPSGallery          The PowerShell Contoso Server deployment tools...

PS C:\windows\system32> Update-Module -Name ContosoServer -AllowPrerelease
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
3.0.0-alpha ContosoServer MSPSGallery ContosoServer module

```


### <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a><span data-ttu-id="1bfe2-122">Actualice el módulo TestDepWithNestedRequiredModules1 con dependencias.</span><span class="sxs-lookup"><span data-stu-id="1bfe2-122">Update the TestDepWithNestedRequiredModules1 module with dependencies.</span></span>
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module



```

