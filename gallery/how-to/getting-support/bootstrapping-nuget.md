---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Arranque de NuGet
ms.openlocfilehash: 6d8f106bc3b8741203e87e4c097948a843f06d6e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679728"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="ada98-103">Arrancar el proveedor de NuGet y NuGet.exe</span><span class="sxs-lookup"><span data-stu-id="ada98-103">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="ada98-104">El proveedor de NuGet más reciente no incluye NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="ada98-104">NuGet.exe is not included in the latest NuGet provider.</span></span> <span data-ttu-id="ada98-105">Para operaciones de publicación de un módulo o script, PowerShellGet requiere el archivo ejecutable binario NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="ada98-105">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span> <span data-ttu-id="ada98-106">Solo se requiere el proveedor de NuGet para todas las demás operaciones, como *buscar*, *instalar*, *guardar* y *desinstalar*.</span><span class="sxs-lookup"><span data-stu-id="ada98-106">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="ada98-107">PowerShell incluye una lógica para controlar un arranque combinado del proveedor de NuGet y NuGet.exe o el arranque únicamente del proveedor de NuGet.</span><span class="sxs-lookup"><span data-stu-id="ada98-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span> <span data-ttu-id="ada98-108">Cualquiera sea el caso, solo debe haber un mensaje de solicitud.</span><span class="sxs-lookup"><span data-stu-id="ada98-108">In either case, only a single prompt message should occur.</span></span> <span data-ttu-id="ada98-109">Si la máquina no está conectada a Internet, el usuario o un administrador debe copiar una instancia de confianza del proveedor de NuGet o del archivo NuGet.exe en la máquina desconectada.</span><span class="sxs-lookup"><span data-stu-id="ada98-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

> [!NOTE]
> <span data-ttu-id="ada98-110">A partir de la versión 6, el proveedor de NuGet se incluye en la instalación de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ada98-110">Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span>

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="ada98-111">Resolución de errores cuando el proveedor de NuGet no está instalado en una máquina conectada a Internet</span><span class="sxs-lookup"><span data-stu-id="ada98-111">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="ada98-112">Resolución de errores cuando el proveedor de NuGet está disponible y NuGet.exe no lo está durante la operación de publicación en una máquina conectada a Internet</span><span class="sxs-lookup"><span data-stu-id="ada98-112">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="ada98-113">Resolución de errores cuando ni el proveedor de NuGet ni NuGet.exe están disponibles durante la operación de publicación en una máquina conectada a Internet</span><span class="sxs-lookup"><span data-stu-id="ada98-113">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="ada98-114">Arranque manual del proveedor de NuGet en una máquina no conectada a Internet</span><span class="sxs-lookup"><span data-stu-id="ada98-114">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="ada98-115">En los procesos mostrados anteriormente se presume que la máquina está conectada a Internet y que se pueden descargar archivos desde una ubicación pública.</span><span class="sxs-lookup"><span data-stu-id="ada98-115">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span> <span data-ttu-id="ada98-116">Si no es posible, la única opción es arrancar una máquina con los procesos mencionados y copiar manualmente el proveedor en el nodo aislado a través de un proceso de confianza sin conexión.</span><span class="sxs-lookup"><span data-stu-id="ada98-116">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span> <span data-ttu-id="ada98-117">El caso de uso más común de este escenario se da cuando una galería privada está disponible para admitir un entorno aislado.</span><span class="sxs-lookup"><span data-stu-id="ada98-117">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="ada98-118">Después de seguir el proceso anterior para arrancar una máquina conectada a Internet, encontrará los archivos de proveedor en esta ubicación:</span><span class="sxs-lookup"><span data-stu-id="ada98-118">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

`C:\Program Files\PackageManagement\ProviderAssemblies\`

<span data-ttu-id="ada98-119">La estructura de carpetas/archivos del proveedor de NuGet será la siguiente (posiblemente con un número de versión distinto):</span><span class="sxs-lookup"><span data-stu-id="ada98-119">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

<span data-ttu-id="ada98-120">Copie estas carpetas y archivos con un proceso de confianza en las máquinas sin conexión.</span><span class="sxs-lookup"><span data-stu-id="ada98-120">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="ada98-121">Arranque manual de NuGet.exe para admitir operaciones de publicación en una máquina no conectada a Internet</span><span class="sxs-lookup"><span data-stu-id="ada98-121">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="ada98-122">Además del proceso para arrancar manualmente el proveedor de NuGet, si la máquina se usará para publicar módulos o scripts en una galería privada con los cmdlets `Publish-Module` o `Publish-Script`, se requerirá el archivo ejecutable binario NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="ada98-122">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the `Publish-Module` or `Publish-Script` cmdlets, the NuGet.exe binary executable file will be required.</span></span>

<span data-ttu-id="ada98-123">El caso de uso más común de este escenario se da cuando una galería privada está disponible para admitir un entorno aislado.</span><span class="sxs-lookup"><span data-stu-id="ada98-123">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span> <span data-ttu-id="ada98-124">Hay dos opciones para obtener el archivo NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="ada98-124">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="ada98-125">Una opción es arrancar una máquina conectada a Internet y copiar los archivos en las máquinas sin conexión mediante un proceso de confianza.</span><span class="sxs-lookup"><span data-stu-id="ada98-125">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span> <span data-ttu-id="ada98-126">Después de arrancar la máquina conectada a Internet, el archivo binario NuGet.exe se ubicará en una de estas dos carpetas:</span><span class="sxs-lookup"><span data-stu-id="ada98-126">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="ada98-127">Si los cmdlets `Publish-Module` o `Publish-Script` se ejecutaron con permisos elevados (como administrador):</span><span class="sxs-lookup"><span data-stu-id="ada98-127">If the `Publish-Module` or `Publish-Script` cmdlets were executed with elevated permissions (As an Administrator):</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="ada98-128">Si los cmdlets se ejecutaron como usuario sin permisos elevados:</span><span class="sxs-lookup"><span data-stu-id="ada98-128">If the cmdlets were executed as a user without elevated permissions:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="ada98-129">Una segunda opción es descargar NuGet.exe desde el sitio web NuGet.Org: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads)Cuando se selecciona una versión de NuGet para máquinas de producción, asegúrese de que sea una versión posterior a 2.8.5.208 e identifique la versión etiquetada como "recomendada".</span><span class="sxs-lookup"><span data-stu-id="ada98-129">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span> <span data-ttu-id="ada98-130">Recuerde desbloquear el archivo si se descargó con un explorador.</span><span class="sxs-lookup"><span data-stu-id="ada98-130">Remember to unblock the file if it was downloaded using a browser.</span></span> <span data-ttu-id="ada98-131">Para ello, use el cmdlet `Unblock-File`.</span><span class="sxs-lookup"><span data-stu-id="ada98-131">This can be performed by using the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="ada98-132">En cualquier caso, el archivo NuGet.exe se puede copiar a cualquier ubicación en `$env:path`, pero las ubicaciones estándar son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="ada98-132">In either case, the NuGet.exe file can be copied to any location in `$env:path`, but the standard locations are:</span></span>

<span data-ttu-id="ada98-133">Para hacer que el ejecutable esté disponible para que todos los usuarios puedan usar los cmdlets `Publish-Module` y `Publish-Script`:</span><span class="sxs-lookup"><span data-stu-id="ada98-133">To make the executable available so that all users can use `Publish-Module` and `Publish-Script` cmdlets:</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="ada98-134">Para hacer que el ejecutable esté disponible solo para un usuario específico, cópielo en la ubicación solo dentro del perfil de ese usuario:</span><span class="sxs-lookup"><span data-stu-id="ada98-134">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```
