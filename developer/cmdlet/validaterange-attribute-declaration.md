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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067117"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="2cd23-102">Declaración de atributo ValidateRange</span><span class="sxs-lookup"><span data-stu-id="2cd23-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="2cd23-103">El atributo ValidateRange especifica los valores mínimos y máximo (el rango) para el argumento del parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2cd23-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="2cd23-104">Este atributo también se puede usar las funciones de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2cd23-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="2cd23-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2cd23-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="2cd23-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="2cd23-106">Parameters</span></span>

<span data-ttu-id="2cd23-107">`MinRange` ([System.Object](/dotnet/api/system.object)) necesarios.</span><span class="sxs-lookup"><span data-stu-id="2cd23-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="2cd23-108">Especifica el valor mínimo permitido.</span><span class="sxs-lookup"><span data-stu-id="2cd23-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="2cd23-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) necesarios.</span><span class="sxs-lookup"><span data-stu-id="2cd23-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="2cd23-110">Especifica el valor máximo permitido.</span><span class="sxs-lookup"><span data-stu-id="2cd23-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="2cd23-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2cd23-111">Remarks</span></span>

- <span data-ttu-id="2cd23-112">El tiempo de ejecución de Windows PowerShell genera un error de construcción cuando el valor de la `MinRange` parámetro es mayor que el valor de la `MaxRange` parámetro.</span><span class="sxs-lookup"><span data-stu-id="2cd23-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="2cd23-113">El tiempo de ejecución de Windows PowerShell, produce un error de validación en las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="2cd23-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="2cd23-114">Cuando el valor del argumento es menor que el `MinRange` límite o mayor que el `MaxRange` límite.</span><span class="sxs-lookup"><span data-stu-id="2cd23-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="2cd23-115">Cuando el argumento no es del mismo tipo como el `MinRange` y `MaxRange` parámetros.</span><span class="sxs-lookup"><span data-stu-id="2cd23-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="2cd23-116">El atributo ValidateRange está definido por el [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) clase.</span><span class="sxs-lookup"><span data-stu-id="2cd23-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="2cd23-117">Véase también</span><span class="sxs-lookup"><span data-stu-id="2cd23-117">See Also</span></span>

[<span data-ttu-id="2cd23-118">System.Management.Automation.Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="2cd23-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="2cd23-119">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2cd23-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
