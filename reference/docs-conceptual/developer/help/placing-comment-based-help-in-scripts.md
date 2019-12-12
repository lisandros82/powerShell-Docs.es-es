---
title: Colocar ayuda basada en comentarios en scripts | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361184"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="6dc40-102">Colocación de la Ayuda basada en comentarios en los scripts</span><span class="sxs-lookup"><span data-stu-id="6dc40-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="6dc40-103">En este tema se explica dónde colocar la ayuda basada en comentarios de un script para que el cmdlet de `Get-Help` asocie el tema de ayuda basado en comentarios con scripts y no con las funciones que podrían estar en el script.</span><span class="sxs-lookup"><span data-stu-id="6dc40-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="6dc40-104">Dónde colocar la ayuda basada en comentarios de un script</span><span class="sxs-lookup"><span data-stu-id="6dc40-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="6dc40-105">Al principio del archivo de script.</span><span class="sxs-lookup"><span data-stu-id="6dc40-105">At the beginning of the script file.</span></span> <span data-ttu-id="6dc40-106">La ayuda de script solo puede ir precedida del script en los comentarios y las líneas en blanco.</span><span class="sxs-lookup"><span data-stu-id="6dc40-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="6dc40-107">Al final del archivo de script.</span><span class="sxs-lookup"><span data-stu-id="6dc40-107">At the end of the script file.</span></span>

  <span data-ttu-id="6dc40-108">Si el primer elemento del cuerpo del script (después de la ayuda) es una declaración de función, debe haber al menos dos líneas en blanco entre el final de la ayuda del script y la declaración de la función.</span><span class="sxs-lookup"><span data-stu-id="6dc40-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="6dc40-109">De lo contrario, la ayuda se interpreta como ayuda para la función, no ayuda para el script.</span><span class="sxs-lookup"><span data-stu-id="6dc40-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="6dc40-110">Ejemplos de ubicación de la ayuda en un script</span><span class="sxs-lookup"><span data-stu-id="6dc40-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="6dc40-111">En los siguientes ejemplos se muestra cada una de las opciones de selección de ubicación para la ayuda basada en comentarios de un script.</span><span class="sxs-lookup"><span data-stu-id="6dc40-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="6dc40-112">Ayuda al principio de un script</span><span class="sxs-lookup"><span data-stu-id="6dc40-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="6dc40-113">En el ejemplo siguiente se muestra basada en comentarios al principio de un script.</span><span class="sxs-lookup"><span data-stu-id="6dc40-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="6dc40-114">Ayuda al final de un script</span><span class="sxs-lookup"><span data-stu-id="6dc40-114">Help at the End of a Script</span></span>

 <span data-ttu-id="6dc40-115">En el ejemplo siguiente se muestra basada en comentarios al final de un script.</span><span class="sxs-lookup"><span data-stu-id="6dc40-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```