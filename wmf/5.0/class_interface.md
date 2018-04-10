---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 2c007321789ae22b4a2e048d2d64162b065f9a75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="c2948-102">Declarar la interfaz implementada</span><span class="sxs-lookup"><span data-stu-id="c2948-102">Declare Implemented Interface</span></span>

<span data-ttu-id="c2948-103">Puede declarar interfaces implementadas después de los tipos base o inmediatamente después de dos puntos (:) si no existe ningún tipo base especificado.</span><span class="sxs-lookup"><span data-stu-id="c2948-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="c2948-104">Separe todos los nombres de tipo con comas.</span><span class="sxs-lookup"><span data-stu-id="c2948-104">Separate all type names by using commas.</span></span> <span data-ttu-id="c2948-105">Es muy similar a la sintaxis de C#.</span><span class="sxs-lookup"><span data-stu-id="c2948-105">It’s very similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```