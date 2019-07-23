---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso WaitForSome de DSC
ms.openlocfilehash: 2260f37002171154a6f2c3996b2af1bd9120039d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726772"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="a3347-103">Recurso WaitForSome de DSC</span><span class="sxs-lookup"><span data-stu-id="a3347-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="a3347-104">Se aplica a: Windows PowerShell 5.0 y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="a3347-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="a3347-105">El recurso **WaitForSome** de Desired State Configuration (DSC) se puede usar dentro de un bloque de nodos en una [configuración de DSC](../../../configurations/configurations.md) para especificar las dependencias de las configuraciones de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="a3347-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="a3347-106">Este recurso se ejecuta si el recurso especificado por la propiedad **ResourceName** está en el estado deseado en un número mínimo de nodos (especificado por **NodeCount**) definido por la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="a3347-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="a3347-107">El recurso **WaitForSome** usa Administración remota de Windows para comprobar el estado de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="a3347-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="a3347-108">Para obtener más información sobre los requisitos de seguridad y puerto de WinRM, vea [Consideraciones de seguridad de comunicación remota de PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="a3347-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="a3347-109">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="a3347-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="a3347-110">Propiedades</span><span class="sxs-lookup"><span data-stu-id="a3347-110">Properties</span></span>

|  <span data-ttu-id="a3347-111">Propiedad</span><span class="sxs-lookup"><span data-stu-id="a3347-111">Property</span></span>  |  <span data-ttu-id="a3347-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="a3347-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="a3347-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="a3347-113">NodeCount</span></span>| <span data-ttu-id="a3347-114">El número mínimo de nodos que deben tener el estado deseado para que se ejecute este recurso.</span><span class="sxs-lookup"><span data-stu-id="a3347-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="a3347-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="a3347-115">NodeName</span></span>| <span data-ttu-id="a3347-116">Los nodos de destino del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="a3347-116">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="a3347-117">nombreDelRecurso</span><span class="sxs-lookup"><span data-stu-id="a3347-117">ResourceName</span></span>| <span data-ttu-id="a3347-118">El nombre del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="a3347-118">The resource name to depend on.</span></span> <span data-ttu-id="a3347-119">Si el recurso pertenece a una configuración diferente, asegúrese de que el formato del nombre sea el siguiente: "[__TipoDeRecurso__]__NombreDeRecurso__::[__NombreDeConfiguración__]::[__NombreDeConfiguración__]".</span><span class="sxs-lookup"><span data-stu-id="a3347-119">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="a3347-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="a3347-120">RetryIntervalSec</span></span>| <span data-ttu-id="a3347-121">El número de segundos antes de reintentar la operación.</span><span class="sxs-lookup"><span data-stu-id="a3347-121">The number of seconds before retrying.</span></span> <span data-ttu-id="a3347-122">El valor mínimo es 1.</span><span class="sxs-lookup"><span data-stu-id="a3347-122">Minimum is 1.</span></span>|
| <span data-ttu-id="a3347-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="a3347-123">RetryCount</span></span>| <span data-ttu-id="a3347-124">El número máximo de reintentos.</span><span class="sxs-lookup"><span data-stu-id="a3347-124">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="a3347-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="a3347-125">ThrottleLimit</span></span>| <span data-ttu-id="a3347-126">El número de máquinas que se pueden conectar de forma simultánea.</span><span class="sxs-lookup"><span data-stu-id="a3347-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="a3347-127">El valor predeterminado es new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="a3347-127">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="a3347-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a3347-128">DependsOn</span></span> | <span data-ttu-id="a3347-129">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="a3347-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a3347-130">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a3347-130">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="a3347-131">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a3347-131">PsDscRunAsCredential</span></span> | <span data-ttu-id="a3347-132">Consulte el artículo sobre el [uso de DSC con credenciales de usuario](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="a3347-132">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="a3347-133">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a3347-133">Example</span></span>

<span data-ttu-id="a3347-134">Para un ejemplo de cómo usar este recurso, consulte [Especificación de dependencias entre nodos](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="a3347-134">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
