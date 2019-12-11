---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso ServiceSet de DSC
ms.openlocfilehash: 97c25f46940d69ed6c696e2692e29131e9a997b0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953032"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="ba7fb-103">Recurso ServiceSet de DSC</span><span class="sxs-lookup"><span data-stu-id="ba7fb-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="ba7fb-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="ba7fb-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="ba7fb-105">El recurso **ServiceSet** del servicio de configuración de estado deseado (DSC) de Windows PowerShell (DSC) proporciona un mecanismo para administrar los servicios del nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="ba7fb-106">Este es un [recurso compuesto](../../../resources/authoringResourceComposite.md) que llama el [recurso de servicio](serviceResource.md) de cada uno de los servicios que se especifica en la propiedad **Name**.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the **Name** property.</span></span>

<span data-ttu-id="ba7fb-107">Este recurso se usa cuando se desea configurar varios servicios para que tengan el mismo estado.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="ba7fb-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ba7fb-108">Syntax</span></span>

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="ba7fb-109">Propiedades</span><span class="sxs-lookup"><span data-stu-id="ba7fb-109">Properties</span></span>

|<span data-ttu-id="ba7fb-110">Propiedad</span><span class="sxs-lookup"><span data-stu-id="ba7fb-110">Property</span></span> |<span data-ttu-id="ba7fb-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="ba7fb-111">Description</span></span> |
|---|---|
|<span data-ttu-id="ba7fb-112">Nombre</span><span class="sxs-lookup"><span data-stu-id="ba7fb-112">Name</span></span> |<span data-ttu-id="ba7fb-113">Indica los nombres de servicio.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-113">Indicates the service names.</span></span> <span data-ttu-id="ba7fb-114">Tenga en cuenta que son distintos de los nombres que se muestran.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="ba7fb-115">Con el cmdlet `Get-Service` puede obtener una lista de los servicios y sus estados actuales.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-115">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="ba7fb-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="ba7fb-116">StartupType</span></span> |<span data-ttu-id="ba7fb-117">Indica el tipo de inicio de los servicios.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-117">Indicates the startup type for the services.</span></span> <span data-ttu-id="ba7fb-118">Los valores permitidos para esta propiedad son: **Automatic**, **Disabled** y **Manual**.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="ba7fb-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="ba7fb-119">BuiltInAccount</span></span> |<span data-ttu-id="ba7fb-120">Indica la cuenta de inicio de sesión que se usa para los servicios.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="ba7fb-121">Los valores permitidos para esta propiedad son: **LocalService**, **LocalSystem** y **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="ba7fb-122">Estado</span><span class="sxs-lookup"><span data-stu-id="ba7fb-122">State</span></span> |<span data-ttu-id="ba7fb-123">Indica el estado que quiere comprobar para los servicios: **Stopped** o **Running**.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span> |
|<span data-ttu-id="ba7fb-124">Credential</span><span class="sxs-lookup"><span data-stu-id="ba7fb-124">Credential</span></span> |<span data-ttu-id="ba7fb-125">Indica las credenciales para la cuenta en la que se ejecutará el recurso del servicio.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-125">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="ba7fb-126">Esta propiedad no se puede utilizar junto con la propiedad **BuiltinAccount**.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-126">This property and the **BuiltinAccount** property cannot be used together.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="ba7fb-127">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="ba7fb-127">Common properties</span></span>

|<span data-ttu-id="ba7fb-128">Propiedad</span><span class="sxs-lookup"><span data-stu-id="ba7fb-128">Property</span></span> |<span data-ttu-id="ba7fb-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="ba7fb-129">Description</span></span> |
|---|---|
|<span data-ttu-id="ba7fb-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ba7fb-130">DependsOn</span></span> |<span data-ttu-id="ba7fb-131">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ba7fb-132">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="ba7fb-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="ba7fb-133">Ensure</span></span> |<span data-ttu-id="ba7fb-134">Indica si los servicios existen en el sistema.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-134">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="ba7fb-135">Establezca esta propiedad en **Absent** para asegurarse de que los servicios no existen.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-135">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="ba7fb-136">Si la establece en **Present**, se asegura de que los servicios de destino existen.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-136">Setting it to **Present** ensures that target services exist.</span></span> <span data-ttu-id="ba7fb-137">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="ba7fb-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ba7fb-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="ba7fb-139">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="ba7fb-140">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="ba7fb-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="ba7fb-141">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="ba7fb-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="ba7fb-142">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ba7fb-142">Example</span></span>

<span data-ttu-id="ba7fb-143">La siguiente configuración inicia los servicios de "Audio de Windows" y "Servicios de Escritorio remoto".</span><span class="sxs-lookup"><span data-stu-id="ba7fb-143">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```