---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 116f79a95126d0a1c579a95ec99eb5d8b75cc1e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="c3073-102">Declarar la interfaz implementada</span><span class="sxs-lookup"><span data-stu-id="c3073-102">Declare Implemented Interface</span></span>

<span data-ttu-id="c3073-103">Puede declarar interfaces implementadas después de los tipos base o inmediatamente después de dos puntos (:) si no existe ningún tipo base especificado.</span><span class="sxs-lookup"><span data-stu-id="c3073-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="c3073-104">Separe todos los nombres de tipo con comas.</span><span class="sxs-lookup"><span data-stu-id="c3073-104">Separate all type names by using commas.</span></span> <span data-ttu-id="c3073-105">Es muy similar a la sintaxis de C#.</span><span class="sxs-lookup"><span data-stu-id="c3073-105">It’s very similar to C# syntax.</span></span>

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
