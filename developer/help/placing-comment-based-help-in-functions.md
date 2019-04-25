---
title: Colocación de Ayuda basada en comentarios en las funciones de | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083202"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="dc4f4-102">Colocación de la Ayuda basada en comentarios en las funciones</span><span class="sxs-lookup"><span data-stu-id="dc4f4-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="dc4f4-103">En este tema se explica dónde colocar Ayuda basada en comentarios de una función para que el `Get-Help` cmdlet asocia el tema de Ayuda basada en comentarios de la función correcta.</span><span class="sxs-lookup"><span data-stu-id="dc4f4-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="dc4f4-104">Dónde colocar Ayuda basada en comentarios de una función</span><span class="sxs-lookup"><span data-stu-id="dc4f4-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="dc4f4-105">Al principio del cuerpo de función.</span><span class="sxs-lookup"><span data-stu-id="dc4f4-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="dc4f4-106">Al final del cuerpo de función.</span><span class="sxs-lookup"><span data-stu-id="dc4f4-106">At the end of the function body.</span></span>

- <span data-ttu-id="dc4f4-107">Antes de la `Function` palabra clave.</span><span class="sxs-lookup"><span data-stu-id="dc4f4-107">Before the `Function` keyword.</span></span> <span data-ttu-id="dc4f4-108">Cuando la función está en un script o un módulo de script, no puede haber más de una línea en blanco entre la última línea de la Ayuda basada en comentarios y `Function` palabra clave.</span><span class="sxs-lookup"><span data-stu-id="dc4f4-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="dc4f4-109">En caso contrario, `Get-Help` asocia la ayuda con la secuencia de comandos, no con la función.</span><span class="sxs-lookup"><span data-stu-id="dc4f4-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="dc4f4-110">Ejemplos de una posición de la Ayuda en una función</span><span class="sxs-lookup"><span data-stu-id="dc4f4-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="dc4f4-111">Los ejemplos siguientes muestran cada una de las opciones de colocación de tres para Ayuda basada en comentarios de una función.</span><span class="sxs-lookup"><span data-stu-id="dc4f4-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="dc4f4-112">Ayuda al principio de un cuerpo de función</span><span class="sxs-lookup"><span data-stu-id="dc4f4-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="dc4f4-113">El ejemplo siguiente se muestra basada en comentarios al principio de un cuerpo de función.</span><span class="sxs-lookup"><span data-stu-id="dc4f4-113">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="dc4f4-114">Ayuda al final de un cuerpo de función</span><span class="sxs-lookup"><span data-stu-id="dc4f4-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="dc4f4-115">El ejemplo siguiente se muestra basada en comentarios al final del cuerpo de una función.</span><span class="sxs-lookup"><span data-stu-id="dc4f4-115">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="dc4f4-116">Ayudar a antes de la palabra clave Function</span><span class="sxs-lookup"><span data-stu-id="dc4f4-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="dc4f4-117">Los ejemplos siguientes se muestra basada en comentarios en la línea antes de la palabra clave function.</span><span class="sxs-lookup"><span data-stu-id="dc4f4-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```