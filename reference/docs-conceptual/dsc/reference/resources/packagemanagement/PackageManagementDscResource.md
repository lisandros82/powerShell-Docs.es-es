---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso PackageManagement de DSC
ms.openlocfilehash: dfc23bfabbc45041e15c56a29a77c5bdda430a30
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953242"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="f83d8-103">Recurso PackageManagement de DSC</span><span class="sxs-lookup"><span data-stu-id="f83d8-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="f83d8-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f83d8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="f83d8-105">El recurso **PackageManagement** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para instalar o desinstalar paquetes de administración de paquetes, en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="f83d8-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="f83d8-106">Este recurso requiere el módulo **PackageManagement**, disponible en [http://PowerShellGallery.com](https://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="f83d8-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f83d8-107">El módulo **PackageManagement** debe tener al menos la versión 1.1.7.0 para que la siguiente información de propiedad sea correcta.</span><span class="sxs-lookup"><span data-stu-id="f83d8-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="f83d8-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f83d8-108">Syntax</span></span>

```Syntax
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ AdditionalParameters = [HashTable] ]
    [ MaximumVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ ProviderName = [string] ]
    [ RequiredVersion = [string] ]
    [ Source = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="f83d8-109">Propiedades</span><span class="sxs-lookup"><span data-stu-id="f83d8-109">Properties</span></span>

|<span data-ttu-id="f83d8-110">Propiedad</span><span class="sxs-lookup"><span data-stu-id="f83d8-110">Property</span></span> |<span data-ttu-id="f83d8-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="f83d8-111">Description</span></span> |
|---|---|
|<span data-ttu-id="f83d8-112">Nombre</span><span class="sxs-lookup"><span data-stu-id="f83d8-112">Name</span></span> |<span data-ttu-id="f83d8-113">Especifica el nombre del paquete que se va a instalar o desinstalar.</span><span class="sxs-lookup"><span data-stu-id="f83d8-113">Specifies the name of the Package to be installed or uninstalled.</span></span> |
|<span data-ttu-id="f83d8-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="f83d8-114">AdditionalParameters</span></span> |<span data-ttu-id="f83d8-115">La tabla hash de parámetros específica del proveedor que se pasará a `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="f83d8-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="f83d8-116">Por ejemplo, para el proveedor NuGet puede pasar parámetros adicionales, como DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="f83d8-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span> |
|<span data-ttu-id="f83d8-117">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="f83d8-117">MaximumVersion</span></span> |<span data-ttu-id="f83d8-118">Especifica la versión máxima permitida del paquete que desea encontrar.</span><span class="sxs-lookup"><span data-stu-id="f83d8-118">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="f83d8-119">Si no agrega este parámetro, el recurso busca la versión disponible más alta del paquete.</span><span class="sxs-lookup"><span data-stu-id="f83d8-119">If you do not add this parameter, the resource finds the highest available version of the package.</span></span> |
|<span data-ttu-id="f83d8-120">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="f83d8-120">MinimumVersion</span></span> |<span data-ttu-id="f83d8-121">Especifica la versión mínima permitida del paquete que desea encontrar.</span><span class="sxs-lookup"><span data-stu-id="f83d8-121">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="f83d8-122">Si no se agrega este parámetro, este recurso busca la versión más alta disponible del paquete que también admite cualquier versión máxima especificada por el parámetro **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="f83d8-122">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="f83d8-123">ProviderName</span><span class="sxs-lookup"><span data-stu-id="f83d8-123">ProviderName</span></span> |<span data-ttu-id="f83d8-124">Especifica un nombre de proveedor del paquete que se va a dirigir la búsqueda del paquete.</span><span class="sxs-lookup"><span data-stu-id="f83d8-124">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="f83d8-125">Puede obtener los nombres de proveedor del paquete mediante la ejecución del cmdlet `Get-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="f83d8-125">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span> |
|<span data-ttu-id="f83d8-126">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="f83d8-126">RequiredVersion</span></span> |<span data-ttu-id="f83d8-127">Especifica la versión exacta del paquete que desea instalar.</span><span class="sxs-lookup"><span data-stu-id="f83d8-127">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="f83d8-128">Si no se especifica este parámetro, este recurso de DSC instala la versión más reciente disponible del paquete que también admite cualquier versión máxima especificada por el parámetro **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="f83d8-128">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="f83d8-129">Origen</span><span class="sxs-lookup"><span data-stu-id="f83d8-129">Source</span></span> |<span data-ttu-id="f83d8-130">Especifica el nombre del origen del paquete donde se encuentra el paquete.</span><span class="sxs-lookup"><span data-stu-id="f83d8-130">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="f83d8-131">Puede ser un URI o un origen registrado con `Register-PackageSource` o el recurso de DSC PackageManagementSource.</span><span class="sxs-lookup"><span data-stu-id="f83d8-131">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span> |
|<span data-ttu-id="f83d8-132">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="f83d8-132">SourceCredential</span></span> |<span data-ttu-id="f83d8-133">Especifica una cuenta de usuario que tenga derechos para instalar un paquete para un proveedor u origen de paquetes especificado.</span><span class="sxs-lookup"><span data-stu-id="f83d8-133">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span> |

## <a name="additional-parameters"></a><span data-ttu-id="f83d8-134">Parámetros adicionales</span><span class="sxs-lookup"><span data-stu-id="f83d8-134">Additional Parameters</span></span>

<span data-ttu-id="f83d8-135">En la tabla siguiente se enumeran las opciones de la propiedad AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="f83d8-135">The following table lists options for the AdditionalParameters property.</span></span>

|<span data-ttu-id="f83d8-136">Parámetro</span><span class="sxs-lookup"><span data-stu-id="f83d8-136">Parameter</span></span> |<span data-ttu-id="f83d8-137">Descripción</span><span class="sxs-lookup"><span data-stu-id="f83d8-137">Description</span></span> |
|---|---|
|<span data-ttu-id="f83d8-138">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="f83d8-138">DestinationPath</span></span> |<span data-ttu-id="f83d8-139">Usada por proveedores como el proveedor integrado de Nuget.</span><span class="sxs-lookup"><span data-stu-id="f83d8-139">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="f83d8-140">Especifica una ubicación del archivo donde desea que se instale el paquete.</span><span class="sxs-lookup"><span data-stu-id="f83d8-140">Specifies a file location where you want the package to be installed.</span></span> |
|<span data-ttu-id="f83d8-141">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="f83d8-141">InstallationPolicy</span></span> |<span data-ttu-id="f83d8-142">Usada por proveedores como el proveedor integrado de Nuget.</span><span class="sxs-lookup"><span data-stu-id="f83d8-142">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="f83d8-143">Determina si puede confiar en el origen del paquete.</span><span class="sxs-lookup"><span data-stu-id="f83d8-143">Determines whether you trust the package's source.</span></span> <span data-ttu-id="f83d8-144">Uno de los valores siguientes: **No es de confianza** o **De confianza**.</span><span class="sxs-lookup"><span data-stu-id="f83d8-144">One of: **Untrusted** or **Trusted**.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="f83d8-145">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="f83d8-145">Common properties</span></span>

|<span data-ttu-id="f83d8-146">Propiedad</span><span class="sxs-lookup"><span data-stu-id="f83d8-146">Property</span></span> |<span data-ttu-id="f83d8-147">Descripción</span><span class="sxs-lookup"><span data-stu-id="f83d8-147">Description</span></span> |
|---|---|
|<span data-ttu-id="f83d8-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f83d8-148">DependsOn</span></span> |<span data-ttu-id="f83d8-149">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="f83d8-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f83d8-150">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f83d8-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="f83d8-151">Ensure</span><span class="sxs-lookup"><span data-stu-id="f83d8-151">Ensure</span></span> |<span data-ttu-id="f83d8-152">Determina si el paquete se puede instalar o desinstalar.</span><span class="sxs-lookup"><span data-stu-id="f83d8-152">Determines whether the package is to be installed or uninstalled.</span></span> <span data-ttu-id="f83d8-153">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="f83d8-153">The default value is **Present**.</span></span> |
|<span data-ttu-id="f83d8-154">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f83d8-154">PsDscRunAsCredential</span></span> |<span data-ttu-id="f83d8-155">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="f83d8-155">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="f83d8-156">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="f83d8-156">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="f83d8-157">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="f83d8-157">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="f83d8-158">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f83d8-158">Example</span></span>

<span data-ttu-id="f83d8-159">Este ejemplo se instala el paquete NuGet **JQuery** y el módulo **GistProvider** de PowerShell mediante el recurso **PackageManagement** de DSC.</span><span class="sxs-lookup"><span data-stu-id="f83d8-159">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="f83d8-160">Este ejemplo primero garantiza que los orígenes del paquete necesarios están disponibles y después define el estado esperado de los paquetes **JQuery** y **GistProvider** (NuGet y PowerShell, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="f83d8-160">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```