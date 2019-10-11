---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso WaitForAny Resource de DSC
ms.openlocfilehash: 61fee456d2652e08ed9bdbe64457627ff5b2e145
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953002"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="3abdc-103">Recurso WaitForAny Resource de DSC</span><span class="sxs-lookup"><span data-stu-id="3abdc-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="3abdc-104">Se aplica a: Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="3abdc-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="3abdc-105">El recurso **WaitForAny** de Desired State Configuration (DSC) se puede usar dentro de un bloque de nodos en una [configuración de DSC](../../../configurations/configurations.md) para especificar las dependencias de las configuraciones de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="3abdc-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="3abdc-106">Este recurso se ejecuta si el recurso especificado por la propiedad **ResourceName** está en el estado deseado en cualquier nodo de destino definido en la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="3abdc-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="3abdc-107">El recurso **WaitForAny** usa Administración remota de Windows para comprobar el estado de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="3abdc-107">**WaitForAny** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="3abdc-108">Para obtener más información sobre los requisitos de seguridad y puerto de WinRM, vea [Consideraciones de seguridad de comunicación remota de PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="3abdc-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="3abdc-109">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3abdc-109">Syntax</span></span>

```Syntax
WaitForAny [string] #ResourceName
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

## <a name="properties"></a><span data-ttu-id="3abdc-110">Propiedades</span><span class="sxs-lookup"><span data-stu-id="3abdc-110">Properties</span></span>

|<span data-ttu-id="3abdc-111">Propiedad</span><span class="sxs-lookup"><span data-stu-id="3abdc-111">Property</span></span> |<span data-ttu-id="3abdc-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="3abdc-112">Description</span></span> |
|---|---|
|<span data-ttu-id="3abdc-113">nombreDelRecurso</span><span class="sxs-lookup"><span data-stu-id="3abdc-113">ResourceName</span></span> |<span data-ttu-id="3abdc-114">El nombre del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="3abdc-114">The resource name to depend on.</span></span> <span data-ttu-id="3abdc-115">Si este recurso pertenece a una configuración diferente, dé el siguiente formato al nombre: `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span><span class="sxs-lookup"><span data-stu-id="3abdc-115">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="3abdc-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="3abdc-116">NodeName</span></span> |<span data-ttu-id="3abdc-117">Los nodos de destino del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="3abdc-117">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="3abdc-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="3abdc-118">RetryIntervalSec</span></span> |<span data-ttu-id="3abdc-119">El número de segundos antes de reintentar la operación.</span><span class="sxs-lookup"><span data-stu-id="3abdc-119">The number of seconds before retrying.</span></span> <span data-ttu-id="3abdc-120">El valor mínimo es 1.</span><span class="sxs-lookup"><span data-stu-id="3abdc-120">Minimum is 1.</span></span> |
|<span data-ttu-id="3abdc-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="3abdc-121">RetryCount</span></span> |<span data-ttu-id="3abdc-122">El número máximo de reintentos.</span><span class="sxs-lookup"><span data-stu-id="3abdc-122">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="3abdc-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="3abdc-123">ThrottleLimit</span></span> |<span data-ttu-id="3abdc-124">El número de máquinas que se pueden conectar de forma simultánea.</span><span class="sxs-lookup"><span data-stu-id="3abdc-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="3abdc-125">El valor predeterminado es `New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="3abdc-125">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="3abdc-126">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="3abdc-126">Common properties</span></span>

|<span data-ttu-id="3abdc-127">Propiedad</span><span class="sxs-lookup"><span data-stu-id="3abdc-127">Property</span></span> |<span data-ttu-id="3abdc-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="3abdc-128">Description</span></span> |
|---|---|
|<span data-ttu-id="3abdc-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="3abdc-129">DependsOn</span></span> |<span data-ttu-id="3abdc-130">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="3abdc-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3abdc-131">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="3abdc-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="3abdc-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="3abdc-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="3abdc-133">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="3abdc-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="3abdc-134">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="3abdc-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="3abdc-135">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="3abdc-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="3abdc-136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3abdc-136">Example</span></span>

<span data-ttu-id="3abdc-137">Para un ejemplo de cómo usar este recurso, consulte [Especificación de dependencias entre nodos](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="3abdc-137">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>