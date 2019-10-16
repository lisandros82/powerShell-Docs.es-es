---
title: Declaración de atributo ValidateRange | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369134"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="e9c32-102">Declaración de atributo ValidateRange</span><span class="sxs-lookup"><span data-stu-id="e9c32-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="e9c32-103">El atributo ValidateRange especifica los valores mínimo y máximo (el intervalo) para el argumento del parámetro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e9c32-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="e9c32-104">Este atributo también se puede usar en las funciones de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9c32-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="e9c32-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e9c32-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="e9c32-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e9c32-106">Parameters</span></span>

<span data-ttu-id="e9c32-107">se requiere `MinRange` ([System. Object](/dotnet/api/system.object)).</span><span class="sxs-lookup"><span data-stu-id="e9c32-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="e9c32-108">Especifica el valor mínimo permitido.</span><span class="sxs-lookup"><span data-stu-id="e9c32-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="e9c32-109">se requiere `MaxRange` ([System. Object](/dotnet/api/system.object)).</span><span class="sxs-lookup"><span data-stu-id="e9c32-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="e9c32-110">Especifica el valor máximo permitido.</span><span class="sxs-lookup"><span data-stu-id="e9c32-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9c32-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e9c32-111">Remarks</span></span>

- <span data-ttu-id="e9c32-112">El tiempo de ejecución de Windows PowerShell genera un error de construcción cuando el valor del parámetro `MinRange` es mayor que el valor del parámetro `MaxRange`.</span><span class="sxs-lookup"><span data-stu-id="e9c32-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="e9c32-113">El tiempo de ejecución de Windows PowerShell genera un error de validación en las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="e9c32-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="e9c32-114">Cuando el valor del argumento es menor que el límite de `MinRange` o mayor que el límite de `MaxRange`.</span><span class="sxs-lookup"><span data-stu-id="e9c32-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="e9c32-115">Cuando el argumento no es del mismo tipo que los parámetros `MinRange` y `MaxRange`.</span><span class="sxs-lookup"><span data-stu-id="e9c32-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="e9c32-116">La clase [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) define el atributo ValidateRange.</span><span class="sxs-lookup"><span data-stu-id="e9c32-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9c32-117">Véase también</span><span class="sxs-lookup"><span data-stu-id="e9c32-117">See Also</span></span>

[<span data-ttu-id="e9c32-118">System. Management. Automation. Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="e9c32-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="e9c32-119">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9c32-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
