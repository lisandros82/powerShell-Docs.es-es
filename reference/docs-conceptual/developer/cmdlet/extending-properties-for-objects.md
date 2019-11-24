---
title: Extender propiedades para objetos | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364454"
---
# <a name="extending-properties-for-objects"></a>Extensión de las propiedades de los objetos

Al extender .NET Framework objetos, puede Agregar propiedades de alias, propiedades de código, propiedades de notas, propiedades de script y conjuntos de propiedades a los objetos. El XML que define estas propiedades se describe en las secciones siguientes.

> [!NOTE]
> Los ejemplos de las secciones siguientes son del archivo de tipos de `Types.ps1xml` predeterminado en el directorio de instalación de PowerShell (`$PSHOME`). Para obtener más información, vea [About Types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="alias-properties"></a>Propiedades de alias

Una propiedad de alias define un nuevo nombre para una propiedad existente.

En el ejemplo siguiente, la propiedad **Count** se agrega al tipo [System. Array](/dotnet/api/System.Array) . El elemento [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) define la propiedad extendida como una propiedad de alias. El elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica el nuevo nombre. Y el elemento [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) especifica la propiedad existente a la que hace referencia el alias. También puede Agregar el elemento `AliasProperty` a los miembros del elemento [MemberSets](/dotnet/api/system.management.automation.psmemberset) .

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

Una propiedad de código hace referencia a una propiedad estática de un objeto .NET Framework.

En el ejemplo siguiente, la propiedad **mode** se agrega al tipo [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) . El elemento [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) define la propiedad extendida como una propiedad de código. El elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica el nombre de la propiedad extendida. Y el elemento [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) define el método estático al que hace referencia la propiedad extendida. También puede Agregar el elemento `CodeProperty` a los miembros del elemento [MemberSets](/dotnet/api/system.management.automation.psmemberset) .

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

Una propiedad note define una propiedad que tiene un valor estático.

En el ejemplo siguiente, la propiedad **status** , cuyo valor es siempre **Success**, se agrega al tipo [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) . El elemento [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) define la propiedad extendida como una propiedad de nota. El elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica el nombre de la propiedad extendida. El elemento [Value](/dotnet/api/system.management.automation.psnoteproperty.value) especifica el valor estático de la propiedad extendida. También se puede Agregar el elemento `NoteProperty` a los miembros del elemento [MemberSets](/dotnet/api/system.management.automation.psmemberset) .

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

## <a name="script-properties"></a>Propiedades del script

Una propiedad de script define una propiedad cuyo valor es la salida de un script.

En el ejemplo siguiente, la propiedad **versionInfo** se agrega al tipo [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) . El elemento [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) define la propiedad extendida como una propiedad de script. El elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica el nombre de la propiedad extendida. Y el elemento [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) especifica el script que genera el valor de propiedad. También puede Agregar el elemento `ScriptProperty` a los miembros del elemento [MemberSets](/dotnet/api/system.management.automation.psmemberset) .

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

Un conjunto de propiedades define un grupo de propiedades extendidas al que se puede hacer referencia mediante el nombre del conjunto.
Por ejemplo, el parámetro de **propiedad** [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
puede especificar un conjunto de propiedades específico que se mostrará. Cuando se especifica un conjunto de propiedades, solo se muestran las propiedades que pertenecen al conjunto.

No hay ninguna restricción en el número de conjuntos de propiedades que se pueden definir para un objeto. Sin embargo, los conjuntos de propiedades que se usan para definir las propiedades de presentación predeterminadas de un objeto deben especificarse en el conjunto de miembros **PSStandardMembers** . En el archivo de tipos de `Types.ps1xml`, los nombres de los conjuntos de propiedades predeterminados son **DefaultDisplayProperty**, **DefaultDisplayPropertySet**y **DefaultKeyPropertySet**. Se omiten los conjuntos de propiedades adicionales que se agreguen al conjunto de miembros **PSStandardMembers** .

En el ejemplo siguiente, el conjunto de propiedades **DefaultDisplayPropertySet** se agrega al conjunto de miembros **PSStandardMembers** del tipo [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) . El elemento [PropertySet](/dotnet/api/system.management.automation.pspropertyset) define el grupo de propiedades. El elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica el nombre del conjunto de propiedades. Y el elemento [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) especifica las propiedades del conjunto. También puede Agregar el elemento `PropertySet` a los miembros del elemento [Type](/dotnet/api/system.management.automation.pstypename) .

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

## <a name="see-also"></a>Vea también

[Acerca de types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[System. Management. Automation](/dotnet/api/System.Management.Automation)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
