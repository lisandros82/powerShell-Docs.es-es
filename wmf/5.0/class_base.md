---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 5dbaa126cf9ae3917c3a8787ffc5ef5ac77b19c1
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2017
---
# <a name="declare-base-class"></a><span data-ttu-id="8c473-102">Declarar una clase base</span><span class="sxs-lookup"><span data-stu-id="8c473-102">Declare Base Class</span></span>
<span data-ttu-id="8c473-103">Puede declarar una clase de Windows PowerShell como un tipo base para otra clase de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c473-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

```powershell
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

<span data-ttu-id="8c473-104">También puede usar los tipos de .NET Framework existentes como clases base:</span><span class="sxs-lookup"><span data-stu-id="8c473-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    
}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

