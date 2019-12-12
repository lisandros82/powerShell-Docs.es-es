---
title: Sintaxis de la ayuda basada en comentarios | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367764"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="00d98-102">Sintaxis de la Ayuda basada en comentarios</span><span class="sxs-lookup"><span data-stu-id="00d98-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="00d98-103">En esta sección se describe la sintaxis de la ayuda basada en Comentarios.</span><span class="sxs-lookup"><span data-stu-id="00d98-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="00d98-104">Diagrama de sintaxis</span><span class="sxs-lookup"><span data-stu-id="00d98-104">Syntax Diagram</span></span>

 <span data-ttu-id="00d98-105">La sintaxis de la ayuda basada en comentarios es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="00d98-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="00d98-106">Descripción de la sintaxis</span><span class="sxs-lookup"><span data-stu-id="00d98-106">Syntax Description</span></span>

 <span data-ttu-id="00d98-107">La ayuda basada en comentarios se escribe como una serie de comentarios.</span><span class="sxs-lookup"><span data-stu-id="00d98-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="00d98-108">Puede escribir un símbolo de comentario (#) antes de cada línea de comentarios, o puede usar los símbolos "\<#" y "# >" para crear un bloque de comentario.</span><span class="sxs-lookup"><span data-stu-id="00d98-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="00d98-109">Todas las líneas del bloque de comentario se interpretan como comentarios.</span><span class="sxs-lookup"><span data-stu-id="00d98-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="00d98-110">Cada sección de la ayuda basada en comentarios se define mediante una palabra clave y cada palabra clave va precedida de un punto (.).</span><span class="sxs-lookup"><span data-stu-id="00d98-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="00d98-111">Las palabras clave pueden aparecer en cualquier orden.</span><span class="sxs-lookup"><span data-stu-id="00d98-111">The keywords can appear in any order.</span></span> <span data-ttu-id="00d98-112">Los nombres de palabra clave no distinguen mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="00d98-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="00d98-113">Un bloque de comentario debe contener al menos una palabra clave de ayuda.</span><span class="sxs-lookup"><span data-stu-id="00d98-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="00d98-114">Algunas de las palabras clave, como ejemplo, pueden aparecer muchas veces en el mismo bloque de comentario.</span><span class="sxs-lookup"><span data-stu-id="00d98-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="00d98-115">El contenido de la ayuda de cada palabra clave comienza en la línea después de la palabra clave y puede abarcar varias líneas.</span><span class="sxs-lookup"><span data-stu-id="00d98-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="00d98-116">Todas las líneas de un tema de ayuda basado en comentarios deben ser contiguas.</span><span class="sxs-lookup"><span data-stu-id="00d98-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="00d98-117">Si un tema de ayuda basado en comentarios sigue a un comentario que no forma parte del tema de ayuda, debe haber al menos una línea en blanco entre la última línea de comentario que no sea de ayuda y el principio de la ayuda basada en Comentarios.</span><span class="sxs-lookup"><span data-stu-id="00d98-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="00d98-118">Por ejemplo, el siguiente tema de ayuda basado en comentarios contiene el. Palabra clave Description y su valor, que es una descripción de una función o un script.</span><span class="sxs-lookup"><span data-stu-id="00d98-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```