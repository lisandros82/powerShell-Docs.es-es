---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso PackageManagement de DSC
ms.openlocfilehash: e6eea9f0bae42e131976dacb9813da759ff31239
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="53ccf-103">Recurso PackageManagement de DSC</span><span class="sxs-lookup"><span data-stu-id="53ccf-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="53ccf-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="53ccf-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="53ccf-105">El recurso **PackageManagement** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para instalar o desinstalar paquetes de administración de paquetes, en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="53ccf-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="53ccf-106">Este recurso requiere el módulo **PackageManagement**, disponible en http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="53ccf-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="53ccf-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="53ccf-107">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="53ccf-108">Propiedades</span><span class="sxs-lookup"><span data-stu-id="53ccf-108">Properties</span></span>
|  <span data-ttu-id="53ccf-109">Propiedad</span><span class="sxs-lookup"><span data-stu-id="53ccf-109">Property</span></span>  |  <span data-ttu-id="53ccf-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="53ccf-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="53ccf-111">Nombre</span><span class="sxs-lookup"><span data-stu-id="53ccf-111">Name</span></span>| <span data-ttu-id="53ccf-112">Especifica el nombre del paquete que se va a instalar o desinstalar.</span><span class="sxs-lookup"><span data-stu-id="53ccf-112">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="53ccf-113">Origen</span><span class="sxs-lookup"><span data-stu-id="53ccf-113">Source</span></span>| <span data-ttu-id="53ccf-114">Especifica el nombre del origen del paquete donde se encuentra el paquete.</span><span class="sxs-lookup"><span data-stu-id="53ccf-114">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="53ccf-115">Puede ser un URI o un origen registrado con el recurso de registro de DSC Register-PackageSource o PackageManagementSource.</span><span class="sxs-lookup"><span data-stu-id="53ccf-115">This can either be a URI or a source registered with Register-PackageSource or PackageManagementSource DSC resource.</span></span> <span data-ttu-id="53ccf-116">El recurso MSFT_PackageManagementSource de DSC también puede registrar un origen del paquete.</span><span class="sxs-lookup"><span data-stu-id="53ccf-116">The DSC resource MSFT_PackageManagementSource can also register a package source.</span></span>|
| <span data-ttu-id="53ccf-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="53ccf-117">Ensure</span></span>| <span data-ttu-id="53ccf-118">Determina si el paquete se puede instalar o desinstalar.</span><span class="sxs-lookup"><span data-stu-id="53ccf-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="53ccf-119">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="53ccf-119">RequiredVersion</span></span>| <span data-ttu-id="53ccf-120">Especifica la versión exacta del paquete que desea instalar.</span><span class="sxs-lookup"><span data-stu-id="53ccf-120">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="53ccf-121">Si no se especifica este parámetro, este recurso de DSC instala la versión más reciente disponible del paquete que también admite cualquier versión máxima especificada por el parámetro MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="53ccf-121">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the MaximumVersion parameter.</span></span>|
| <span data-ttu-id="53ccf-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="53ccf-122">MinimumVersion</span></span>| <span data-ttu-id="53ccf-123">Especifica la versión mínima permitida del paquete que desea instalar.</span><span class="sxs-lookup"><span data-stu-id="53ccf-123">Specifies the minimum allowed version of the package that you want to install.</span></span> <span data-ttu-id="53ccf-124">Si no se agrega este parámetro, este recurso de DSC instala la versión más alta disponible del paquete que también admite cualquier versión máxima especificada por el parámetro MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="53ccf-124">If you do not add this parameter, this DSC resource intalls the highest available version of the package that also satisfies any maximum specified version specified by the MaximumVersion parameter.</span></span>|
| <span data-ttu-id="53ccf-125">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="53ccf-125">MaximumVersion</span></span>| <span data-ttu-id="53ccf-126">Especifica la versión máxima permitida del paquete que desea instalar.</span><span class="sxs-lookup"><span data-stu-id="53ccf-126">Specifies the maximum allowed version of the package that you want to install.</span></span> <span data-ttu-id="53ccf-127">Si no se especifica este parámetro, este recurso de DSC instala la versión del paquete disponible con el número mayor.</span><span class="sxs-lookup"><span data-stu-id="53ccf-127">If you do not specify this parameter, this DSC resource installs the highest-numbered available version of the package.</span></span>|
| <span data-ttu-id="53ccf-128">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="53ccf-128">SourceCredential</span></span> | <span data-ttu-id="53ccf-129">Especifica una cuenta de usuario que tenga derechos para instalar un paquete para un proveedor u origen de paquetes especificado.</span><span class="sxs-lookup"><span data-stu-id="53ccf-129">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|
| <span data-ttu-id="53ccf-130">ProviderName</span><span class="sxs-lookup"><span data-stu-id="53ccf-130">ProviderName</span></span>| <span data-ttu-id="53ccf-131">Especifica un nombre de proveedor del paquete que se va a dirigir la búsqueda del paquete.</span><span class="sxs-lookup"><span data-stu-id="53ccf-131">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="53ccf-132">Puede obtener los nombres de proveedor del paquete mediante la ejecución del cmdlet Get-PackageProvider.</span><span class="sxs-lookup"><span data-stu-id="53ccf-132">You can get package provider names by running the Get-PackageProvider cmdlet.</span></span>|
| <span data-ttu-id="53ccf-133">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="53ccf-133">AdditionalParameters</span></span>| <span data-ttu-id="53ccf-134">Parámetros específicos del proveedor que se pasan como una tabla hash.</span><span class="sxs-lookup"><span data-stu-id="53ccf-134">Provider specific parameters that are passed as an Hashtable.</span></span> <span data-ttu-id="53ccf-135">Por ejemplo, para el proveedor NuGet puede pasar parámetros adicionales, como DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="53ccf-135">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="53ccf-136">Parámetros adicionales</span><span class="sxs-lookup"><span data-stu-id="53ccf-136">Additional Parameters</span></span>
<span data-ttu-id="53ccf-137">En la tabla siguiente se enumeran las opciones de la propiedad AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="53ccf-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="53ccf-138">Parámetro</span><span class="sxs-lookup"><span data-stu-id="53ccf-138">Parameter</span></span>  | <span data-ttu-id="53ccf-139">Descripción</span><span class="sxs-lookup"><span data-stu-id="53ccf-139">Description</span></span>   |
|---|---|
| <span data-ttu-id="53ccf-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="53ccf-140">DestinationPath</span></span>| <span data-ttu-id="53ccf-141">Usada por proveedores como el proveedor integrado de Nuget.</span><span class="sxs-lookup"><span data-stu-id="53ccf-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="53ccf-142">Especifica una ubicación del archivo donde desea que se instale el paquete.</span><span class="sxs-lookup"><span data-stu-id="53ccf-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="53ccf-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="53ccf-143">InstallationPolicy</span></span>| <span data-ttu-id="53ccf-144">Usada por proveedores como el proveedor integrado de Nuget.</span><span class="sxs-lookup"><span data-stu-id="53ccf-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="53ccf-145">Determina si puede confiar en el origen del paquete.</span><span class="sxs-lookup"><span data-stu-id="53ccf-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="53ccf-146">Uno de los valores siguientes: "No es de confianza", "De confianza".</span><span class="sxs-lookup"><span data-stu-id="53ccf-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="53ccf-147">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="53ccf-147">Example</span></span>

<span data-ttu-id="53ccf-148">Este ejemplo se instala el paquete NuGet **JQuery** y el módulo **GistProvider** de PowerShell mediante el recurso **PackageManagement** de DSC.</span><span class="sxs-lookup"><span data-stu-id="53ccf-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="53ccf-149">Este ejemplo primero garantiza que los orígenes del paquete necesarios están disponibles y después define el estado esperado de los paquetes **JQuery** y **GistProvider** (NuGet y PowerShell, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="53ccf-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceUri   = "https://www.powershellgallery.com/api/v2/"
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