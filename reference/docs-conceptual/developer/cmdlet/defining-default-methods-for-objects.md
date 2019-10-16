---
title: Definir métodos predeterminados para objetos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: 346a194c6b4c81aa61a6331cdb62ae380a17bb1e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365694"
---
# <a name="defining-default-methods-for-objects"></a>Definición de métodos predeterminados para los objetos

Al extender .NET Framework objetos, puede Agregar métodos de código y métodos de script a los objetos.
El XML que se usa para definir estos métodos se describe en las secciones siguientes.

> [!NOTE]
> Los ejemplos de las secciones siguientes son del archivo de tipos `Types.ps1xml` en el directorio de instalación de Windows PowerShell (`$PSHOME`). Para obtener más información, vea [About Types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="code-methods"></a>Métodos de código

Un método de código hace referencia a un método estático de un objeto .NET Framework.

En el ejemplo siguiente, el método **ToString** se agrega al tipo [System. Xml. XmlNode](/dotnet/api/System.Xml.XmlNode) . El elemento [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) define el método extendido como un método de código. El elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) especifica el nombre del método extendido. Y el elemento [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) especifica el método estático. También puede Agregar el elemento [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) a los miembros del elemento [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a>Métodos de script

Un método de script define un método cuyo valor es la salida de un script. En el ejemplo siguiente, el método **ConvertToDateTime** se agrega al tipo [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) . El elemento [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) define el método extendido como un método de script. El elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) especifica el nombre del método extendido. Y el elemento [script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) especifica el script que genera el valor del método. También puede Agregar el elemento [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) a los miembros del elemento [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a>Consulta también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
