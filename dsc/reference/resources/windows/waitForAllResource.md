---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso WaitForAll Resource de DSC
ms.openlocfilehash: c1125b7c5b68b9b520ed052800b6a2abf4e53b85
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726866"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="b9458-103">Recurso WaitForAll Resource de DSC</span><span class="sxs-lookup"><span data-stu-id="b9458-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="b9458-104">Se aplica a: Windows PowerShell 5.0 y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="b9458-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="b9458-105">El recurso **WaitForAll** de Desired State Configuration (DSC) se puede usar dentro de un bloque de nodos en una [configuración de DSC](../../../configurations/configurations.md) para especificar las dependencias de las configuraciones de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="b9458-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="b9458-106">Este recurso se ejecuta si el recurso especificado por la propiedad **ResourceName** está en el estado deseado en todos los nodos de destino definidos en la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="b9458-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="b9458-107">El recurso **WaitForAll** usa Administración remota de Windows para comprobar el estado de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="b9458-107">**WaitForAll** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="b9458-108">Para obtener más información sobre los requisitos de seguridad y puerto de WinRM, vea [Consideraciones de seguridad de comunicación remota de PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="b9458-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="b9458-109">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b9458-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="b9458-110">Propiedades</span><span class="sxs-lookup"><span data-stu-id="b9458-110">Properties</span></span>

|  <span data-ttu-id="b9458-111">Propiedad</span><span class="sxs-lookup"><span data-stu-id="b9458-111">Property</span></span>  |  <span data-ttu-id="b9458-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="b9458-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="b9458-113">nombreDelRecurso</span><span class="sxs-lookup"><span data-stu-id="b9458-113">ResourceName</span></span>| <span data-ttu-id="b9458-114">El nombre del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="b9458-114">The resource name to depend on.</span></span> <span data-ttu-id="b9458-115">Si el recurso pertenece a una configuración diferente, asegúrese de que el formato del nombre sea el siguiente: "[__TipoDeRecurso__]__NombreDeRecurso__::[__NombreDeConfiguración__]::[__NombreDeConfiguración__]".</span><span class="sxs-lookup"><span data-stu-id="b9458-115">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="b9458-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="b9458-116">NodeName</span></span>| <span data-ttu-id="b9458-117">Los nodos de destino del recurso de dependencia.</span><span class="sxs-lookup"><span data-stu-id="b9458-117">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="b9458-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="b9458-118">RetryIntervalSec</span></span>| <span data-ttu-id="b9458-119">El número de segundos antes de reintentar la operación.</span><span class="sxs-lookup"><span data-stu-id="b9458-119">The number of seconds before retrying.</span></span> <span data-ttu-id="b9458-120">El valor mínimo es 1.</span><span class="sxs-lookup"><span data-stu-id="b9458-120">Minimum is 1.</span></span>|
| <span data-ttu-id="b9458-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="b9458-121">RetryCount</span></span>| <span data-ttu-id="b9458-122">El número máximo de reintentos.</span><span class="sxs-lookup"><span data-stu-id="b9458-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="b9458-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="b9458-123">ThrottleLimit</span></span>| <span data-ttu-id="b9458-124">El número de máquinas que se pueden conectar de forma simultánea.</span><span class="sxs-lookup"><span data-stu-id="b9458-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="b9458-125">El valor predeterminado es new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="b9458-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="b9458-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b9458-126">DependsOn</span></span> | <span data-ttu-id="b9458-127">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="b9458-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b9458-128">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b9458-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="b9458-129">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b9458-129">Example</span></span>

<span data-ttu-id="b9458-130">Para un ejemplo de cómo usar este recurso, consulte [Especificación de dependencias entre nodos](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="b9458-130">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
