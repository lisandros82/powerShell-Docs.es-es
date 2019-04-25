---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 042e9a30068d32dc5860255bdec960371121d866
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085310"
---
# <a name="packagemanagement-cmdlets"></a><span data-ttu-id="b1eda-102">Cmdlets PackageManagement</span><span class="sxs-lookup"><span data-stu-id="b1eda-102">PackageManagement Cmdlets</span></span>

<span data-ttu-id="b1eda-103">Este es el núcleo de PackageManagement para admitir la detección, la instalación y el inventario de software (SDII).</span><span class="sxs-lookup"><span data-stu-id="b1eda-103">This is the core of PackageManagement to support software discovery, installation, and inventory (SDII).</span></span> <span data-ttu-id="b1eda-104">Pruebe los cmdlets para estas operaciones:</span><span class="sxs-lookup"><span data-stu-id="b1eda-104">Try out the cmdlets for these operations:</span></span>

- `Find-Package`
- `Find-PackageProvider`
- `Get-Package`
- `Get-PackageProvider`
- `Get-PackageSource`
- `Import-PackageProvider`
- `Install-Package`
- `Install-PackageProvider`
- `Register-PackageSource`
- `Save-Package`
- `Set-PackageSource`
- `Uninstall-Package`
- `Unregister-PackageSource`

<span data-ttu-id="b1eda-105">Dado que PackageManagement es un módulo de PowerShell, puede hacer lo siguiente para actualizar PackageManagement:</span><span class="sxs-lookup"><span data-stu-id="b1eda-105">As PackageManagement is a PowerShell module, you can do the following to update PackageManagement itself:</span></span>

```powershell
Install-Module PackageManagement –Force
```

<span data-ttu-id="b1eda-106">En este caso, deberá volver a iniciar una sesión de PowerShell para cambiar a la nueva versión de PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="b1eda-106">In this case, you will have to re-enter PowerShell session to switch to the new version of PackageManagement.</span></span>

## <a name="find-package-cmdletpowershellmodulepackagemanagementfind-package"></a>[<span data-ttu-id="b1eda-107">Cmdlet Find-Package</span><span class="sxs-lookup"><span data-stu-id="b1eda-107">Find-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Find-Package)

<span data-ttu-id="b1eda-108">Este cmdlet permite la detección de paquetes de software en los orígenes de paquetes disponibles mediante los proveedores de paquetes cargados.</span><span class="sxs-lookup"><span data-stu-id="b1eda-108">This cmdlet allows discovery of software packages in available package sources using loaded package providers.</span></span>

```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -ProviderName PowerShellGet -Source as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdletpowershellmodulepackagemanagementfind-packageprovider"></a>[<span data-ttu-id="b1eda-109">Cmdlet Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b1eda-109">Find-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Find-PackageProvider)

<span data-ttu-id="b1eda-110">El cmdlet `Find-PackageProvider` busca proveedores de PackageManagement coincidentes que estén disponibles en los orígenes de paquetes registrados con PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="b1eda-110">The `Find-PackageProvider` cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span> <span data-ttu-id="b1eda-111">Estos son los proveedores de paquetes disponibles para la instalación con el cmdlet `Install-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="b1eda-111">These are package providers available for installation with the `Install-PackageProvider` cmdlet.</span></span> <span data-ttu-id="b1eda-112">De forma predeterminada, se incluyen los módulos disponibles en la Galería de PowerShell con las etiquetas "PackageManagement" y "Provider".</span><span class="sxs-lookup"><span data-stu-id="b1eda-112">By default, this includes modules available in the PowerShell Gallery with the 'PackageManagement' and 'Provider' Tags.</span></span>

<span data-ttu-id="b1eda-113">`Find-PackageProvider` también busca proveedores de PackageManagement coincidentes que estén disponibles en el almacén de blobs de Azure de PackageManagement donde se usa el proveedor de programa previo de PackageManagement para buscarlos e instalarlos.</span><span class="sxs-lookup"><span data-stu-id="b1eda-113">`Find-PackageProvider` also finds matching PackageManagement providers that are available in the PackageManagement azure blob store where we use the PackageManagement boostrapper provider for finding and installing them.</span></span>

```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdletpowershellmodulepackagemanagementget-package"></a>[<span data-ttu-id="b1eda-114">Cmdlet Get-Package</span><span class="sxs-lookup"><span data-stu-id="b1eda-114">Get-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Get-Package)

<span data-ttu-id="b1eda-115">Este cmdlet devuelve una lista de todos los paquetes de software instalados con PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="b1eda-115">This cmdlet returns a list of all software packages that have been installed using PackageManagement.</span></span>

```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdletpowershellmodulepackagemanagementget-packageprovider"></a>[<span data-ttu-id="b1eda-116">Cmdlet Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b1eda-116">Get-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Get-PackageProvider)

<span data-ttu-id="b1eda-117">Los proveedores de paquetes que están cargados y listos para usar en el equipo local pueden incluirse en el inventario mediante el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b1eda-117">Package providers that are loaded and ready to be used on the local machine can be inventoried by using the cmdlet.</span></span>

```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdletpowershellmodulepackagemanagementget-packagesource"></a>[<span data-ttu-id="b1eda-118">Cmdlet Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="b1eda-118">Get-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Get-PackageSource)

<span data-ttu-id="b1eda-119">Este cmdlet obtiene una lista de los orígenes de paquetes que están registrados para un proveedor de paquetes.</span><span class="sxs-lookup"><span data-stu-id="b1eda-119">This cmdlet gets a list of package sources that are registered for a package provider.</span></span>

```powershell
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdletpowershellmodulepackagemanagementimport-packageprovider"></a>[<span data-ttu-id="b1eda-120">Cmdlet Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b1eda-120">Import-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Import-PackageProvider)

<span data-ttu-id="b1eda-121">Este cmdlet agrega proveedores de paquetes de PackageManagement a la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="b1eda-121">This cmdlet adds Package Management package providers to the current session.</span></span>

```powershell
# Import a package provider from the local machine
Import-PackageProvider –Name MyProvider

#The -Name parameter can be either the name of the provider or the full path to the provider. Currently, we support .dll, .exe and.psm1 for the full path case. If the name of the provider is used for the -Name parameter, then additional version parameters such as -RequiredVersion, -MinimumVersion and -MaximumVersion may be specified. Otherwise, the latest version of the provider will be imported.

#If a package provider is not yet loaded to your system, we can discover and install on-demand. You can use explicit discovery and install cmdlets to do so:
 Find-PackageProvider
 Install-PackageProvider –Name MyProvider

#After installed, follow the Import-PackageProvider to load it to your system.

# Import a specific version of a package provider. PackageManagement supports installations of multiple versions of a package provider using PackageProvider cmdlets (not by bootstrapper provider). You can install another version of a package provider given that you already have one up running by:
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider –ListAvailable
Import-PackageProvider –Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
Import-PackageProvider –Name MyProvider –RequiredVersion xxxx -force
```

## <a name="install-package-cmdletpowershellmodulepackagemanagementinstall-package"></a>[<span data-ttu-id="b1eda-122">Cmdlet Install-Package</span><span class="sxs-lookup"><span data-stu-id="b1eda-122">Install-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Install-Package)

<span data-ttu-id="b1eda-123">Este cmdlet permite la instalación de paquetes de software en los orígenes de paquetes disponibles mediante los proveedores de paquetes cargados.</span><span class="sxs-lookup"><span data-stu-id="b1eda-123">This cmdlet allows installation of software packages in available package sources using loaded package providers.</span></span>

```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdletpowershellmodulepackagemanagementinstall-packageprovider"></a>[<span data-ttu-id="b1eda-124">Cmdlet Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b1eda-124">Install-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Install-PackageProvider)

<span data-ttu-id="b1eda-125">Este cmdlet instala uno o varios proveedores de paquetes de PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="b1eda-125">This cmdlet installs one or more Package Management package providers.</span></span>

```powershell
# Install a package provider from the PowerShell Gallery
Install-PackageProvider –Name "Gistprovider" -Verbose

# Install a specified version of a package provider
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force

# Find a provider and install it
Find-PackageProvider –Name "Gistprovider" | Install-PackageProvider -Verbose

# Install a provider to the current user’s module folder
Install-PackageProvider –Name Gistprovider –Verbose –Scope CurrentUser
```

## <a name="register-packagesource-cmdletpowershellmodulepackagemanagementregister-packagesource"></a>[<span data-ttu-id="b1eda-126">Cmdlet Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="b1eda-126">Register-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Register-PackageSource)

<span data-ttu-id="b1eda-127">Este cmdlet agrega un origen de paquete para un proveedor de paquetes especificado.</span><span class="sxs-lookup"><span data-stu-id="b1eda-127">This cmdlet adds a package source for a specified package provider.</span></span>
<span data-ttu-id="b1eda-128">Cada proveedor de PackageManagement puede tener uno o varios orígenes de software o repositorios.</span><span class="sxs-lookup"><span data-stu-id="b1eda-128">Each PackageManagement provider may have one or multiple software sources, or repositories.</span></span> <span data-ttu-id="b1eda-129">PackageManagement proporciona cmdlets de PowerShell para agregar, quitar o consultar el origen.</span><span class="sxs-lookup"><span data-stu-id="b1eda-129">PackageManagement provides PowerShell cmdlets to add/remove/query the source.</span></span> <span data-ttu-id="b1eda-130">Por ejemplo, puede registrar un origen de paquete para el proveedor de NuGet:</span><span class="sxs-lookup"><span data-stu-id="b1eda-130">For example, you can register a package source for the NuGet provider:</span></span>

```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdletpowershellmodulepackagemanagementsave-package"></a>[<span data-ttu-id="b1eda-131">Cmdlet Save-Package</span><span class="sxs-lookup"><span data-stu-id="b1eda-131">Save-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Save-Package)

<span data-ttu-id="b1eda-132">Este cmdlet guarda los paquetes en el equipo local sin instalarlos.</span><span class="sxs-lookup"><span data-stu-id="b1eda-132">This cmdlet saves packages to the local computer without installing them.</span></span>

```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -Source c:\test
```

## <a name="set-packagesource-cmdletpowershellmodulepackagemanagementset-packagesource"></a>[<span data-ttu-id="b1eda-133">Cmdlet Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="b1eda-133">Set-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Set-PackageSource)

<span data-ttu-id="b1eda-134">Este cmdlet cambia información sobre un origen de paquete existente.</span><span class="sxs-lookup"><span data-stu-id="b1eda-134">This cmdlet changes information about an existing package source.</span></span>

```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2
```

## <a name="uninstall-package-cmdletpowershellmodulepackagemanagementuninstall-package"></a>[<span data-ttu-id="b1eda-135">Cmdlet Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="b1eda-135">Uninstall-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Uninstall-Package)

<span data-ttu-id="b1eda-136">Este cmdlet desinstala los paquetes instalados en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="b1eda-136">This cmdlet uninstalls packages installed on the local computer.</span></span>

```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdletpowershellmodulepackagemanagementunregister-packagesource"></a>[<span data-ttu-id="b1eda-137">Cmdlet Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="b1eda-137">Unregister-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Unregister-PackageSource)

```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```