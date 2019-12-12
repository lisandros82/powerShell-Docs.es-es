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
# <a name="defining-default-member-sets-for-objects"></a>Definición de conjuntos de miembros predeterminados para los objetos

Windows PowerShell usa el conjunto de miembros PSStandardMembers para definir los conjuntos de propiedades predeterminados para un objeto. Los comandos, como los cmdlets de formato, pueden usar los conjuntos de propiedades predeterminados para mostrar solo las propiedades definidas por el conjunto de propiedades. Entre los conjuntos de propiedades predeterminadas se incluyen DefaultDisplayProperty, DefaultDisplayPropertySet y DefaultKeyPropertySet. Windows PowerShell omite todos los demás conjuntos de miembros y cualquier otro conjunto de propiedades agregado al conjunto de miembros PSStandardMembers.

## <a name="member-set-for-systemdiagnosticsprocess"></a>Conjunto de miembros para System. Diagnostics. Process

En el ejemplo siguiente, el conjunto de miembros PSStandardMembers define el conjunto de propiedades DefaultDisplayPropertySet para los objetos [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) . Este conjunto de propiedades lo usa el cmdlet [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) .

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

En el resultado siguiente se muestran las propiedades predeterminadas devueltas por el cmdlet [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) . Solo se devuelven las propiedades `Id`, `Handles`, `CPU`y `Name` para cada objeto de proceso.

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

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
