---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso WaitForAny Resource de DSC
ms.openlocfilehash: 55869f665837b422c006f4cfb3e91366fac60362
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076837"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="da59c-103">Recurso WaitForAny Resource de DSC</span><span class="sxs-lookup"><span data-stu-id="da59c-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="da59c-104">Se aplica a: Windows PowerShell 5.1 y posterior</span><span class="sxs-lookup"><span data-stu-id="da59c-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="da59c-105">El recurso **WaitForAny** de Desired State Configuration (DSC) se puede usar dentro de un bloque de nodos en una [configuración de DSC](../../../configurations/configurations.md) para especificar las dependencias de las configuraciones de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="da59c-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="da59c-106">Este recurso se ejecuta si el recurso especificado por la propiedad **ResourceName** está en el estado deseado en cualquier nodo de destino definido en la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="da59c-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="da59c-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="da59c-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="da59c-108">Propiedades</span><span class="sxs-lookup"><span data-stu-id="da59c-108">Properties</span></span>

|  <span data-ttu-id="da59c-109">Propiedad</span><span class="sxs-lookup"><span data-stu-id="da59c-109">Property</span></span>  |  <span data-ttu-id="da59c-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="da59c-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="da59c-111">nombreDelRecurso</span><span class="sxs-lookup"><span data-stu-id="da59c-111">ResourceName</span></span>| <span data-ttu-id="da59c-112">El nombre del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="da59c-112">The resource name to depend on.</span></span> <span data-ttu-id="da59c-113">Si el recurso pertenece a una configuración diferente, asegúrese de que el formato del nombre sea el siguiente: "[__TipoDeRecurso__]__NombreDeRecurso__::[__NombreDeConfiguración__]::[__NombreDeConfiguración__]".</span><span class="sxs-lookup"><span data-stu-id="da59c-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="da59c-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="da59c-114">NodeName</span></span>| <span data-ttu-id="da59c-115">Los nodos de destino del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="da59c-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="da59c-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="da59c-116">RetryIntervalSec</span></span>| <span data-ttu-id="da59c-117">El número de segundos antes de reintentar la operación.</span><span class="sxs-lookup"><span data-stu-id="da59c-117">The number of seconds before retrying.</span></span> <span data-ttu-id="da59c-118">El valor mínimo es 1.</span><span class="sxs-lookup"><span data-stu-id="da59c-118">Minimum is 1.</span></span>|
| <span data-ttu-id="da59c-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="da59c-119">RetryCount</span></span>| <span data-ttu-id="da59c-120">El número máximo de reintentos.</span><span class="sxs-lookup"><span data-stu-id="da59c-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="da59c-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="da59c-121">ThrottleLimit</span></span>| <span data-ttu-id="da59c-122">El número de máquinas que se pueden conectar de forma simultánea.</span><span class="sxs-lookup"><span data-stu-id="da59c-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="da59c-123">El valor predeterminado es new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="da59c-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="da59c-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="da59c-124">DependsOn</span></span> | <span data-ttu-id="da59c-125">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="da59c-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="da59c-126">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="da59c-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="da59c-127">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="da59c-127">Example</span></span>

<span data-ttu-id="da59c-128">Para un ejemplo de cómo usar este recurso, consulte [Especificación de dependencias entre nodos](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="da59c-128">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
