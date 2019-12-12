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
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369184"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="10685-102">Declaración de atributo ValidateLength</span><span class="sxs-lookup"><span data-stu-id="10685-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="10685-103">El atributo ValidateLength especifica el número mínimo y máximo de caracteres para un argumento de parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="10685-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="10685-104">Este atributo también se puede usar en las funciones de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="10685-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="10685-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="10685-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="10685-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="10685-106">Parameters</span></span>

<span data-ttu-id="10685-107">se requiere `MinLength` ([System. Int32](/dotnet/api/System.Int32)).</span><span class="sxs-lookup"><span data-stu-id="10685-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="10685-108">Especifica el número mínimo de caracteres permitidos.</span><span class="sxs-lookup"><span data-stu-id="10685-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="10685-109">se requiere `MaxLength` ([System. Int32](/dotnet/api/System.Int32)).</span><span class="sxs-lookup"><span data-stu-id="10685-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="10685-110">Especifica el número máximo de caracteres permitidos.</span><span class="sxs-lookup"><span data-stu-id="10685-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="10685-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="10685-111">Remarks</span></span>

- <span data-ttu-id="10685-112">Para obtener más información sobre cómo declarar este atributo, vea [cómo declarar reglas de validación de entrada](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="10685-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="10685-113">Cuando no se utiliza este atributo, el argumento de parámetro correspondiente puede tener cualquier longitud.</span><span class="sxs-lookup"><span data-stu-id="10685-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="10685-114">El tiempo de ejecución de Windows PowerShell genera un error en las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="10685-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="10685-115">Cuando el valor del parámetro del atributo `MaxLength` es menor que el valor del parámetro del atributo `MinLength`.</span><span class="sxs-lookup"><span data-stu-id="10685-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="10685-116">Cuando el parámetro del atributo `MaxLength` está establecido en 0.</span><span class="sxs-lookup"><span data-stu-id="10685-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="10685-117">Cuando el argumento no es una cadena.</span><span class="sxs-lookup"><span data-stu-id="10685-117">When the argument is not a string.</span></span>

- <span data-ttu-id="10685-118">La clase [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) define el atributo ValidateLength.</span><span class="sxs-lookup"><span data-stu-id="10685-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="10685-119">Véase también</span><span class="sxs-lookup"><span data-stu-id="10685-119">See Also</span></span>

[<span data-ttu-id="10685-120">System. Management. Automation. Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="10685-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="10685-121">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="10685-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
