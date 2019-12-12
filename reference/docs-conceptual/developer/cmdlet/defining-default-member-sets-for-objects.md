---
title: Definir conjuntos de miembros predeterminados para objetos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369784"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="0ad59-102">Definición de conjuntos de miembros predeterminados para los objetos</span><span class="sxs-lookup"><span data-stu-id="0ad59-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="0ad59-103">Windows PowerShell usa el conjunto de miembros PSStandardMembers para definir los conjuntos de propiedades predeterminados para un objeto.</span><span class="sxs-lookup"><span data-stu-id="0ad59-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="0ad59-104">Los comandos, como los cmdlets de formato, pueden usar los conjuntos de propiedades predeterminados para mostrar solo las propiedades definidas por el conjunto de propiedades.</span><span class="sxs-lookup"><span data-stu-id="0ad59-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="0ad59-105">Entre los conjuntos de propiedades predeterminadas se incluyen DefaultDisplayProperty, DefaultDisplayPropertySet y DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="0ad59-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="0ad59-106">Windows PowerShell omite todos los demás conjuntos de miembros y cualquier otro conjunto de propiedades agregado al conjunto de miembros PSStandardMembers.</span><span class="sxs-lookup"><span data-stu-id="0ad59-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="0ad59-107">Conjunto de miembros para System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="0ad59-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="0ad59-108">En el ejemplo siguiente, el conjunto de miembros PSStandardMembers define el conjunto de propiedades DefaultDisplayPropertySet para los objetos [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="0ad59-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="0ad59-109">Este conjunto de propiedades lo usa el cmdlet [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) .</span><span class="sxs-lookup"><span data-stu-id="0ad59-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="0ad59-110">En el resultado siguiente se muestran las propiedades predeterminadas devueltas por el cmdlet [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) .</span><span class="sxs-lookup"><span data-stu-id="0ad59-110">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="0ad59-111">Solo se devuelven las propiedades `Id`, `Handles`, `CPU`y `Name` para cada objeto de proceso.</span><span class="sxs-lookup"><span data-stu-id="0ad59-111">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0ad59-112">Véase también</span><span class="sxs-lookup"><span data-stu-id="0ad59-112">See Also</span></span>

[<span data-ttu-id="0ad59-113">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0ad59-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
