---
title: Definir el miembro predeterminado se establece para los objetos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: e8185eb7221a3be0445eddc537dbca89478c74f2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859801"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="f084c-102">Definición de conjuntos de miembros predeterminados para los objetos</span><span class="sxs-lookup"><span data-stu-id="f084c-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="f084c-103">El conjunto de miembros PSStandardMembers usando Windows PowerShell para definir los conjuntos de propiedades predeterminado para un objeto.</span><span class="sxs-lookup"><span data-stu-id="f084c-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="f084c-104">Los conjuntos de propiedades predeterminado se pueden usar los comandos como los cmdlets de formato para mostrar solo esas propiedades definidas por el conjunto de propiedades.</span><span class="sxs-lookup"><span data-stu-id="f084c-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="f084c-105">Los conjuntos de propiedades predeterminada incluyen DefaultDisplayProperty, DefaultDisplayPropertySet y DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="f084c-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="f084c-106">Windows PowerShell omite todos los demás conjuntos de miembros y otros conjuntos de propiedad agregados al conjunto de miembros PSStandardMembers.</span><span class="sxs-lookup"><span data-stu-id="f084c-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="f084c-107">Conjunto de miembros para System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="f084c-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="f084c-108">En el ejemplo siguiente, el conjunto de miembros PSStandardMembers define la propiedad DefaultDisplayPropertySet establecida para [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objetos.</span><span class="sxs-lookup"><span data-stu-id="f084c-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="f084c-109">Establecer esta propiedad se usa por la [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f084c-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>
<span data-ttu-id="f084c-110">En el ejemplo siguiente, el conjunto de miembros PSStandardMembers define la propiedad DefaultDisplayPropertySet establecida para [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objetos.</span><span class="sxs-lookup"><span data-stu-id="f084c-110">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="f084c-111">Establecer esta propiedad se usa por la [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f084c-111">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

```xml
<Type>
  <Name>System.Diagnostics.Process</Name>
  <Members>
    <MemberSet>
     <Name>PSStandardMembers</Name>
     <Members>
       <PropertySet>
         <Name>DefaultDisplayPropertySet</Name>
         <ReferencedProperties>
           <Name>Id</Name>
           <Name>Handles</Name>
           <Name>CPU</Name>
           <Name>Name</Name>
         </ReferencedProperties>
      </PropertySet>
    </Members>
  </MemberSet>
```

<span data-ttu-id="f084c-112">La salida siguiente muestra las propiedades predeterminadas devueltas por la [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f084c-112">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="f084c-113">Solo el `Id`, `Handles`, `CPU`, y `Name` se devuelven las propiedades para cada objeto de proceso.</span><span class="sxs-lookup"><span data-stu-id="f084c-113">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>
<span data-ttu-id="f084c-114">La salida siguiente muestra las propiedades predeterminadas devueltas por la [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f084c-114">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="f084c-115">Solo el `Id`, `Handles`, `CPU`, y `Name` se devuelven las propiedades para cada objeto de proceso.</span><span class="sxs-lookup"><span data-stu-id="f084c-115">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

```powershell
Get-Process | format-list
```

```output
Id      : 2036
Handles : 27
CPU     :
Name    : AEADISRV

Id      : 272
Handles : 38
CPU     :
Name    : agrsmsvc
...
```

## <a name="see-also"></a><span data-ttu-id="f084c-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="f084c-116">See Also</span></span>

[<span data-ttu-id="f084c-117">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f084c-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
