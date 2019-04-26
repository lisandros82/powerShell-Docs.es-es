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
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068256"
---
# <a name="defining-default-member-sets-for-objects"></a>Definición de conjuntos de miembros predeterminados para los objetos

El conjunto de miembros PSStandardMembers usando Windows PowerShell para definir los conjuntos de propiedades predeterminado para un objeto. Los conjuntos de propiedades predeterminado se pueden usar los comandos como los cmdlets de formato para mostrar solo esas propiedades definidas por el conjunto de propiedades. Los conjuntos de propiedades predeterminada incluyen DefaultDisplayProperty, DefaultDisplayPropertySet y DefaultKeyPropertySet. Windows PowerShell omite todos los demás conjuntos de miembros y otros conjuntos de propiedad agregados al conjunto de miembros PSStandardMembers.

## <a name="member-set-for-systemdiagnosticsprocess"></a>Conjunto de miembros para System.Diagnostics.Process

En el ejemplo siguiente, el conjunto de miembros PSStandardMembers define la propiedad DefaultDisplayPropertySet establecida para [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objetos. Establecer esta propiedad se usa por la [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.

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

La salida siguiente muestra las propiedades predeterminadas devueltas por la [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet. Solo el `Id`, `Handles`, `CPU`, y `Name` se devuelven las propiedades para cada objeto de proceso.

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
