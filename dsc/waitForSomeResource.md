---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso WaitForSome de DSC
ms.openlocfilehash: 5d67a9111f6358240590b651e627ffb96abc0896
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="091aa-103">Recurso WaitForSome de DSC</span><span class="sxs-lookup"><span data-stu-id="091aa-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="091aa-104">Se aplica a: Windows PowerShell 5.0 y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="091aa-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="091aa-105">El recurso **WaitForAny** de Desired State Configuration (DSC) se puede usar dentro de un bloque de nodos en una [configuración de DSC](configurations.md) para especificar las dependencias de las configuraciones de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="091aa-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="091aa-106">Este recurso se ejecuta si el recurso especificado por la propiedad **ResourceName** está en el estado deseado en un número mínimo de nodos (especificado por **NodeCount**) definido por la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="091aa-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="091aa-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="091aa-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    NodeCount = [Uint32]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="091aa-108">Propiedades</span><span class="sxs-lookup"><span data-stu-id="091aa-108">Properties</span></span>

|  <span data-ttu-id="091aa-109">Propiedad</span><span class="sxs-lookup"><span data-stu-id="091aa-109">Property</span></span>  |  <span data-ttu-id="091aa-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="091aa-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="091aa-111">nombreDelRecurso</span><span class="sxs-lookup"><span data-stu-id="091aa-111">ResourceName</span></span>| <span data-ttu-id="091aa-112">El nombre del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="091aa-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="091aa-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="091aa-113">NodeName</span></span>| <span data-ttu-id="091aa-114">Los nodos de destino del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="091aa-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="091aa-115">NodeCount</span><span class="sxs-lookup"><span data-stu-id="091aa-115">NodeCount</span></span>| <span data-ttu-id="091aa-116">El número mínimo de nodos que deben tener el estado deseado para que se ejecute este recurso.</span><span class="sxs-lookup"><span data-stu-id="091aa-116">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="091aa-117">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="091aa-117">RetryIntervalSec</span></span>| <span data-ttu-id="091aa-118">El número de segundos antes de reintentar la operación.</span><span class="sxs-lookup"><span data-stu-id="091aa-118">The number of seconds before retrying.</span></span> <span data-ttu-id="091aa-119">El valor mínimo es 1.</span><span class="sxs-lookup"><span data-stu-id="091aa-119">Minimum is 1.</span></span>| 
| <span data-ttu-id="091aa-120">RetryCount</span><span class="sxs-lookup"><span data-stu-id="091aa-120">RetryCount</span></span>| <span data-ttu-id="091aa-121">El número máximo de reintentos.</span><span class="sxs-lookup"><span data-stu-id="091aa-121">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="091aa-122">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="091aa-122">ThrottleLimit</span></span>| <span data-ttu-id="091aa-123">El número de máquinas que se pueden conectar de forma simultánea.</span><span class="sxs-lookup"><span data-stu-id="091aa-123">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="091aa-124">El valor predeterminado es new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="091aa-124">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="091aa-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="091aa-125">DependsOn</span></span> | <span data-ttu-id="091aa-126">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="091aa-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="091aa-127">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="091aa-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="091aa-128">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="091aa-128">Example</span></span>

<span data-ttu-id="091aa-129">Para un ejemplo de cómo usar este recurso, consulte [Especificación de dependencias entre nodos](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="091aa-129">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

