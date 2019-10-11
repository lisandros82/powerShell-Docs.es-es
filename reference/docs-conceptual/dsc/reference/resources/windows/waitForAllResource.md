---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso WaitForAll Resource de DSC
ms.openlocfilehash: 1bdaa63812766cfe5ec0778ef07689109683b994
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953022"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="64826-103">Recurso WaitForAll Resource de DSC</span><span class="sxs-lookup"><span data-stu-id="64826-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="64826-104">Se aplica a: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="64826-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="64826-105">El recurso **WaitForAll** de Desired State Configuration (DSC) se puede usar dentro de un bloque de nodos en una [configuración de DSC](../../../configurations/configurations.md) para especificar las dependencias de las configuraciones de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="64826-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="64826-106">Este recurso se ejecuta si el recurso especificado por la propiedad **ResourceName** está en el estado deseado en todos los nodos de destino definidos en la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="64826-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="64826-107">El recurso **WaitForAll** usa Administración remota de Windows para comprobar el estado de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="64826-107">**WaitForAll** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="64826-108">Para obtener más información sobre los requisitos de seguridad y puerto de WinRM, vea [Consideraciones de seguridad de comunicación remota de PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="64826-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="64826-109">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="64826-109">Syntax</span></span>

```Syntax
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string[]]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="64826-110">Propiedades</span><span class="sxs-lookup"><span data-stu-id="64826-110">Properties</span></span>

|<span data-ttu-id="64826-111">Propiedad</span><span class="sxs-lookup"><span data-stu-id="64826-111">Property</span></span> |<span data-ttu-id="64826-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="64826-112">Description</span></span> |
|---|---|
|<span data-ttu-id="64826-113">nombreDelRecurso</span><span class="sxs-lookup"><span data-stu-id="64826-113">ResourceName</span></span> |<span data-ttu-id="64826-114">El nombre del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="64826-114">The resource name to depend on.</span></span> <span data-ttu-id="64826-115">Si este recurso pertenece a una configuración diferente, dé el siguiente formato al nombre: `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span><span class="sxs-lookup"><span data-stu-id="64826-115">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="64826-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="64826-116">NodeName</span></span> |<span data-ttu-id="64826-117">Los nodos de destino del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="64826-117">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="64826-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="64826-118">RetryIntervalSec</span></span> |<span data-ttu-id="64826-119">El número de segundos antes de reintentar la operación.</span><span class="sxs-lookup"><span data-stu-id="64826-119">The number of seconds before retrying.</span></span> <span data-ttu-id="64826-120">El valor mínimo es 1.</span><span class="sxs-lookup"><span data-stu-id="64826-120">Minimum is 1.</span></span> |
|<span data-ttu-id="64826-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="64826-121">RetryCount</span></span> |<span data-ttu-id="64826-122">El número máximo de reintentos.</span><span class="sxs-lookup"><span data-stu-id="64826-122">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="64826-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="64826-123">ThrottleLimit</span></span> |<span data-ttu-id="64826-124">El número de máquinas que se pueden conectar de forma simultánea.</span><span class="sxs-lookup"><span data-stu-id="64826-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="64826-125">El valor predeterminado es `New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="64826-125">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="64826-126">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="64826-126">Common properties</span></span>

|<span data-ttu-id="64826-127">Propiedad</span><span class="sxs-lookup"><span data-stu-id="64826-127">Property</span></span> |<span data-ttu-id="64826-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="64826-128">Description</span></span> |
|---|---|
|<span data-ttu-id="64826-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="64826-129">DependsOn</span></span> |<span data-ttu-id="64826-130">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="64826-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="64826-131">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="64826-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="64826-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="64826-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="64826-133">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="64826-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="64826-134">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="64826-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="64826-135">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="64826-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="64826-136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="64826-136">Example</span></span>

<span data-ttu-id="64826-137">Para un ejemplo de cómo usar este recurso, consulte [Especificación de dependencias entre nodos](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="64826-137">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>