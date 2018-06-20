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
# <a name="call-base-class-constructor"></a>Llamar al constructor de clase base

Para llamar a un constructor de clase base desde una subclase, use la palabra clave **base**:

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

Si una clase base tiene un constructor predeterminado (sin parámetros), se puede omitir una llamada explícita al constructor:

```powershell
class C : B
{
    C([int]$c) {}
}
```
