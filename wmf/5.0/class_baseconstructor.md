---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225613"
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="2bd87-102">Llamar al constructor de clase base</span><span class="sxs-lookup"><span data-stu-id="2bd87-102">Call Base Class Constructor</span></span>

<span data-ttu-id="2bd87-103">Para llamar a un constructor de clase base desde una subclase, use la palabra clave **base**:</span><span class="sxs-lookup"><span data-stu-id="2bd87-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

<span data-ttu-id="2bd87-104">Si una clase base tiene un constructor predeterminado (sin parámetros), se puede omitir una llamada explícita al constructor:</span><span class="sxs-lookup"><span data-stu-id="2bd87-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```
