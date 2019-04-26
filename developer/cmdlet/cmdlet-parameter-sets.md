---
title: Establece el parámetro de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068519"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="5299c-102">Conjuntos de parámetros del cmdlet</span><span class="sxs-lookup"><span data-stu-id="5299c-102">Cmdlet Parameter Sets</span></span>

<span data-ttu-id="5299c-103">Windows PowerShell usa conjuntos de parámetros para que pueda escribir un solo cmdlet que puede realizar acciones diferentes para distintos escenarios.</span><span class="sxs-lookup"><span data-stu-id="5299c-103">Windows PowerShell uses parameter sets to enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span> <span data-ttu-id="5299c-104">Conjuntos de parámetros le permiten exponer diferentes parámetros para el usuario y para devolver información diferente en función de los parámetros especificados por el usuario.</span><span class="sxs-lookup"><span data-stu-id="5299c-104">Parameter sets enable you to expose different parameters to the user and to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="5299c-105">Ejemplos de conjuntos de parámetros</span><span class="sxs-lookup"><span data-stu-id="5299c-105">Examples of Parameter Sets</span></span>

<span data-ttu-id="5299c-106">Por ejemplo, el `Get-EventLog` cmdlet (proporcionado por Windows PowerShell) devuelve información diferente dependiendo de si el usuario especifica la `List` o `LogName` parámetro.</span><span class="sxs-lookup"><span data-stu-id="5299c-106">For example, the `Get-EventLog` cmdlet (provided by Windows PowerShell) returns different information depending on whether the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="5299c-107">Si el `List` parámetro se especifica, el cmdlet devuelve información acerca de los archivos de registro a sí mismos, pero no la información de evento que contienen.</span><span class="sxs-lookup"><span data-stu-id="5299c-107">If the `List` parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="5299c-108">Si el `LogName` parámetro se especifica, el cmdlet devuelve información acerca de los eventos en un registro de eventos específico.</span><span class="sxs-lookup"><span data-stu-id="5299c-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="5299c-109">El `List` y `LogName` parámetros identifican dos conjuntos de parámetros independiente.</span><span class="sxs-lookup"><span data-stu-id="5299c-109">The `List` and `LogName` parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="5299c-110">Parámetro único</span><span class="sxs-lookup"><span data-stu-id="5299c-110">Unique Parameter</span></span>

<span data-ttu-id="5299c-111">Cada conjunto de parámetros debe tener un parámetro único que puede utilizar el tiempo de ejecución de Windows PowerShell para exponer el conjunto de parámetros apropiado.</span><span class="sxs-lookup"><span data-stu-id="5299c-111">Each parameter set must have a unique parameter that the Windows PowerShell runtime can use to expose the appropriate parameter set.</span></span> <span data-ttu-id="5299c-112">Si es posible, el único parámetro debe ser un parámetro obligatorio.</span><span class="sxs-lookup"><span data-stu-id="5299c-112">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="5299c-113">Cuando un parámetro es obligatorio, se obliga al usuario especificar el parámetro y el tiempo de ejecución de Windows PowerShell puede usar ese parámetro para identificar el parámetro configurado para usar.</span><span class="sxs-lookup"><span data-stu-id="5299c-113">When a parameter is mandatory, the user is forced to specify the parameter, and the Windows PowerShell runtime can use that parameter to identify the parameter set to use.</span></span> <span data-ttu-id="5299c-114">El parámetro unique no puede ser obligatorio si el cmdlet está diseñado para ejecutarse sin especificar ningún parámetro.</span><span class="sxs-lookup"><span data-stu-id="5299c-114">The unique parameter cannot be mandatory if your cmdlet is designed to be run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="5299c-115">Varios conjuntos de parámetros</span><span class="sxs-lookup"><span data-stu-id="5299c-115">Multiple Parameter Sets</span></span>

<span data-ttu-id="5299c-116">En la siguiente ilustración, la columna izquierda muestra tres conjuntos de parámetros válidos.</span><span class="sxs-lookup"><span data-stu-id="5299c-116">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="5299c-117">Un parámetro es único para el primer conjunto de parámetros, parámetro B es único para el segundo conjunto de parámetros y parámetro C es único para el tercer conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="5299c-117">Parameter A is unique to the first parameter set, parameter B is unique to the second parameter set, and parameter C is unique to the third parameter set.</span></span> <span data-ttu-id="5299c-118">Sin embargo, en la columna derecha, los conjuntos de parámetros no tienen un parámetro único.</span><span class="sxs-lookup"><span data-stu-id="5299c-118">However, in the right column, the parameter sets do not have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="5299c-120">Requisitos del conjunto de parámetros</span><span class="sxs-lookup"><span data-stu-id="5299c-120">Parameter Set Requirements</span></span>

<span data-ttu-id="5299c-121">Los siguientes requisitos se aplican a todos los conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="5299c-121">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="5299c-122">Cada conjunto de parámetros debe tener al menos un parámetro único.</span><span class="sxs-lookup"><span data-stu-id="5299c-122">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="5299c-123">Asegúrese de este parámetro si es posible, un parámetro obligatorio.</span><span class="sxs-lookup"><span data-stu-id="5299c-123">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="5299c-124">Un conjunto de parámetros que contiene varios parámetros posicionales debe definir posiciones únicas para cada parámetro.</span><span class="sxs-lookup"><span data-stu-id="5299c-124">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="5299c-125">No hay dos parámetros posicionales pueden especificar la misma posición.</span><span class="sxs-lookup"><span data-stu-id="5299c-125">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="5299c-126">Solo un parámetro en un conjunto se puede declarar el `ValueFromPipeline` palabra clave con un valor de `true`.</span><span class="sxs-lookup"><span data-stu-id="5299c-126">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="5299c-127">Pueden definir varios parámetros la `ValueFromPipelineByPropertyName` palabra clave con un valor de `true`.</span><span class="sxs-lookup"><span data-stu-id="5299c-127">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="5299c-128">Si no se especifica ningún conjunto de parámetros para un parámetro, el parámetro pertenece a todos los conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="5299c-128">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="5299c-129">Conjuntos de parámetros predeterminados</span><span class="sxs-lookup"><span data-stu-id="5299c-129">Default Parameter Sets</span></span>

<span data-ttu-id="5299c-130">Cuando se definen varios conjuntos de parámetros, puede usar el `DefaultParameterSetName` palabra clave del atributo de Cmdlet para especificar el conjunto de parámetros de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="5299c-130">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the Cmdlet attribute to specify the default parameter set.</span></span> <span data-ttu-id="5299c-131">Windows PowerShell usa el parámetro predeterminado configurado si no se puede determinar el parámetro establecido en utilizar según la información proporcionada por el comando.</span><span class="sxs-lookup"><span data-stu-id="5299c-131">Windows PowerShell uses the default parameter set if it cannot determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="5299c-132">Para obtener más información sobre el atributo de Cmdlet, consulte [declaración de atributo de Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5299c-132">For more information about the Cmdlet attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="5299c-133">Declarar los conjuntos de parámetros</span><span class="sxs-lookup"><span data-stu-id="5299c-133">Declaring Parameter Sets</span></span>

<span data-ttu-id="5299c-134">Para crear un conjunto de parámetros, debe especificar el `ParameterSetName` palabra clave cuando se declara el atributo de parámetro para cada parámetro en el conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="5299c-134">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the Parameter attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="5299c-135">Para los parámetros que pertenecen a varios conjuntos de parámetros, agregue un atributo de parámetro para cada conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="5299c-135">For parameters that belong to multiple parameter sets, add a Parameter attribute for each parameter set.</span></span> <span data-ttu-id="5299c-136">Esto le permite definir el parámetro de forma diferente para cada conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="5299c-136">This enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="5299c-137">Por ejemplo, puede definir un parámetro como obligatorio en un conjunto y opcional en otro.</span><span class="sxs-lookup"><span data-stu-id="5299c-137">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="5299c-138">Sin embargo, cada conjunto de parámetros debe contener un parámetro único.</span><span class="sxs-lookup"><span data-stu-id="5299c-138">However, each parameter set must contain one unique parameter.</span></span>

<span data-ttu-id="5299c-139">En el ejemplo siguiente, la `UserName` parámetro es el único parámetro del conjunto de parámetro Test01 y el `ComputerName` parámetro es el único parámetro del conjunto de parámetro Prueba02.</span><span class="sxs-lookup"><span data-stu-id="5299c-139">In the following example, the `UserName` parameter is the unique parameter of the Test01 parameter set, and the `ComputerName` parameter is the unique parameter of the Test02 parameter set.</span></span> <span data-ttu-id="5299c-140">El `SharedParam` parámetro pertenece a ambos conjuntos y es obligatorio para el parámetro Test01 establecer pero opcional para el conjunto de parámetros Prueba02.</span><span class="sxs-lookup"><span data-stu-id="5299c-140">The `SharedParam` parameter belongs to both sets and is mandatory for the Test01 parameter set but optional for the Test02 parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```