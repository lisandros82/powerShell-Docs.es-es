---
title: Parámetros de cmdlet | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365934"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="e1121-102">Parámetros del cmdlet</span><span class="sxs-lookup"><span data-stu-id="e1121-102">Cmdlet Parameters</span></span>

<span data-ttu-id="e1121-103">Los parámetros de cmdlet proporcionan el mecanismo que permite a un cmdlet aceptar la entrada.</span><span class="sxs-lookup"><span data-stu-id="e1121-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="e1121-104">Los parámetros pueden aceptar la entrada directamente desde la línea de comandos o desde los objetos pasados al cmdlet a través de la canalización, los argumentos (también conocidos como *valores*) de estos parámetros pueden especificar la entrada que el cmdlet acepta, cómo el cmdlet debe realizar sus acciones y los datos que el cmdlet devuelve a la canalización.</span><span class="sxs-lookup"><span data-stu-id="e1121-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e1121-105">En esta sección</span><span class="sxs-lookup"><span data-stu-id="e1121-105">In This Section</span></span>

<span data-ttu-id="e1121-106">[Declarar propiedades como parámetros](./declaring-properties-as-parameters.md) Proporciona información básica que debe conocer antes de declarar los parámetros de un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e1121-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="e1121-107">[Tipos de parámetros de cmdlet](./types-of-cmdlet-parameters.md) Describe los diferentes tipos de parámetros que se pueden declarar en los cmdlets de.</span><span class="sxs-lookup"><span data-stu-id="e1121-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="e1121-108">[Instrucciones del nombre y la funcionalidad de los parámetros de cmdlet](./standard-cmdlet-parameter-names-and-types.md) Discuses los nombres, el tipo de datos recomendado y la funcionalidad de los parámetros estándar.</span><span class="sxs-lookup"><span data-stu-id="e1121-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="e1121-109">[Alias de parámetro](./parameter-aliases.md) Describe los alias que se pueden definir para los parámetros.</span><span class="sxs-lookup"><span data-stu-id="e1121-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="e1121-110">[Nombres de parámetros comunes](./common-parameter-names.md) En este tema se describen los parámetros que Windows PowerShell agrega a los cmdlets de.</span><span class="sxs-lookup"><span data-stu-id="e1121-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="e1121-111">[Conjuntos de parámetros de cmdlet](./cmdlet-parameter-sets.md) Describe cómo los conjuntos de parámetros le permiten escribir un único cmdlet que puede realizar diferentes acciones en diferentes escenarios.</span><span class="sxs-lookup"><span data-stu-id="e1121-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="e1121-112">[Parámetros dinámicos de cmdlet](./cmdlet-dynamic-parameters.md) Describe los parámetros que están disponibles para el usuario en condiciones especiales.</span><span class="sxs-lookup"><span data-stu-id="e1121-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="e1121-113">[Compatibilidad con caracteres comodín en parámetros de cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describe cómo proporcionar compatibilidad con caracteres comodín al diseñar un cmdlet que se ejecutará en un grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="e1121-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="e1121-114">[Validar la entrada de parámetros](./validating-parameter-input.md) Describe cómo Windows PowerShell valida los argumentos pasados a los parámetros de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e1121-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="e1121-115">[Parámetros de filtro de entrada](./input-filter-parameters.md) Describe los parámetros `Filter`, `Include`y `Exclude` que filtran el conjunto de objetos de entrada al que afecta el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e1121-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="e1121-116">Secciones relacionadas</span><span class="sxs-lookup"><span data-stu-id="e1121-116">Related Sections</span></span>

[<span data-ttu-id="e1121-117">Cómo validar la entrada de parámetros</span><span class="sxs-lookup"><span data-stu-id="e1121-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="e1121-118">Véase también</span><span class="sxs-lookup"><span data-stu-id="e1121-118">See Also</span></span>

[<span data-ttu-id="e1121-119">Declaración de atributo de parámetro</span><span class="sxs-lookup"><span data-stu-id="e1121-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="e1121-120">Cmdlets de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1121-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
