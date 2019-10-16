---
title: Colocar la ayuda basada en comentarios en las funciones | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367784"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="70ac5-102">Colocación de la Ayuda basada en comentarios en las funciones</span><span class="sxs-lookup"><span data-stu-id="70ac5-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="70ac5-103">En este tema se explica dónde colocar la ayuda basada en comentarios de una función para que el cmdlet `Get-Help` asocie el tema de ayuda basado en comentarios con la función correcta.</span><span class="sxs-lookup"><span data-stu-id="70ac5-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="70ac5-104">Dónde colocar la ayuda basada en comentarios para una función</span><span class="sxs-lookup"><span data-stu-id="70ac5-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="70ac5-105">Al principio del cuerpo de la función.</span><span class="sxs-lookup"><span data-stu-id="70ac5-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="70ac5-106">Al final del cuerpo de la función.</span><span class="sxs-lookup"><span data-stu-id="70ac5-106">At the end of the function body.</span></span>

- <span data-ttu-id="70ac5-107">Antes de la palabra clave `Function`.</span><span class="sxs-lookup"><span data-stu-id="70ac5-107">Before the `Function` keyword.</span></span> <span data-ttu-id="70ac5-108">Cuando la función está en un módulo de script o script, no puede haber más de una línea en blanco entre la última línea de la ayuda basada en comentarios y la palabra clave `Function`.</span><span class="sxs-lookup"><span data-stu-id="70ac5-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="70ac5-109">De lo contrario, `Get-Help` asocia la ayuda al script, no a la función.</span><span class="sxs-lookup"><span data-stu-id="70ac5-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="70ac5-110">Ejemplos de colocación de la ayuda en una función</span><span class="sxs-lookup"><span data-stu-id="70ac5-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="70ac5-111">En los siguientes ejemplos se muestra cada una de las tres opciones de selección de ubicación para la ayuda basada en comentarios de una función.</span><span class="sxs-lookup"><span data-stu-id="70ac5-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="70ac5-112">Ayuda al principio del cuerpo de una función</span><span class="sxs-lookup"><span data-stu-id="70ac5-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="70ac5-113">En el ejemplo siguiente se muestra basada en comentarios al principio del cuerpo de una función.</span><span class="sxs-lookup"><span data-stu-id="70ac5-113">The following example shows comment-based at the beginning of a function body.</span></span>

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="70ac5-114">Ayuda al final del cuerpo de una función</span><span class="sxs-lookup"><span data-stu-id="70ac5-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="70ac5-115">En el ejemplo siguiente se muestra basada en comentarios al final de un cuerpo de función.</span><span class="sxs-lookup"><span data-stu-id="70ac5-115">The following example shows comment-based at the end of a function body.</span></span>

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="70ac5-116">Ayuda antes de la palabra clave function</span><span class="sxs-lookup"><span data-stu-id="70ac5-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="70ac5-117">En los siguientes ejemplos se muestra el comentario basado en la línea antes de la palabra clave function.</span><span class="sxs-lookup"><span data-stu-id="70ac5-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```