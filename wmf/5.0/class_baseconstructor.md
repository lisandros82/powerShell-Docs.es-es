---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 403a79e17b832b5c58fd21a138fcebb8adb76d40
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="48998-102">Llamar al constructor de clase base</span><span class="sxs-lookup"><span data-stu-id="48998-102">Call Base Class Constructor</span></span>

<span data-ttu-id="48998-103">Para llamar a un constructor de clase base desde una subclase, use la palabra clave **base**:</span><span class="sxs-lookup"><span data-stu-id="48998-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

```PowerShell
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

<span data-ttu-id="48998-104">Si una clase base tiene un constructor predeterminado (sin parámetros), se puede omitir una llamada explícita al constructor:</span><span class="sxs-lookup"><span data-stu-id="48998-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```PowerShell
class C : B
{
    C([int]$c) {}
}
```

