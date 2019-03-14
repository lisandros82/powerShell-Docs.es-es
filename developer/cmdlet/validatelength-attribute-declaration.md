---
title: Declaración de atributo ValidateLength | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 3a4c5f279ce8587eeb5d583376ea3d2286210b83
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794338"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="b3960-102">Declaración de atributo ValidateLength</span><span class="sxs-lookup"><span data-stu-id="b3960-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="b3960-103">El atributo ValidateLength especifica el número mínimo y máximo de caracteres para un argumento de parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3960-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="b3960-104">Este atributo también se puede usar las funciones de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3960-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="b3960-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b3960-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="b3960-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b3960-106">Parameters</span></span>

<span data-ttu-id="b3960-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) necesarios.</span><span class="sxs-lookup"><span data-stu-id="b3960-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="b3960-108">Especifica el número mínimo de caracteres permitidos.</span><span class="sxs-lookup"><span data-stu-id="b3960-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="b3960-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) necesarios.</span><span class="sxs-lookup"><span data-stu-id="b3960-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="b3960-110">Especifica el número máximo de caracteres permitidos.</span><span class="sxs-lookup"><span data-stu-id="b3960-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3960-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b3960-111">Remarks</span></span>

- <span data-ttu-id="b3960-112">Para obtener más información acerca de cómo declarar este atributo, vea [cómo declarar las reglas de validación de entrada](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="b3960-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="b3960-113">Cuando no se usa este atributo, el argumento correspondiente del parámetro puede tener cualquier longitud.</span><span class="sxs-lookup"><span data-stu-id="b3960-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="b3960-114">El tiempo de ejecución de Windows PowerShell, produce un error en las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="b3960-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="b3960-115">Cuando el valor de la `MaxLength` parámetro de atributo es menor que el valor de la `MinLength` parámetro de atributo.</span><span class="sxs-lookup"><span data-stu-id="b3960-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="b3960-116">Cuando el `MaxLength` parámetro de atributo se establece en 0.</span><span class="sxs-lookup"><span data-stu-id="b3960-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="b3960-117">Cuando el argumento no es una cadena.</span><span class="sxs-lookup"><span data-stu-id="b3960-117">When the argument is not a string.</span></span>

- <span data-ttu-id="b3960-118">El atributo ValidateLength está definido por el [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) clase.</span><span class="sxs-lookup"><span data-stu-id="b3960-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3960-119">Véase también</span><span class="sxs-lookup"><span data-stu-id="b3960-119">See Also</span></span>

[<span data-ttu-id="b3960-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="b3960-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="b3960-121">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3960-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
