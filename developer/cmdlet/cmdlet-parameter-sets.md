---
title: Conjuntos de parámetros de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: d8c00c7ffd369a32af151836785a2c5f47b05a68
ms.sourcegitcommit: 889b93d170aeb3d444288e7ccf67e62ce822cb7c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936196"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="981d9-102">Conjuntos de parámetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="981d9-102">Cmdlet parameter sets</span></span>

<span data-ttu-id="981d9-103">PowerShell usa conjuntos de parámetros para que pueda escribir un único cmdlet que puede realizar diferentes acciones en diferentes escenarios.</span><span class="sxs-lookup"><span data-stu-id="981d9-103">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="981d9-104">Los conjuntos de parámetros permiten exponer diferentes parámetros al usuario.</span><span class="sxs-lookup"><span data-stu-id="981d9-104">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="981d9-105">Y, para devolver información diferente en función de los parámetros especificados por el usuario.</span><span class="sxs-lookup"><span data-stu-id="981d9-105">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="981d9-106">Ejemplos de conjuntos de parámetros</span><span class="sxs-lookup"><span data-stu-id="981d9-106">Examples of parameter sets</span></span>

<span data-ttu-id="981d9-107">Por ejemplo, el cmdlet `Get-EventLog` de PowerShell devuelve información diferente en función de si el usuario especifica el parámetro **List** o **logname** .</span><span class="sxs-lookup"><span data-stu-id="981d9-107">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="981d9-108">Si se especifica el parámetro **List** , el cmdlet devuelve información sobre los propios archivos de registro, pero no la información de evento que contienen.</span><span class="sxs-lookup"><span data-stu-id="981d9-108">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="981d9-109">Si se especifica el parámetro **logname** , el cmdlet devuelve información sobre los eventos de un registro de eventos específico.</span><span class="sxs-lookup"><span data-stu-id="981d9-109">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="981d9-110">Los parámetros **List** y **logname** identifican dos conjuntos de parámetros independientes.</span><span class="sxs-lookup"><span data-stu-id="981d9-110">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="981d9-111">Parámetro único</span><span class="sxs-lookup"><span data-stu-id="981d9-111">Unique parameter</span></span>

<span data-ttu-id="981d9-112">Cada conjunto de parámetros debe tener un parámetro único que el motor en tiempo de ejecución de PowerShell use para exponer el conjunto de parámetros adecuado.</span><span class="sxs-lookup"><span data-stu-id="981d9-112">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="981d9-113">Si es posible, el parámetro único debe ser un parámetro obligatorio.</span><span class="sxs-lookup"><span data-stu-id="981d9-113">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="981d9-114">Cuando un parámetro es obligatorio, el usuario debe especificar el parámetro y el tiempo de ejecución de PowerShell usa ese parámetro para identificar el conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="981d9-114">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="981d9-115">El parámetro Unique no puede ser obligatorio si el cmdlet está diseñado para ejecutarse sin especificar ningún parámetro.</span><span class="sxs-lookup"><span data-stu-id="981d9-115">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="981d9-116">Varios conjuntos de parámetros</span><span class="sxs-lookup"><span data-stu-id="981d9-116">Multiple parameter sets</span></span>

<span data-ttu-id="981d9-117">En la ilustración siguiente, la columna izquierda muestra tres conjuntos de parámetros válidos.</span><span class="sxs-lookup"><span data-stu-id="981d9-117">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="981d9-118">El **parámetro** a es único para el primer conjunto de parámetros, el **parámetro B** es único para el segundo conjunto de parámetros y el **parámetro C** es único para el tercer conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="981d9-118">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="981d9-119">En la columna derecha, los conjuntos de parámetros no tienen un parámetro único.</span><span class="sxs-lookup"><span data-stu-id="981d9-119">In the right column, the parameter sets don't have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="981d9-121">Requisitos del conjunto de parámetros</span><span class="sxs-lookup"><span data-stu-id="981d9-121">Parameter set requirements</span></span>

<span data-ttu-id="981d9-122">Los siguientes requisitos se aplican a todos los conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="981d9-122">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="981d9-123">Cada conjunto de parámetros debe tener al menos un parámetro único.</span><span class="sxs-lookup"><span data-stu-id="981d9-123">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="981d9-124">Si es posible, convierta este parámetro en un parámetro obligatorio.</span><span class="sxs-lookup"><span data-stu-id="981d9-124">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="981d9-125">Un conjunto de parámetros que contiene varios parámetros posicionales debe definir posiciones únicas para cada parámetro.</span><span class="sxs-lookup"><span data-stu-id="981d9-125">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="981d9-126">Dos parámetros posicionales no pueden especificar la misma posición.</span><span class="sxs-lookup"><span data-stu-id="981d9-126">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="981d9-127">Solo un parámetro de un conjunto puede declarar la `ValueFromPipeline` palabra clave con un valor `true`de.</span><span class="sxs-lookup"><span data-stu-id="981d9-127">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="981d9-128">Varios parámetros pueden definir la `ValueFromPipelineByPropertyName` palabra clave con un valor `true`de.</span><span class="sxs-lookup"><span data-stu-id="981d9-128">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="981d9-129">Si no se especifica ningún conjunto de parámetros para un parámetro, el parámetro pertenece a todos los conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="981d9-129">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="981d9-130">Para un cmdlet o una función, hay un límite de 32 conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="981d9-130">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="981d9-131">Conjuntos de parámetros predeterminados</span><span class="sxs-lookup"><span data-stu-id="981d9-131">Default parameter sets</span></span>

<span data-ttu-id="981d9-132">Cuando se definen varios conjuntos de parámetros, puede usar la `DefaultParameterSetName` palabra clave del atributo **cmdlet** para especificar el conjunto de parámetros predeterminado.</span><span class="sxs-lookup"><span data-stu-id="981d9-132">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="981d9-133">PowerShell usa el conjunto de parámetros predeterminado si no puede determinar el conjunto de parámetros que se va a usar según la información proporcionada por el comando.</span><span class="sxs-lookup"><span data-stu-id="981d9-133">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="981d9-134">Para obtener más información sobre el atributo **cmdlet** , consulte [declaración de atributos de cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="981d9-134">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="981d9-135">Declarar conjuntos de parámetros</span><span class="sxs-lookup"><span data-stu-id="981d9-135">Declaring parameter sets</span></span>

<span data-ttu-id="981d9-136">Para crear un conjunto de parámetros, debe especificar la `ParameterSetName` palabra clave al declarar el atributo de **parámetro** para cada parámetro del conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="981d9-136">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="981d9-137">Para los parámetros que pertenecen a varios conjuntos de parámetros, agregue un atributo de **parámetro** para cada conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="981d9-137">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="981d9-138">Este atributo permite definir el parámetro de forma diferente para cada conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="981d9-138">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="981d9-139">Por ejemplo, puede definir un parámetro como obligatorio en un conjunto y opcional en otro.</span><span class="sxs-lookup"><span data-stu-id="981d9-139">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="981d9-140">Sin embargo, cada conjunto de parámetros debe contener un parámetro único.</span><span class="sxs-lookup"><span data-stu-id="981d9-140">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="981d9-141">Para obtener más información, vea [declaración de atributos de parámetros](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="981d9-141">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="981d9-142">En el ejemplo siguiente, el parámetro de **nombre de usuario** es el parámetro `Test01` único del conjunto de parámetros y el parámetro **ComputerName** `Test02` es el parámetro único del conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="981d9-142">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="981d9-143">El parámetro **SharedParam** pertenece a ambos conjuntos y es obligatorio para el `Test01` conjunto de parámetros, pero es `Test02` opcional para el conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="981d9-143">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

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
private string sharedParam;
```
