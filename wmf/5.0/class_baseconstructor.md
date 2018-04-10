---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 3269c8cc871f22488b64fb072dac72698983f360
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="58f2b-102">Llamar al constructor de clase base</span><span class="sxs-lookup"><span data-stu-id="58f2b-102">Call Base Class Constructor</span></span>

<span data-ttu-id="58f2b-103">Para llamar a un constructor de clase base desde una subclase, use la palabra clave **base**:</span><span class="sxs-lookup"><span data-stu-id="58f2b-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="58f2b-104">Si una clase base tiene un constructor predeterminado (sin parámetros), se puede omitir una llamada explícita al constructor:</span><span class="sxs-lookup"><span data-stu-id="58f2b-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```