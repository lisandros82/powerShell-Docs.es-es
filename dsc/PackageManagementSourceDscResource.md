---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso PackageManagementSource de DSC
ms.openlocfilehash: 1c904c70369a75802484c3c0520df63602760361
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="61a16-103">Recurso PackageManagementSource de DSC</span><span class="sxs-lookup"><span data-stu-id="61a16-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="61a16-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="61a16-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="61a16-105">El recurso **PackageManagementSource** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para registrar o anular el registro de los orígenes de administración de paquetes en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="61a16-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="61a16-106">**Los orígenes de administración de paquetes registrados de este modo se registran en el contexto del sistema y pueden usarse por la cuenta del sistema o por el motor de DSC.**</span><span class="sxs-lookup"><span data-stu-id="61a16-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="61a16-107">Este recurso requiere el módulo **PackageManagement**, disponible en http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="61a16-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="61a16-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="61a16-108">Syntax</span></span>

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="61a16-109">Propiedades</span><span class="sxs-lookup"><span data-stu-id="61a16-109">Properties</span></span>
|  <span data-ttu-id="61a16-110">Propiedad</span><span class="sxs-lookup"><span data-stu-id="61a16-110">Property</span></span>  |  <span data-ttu-id="61a16-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="61a16-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="61a16-112">Nombre</span><span class="sxs-lookup"><span data-stu-id="61a16-112">Name</span></span>| <span data-ttu-id="61a16-113">Especifica el nombre del origen del paquete que se registra o se anula su registro del sistema.</span><span class="sxs-lookup"><span data-stu-id="61a16-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>| 
| <span data-ttu-id="61a16-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="61a16-114">Ensure</span></span>| <span data-ttu-id="61a16-115">Determina si el origen del paquete se registra o no.</span><span class="sxs-lookup"><span data-stu-id="61a16-115">Determines whether the package source is to be registered or unregistered.</span></span>| 
| <span data-ttu-id="61a16-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="61a16-116">InstallationPolicy</span></span>| <span data-ttu-id="61a16-117">Determina si se puede confiar en el origen del paquete.</span><span class="sxs-lookup"><span data-stu-id="61a16-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="61a16-118">Uno de los valores siguientes: "No es de confianza", "De confianza".</span><span class="sxs-lookup"><span data-stu-id="61a16-118">One of: "Untrusted", "Trusted".</span></span>| 
| <span data-ttu-id="61a16-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="61a16-119">ProviderName</span></span>| <span data-ttu-id="61a16-120">Especifica el nombre del proveedor de OneGet que permite la interoperabilidad con el origen del paquete.</span><span class="sxs-lookup"><span data-stu-id="61a16-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>| 
| <span data-ttu-id="61a16-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="61a16-121">SourceUri</span></span>| <span data-ttu-id="61a16-122">Especifica el URI del origen del paquete.</span><span class="sxs-lookup"><span data-stu-id="61a16-122">Specifies the URI of the package source.</span></span>| 
| <span data-ttu-id="61a16-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="61a16-123">SourceCredential</span></span>| <span data-ttu-id="61a16-124">Proporciona acceso al paquete en un origen remoto.</span><span class="sxs-lookup"><span data-stu-id="61a16-124">Provides access to the package on a remote source.</span></span>| 

## <a name="example"></a><span data-ttu-id="61a16-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="61a16-125">Example</span></span>

<span data-ttu-id="61a16-126">Este ejemplo registra el origen del paquete http://nuget.org mediante el recurso **PackageManagementSource** de DSC.</span><span class="sxs-lookup"><span data-stu-id="61a16-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```

