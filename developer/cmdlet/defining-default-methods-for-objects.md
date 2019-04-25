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
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="e156b-102">Definición de métodos predeterminados para los objetos</span><span class="sxs-lookup"><span data-stu-id="e156b-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="e156b-103">Al extender los objetos de .NET Framework, puede agregar métodos de código y los métodos de script a los objetos.</span><span class="sxs-lookup"><span data-stu-id="e156b-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="e156b-104">El XML que se utiliza para definir estos métodos se describe en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="e156b-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="e156b-105">Los ejemplos en las secciones siguientes son del archivo Types.ps1xml tipos en el directorio de instalación de Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="e156b-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="e156b-106">Métodos de código</span><span class="sxs-lookup"><span data-stu-id="e156b-106">Code Methods</span></span>

<span data-ttu-id="e156b-107">Un método de código hace referencia a un método estático de un objeto de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e156b-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="e156b-108">¿En el ejemplo siguiente, la **ConvertLargeIntegerToInt64** método se agrega a la [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) tipo.</span><span class="sxs-lookup"><span data-stu-id="e156b-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="e156b-109">El [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) elemento define el método extendido como un método de código.</span><span class="sxs-lookup"><span data-stu-id="e156b-109">The [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element defines the extended method as a code method.</span></span> <span data-ttu-id="e156b-110">El [nombre](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento especifica el nombre del método extendido.</span><span class="sxs-lookup"><span data-stu-id="e156b-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="e156b-111">Y, el [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) elemento especifica el método estático.</span><span class="sxs-lookup"><span data-stu-id="e156b-111">And, the [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element specifies the static method.</span></span> <span data-ttu-id="e156b-112">(También puede agregar el [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) elemento a los miembros de la [conjuntos de miembros](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="e156b-112">(You can also add the [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="e156b-113">Métodos de script</span><span class="sxs-lookup"><span data-stu-id="e156b-113">Script Methods</span></span>

<span data-ttu-id="e156b-114">Un método de secuencia de comandos define un método cuyo valor es el resultado de una secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="e156b-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="e156b-115">¿En el ejemplo siguiente, la **ConvertToDateTime** método se agrega a la [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) tipo.</span><span class="sxs-lookup"><span data-stu-id="e156b-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="e156b-116">El [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) elemento define el método extendido como un método de secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="e156b-116">The [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element defines the extended method as a script method.</span></span> <span data-ttu-id="e156b-117">El [nombre](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento especifica el nombre del método extendido.</span><span class="sxs-lookup"><span data-stu-id="e156b-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="e156b-118">Y, el [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) elemento especifica el script que genera el valor del método.</span><span class="sxs-lookup"><span data-stu-id="e156b-118">And, the [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element specifies the script that generates the method value.</span></span> <span data-ttu-id="e156b-119">(También puede agregar el [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) elemento a los miembros de la [conjuntos de miembros](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="e156b-119">(You can also add the [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e156b-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="e156b-120">See Also</span></span>

[<span data-ttu-id="e156b-121">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e156b-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)