---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 43b26426a76b6503a83e35ae0c02a0af69902ed6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="declare-base-class"></a><span data-ttu-id="08053-102">Declarar una clase base</span><span class="sxs-lookup"><span data-stu-id="08053-102">Declare Base Class</span></span>
<span data-ttu-id="08053-103">Puede declarar una clase de Windows PowerShell como un tipo base para otra clase de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="08053-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

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

<span data-ttu-id="08053-104">También puede usar los tipos de .NET Framework existentes como clases base:</span><span class="sxs-lookup"><span data-stu-id="08053-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```