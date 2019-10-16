---
title: Declaración de atributo de parámetro | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365364"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="5f0b1-102">Declaración de atributo de parámetro</span><span class="sxs-lookup"><span data-stu-id="5f0b1-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="5f0b1-103">El atributo Parameter identifica una propiedad pública de la clase cmdlet como un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f0b1-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5f0b1-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="5f0b1-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5f0b1-105">Parameters</span></span>

<span data-ttu-id="5f0b1-106">parámetro con nombre opcional `Mandatory` ([System. Boolean](/dotnet/api/System.Boolean)).</span><span class="sxs-lookup"><span data-stu-id="5f0b1-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="5f0b1-107">`True` indica que se requiere el parámetro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="5f0b1-108">Si no se proporciona un parámetro necesario cuando se invoca el cmdlet, Windows PowerShell solicita al usuario un valor de parámetro.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="5f0b1-109">El valor predeterminado es `false`.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-109">The default is `false`.</span></span>

<span data-ttu-id="5f0b1-110">parámetro con nombre opcional `ParameterSetName` ([System. String](/dotnet/api/System.String)).</span><span class="sxs-lookup"><span data-stu-id="5f0b1-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="5f0b1-111">Especifica el conjunto de parámetros al que pertenece este parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="5f0b1-112">Si no se especifica ningún conjunto de parámetros, el parámetro pertenece a todos los conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="5f0b1-113">parámetro con nombre opcional `Position` ([System. Int32](/dotnet/api/System.Int32)).</span><span class="sxs-lookup"><span data-stu-id="5f0b1-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="5f0b1-114">Especifica la posición del parámetro en un comando de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="5f0b1-115">parámetro con nombre opcional `ValueFromPipeline` ([System. Boolean](/dotnet/api/System.Boolean)).</span><span class="sxs-lookup"><span data-stu-id="5f0b1-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="5f0b1-116">`True` indica que el parámetro del cmdlet toma su valor de un objeto de canalización.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="5f0b1-117">Especifique esta palabra clave si el cmdlet tiene acceso al objeto completo, no solo a una propiedad del objeto.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="5f0b1-118">El valor predeterminado es `false`.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-118">The default is `false`.</span></span>

<span data-ttu-id="5f0b1-119">parámetro con nombre opcional `ValueFromPipelineByPropertyName` ([System. Boolean](/dotnet/api/System.Boolean)).</span><span class="sxs-lookup"><span data-stu-id="5f0b1-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="5f0b1-120">`True` indica que el parámetro del cmdlet toma su valor de una propiedad de un objeto de canalización que tiene el mismo nombre o el mismo alias que este parámetro.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="5f0b1-121">Por ejemplo, si el cmdlet tiene un parámetro `Name` y el objeto de canalización también tiene una propiedad `Name`, el valor de la propiedad `Name` se asigna al parámetro `Name` del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="5f0b1-122">El valor predeterminado es `false`.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-122">The default is `false`.</span></span>

<span data-ttu-id="5f0b1-123">parámetro con nombre opcional `ValueFromRemainingArguments` ([System. Boolean](/dotnet/api/System.Boolean)).</span><span class="sxs-lookup"><span data-stu-id="5f0b1-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="5f0b1-124">`True` indica que el parámetro del cmdlet acepta todos los argumentos restantes que se pasan al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="5f0b1-125">El valor predeterminado es `false`.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-125">The default is `false`.</span></span>

<span data-ttu-id="5f0b1-126">`HelpMessage` parámetro con nombre opcional.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="5f0b1-127">Especifica una breve descripción del parámetro.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="5f0b1-128">Windows PowerShell muestra este mensaje cuando se ejecuta un cmdlet y no se especifica un parámetro obligatorio.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="5f0b1-129">`HelpMessageBaseName` parámetro con nombre opcional. Especifica la ubicación donde residen los identificadores de recursos.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="5f0b1-130">Por ejemplo, este parámetro puede especificar un ensamblado de recursos que contiene los mensajes de ayuda que desea localizar.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="5f0b1-131">`HelpMessageResourceId` parámetro con nombre opcional. Especifica el identificador de recurso de un mensaje de ayuda.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="5f0b1-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="5f0b1-132">Remarks</span></span>

- <span data-ttu-id="5f0b1-133">Para obtener más información sobre cómo declarar este atributo, vea [cómo declarar parámetros de cmdlet](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5f0b1-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="5f0b1-134">Un cmdlet puede tener cualquier número de parámetros.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="5f0b1-135">Sin embargo, para una mejor experiencia de usuario, limite el número de parámetros.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="5f0b1-136">Los parámetros se deben declarar en campos o propiedades públicos no estáticos.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="5f0b1-137">Los parámetros se deben declarar en las propiedades.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="5f0b1-138">La propiedad debe tener un descriptor de acceso set público y, si se especifica la palabra clave `ValueFromPipeline` o `ValueFromPipelineByPropertyName`, la propiedad debe tener un descriptor de acceso get público.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="5f0b1-139">Al especificar parámetros posicionales, limite el número de parámetros posicionales en un parámetro establecido en un valor inferior a cinco.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="5f0b1-140">Y, los parámetros posicionales no tienen que ser contiguos.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="5f0b1-141">Las posiciones 5, 100 y 250 funcionan igual que las posiciones 0, 1 y 2.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="5f0b1-142">Cuando no se especifica la palabra clave `Position`, se debe hacer referencia al parámetro del cmdlet por su nombre.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="5f0b1-143">Cuando use conjuntos de parámetros, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="5f0b1-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="5f0b1-144">Cada conjunto de parámetros debe tener al menos un parámetro único.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="5f0b1-145">Un buen diseño de cmdlet indica que este parámetro único también debe ser obligatorio si es posible.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="5f0b1-146">Si el cmdlet está diseñado para ejecutarse sin parámetros, el parámetro único no puede ser obligatorio.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="5f0b1-147">Ningún conjunto de parámetros debe contener más de un parámetro posicional con la misma posición.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="5f0b1-148">Solo un parámetro de un conjunto de parámetros debe declarar `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="5f0b1-149">Varios parámetros pueden definir `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="5f0b1-150">Varios parámetros pueden definir `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="5f0b1-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="5f0b1-151">Para obtener más información sobre las directrices para los nombres de parámetro, consulte [nombres de parámetros de cmdlet](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="5f0b1-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="5f0b1-152">El atributo Parameter se define mediante la clase [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .</span><span class="sxs-lookup"><span data-stu-id="5f0b1-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f0b1-153">Véase también</span><span class="sxs-lookup"><span data-stu-id="5f0b1-153">See Also</span></span>

[<span data-ttu-id="5f0b1-154">System. Management. Automation. Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="5f0b1-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="5f0b1-155">Nombres de parámetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f0b1-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="5f0b1-156">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f0b1-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
