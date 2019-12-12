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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369234"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="c18df-102">Declaración de atributo ValidateCount</span><span class="sxs-lookup"><span data-stu-id="c18df-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="c18df-103">El atributo ValidateCount especifica el número mínimo y máximo de argumentos permitidos para un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c18df-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="c18df-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c18df-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="c18df-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c18df-105">Parameters</span></span>

<span data-ttu-id="c18df-106">se requiere `MinLength` ([System.Int32][]).</span><span class="sxs-lookup"><span data-stu-id="c18df-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="c18df-107">Especifica el número mínimo de argumentos.</span><span class="sxs-lookup"><span data-stu-id="c18df-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="c18df-108">se requiere `MaxLength`([System.Int32][]).</span><span class="sxs-lookup"><span data-stu-id="c18df-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="c18df-109">Especifica el número máximo de argumentos.</span><span class="sxs-lookup"><span data-stu-id="c18df-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="c18df-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="c18df-110">Remarks</span></span>

- <span data-ttu-id="c18df-111">Para obtener más información sobre cómo declarar este atributo, vea [cómo validar un número de argumentos][].</span><span class="sxs-lookup"><span data-stu-id="c18df-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="c18df-112">Cuando no se invoca este atributo, el parámetro de cmdlet correspondiente puede tener cualquier número de argumentos.</span><span class="sxs-lookup"><span data-stu-id="c18df-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="c18df-113">El tiempo de ejecución de Windows PowerShell genera un error en las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="c18df-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="c18df-114">Los parámetros del atributo `MinLength` y `MaxLength` no son del tipo [System.Int32][].</span><span class="sxs-lookup"><span data-stu-id="c18df-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="c18df-115">El valor del parámetro del atributo `MaxLength` es menor que el valor del parámetro del atributo `MinLength`.</span><span class="sxs-lookup"><span data-stu-id="c18df-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="c18df-116">La clase [System. Management. Automation. ValidateCountAttribute][] define el atributo ValidateCount.</span><span class="sxs-lookup"><span data-stu-id="c18df-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="c18df-117">Véase también</span><span class="sxs-lookup"><span data-stu-id="c18df-117">See Also</span></span>

<span data-ttu-id="c18df-118">[System. Management. Automation. ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="c18df-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="c18df-119">[Cómo validar un número de argumentos][]</span><span class="sxs-lookup"><span data-stu-id="c18df-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="c18df-120">[Escribir un cmdlet de Windows PowerShell][]</span><span class="sxs-lookup"><span data-stu-id="c18df-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Cómo validar un número de argumentos]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Escribir un cmdlet de Windows PowerShell]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
