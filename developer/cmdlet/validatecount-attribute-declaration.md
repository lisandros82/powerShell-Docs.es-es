---
title: Declaración de atributo ValidateCount | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 4e0be34b6f7a56dcf02a4381de4d2a5d08db14df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794455"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="375a7-102">Declaración de atributo ValidateCount</span><span class="sxs-lookup"><span data-stu-id="375a7-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="375a7-103">El atributo ValidateCount especifica el número mínimo y máximo de argumentos que se permite para un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="375a7-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="375a7-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="375a7-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="375a7-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="375a7-105">Parameters</span></span>

<span data-ttu-id="375a7-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) necesarios.</span><span class="sxs-lookup"><span data-stu-id="375a7-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="375a7-107">Especifica el número mínimo de argumentos.</span><span class="sxs-lookup"><span data-stu-id="375a7-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="375a7-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) necesarios.</span><span class="sxs-lookup"><span data-stu-id="375a7-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="375a7-109">Especifica el número máximo de argumentos.</span><span class="sxs-lookup"><span data-stu-id="375a7-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="375a7-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="375a7-110">Remarks</span></span>

- <span data-ttu-id="375a7-111">Para obtener más información acerca de cómo declarar este atributo, vea [cómo declarar las reglas de validación de entrada](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="375a7-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="375a7-112">Cuando este atributo no se invoca, el parámetro de cmdlet correspondiente puede tener cualquier número de argumentos.</span><span class="sxs-lookup"><span data-stu-id="375a7-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="375a7-113">El tiempo de ejecución de Windows PowerShell, produce un error en las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="375a7-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="375a7-114">El `MinLength` y `MaxLength` parámetros de atributo no son de tipo [System.Int32](/dotnet/api/System.Int32).</span><span class="sxs-lookup"><span data-stu-id="375a7-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="375a7-115">El valor de la `MaxLength` parámetro de atributo es menor que el valor de la `MinLength` parámetro de atributo.</span><span class="sxs-lookup"><span data-stu-id="375a7-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="375a7-116">El atributo ValidateCount está definido por el [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) clase.</span><span class="sxs-lookup"><span data-stu-id="375a7-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="375a7-117">Véase también</span><span class="sxs-lookup"><span data-stu-id="375a7-117">See Also</span></span>

[<span data-ttu-id="375a7-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="375a7-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="375a7-119">Cómo declarar las reglas de validación de entrada</span><span class="sxs-lookup"><span data-stu-id="375a7-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="375a7-120">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="375a7-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
