---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 424e0b7a4d62fc35e5040a7e425950e887021d7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085888"
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
