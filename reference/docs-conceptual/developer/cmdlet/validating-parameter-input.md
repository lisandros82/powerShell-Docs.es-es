---
title: Validando entrada de parámetro | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363514"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="515cd-102">Validación de la entrada de parámetros</span><span class="sxs-lookup"><span data-stu-id="515cd-102">Validating Parameter Input</span></span>

<span data-ttu-id="515cd-103">PowerShell puede validar los argumentos que se pasan a los parámetros de cmdlet de varias maneras.</span><span class="sxs-lookup"><span data-stu-id="515cd-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="515cd-104">PowerShell puede validar la longitud, el intervalo y el patrón de los caracteres del argumento.</span><span class="sxs-lookup"><span data-stu-id="515cd-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="515cd-105">Puede validar el número de argumentos disponibles (el recuento).</span><span class="sxs-lookup"><span data-stu-id="515cd-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="515cd-106">Estas reglas de validación se definen mediante atributos de validación que se declaran con el atributo Parameter en las propiedades públicas de la clase cmdlet.</span><span class="sxs-lookup"><span data-stu-id="515cd-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="515cd-107">Para validar un argumento de parámetro, el tiempo de ejecución de PowerShell usa la información proporcionada por los atributos de validación para confirmar el valor del parámetro antes de que se ejecute el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="515cd-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="515cd-108">Si la entrada del parámetro no es válida, el usuario recibe un mensaje de error.</span><span class="sxs-lookup"><span data-stu-id="515cd-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="515cd-109">Cada parámetro de validación define una regla de validación que se aplica mediante PowerShell.</span><span class="sxs-lookup"><span data-stu-id="515cd-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="515cd-110">PowerShell aplica las reglas de validación en función de los siguientes atributos.</span><span class="sxs-lookup"><span data-stu-id="515cd-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="515cd-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="515cd-111">ValidateCount</span></span>

<span data-ttu-id="515cd-112">Especifica el número mínimo y máximo de argumentos que puede aceptar un parámetro.</span><span class="sxs-lookup"><span data-stu-id="515cd-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="515cd-113">Para obtener más información, vea [declaración de atributos de ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="515cd-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="515cd-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="515cd-114">ValidateLength</span></span>

<span data-ttu-id="515cd-115">Especifica el número mínimo y máximo de caracteres en el argumento de parámetro.</span><span class="sxs-lookup"><span data-stu-id="515cd-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="515cd-116">Para obtener más información, vea [declaración de atributos de ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="515cd-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="515cd-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="515cd-117">ValidatePattern</span></span>

<span data-ttu-id="515cd-118">Especifica una expresión regular que valida el argumento del parámetro.</span><span class="sxs-lookup"><span data-stu-id="515cd-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="515cd-119">Para obtener más información, vea [declaración de atributos de ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="515cd-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="515cd-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="515cd-120">ValidateRange</span></span>

<span data-ttu-id="515cd-121">Especifica los valores mínimo y máximo del argumento de parámetro.</span><span class="sxs-lookup"><span data-stu-id="515cd-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="515cd-122">Para obtener más información, vea [declaración de atributos de ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="515cd-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="515cd-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="515cd-123">ValidateSet</span></span>

<span data-ttu-id="515cd-124">Especifica los valores válidos para el argumento del parámetro.</span><span class="sxs-lookup"><span data-stu-id="515cd-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="515cd-125">Para obtener más información, vea [declaración de atributos de ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="515cd-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="515cd-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="515cd-126">See Also</span></span>

[<span data-ttu-id="515cd-127">Cómo validar la entrada de parámetros</span><span class="sxs-lookup"><span data-stu-id="515cd-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="515cd-128">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="515cd-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
