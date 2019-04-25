---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4b593e9a1eca43ee7ad85fc921ae3c1d62722db9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085871"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="3fcdd-102">Declarar la interfaz implementada</span><span class="sxs-lookup"><span data-stu-id="3fcdd-102">Declare Implemented Interface</span></span>

<span data-ttu-id="3fcdd-103">Puede declarar interfaces implementadas después de los tipos base o inmediatamente después de dos puntos (:) si no existe ningún tipo base especificado.</span><span class="sxs-lookup"><span data-stu-id="3fcdd-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="3fcdd-104">Separe todos los nombres de tipo con comas.</span><span class="sxs-lookup"><span data-stu-id="3fcdd-104">Separate all type names by using commas.</span></span> <span data-ttu-id="3fcdd-105">Es muy similar a la sintaxis de C#.</span><span class="sxs-lookup"><span data-stu-id="3fcdd-105">It’s very similar to C# syntax.</span></span>

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
