---
title: Declaración de atributo ValidateSet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364284"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="558f3-102">Declaración de atributo ValidateSet</span><span class="sxs-lookup"><span data-stu-id="558f3-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="558f3-103">El atributo ValidateSetAttribute especifica un conjunto de valores posibles para un argumento de parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="558f3-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="558f3-104">Este atributo también se puede usar en las funciones de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="558f3-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="558f3-105">Cuando se especifica este atributo, el tiempo de ejecución de Windows PowerShell determina si el argumento proporcionado para el parámetro de cmdlet coincide con un elemento del conjunto de elementos proporcionado.</span><span class="sxs-lookup"><span data-stu-id="558f3-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="558f3-106">El cmdlet se ejecuta solo si el argumento de parámetro coincide con un elemento del conjunto.</span><span class="sxs-lookup"><span data-stu-id="558f3-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="558f3-107">Si no se encuentra ninguna coincidencia, el tiempo de ejecución de Windows PowerShell produce un error.</span><span class="sxs-lookup"><span data-stu-id="558f3-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="558f3-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="558f3-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="558f3-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="558f3-109">Parameters</span></span>

<span data-ttu-id="558f3-110">`ValidValues` ([System. String](/dotnet/api/System.String)) requerido.</span><span class="sxs-lookup"><span data-stu-id="558f3-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="558f3-111">Especifica los valores de elemento de parámetro válidos.</span><span class="sxs-lookup"><span data-stu-id="558f3-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="558f3-112">En el ejemplo siguiente se muestra cómo especificar un elemento o varios elementos.</span><span class="sxs-lookup"><span data-stu-id="558f3-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="558f3-113">parámetro con nombre opcional `IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)).</span><span class="sxs-lookup"><span data-stu-id="558f3-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="558f3-114">El valor predeterminado de `true` indica que se omite el caso.</span><span class="sxs-lookup"><span data-stu-id="558f3-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="558f3-115">Un valor de `false` hace que el cmdlet distinga mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="558f3-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="558f3-116">Observaciones</span><span class="sxs-lookup"><span data-stu-id="558f3-116">Remarks</span></span>

- <span data-ttu-id="558f3-117">Este atributo solo se puede usar una vez por parámetro.</span><span class="sxs-lookup"><span data-stu-id="558f3-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="558f3-118">Si el valor del parámetro es una matriz, cada elemento de la matriz debe coincidir con un elemento del conjunto de atributos.</span><span class="sxs-lookup"><span data-stu-id="558f3-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="558f3-119">La clase [System. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) define el atributo ValidateSetAttribute.</span><span class="sxs-lookup"><span data-stu-id="558f3-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="558f3-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="558f3-120">See Also</span></span>

[<span data-ttu-id="558f3-121">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="558f3-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="558f3-122">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="558f3-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
