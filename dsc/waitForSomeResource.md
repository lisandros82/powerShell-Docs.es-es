---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso WaitForSome de DSC
ms.openlocfilehash: 8132b584fad350530f6fc80175980881a399ac2e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="dc2f5-103">Recurso WaitForSome de DSC</span><span class="sxs-lookup"><span data-stu-id="dc2f5-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="dc2f5-104">Se aplica a: Windows PowerShell 5.0 y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="dc2f5-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="dc2f5-105">El recurso **WaitForAny** de Desired State Configuration (DSC) se puede usar dentro de un bloque de nodos en una [configuración de DSC](configurations.md) para especificar las dependencias de las configuraciones de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="dc2f5-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="dc2f5-106">Este recurso se ejecuta si el recurso especificado por la propiedad **ResourceName** está en el estado deseado en un número mínimo de nodos (especificado por **NodeCount**) definido por la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="dc2f5-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="dc2f5-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="dc2f5-107">Syntax</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a><span data-ttu-id="dc2f5-108">Propiedades</span><span class="sxs-lookup"><span data-stu-id="dc2f5-108">Properties</span></span>

|  <span data-ttu-id="dc2f5-109">Propiedad</span><span class="sxs-lookup"><span data-stu-id="dc2f5-109">Property</span></span>  |  <span data-ttu-id="dc2f5-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="dc2f5-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="dc2f5-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="dc2f5-111">NodeCount</span></span>| <span data-ttu-id="dc2f5-112">El número mínimo de nodos que deben tener el estado deseado para que se ejecute este recurso.</span><span class="sxs-lookup"><span data-stu-id="dc2f5-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="dc2f5-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="dc2f5-113">NodeName</span></span>| <span data-ttu-id="dc2f5-114">Los nodos de destino del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="dc2f5-114">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="dc2f5-115">nombreDelRecurso</span><span class="sxs-lookup"><span data-stu-id="dc2f5-115">ResourceName</span></span>| <span data-ttu-id="dc2f5-116">El nombre del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="dc2f5-116">The resource name to depend on.</span></span> <span data-ttu-id="dc2f5-117">Si el recurso pertenece a una configuración diferente, asegúrese de que el formato del nombre sea el siguiente: "[__TipoDeRecurso__]__NombreDeRecurso__::[__NombreDeConfiguración__]::[__NombreDeConfiguración__]".</span><span class="sxs-lookup"><span data-stu-id="dc2f5-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="dc2f5-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="dc2f5-118">RetryIntervalSec</span></span>| <span data-ttu-id="dc2f5-119">El número de segundos antes de reintentar la operación.</span><span class="sxs-lookup"><span data-stu-id="dc2f5-119">The number of seconds before retrying.</span></span> <span data-ttu-id="dc2f5-120">El valor mínimo es 1.</span><span class="sxs-lookup"><span data-stu-id="dc2f5-120">Minimum is 1.</span></span>|
| <span data-ttu-id="dc2f5-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="dc2f5-121">RetryCount</span></span>| <span data-ttu-id="dc2f5-122">El número máximo de reintentos.</span><span class="sxs-lookup"><span data-stu-id="dc2f5-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="dc2f5-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="dc2f5-123">ThrottleLimit</span></span>| <span data-ttu-id="dc2f5-124">El número de máquinas que se pueden conectar de forma simultánea.</span><span class="sxs-lookup"><span data-stu-id="dc2f5-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="dc2f5-125">El valor predeterminado es new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="dc2f5-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="dc2f5-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="dc2f5-126">DependsOn</span></span> | <span data-ttu-id="dc2f5-127">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="dc2f5-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="dc2f5-128">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="dc2f5-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="dc2f5-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="dc2f5-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="dc2f5-130">Consulte el artículo sobre el [uso de DSC con credenciales de usuario](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="dc2f5-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |


## <a name="example"></a><span data-ttu-id="dc2f5-131">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="dc2f5-131">Example</span></span>

<span data-ttu-id="dc2f5-132">Para un ejemplo de cómo usar este recurso, consulte [Especificación de dependencias entre nodos](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="dc2f5-132">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>