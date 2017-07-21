---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: fc517cd204b8f2647b824f0b9ee8f0f8f62fb821
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="declare-base-class"></a><span data-ttu-id="0cbfb-102">Declarar una clase base</span><span class="sxs-lookup"><span data-stu-id="0cbfb-102">Declare Base Class</span></span>
<span data-ttu-id="0cbfb-103">Puede declarar una clase de Windows PowerShell como un tipo base para otra clase de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0cbfb-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

```PowerShell
class bar
{
   [int]foo() 
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="0cbfb-104">También puede usar los tipos de .NET Framework existentes como clases base:</span><span class="sxs-lookup"><span data-stu-id="0cbfb-104">You can also use existing .NET Framework types as base classes:</span></span>

```PowerShell
class MyIntList : system.collections.generic.list[int]
{
    
}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

