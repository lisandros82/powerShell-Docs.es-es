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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067086"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="bf991-102">Declaración de atributo ValidateSet</span><span class="sxs-lookup"><span data-stu-id="bf991-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="bf991-103">El atributo ValidateSetAttribute especifica un conjunto de valores posibles para un argumento de parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bf991-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="bf991-104">Este atributo también se puede usar las funciones de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bf991-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="bf991-105">Cuando se especifica este atributo, el tiempo de ejecución de Windows PowerShell determina si el argumento proporcionado para el parámetro de cmdlet coincide con un elemento en el conjunto de elemento proporcionada.</span><span class="sxs-lookup"><span data-stu-id="bf991-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="bf991-106">El cmdlet se ejecuta solo si el argumento del parámetro coincide con un elemento del conjunto.</span><span class="sxs-lookup"><span data-stu-id="bf991-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="bf991-107">Si no se encuentra ninguna coincidencia, se produce un error por el tiempo de ejecución de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bf991-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf991-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="bf991-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="bf991-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bf991-109">Parameters</span></span>

<span data-ttu-id="bf991-110">`ValidValues` ([System.String](/dotnet/api/System.String)) necesarios.</span><span class="sxs-lookup"><span data-stu-id="bf991-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="bf991-111">Especifica los valores de elemento de parámetro válido.</span><span class="sxs-lookup"><span data-stu-id="bf991-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="bf991-112">El ejemplo siguiente muestra cómo especificar un elemento o varios elementos.</span><span class="sxs-lookup"><span data-stu-id="bf991-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="bf991-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) con el nombre de parámetro opcional.</span><span class="sxs-lookup"><span data-stu-id="bf991-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="bf991-114">El valor predeterminado de `true` indica que las mayúsculas y minúsculas se ignoran.</span><span class="sxs-lookup"><span data-stu-id="bf991-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="bf991-115">Un valor de `false` hace que el cmdlet que distingue mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="bf991-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf991-116">Observaciones</span><span class="sxs-lookup"><span data-stu-id="bf991-116">Remarks</span></span>

- <span data-ttu-id="bf991-117">Este atributo se puede usar una sola vez por cada parámetro.</span><span class="sxs-lookup"><span data-stu-id="bf991-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="bf991-118">Si el valor del parámetro es una matriz, cada elemento de la matriz debe coincidir con un elemento del conjunto de atributos.</span><span class="sxs-lookup"><span data-stu-id="bf991-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="bf991-119">El atributo ValidateSetAttribute está definido por el [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) clase.</span><span class="sxs-lookup"><span data-stu-id="bf991-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf991-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="bf991-120">See Also</span></span>

[<span data-ttu-id="bf991-121">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="bf991-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="bf991-122">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bf991-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
