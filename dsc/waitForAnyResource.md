---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso WaitForAny Resource de DSC
ms.openlocfilehash: 795c005c67c196ef9afb08af790fe2a1695392ec
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="6ef4c-103">Recurso WaitForAny Resource de DSC</span><span class="sxs-lookup"><span data-stu-id="6ef4c-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="6ef4c-104">Se aplica a: Windows PowerShell 5.1 y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="6ef4c-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="6ef4c-105">El recurso **WaitForSome** de Desired State Configuration (DSC) se puede usar dentro de un bloque de nodos en una [configuración de DSC](configurations.md) para especificar las dependencias de las configuraciones de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="6ef4c-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="6ef4c-106">Este recurso se ejecuta si el recurso especificado por la propiedad **ResourceName** está en el estado deseado en cualquier nodo de destino definido en la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="6ef4c-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="6ef4c-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="6ef4c-107">Syntax</span></span>

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="6ef4c-108">Propiedades</span><span class="sxs-lookup"><span data-stu-id="6ef4c-108">Properties</span></span>

|  <span data-ttu-id="6ef4c-109">Propiedad</span><span class="sxs-lookup"><span data-stu-id="6ef4c-109">Property</span></span>  |  <span data-ttu-id="6ef4c-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="6ef4c-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="6ef4c-111">nombreDelRecurso</span><span class="sxs-lookup"><span data-stu-id="6ef4c-111">ResourceName</span></span>| <span data-ttu-id="6ef4c-112">El nombre del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="6ef4c-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="6ef4c-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="6ef4c-113">NodeName</span></span>| <span data-ttu-id="6ef4c-114">Los nodos de destino del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="6ef4c-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="6ef4c-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="6ef4c-115">RetryIntervalSec</span></span>| <span data-ttu-id="6ef4c-116">El número de segundos antes de reintentar la operación.</span><span class="sxs-lookup"><span data-stu-id="6ef4c-116">The number of seconds before retrying.</span></span> <span data-ttu-id="6ef4c-117">El valor mínimo es 1.</span><span class="sxs-lookup"><span data-stu-id="6ef4c-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="6ef4c-118">RetryCount</span><span class="sxs-lookup"><span data-stu-id="6ef4c-118">RetryCount</span></span>| <span data-ttu-id="6ef4c-119">El número máximo de reintentos.</span><span class="sxs-lookup"><span data-stu-id="6ef4c-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="6ef4c-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6ef4c-120">ThrottleLimit</span></span>| <span data-ttu-id="6ef4c-121">El número de máquinas que se pueden conectar de forma simultánea.</span><span class="sxs-lookup"><span data-stu-id="6ef4c-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="6ef4c-122">El valor predeterminado es new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="6ef4c-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="6ef4c-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6ef4c-123">DependsOn</span></span> | <span data-ttu-id="6ef4c-124">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="6ef4c-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6ef4c-125">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6ef4c-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="6ef4c-126">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6ef4c-126">Example</span></span>

<span data-ttu-id="6ef4c-127">Para un ejemplo de cómo usar este recurso, consulte [Especificación de dependencias entre nodos](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="6ef4c-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

