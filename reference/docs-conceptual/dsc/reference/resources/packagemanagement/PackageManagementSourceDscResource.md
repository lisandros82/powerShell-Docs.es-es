---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso PackageManagementSource de DSC
ms.openlocfilehash: 20b7851e44751d4bd0add718d2f7294d5215ab70
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954792"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="10808-103">Recurso PackageManagementSource de DSC</span><span class="sxs-lookup"><span data-stu-id="10808-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="10808-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="10808-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="10808-105">El recurso **PackageManagementSource** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para registrar o anular el registro de los orígenes de administración de paquetes en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="10808-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span>
<span data-ttu-id="10808-106">**Los orígenes de administración de paquetes registrados de este modo se registran en el contexto del sistema y pueden usarse por la cuenta del sistema o por el motor de DSC.**</span><span class="sxs-lookup"><span data-stu-id="10808-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="10808-107">Este recurso requiere el módulo **PackageManagement**, disponible en la [Galería de PowerShell](https://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="10808-107">This resource requires the **PackageManagement** module, available from the [PowerShell Gallery](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10808-108">El módulo **PackageManagement** debe tener al menos la versión 1.1.7.0 para que la siguiente información de propiedad sea correcta.</span><span class="sxs-lookup"><span data-stu-id="10808-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="10808-109">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="10808-109">Syntax</span></span>

```Syntax
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [ InstallationPolicy = [string]{ Trusted | Untrusted } ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="10808-110">Propiedades</span><span class="sxs-lookup"><span data-stu-id="10808-110">Properties</span></span>

|<span data-ttu-id="10808-111">Propiedad</span><span class="sxs-lookup"><span data-stu-id="10808-111">Property</span></span> |<span data-ttu-id="10808-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="10808-112">Description</span></span> |
|---|---|
|<span data-ttu-id="10808-113">Nombre</span><span class="sxs-lookup"><span data-stu-id="10808-113">Name</span></span> |<span data-ttu-id="10808-114">Especifica el nombre del origen del paquete que se registra o se anula su registro del sistema.</span><span class="sxs-lookup"><span data-stu-id="10808-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span> |
|<span data-ttu-id="10808-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="10808-115">ProviderName</span></span> |<span data-ttu-id="10808-116">Especifica el nombre del proveedor de OneGet que permite la interoperabilidad con el origen del paquete.</span><span class="sxs-lookup"><span data-stu-id="10808-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span> |
|<span data-ttu-id="10808-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="10808-117">SourceLocation</span></span> |<span data-ttu-id="10808-118">Especifica el URI del origen del paquete.</span><span class="sxs-lookup"><span data-stu-id="10808-118">Specifies the URI of the package source.</span></span> |
|<span data-ttu-id="10808-119">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="10808-119">InstallationPolicy</span></span> |<span data-ttu-id="10808-120">Usada por proveedores como el proveedor integrado de Nuget.</span><span class="sxs-lookup"><span data-stu-id="10808-120">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="10808-121">Determina si puede confiar en el origen del paquete.</span><span class="sxs-lookup"><span data-stu-id="10808-121">Determines whether you trust the package's source.</span></span> <span data-ttu-id="10808-122">Uno de los valores siguientes: **No es de confianza** o **De confianza**.</span><span class="sxs-lookup"><span data-stu-id="10808-122">One of: **Untrusted** or **Trusted**.</span></span> |
|<span data-ttu-id="10808-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="10808-123">SourceCredential</span></span> |<span data-ttu-id="10808-124">Proporciona acceso al paquete en un origen remoto.</span><span class="sxs-lookup"><span data-stu-id="10808-124">Provides access to the package on a remote source.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="10808-125">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="10808-125">Common properties</span></span>

|<span data-ttu-id="10808-126">Propiedad</span><span class="sxs-lookup"><span data-stu-id="10808-126">Property</span></span> |<span data-ttu-id="10808-127">Descripción</span><span class="sxs-lookup"><span data-stu-id="10808-127">Description</span></span> |
|---|---|
|<span data-ttu-id="10808-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="10808-128">DependsOn</span></span> |<span data-ttu-id="10808-129">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="10808-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="10808-130">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="10808-130">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="10808-131">Ensure</span><span class="sxs-lookup"><span data-stu-id="10808-131">Ensure</span></span> |<span data-ttu-id="10808-132">Determina si el origen del paquete se registra o no.</span><span class="sxs-lookup"><span data-stu-id="10808-132">Determines whether the package source is to be registered or unregistered.</span></span> <span data-ttu-id="10808-133">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="10808-133">The default value is **Present**.</span></span> |
|<span data-ttu-id="10808-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="10808-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="10808-135">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="10808-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="10808-136">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="10808-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="10808-137">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="10808-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="10808-138">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="10808-138">Example</span></span>

<span data-ttu-id="10808-139">En este ejemplo se registra el origen del paquete `https://nuget.org` con el recurso de DSC **PackageManagementSource** DSC resource.</span><span class="sxs-lookup"><span data-stu-id="10808-139">This example registers the `https://nuget.org` package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "https://api.nuget.org/api/v3/"
        InstallationPolicy ="Trusted"
    }
}
```