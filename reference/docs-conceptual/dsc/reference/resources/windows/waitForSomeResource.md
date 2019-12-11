---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso WaitForSome de DSC
ms.openlocfilehash: 91589c84518a2bd0f4816d11aa011dec1d5305e1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952982"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="0cb60-103">Recurso WaitForSome de DSC</span><span class="sxs-lookup"><span data-stu-id="0cb60-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="0cb60-104">Se aplica a: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="0cb60-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="0cb60-105">El recurso **WaitForSome** de Desired State Configuration (DSC) se puede usar dentro de un bloque de nodos en una [configuración de DSC](../../../configurations/configurations.md) para especificar las dependencias de las configuraciones de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="0cb60-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="0cb60-106">Este recurso se ejecuta si el recurso especificado por la propiedad **ResourceName** está en el estado deseado en un número mínimo de nodos (especificado por **NodeCount**) definido por la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="0cb60-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="0cb60-107">El recurso **WaitForSome** usa Administración remota de Windows para comprobar el estado de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="0cb60-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="0cb60-108">Para obtener más información sobre los requisitos de seguridad y puerto de WinRM, vea [Consideraciones de seguridad de comunicación remota de PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="0cb60-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="0cb60-109">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0cb60-109">Syntax</span></span>

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="0cb60-110">Propiedades</span><span class="sxs-lookup"><span data-stu-id="0cb60-110">Properties</span></span>

|<span data-ttu-id="0cb60-111">Propiedad</span><span class="sxs-lookup"><span data-stu-id="0cb60-111">Property</span></span> |<span data-ttu-id="0cb60-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="0cb60-112">Description</span></span> |
|---|---|
|<span data-ttu-id="0cb60-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="0cb60-113">NodeCount</span></span> |<span data-ttu-id="0cb60-114">El número mínimo de nodos que deben tener el estado deseado para que se ejecute este recurso.</span><span class="sxs-lookup"><span data-stu-id="0cb60-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span> |
|<span data-ttu-id="0cb60-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="0cb60-115">NodeName</span></span> |<span data-ttu-id="0cb60-116">Los nodos de destino del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="0cb60-116">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="0cb60-117">nombreDelRecurso</span><span class="sxs-lookup"><span data-stu-id="0cb60-117">ResourceName</span></span> |<span data-ttu-id="0cb60-118">El nombre del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="0cb60-118">The resource name to depend on.</span></span> <span data-ttu-id="0cb60-119">Si este recurso pertenece a una configuración diferente, dé el siguiente formato al nombre: `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span><span class="sxs-lookup"><span data-stu-id="0cb60-119">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="0cb60-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="0cb60-120">RetryIntervalSec</span></span> |<span data-ttu-id="0cb60-121">El número de segundos antes de reintentar la operación.</span><span class="sxs-lookup"><span data-stu-id="0cb60-121">The number of seconds before retrying.</span></span> <span data-ttu-id="0cb60-122">El valor mínimo es 1.</span><span class="sxs-lookup"><span data-stu-id="0cb60-122">Minimum is 1.</span></span> |
|<span data-ttu-id="0cb60-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="0cb60-123">RetryCount</span></span> |<span data-ttu-id="0cb60-124">El número máximo de reintentos.</span><span class="sxs-lookup"><span data-stu-id="0cb60-124">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="0cb60-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="0cb60-125">ThrottleLimit</span></span> |<span data-ttu-id="0cb60-126">El número de máquinas que se pueden conectar de forma simultánea.</span><span class="sxs-lookup"><span data-stu-id="0cb60-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="0cb60-127">El valor predeterminado es `New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="0cb60-127">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="0cb60-128">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="0cb60-128">Common properties</span></span>

|<span data-ttu-id="0cb60-129">Propiedad</span><span class="sxs-lookup"><span data-stu-id="0cb60-129">Property</span></span> |<span data-ttu-id="0cb60-130">Descripción</span><span class="sxs-lookup"><span data-stu-id="0cb60-130">Description</span></span> |
|---|---|
|<span data-ttu-id="0cb60-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0cb60-131">DependsOn</span></span> |<span data-ttu-id="0cb60-132">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="0cb60-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0cb60-133">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0cb60-133">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="0cb60-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="0cb60-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="0cb60-135">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="0cb60-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="0cb60-136">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="0cb60-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="0cb60-137">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="0cb60-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="0cb60-138">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0cb60-138">Example</span></span>

<span data-ttu-id="0cb60-139">Para un ejemplo de cómo usar este recurso, consulte [Especificación de dependencias entre nodos](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="0cb60-139">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>