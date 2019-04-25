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
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068222"
---
# <a name="defining-default-methods-for-objects"></a>Definición de métodos predeterminados para los objetos

Al extender los objetos de .NET Framework, puede agregar métodos de código y los métodos de script a los objetos. El XML que se utiliza para definir estos métodos se describe en las secciones siguientes.

> [!NOTE]
> Los ejemplos en las secciones siguientes son del archivo Types.ps1xml tipos en el directorio de instalación de Windows PowerShell (`$pshome`).

## <a name="code-methods"></a>Métodos de código

Un método de código hace referencia a un método estático de un objeto de .NET Framework.

¿En el ejemplo siguiente, la **ConvertLargeIntegerToInt64** método se agrega a la [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) tipo. El [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) elemento define el método extendido como un método de código. El [nombre](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento especifica el nombre del método extendido. Y, el [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) elemento especifica el método estático. (También puede agregar el [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) elemento a los miembros de la [conjuntos de miembros](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

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

Un método de secuencia de comandos define un método cuyo valor es el resultado de una secuencia de comandos. ¿En el ejemplo siguiente, la **ConvertToDateTime** método se agrega a la [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) tipo. El [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) elemento define el método extendido como un método de secuencia de comandos. El [nombre](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento especifica el nombre del método extendido. Y, el [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) elemento especifica el script que genera el valor del método. (También puede agregar el [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) elemento a los miembros de la [conjuntos de miembros](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

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