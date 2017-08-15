---
ms.date: 2017-06-12T00:00:00.000Z
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 1fd6d80d6b7effb4bd98c1594d64e531c4e5c9b5
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2017
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

