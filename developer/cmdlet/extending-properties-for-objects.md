---
title: Extender las propiedades de objetos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: dcab755f565cd176c85ef6b9c719bceae10301b4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854531"
---
# <a name="extending-properties-for-objects"></a>Extensión de las propiedades de los objetos

Al extender los objetos de .NET Framework, puede agregar alias propiedades, propiedades de código, las propiedades de nota, las propiedades de la secuencia de comandos y conjuntos de propiedades a los objetos. El XML que se usa para definir estas propiedades se describe en las secciones siguientes.

> [!NOTE]
> Los ejemplos de las siguientes secciones son desde el archivo de tipos predeterminado Types.ps1xml en el directorio de instalación de Windows PowerShell (`$pshome`).

## <a name="alias-properties"></a>Propiedades del alias

Una propiedad de alias define un nombre nuevo para una propiedad existente.

¿En el ejemplo siguiente, la `Count` propiedad se agrega a la [System.Array? Displayproperty = Fullname](/dotnet/api/System.Array) tipo. El [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) elemento define la propiedad extendida como una propiedad de alias. El [nombre](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento especifica el nuevo nombre. Y, el [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) elemento especifica la propiedad existente al que hace referencia el alias. (También puede agregar el [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) elemento a los miembros de la [conjuntos de miembros](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

## <a name="code-properties"></a>Propiedades de código

Una propiedad de código hace referencia a una propiedad estática de un objeto de .NET Framework.

¿En el ejemplo siguiente, la `Node` propiedad se agrega a la [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) tipo. El [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) elemento define la propiedad extendida como una propiedad de código. El [nombre](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento especifica el nombre de la propiedad extendida. Y, el [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) elemento define el método estático al que hace referencia la propiedad extendida. (También puede agregar el [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) elemento a los miembros de la [conjuntos de miembros](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a>Propiedades de nota

Una propiedad de nota define una propiedad que tiene un valor estático.

¿En el ejemplo siguiente, la `Status` propiedad (cuyo valor siempre es "Correcto") se agrega a la [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) tipo. El [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elemento define la propiedad extendida como una propiedad de nota; el [nombre](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento especifica el nombre de la propiedad extendida; y la [valor](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) elemento Especifica el valor estático de la propiedad extendida. (El [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elemento también se puede agregar a los miembros de la [conjuntos de miembros](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

## <a name="script-properties"></a>Propiedades de script

Una propiedad de secuencia de comandos define una propiedad cuyo valor es el resultado de una secuencia de comandos.

¿En el ejemplo siguiente, la `VersionInfo` propiedad se agrega a la [System.IO.Fileinfo? Displayproperty = Fullname](/dotnet/api/System.IO.FileInfo) tipo. El [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) elemento define la propiedad extendida como una propiedad de secuencia de comandos. El [nombre](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento especifica el nombre de la propiedad extendida. Y, el [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) elemento especifica el script que genera el valor de propiedad. (También puede agregar el [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) elemento a los miembros de la [conjuntos de miembros](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
        [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

## <a name="property-sets"></a>Conjuntos de propiedades

Un conjunto de propiedades define un grupo de propiedades extendidas que se puede hacer referencia por el nombre del conjunto. Por ejemplo, el `Property` parámetro de la [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet puede especificar una propiedad específica establecida en mostrarse. Cuando se especifica un conjunto de propiedades, se muestran solo las propiedades que pertenecen al conjunto.
Un conjunto de propiedades define un grupo de propiedades extendidas que se puede hacer referencia por el nombre del conjunto. Por ejemplo, el `Property` parámetro de la [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet puede especificar una propiedad específica establecida en mostrarse. Cuando se especifica un conjunto de propiedades, se muestran solo las propiedades que pertenecen al conjunto.

No hay ninguna restricción en el número de conjuntos de propiedades que se pueden definir para un objeto. Sin embargo, se deben especificar los conjuntos de propiedades que se usan para definir las propiedades de presentación predeterminada de un objeto en el conjunto de miembros PSStandardMembers. En el archivo Types.ps1xml tipos, los nombres de conjunto de propiedades predeterminada incluyen DefaultDisplayProperty, DefaultDisplayPropertySet y DefaultKeyPropertySet. Se omiten los conjuntos de propiedades adicionales que agregue al conjunto de miembros PSStandardMembers.

¿En el ejemplo siguiente, el conjunto de propiedades DefaultDisplayPropertySet se agrega al conjunto de miembros de PSStandardMembers el [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) tipo. El [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) elemento define el grupo de propiedades. El [nombre](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento especifica el nombre del conjunto de propiedades. Y, el [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) elemento especifica las propiedades del conjunto. (También puede agregar el [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) elemento a los miembros de la [tipo](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) elemento.)

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
           <Name>DefaultDisplayPropertySet</Name>
           <ReferencedProperties>
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
