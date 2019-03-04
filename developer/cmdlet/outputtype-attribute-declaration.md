---
title: Declaración de atributo OutputType | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853721"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="62373-102">Declaración de atributo OutputType</span><span class="sxs-lookup"><span data-stu-id="62373-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="62373-103">El `OutputType` atributo identifica los tipos de .NET Framework devueltos por un cmdlet, función o script.</span><span class="sxs-lookup"><span data-stu-id="62373-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="62373-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="62373-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="62373-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="62373-105">Parameters</span></span>

<span data-ttu-id="62373-106">Tipo (`string[]` o `Type[]`) necesarios.</span><span class="sxs-lookup"><span data-stu-id="62373-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="62373-107">Especifica los tipos devueltos por la función del cmdlet o script.</span><span class="sxs-lookup"><span data-stu-id="62373-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="62373-108">ParameterSetName (string[]) Optional.</span><span class="sxs-lookup"><span data-stu-id="62373-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="62373-109">Especifica los conjuntos de parámetros que devuelven los tipos especificados en el `type` parámetro.</span><span class="sxs-lookup"><span data-stu-id="62373-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="62373-110">providerCmdlet opcional.</span><span class="sxs-lookup"><span data-stu-id="62373-110">providerCmdlet Optional.</span></span> <span data-ttu-id="62373-111">Especifica el cmdlet de proveedor que devuelve los tipos especificados en el `type` parámetro.</span><span class="sxs-lookup"><span data-stu-id="62373-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="62373-112">Véase también</span><span class="sxs-lookup"><span data-stu-id="62373-112">See Also</span></span>

[<span data-ttu-id="62373-113">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="62373-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
