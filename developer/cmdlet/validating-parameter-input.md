---
title: Validar la entrada del parámetro | Microsoft Docs
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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858851"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="3e0c6-102">Validación de la entrada de parámetros</span><span class="sxs-lookup"><span data-stu-id="3e0c6-102">Validating Parameter Input</span></span>

<span data-ttu-id="3e0c6-103">Windows PowerShell puede validar los argumentos pasados a los parámetros de cmdlet de varias maneras.</span><span class="sxs-lookup"><span data-stu-id="3e0c6-103">Windows PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span> <span data-ttu-id="3e0c6-104">Windows PowerShell puede validar la longitud, el intervalo y el patrón de los caracteres del argumento.</span><span class="sxs-lookup"><span data-stu-id="3e0c6-104">Windows PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span> <span data-ttu-id="3e0c6-105">Puede validar el número de argumentos disponibles (el recuento).</span><span class="sxs-lookup"><span data-stu-id="3e0c6-105">It can validate the number of arguments available (the count).</span></span> <span data-ttu-id="3e0c6-106">Estas reglas de validación se definen mediante atributos de validación que se declaran con el atributo de parámetro en las propiedades públicas de la clase del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3e0c6-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="3e0c6-107">Para validar un argumento de parámetro, el tiempo de ejecución de Windows PowerShell usa la información proporcionada por los atributos de validación para confirmar el valor del parámetro antes de ejecuta el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3e0c6-107">To validate a parameter argument, the Windows PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span> <span data-ttu-id="3e0c6-108">Si la entrada de parámetro no es válida, el usuario recibe un mensaje de error.</span><span class="sxs-lookup"><span data-stu-id="3e0c6-108">If the parameter input is not valid, the user receives an error message.</span></span> <span data-ttu-id="3e0c6-109">Cada parámetro de validación define una regla de validación que se aplica mediante Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e0c6-109">Each validation parameter defines a validation rule that is enforced by Windows PowerShell.</span></span>

<span data-ttu-id="3e0c6-110">Windows PowerShell aplica las reglas de validación en función de los siguientes atributos.</span><span class="sxs-lookup"><span data-stu-id="3e0c6-110">Windows PowerShell enforces the validation rules based on the following attributes.</span></span>

<span data-ttu-id="3e0c6-111">ValidateCount especifica el número mínimo y máximo de argumentos que puede aceptar un parámetro.</span><span class="sxs-lookup"><span data-stu-id="3e0c6-111">ValidateCount Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span> <span data-ttu-id="3e0c6-112">Para obtener más información sobre la sintaxis que se utiliza para declarar este atributo, vea [ValidateCount la declaración de atributo](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="3e0c6-112">For more information about the syntax used to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

<span data-ttu-id="3e0c6-113">ValidateLength especifica el número mínimo y máximo de caracteres en el argumento del parámetro.</span><span class="sxs-lookup"><span data-stu-id="3e0c6-113">ValidateLength Specifies the minimum and maximum number of characters in the parameter argument.</span></span> <span data-ttu-id="3e0c6-114">Para obtener más información sobre la sintaxis que se utiliza para declarar este atributo, vea [declaración de atributo ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="3e0c6-114">For more information about the syntax used to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

<span data-ttu-id="3e0c6-115">ValidatePattern especifica una expresión regular que valide el argumento del parámetro.</span><span class="sxs-lookup"><span data-stu-id="3e0c6-115">ValidatePattern Specifies a regular expression that validates the parameter argument.</span></span> <span data-ttu-id="3e0c6-116">Para obtener más información sobre la sintaxis que se utiliza para declarar este atributo, vea [ValidatePattern la declaración de atributo](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="3e0c6-116">For more information about the syntax used to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

<span data-ttu-id="3e0c6-117">ValidateRange especifica los valores mínimos y máximo del argumento del parámetro.</span><span class="sxs-lookup"><span data-stu-id="3e0c6-117">ValidateRange Specifies the minimum and maximum values of the parameter argument.</span></span> <span data-ttu-id="3e0c6-118">Para obtener más información sobre la sintaxis que se utiliza para declarar este atributo, vea [ValidateRange la declaración de atributo](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="3e0c6-118">For more information about the syntax used to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

<span data-ttu-id="3e0c6-119">ValidateSet especifica los valores válidos para el argumento del parámetro.</span><span class="sxs-lookup"><span data-stu-id="3e0c6-119">ValidateSet Specifies the valid values for the parameter argument.</span></span> <span data-ttu-id="3e0c6-120">Para obtener más información sobre la sintaxis que se utiliza para declarar este atributo, vea [ValidateSet la declaración de atributo](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="3e0c6-120">For more information about the syntax used to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3e0c6-121">Véase también</span><span class="sxs-lookup"><span data-stu-id="3e0c6-121">See Also</span></span>

[<span data-ttu-id="3e0c6-122">Cómo validar entrada de parámetros</span><span class="sxs-lookup"><span data-stu-id="3e0c6-122">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="3e0c6-123">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e0c6-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
