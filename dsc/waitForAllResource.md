---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso WaitForAll Resource de DSC
ms.openlocfilehash: dcc23ad4e6905bc277ad39348350d5425fc90ad7
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="865e7-103">Recurso WaitForAll Resource de DSC</span><span class="sxs-lookup"><span data-stu-id="865e7-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="865e7-104">Se aplica a: Windows PowerShell 5.0 y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="865e7-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="865e7-105">El recurso **WaitForAll** de Desired State Configuration (DSC) se puede usar dentro de un bloque de nodos en una [configuración de DSC](configurations.md) para especificar las dependencias de las configuraciones de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="865e7-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="865e7-106">Este recurso se ejecuta si el recurso especificado por la propiedad **ResourceName** está en el estado deseado en todos los nodos de destino definidos en la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="865e7-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="865e7-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="865e7-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="865e7-108">Propiedades</span><span class="sxs-lookup"><span data-stu-id="865e7-108">Properties</span></span>

|  <span data-ttu-id="865e7-109">Propiedad</span><span class="sxs-lookup"><span data-stu-id="865e7-109">Property</span></span>  |  <span data-ttu-id="865e7-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="865e7-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="865e7-111">nombreDelRecurso</span><span class="sxs-lookup"><span data-stu-id="865e7-111">ResourceName</span></span>| <span data-ttu-id="865e7-112">El nombre del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="865e7-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="865e7-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="865e7-113">NodeName</span></span>| <span data-ttu-id="865e7-114">Los nodos de destino del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="865e7-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="865e7-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="865e7-115">RetryIntervalSec</span></span>| <span data-ttu-id="865e7-116">El número de segundos antes de reintentar la operación.</span><span class="sxs-lookup"><span data-stu-id="865e7-116">The number of seconds before retrying.</span></span> <span data-ttu-id="865e7-117">El valor mínimo es 1.</span><span class="sxs-lookup"><span data-stu-id="865e7-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="865e7-118">RetryCount</span><span class="sxs-lookup"><span data-stu-id="865e7-118">RetryCount</span></span>| <span data-ttu-id="865e7-119">El número máximo de reintentos.</span><span class="sxs-lookup"><span data-stu-id="865e7-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="865e7-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="865e7-120">ThrottleLimit</span></span>| <span data-ttu-id="865e7-121">El número de máquinas que se pueden conectar de forma simultánea.</span><span class="sxs-lookup"><span data-stu-id="865e7-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="865e7-122">El valor predeterminado es new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="865e7-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="865e7-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="865e7-123">DependsOn</span></span> | <span data-ttu-id="865e7-124">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="865e7-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="865e7-125">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="865e7-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="865e7-126">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="865e7-126">Example</span></span>

<span data-ttu-id="865e7-127">Para un ejemplo de cómo usar este recurso, consulte [Especificación de dependencias entre nodos](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="865e7-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

