---
title: Definir métodos predeterminados de los objetos para | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733986"
---
# <a name="defining-default-methods-for-objects"></a>Definición de métodos predeterminados para los objetos

Al extender los objetos de .NET Framework, puede agregar métodos de código y los métodos de script a los objetos. El XML que se utiliza para definir estos métodos se describe en las secciones siguientes.

> [!NOTE]
> Los ejemplos en las secciones siguientes son del archivo Types.ps1xml tipos en el directorio de instalación de Windows PowerShell (`$pshome`).

## <a name="code-methods"></a>Métodos de código

Un método de código hace referencia a un método estático de un objeto de .NET Framework.

¿En el ejemplo siguiente, la **ConvertLargeIntegerToInt64** método se agrega a la [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) tipo. El [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) elemento define el método extendido como un método de código. El [nombre](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) elemento especifica el nombre del método extendido. Y, el [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) elemento especifica el método estático. (También puede agregar el [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) elemento a los miembros de la [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) elemento.)

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a>Métodos de script

Un método de secuencia de comandos define un método cuyo valor es el resultado de una secuencia de comandos. ¿En el ejemplo siguiente, la **ConvertToDateTime** método se agrega a la [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) tipo. El [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) elemento define el método extendido como un método de secuencia de comandos. El [nombre](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) elemento especifica el nombre del método extendido. Y, el [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) elemento especifica el script que genera el valor del método. (También puede agregar el [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) elemento a los miembros de la [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) elemento.)

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

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
