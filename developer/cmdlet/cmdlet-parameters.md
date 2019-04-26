---
title: Los parámetros de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068409"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="a1c76-102">Parámetros del cmdlet</span><span class="sxs-lookup"><span data-stu-id="a1c76-102">Cmdlet Parameters</span></span>

<span data-ttu-id="a1c76-103">Los parámetros de cmdlet proporcionan el mecanismo que permite que un cmdlet Aceptar la entrada.</span><span class="sxs-lookup"><span data-stu-id="a1c76-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="a1c76-104">Los parámetros pueden aceptar directamente desde la línea de comandos o desde los objetos pasados al cmdlet a través de la canalización, los argumentos de entrada (también conocido como *valores*) de estos parámetros, puede especificar la entrada que el cmdlet acepta, el modo cmdlet debe realizar las acciones y los datos que el cmdlet devuelve a la canalización.</span><span class="sxs-lookup"><span data-stu-id="a1c76-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a1c76-105">En esta sección</span><span class="sxs-lookup"><span data-stu-id="a1c76-105">In This Section</span></span>

<span data-ttu-id="a1c76-106">[Declarar propiedades como parámetros](./declaring-properties-as-parameters.md) proporciona información básica que debe conocer antes de declarar los parámetros de un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a1c76-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="a1c76-107">[Tipos de parámetros de Cmdlet](./types-of-cmdlet-parameters.md) describe los diferentes tipos de parámetros que se pueden declarar en los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a1c76-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="a1c76-108">[Nombre del parámetro de cmdlet y directrices de funcionalidad](./standard-cmdlet-parameter-names-and-types.md) analiza los nombres, se recomienda el tipo de datos y la funcionalidad de los parámetros estándar.</span><span class="sxs-lookup"><span data-stu-id="a1c76-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="a1c76-109">[Alias de parámetro](./parameter-aliases.md) se describen los alias que se pueden definir para los parámetros.</span><span class="sxs-lookup"><span data-stu-id="a1c76-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="a1c76-110">[Los nombres de parámetro comunes](./common-parameter-names.md) en este tema se describe los parámetros que Windows PowerShell agrega a los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a1c76-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="a1c76-111">[Conjuntos de parámetros de cmdlet](./cmdlet-parameter-sets.md) explica cómo conjuntos de parámetros le permiten escribir un solo cmdlet que puede realizar acciones diferentes para distintos escenarios.</span><span class="sxs-lookup"><span data-stu-id="a1c76-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="a1c76-112">[Los parámetros dinámicos de cmdlet](./cmdlet-dynamic-parameters.md) explica los parámetros que están disponibles para el usuario bajo condiciones especiales.</span><span class="sxs-lookup"><span data-stu-id="a1c76-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="a1c76-113">[Compatibilidad con caracteres comodín en los parámetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md) se describe cómo proporcionar compatibilidad con caracteres comodín cuando se diseña un cmdlet que se va a ejecutar en un grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="a1c76-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="a1c76-114">[Validar la entrada del parámetro](./validating-parameter-input.md) se describe cómo Windows PowerShell valida los argumentos pasados a los parámetros de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a1c76-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="a1c76-115">[Parámetros de filtro de entrada](./input-filter-parameters.md) trata la `Filter`, `Include`, y `Exclude` los parámetros que filtran el conjunto de objetos de entrada que afecta el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a1c76-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a1c76-116">Secciones relacionadas</span><span class="sxs-lookup"><span data-stu-id="a1c76-116">Related Sections</span></span>

[<span data-ttu-id="a1c76-117">Cómo validar entrada de parámetros</span><span class="sxs-lookup"><span data-stu-id="a1c76-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="a1c76-118">Véase también</span><span class="sxs-lookup"><span data-stu-id="a1c76-118">See Also</span></span>

[<span data-ttu-id="a1c76-119">Declaración de atributo de parámetro</span><span class="sxs-lookup"><span data-stu-id="a1c76-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="a1c76-120">Cmdlets de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1c76-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
