---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Service
ms.openlocfilehash: 0bef6aa6d3526c9d8d92187c1e738d5c46b5665a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953052"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="8d986-103">Recurso de DSC Service</span><span class="sxs-lookup"><span data-stu-id="8d986-103">DSC Service Resource</span></span>

> <span data-ttu-id="8d986-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="8d986-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="8d986-105">El recurso **Service** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar servicios en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="8d986-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="8d986-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8d986-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="8d986-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="8d986-107">Properties</span></span>

|<span data-ttu-id="8d986-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="8d986-108">Property</span></span> |<span data-ttu-id="8d986-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="8d986-109">Description</span></span> |
|---|---|
|<span data-ttu-id="8d986-110">Nombre</span><span class="sxs-lookup"><span data-stu-id="8d986-110">Name</span></span> |<span data-ttu-id="8d986-111">Indica el nombre del servicio.</span><span class="sxs-lookup"><span data-stu-id="8d986-111">Indicates the service name.</span></span> <span data-ttu-id="8d986-112">Tenga en cuenta que a veces es distinto del nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="8d986-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="8d986-113">Con el cmdlet `Get-Service` puede obtener una lista de los servicios y sus estados actuales.</span><span class="sxs-lookup"><span data-stu-id="8d986-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="8d986-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="8d986-114">BuiltInAccount</span></span> |<span data-ttu-id="8d986-115">Indica la cuenta de inicio de sesión que se utilizará para el servicio.</span><span class="sxs-lookup"><span data-stu-id="8d986-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="8d986-116">Los valores permitidos para esta propiedad son: **LocalService**, **LocalSystem** y **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="8d986-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="8d986-117">Credential</span><span class="sxs-lookup"><span data-stu-id="8d986-117">Credential</span></span> |<span data-ttu-id="8d986-118">Indica las credenciales de la cuenta en la que se ejecutará el servicio.</span><span class="sxs-lookup"><span data-stu-id="8d986-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="8d986-119">Esta propiedad no se puede utilizar junto con la propiedad **BuiltinAccount**.</span><span class="sxs-lookup"><span data-stu-id="8d986-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="8d986-120">StartupType</span><span class="sxs-lookup"><span data-stu-id="8d986-120">StartupType</span></span> |<span data-ttu-id="8d986-121">Indica el tipo de inicio del servicio.</span><span class="sxs-lookup"><span data-stu-id="8d986-121">Indicates the startup type for the service.</span></span> <span data-ttu-id="8d986-122">Los valores permitidos para esta propiedad son: **Automatic**, **Disabled** y **Manual**.</span><span class="sxs-lookup"><span data-stu-id="8d986-122">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="8d986-123">Estado</span><span class="sxs-lookup"><span data-stu-id="8d986-123">State</span></span> |<span data-ttu-id="8d986-124">Indica el estado que quiere garantizar para el servicio.</span><span class="sxs-lookup"><span data-stu-id="8d986-124">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="8d986-125">Los valores son: **Running** o **Stopped**.</span><span class="sxs-lookup"><span data-stu-id="8d986-125">The values are: **Running** or **Stopped**.</span></span> |
|<span data-ttu-id="8d986-126">Descripción</span><span class="sxs-lookup"><span data-stu-id="8d986-126">Description</span></span> |<span data-ttu-id="8d986-127">Indica la descripción del servicio de destino.</span><span class="sxs-lookup"><span data-stu-id="8d986-127">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="8d986-128">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8d986-128">DisplayName</span></span> |<span data-ttu-id="8d986-129">Indica el nombre para mostrar del servicio de destino.</span><span class="sxs-lookup"><span data-stu-id="8d986-129">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="8d986-130">Ruta</span><span class="sxs-lookup"><span data-stu-id="8d986-130">Path</span></span> |<span data-ttu-id="8d986-131">Indica la ruta de acceso al archivo binario para un nuevo servicio.</span><span class="sxs-lookup"><span data-stu-id="8d986-131">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="8d986-132">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="8d986-132">Common properties</span></span>

|<span data-ttu-id="8d986-133">Propiedad</span><span class="sxs-lookup"><span data-stu-id="8d986-133">Property</span></span> |<span data-ttu-id="8d986-134">Descripción</span><span class="sxs-lookup"><span data-stu-id="8d986-134">Description</span></span> |
|---|---|
|<span data-ttu-id="8d986-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8d986-135">DependsOn</span></span> |<span data-ttu-id="8d986-136">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="8d986-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8d986-137">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8d986-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="8d986-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="8d986-138">Ensure</span></span> |<span data-ttu-id="8d986-139">Indica si el servicio de destino existe en el sistema.</span><span class="sxs-lookup"><span data-stu-id="8d986-139">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="8d986-140">Establezca esta propiedad en **Absent** para asegurarse de que el servicio de destino no exista.</span><span class="sxs-lookup"><span data-stu-id="8d986-140">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="8d986-141">Si la establece en **Present**, se asegura de que el servicio de destino existe.</span><span class="sxs-lookup"><span data-stu-id="8d986-141">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="8d986-142">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="8d986-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="8d986-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="8d986-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="8d986-144">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="8d986-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="8d986-145">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="8d986-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="8d986-146">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="8d986-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="8d986-147">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8d986-147">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```