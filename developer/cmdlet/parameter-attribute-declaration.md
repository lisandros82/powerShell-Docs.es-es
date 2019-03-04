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
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: 10c347a8c3dcbf8962295601834f5ba85342a87b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "56863621"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="a9925-102">Declaración de atributo de parámetro</span><span class="sxs-lookup"><span data-stu-id="a9925-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="a9925-103">El atributo de parámetro identifica una propiedad pública de la clase de cmdlet como un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a9925-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="a9925-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="a9925-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="a9925-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9925-105">Parameters</span></span>

<span data-ttu-id="a9925-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) con el nombre de parámetro opcional.</span><span class="sxs-lookup"><span data-stu-id="a9925-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a9925-107">`True` indica que el parámetro de cmdlet es necesario.</span><span class="sxs-lookup"><span data-stu-id="a9925-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="a9925-108">Si no se proporciona un parámetro obligatorio cuando se invoca el cmdlet, Windows PowerShell solicita al usuario para un valor de parámetro.</span><span class="sxs-lookup"><span data-stu-id="a9925-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="a9925-109">El valor predeterminado es `false`.</span><span class="sxs-lookup"><span data-stu-id="a9925-109">The default is `false`.</span></span>

<span data-ttu-id="a9925-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) con el nombre de parámetro opcional.</span><span class="sxs-lookup"><span data-stu-id="a9925-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="a9925-111">Especifica que el parámetro establecido que pertenece este parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a9925-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="a9925-112">Si no se especifica ningún conjunto de parámetros, el parámetro pertenece a todos los conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="a9925-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="a9925-113">`Position` ([System.Integer](/dotnet/api/System.Integer)) con el nombre de parámetro opcional.</span><span class="sxs-lookup"><span data-stu-id="a9925-113">`Position` ([System.Integer](/dotnet/api/System.Integer)) Optional named parameter.</span></span> <span data-ttu-id="a9925-114">Especifica la posición del parámetro dentro de un comando de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9925-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="a9925-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) con el nombre de parámetro opcional.</span><span class="sxs-lookup"><span data-stu-id="a9925-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a9925-116">`True` indica que el parámetro de cmdlet toma su valor de un objeto de canalización.</span><span class="sxs-lookup"><span data-stu-id="a9925-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="a9925-117">Especifique esta palabra clave si el cmdlet obtiene acceso a la completa de objetos, no solo una propiedad del objeto.</span><span class="sxs-lookup"><span data-stu-id="a9925-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="a9925-118">El valor predeterminado es `false`.</span><span class="sxs-lookup"><span data-stu-id="a9925-118">The default is `false`.</span></span>

<span data-ttu-id="a9925-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) con el nombre de parámetro opcional.</span><span class="sxs-lookup"><span data-stu-id="a9925-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a9925-120">`True` indica que el parámetro de cmdlet toma su valor de una propiedad de un objeto de canalización que tiene el mismo nombre o el mismo alias como este parámetro.</span><span class="sxs-lookup"><span data-stu-id="a9925-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="a9925-121">Por ejemplo, si el cmdlet tiene un `Name` parámetro y el objeto de canalización también tiene un `Name` propiedad, el valor de la `Name` propiedad se asigna a la `Name` parámetro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a9925-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="a9925-122">El valor predeterminado es `false`.</span><span class="sxs-lookup"><span data-stu-id="a9925-122">The default is `false`.</span></span>

<span data-ttu-id="a9925-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) con el nombre de parámetro opcional.</span><span class="sxs-lookup"><span data-stu-id="a9925-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a9925-124">`True` indica que el parámetro de cmdlet acepta todos los argumentos restantes que se pasan al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a9925-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="a9925-125">El valor predeterminado es `false`.</span><span class="sxs-lookup"><span data-stu-id="a9925-125">The default is `false`.</span></span>

<span data-ttu-id="a9925-126">`HelpMessage` Parámetro con nombre opcional.</span><span class="sxs-lookup"><span data-stu-id="a9925-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="a9925-127">Especifica una breve descripción del parámetro.</span><span class="sxs-lookup"><span data-stu-id="a9925-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="a9925-128">Windows PowerShell muestra este mensaje cuando se ejecuta un cmdlet y no se especifica un parámetro obligatorio.</span><span class="sxs-lookup"><span data-stu-id="a9925-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="a9925-129">`HelpMessageBaseName` Parámetro con nombre opcional. Especifica la ubicación donde residen los identificadores de recursos.</span><span class="sxs-lookup"><span data-stu-id="a9925-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="a9925-130">Por ejemplo, este parámetro podría especificar un ensamblado de recursos que contiene mensajes de ayuda que desee localizar.</span><span class="sxs-lookup"><span data-stu-id="a9925-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="a9925-131">`HelpMessageResourceId` Parámetro con nombre opcional. Especifica el identificador de recurso para un mensaje de ayuda.</span><span class="sxs-lookup"><span data-stu-id="a9925-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9925-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="a9925-132">Remarks</span></span>

- <span data-ttu-id="a9925-133">Para obtener más información acerca de cómo declarar este atributo, vea [cómo declarar los parámetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a9925-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="a9925-134">Un cmdlet puede tener cualquier número de parámetros.</span><span class="sxs-lookup"><span data-stu-id="a9925-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="a9925-135">Sin embargo, para una mejor experiencia de usuario, limite el número de parámetros.</span><span class="sxs-lookup"><span data-stu-id="a9925-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="a9925-136">Parámetros se deben declarar en los campos no estáticos públicos o propiedades.</span><span class="sxs-lookup"><span data-stu-id="a9925-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="a9925-137">Se deben declarar como parámetros en Propiedades.</span><span class="sxs-lookup"><span data-stu-id="a9925-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="a9925-138">La propiedad debe tener un descriptor de acceso set público y si el `ValueFromPipeline` o `ValueFromPipelineByPropertyName` se especifica la palabra clave, la propiedad debe tener un descriptor de acceso get público.</span><span class="sxs-lookup"><span data-stu-id="a9925-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="a9925-139">Cuando se especifican parámetros posicionales, limitar el número de parámetros posicionales en un parámetro establecido en menos de cinco.</span><span class="sxs-lookup"><span data-stu-id="a9925-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="a9925-140">Y los parámetros posicionales no tiene que ser contiguas.</span><span class="sxs-lookup"><span data-stu-id="a9925-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="a9925-141">Las posiciones 5, 100 y 250 funcionan igual que las posiciones 0, 1 y 2.</span><span class="sxs-lookup"><span data-stu-id="a9925-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="a9925-142">Cuando el `Position` palabra clave no se especifica, el parámetro de cmdlet debe hacer referencia a su nombre.</span><span class="sxs-lookup"><span data-stu-id="a9925-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="a9925-143">Al usar conjuntos de parámetros, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a9925-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="a9925-144">Cada conjunto de parámetros debe tener al menos un parámetro único.</span><span class="sxs-lookup"><span data-stu-id="a9925-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="a9925-145">Cmdlet de buen diseño indica que este parámetro único también debería obligatorio si es posible.</span><span class="sxs-lookup"><span data-stu-id="a9925-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="a9925-146">Si el cmdlet está diseñado para ejecutarse sin parámetros, el único parámetro no puede ser obligatorio.</span><span class="sxs-lookup"><span data-stu-id="a9925-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="a9925-147">Ningún conjunto de parámetros debe contener más de un parámetro de posición con la misma posición.</span><span class="sxs-lookup"><span data-stu-id="a9925-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="a9925-148">Solo un parámetro en un conjunto de parámetros debe declarar `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="a9925-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="a9925-149">Pueden definir varios parámetros `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="a9925-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="a9925-150">Pueden definir varios parámetros `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="a9925-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="a9925-151">Para obtener más información sobre las directrices para los nombres de parámetros, vea [los nombres de parámetro de Cmdlet](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="a9925-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="a9925-152">El atributo de parámetro está definido por el [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) clase.</span><span class="sxs-lookup"><span data-stu-id="a9925-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9925-153">Véase también</span><span class="sxs-lookup"><span data-stu-id="a9925-153">See Also</span></span>

[<span data-ttu-id="a9925-154">System.Management.Automation.Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="a9925-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="a9925-155">Nombres de parámetro de cmdlet</span><span class="sxs-lookup"><span data-stu-id="a9925-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="a9925-156">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a9925-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
