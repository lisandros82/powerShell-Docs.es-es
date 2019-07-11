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
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="67ee4-102">Definición de métodos predeterminados para los objetos</span><span class="sxs-lookup"><span data-stu-id="67ee4-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="67ee4-103">Al extender los objetos de .NET Framework, puede agregar métodos de código y los métodos de script a los objetos.</span><span class="sxs-lookup"><span data-stu-id="67ee4-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="67ee4-104">El XML que se utiliza para definir estos métodos se describe en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="67ee4-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="67ee4-105">Los ejemplos en las secciones siguientes son del archivo Types.ps1xml tipos en el directorio de instalación de Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="67ee4-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="67ee4-106">Métodos de código</span><span class="sxs-lookup"><span data-stu-id="67ee4-106">Code Methods</span></span>

<span data-ttu-id="67ee4-107">Un método de código hace referencia a un método estático de un objeto de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67ee4-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="67ee4-108">¿En el ejemplo siguiente, la **ConvertLargeIntegerToInt64** método se agrega a la [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) tipo.</span><span class="sxs-lookup"><span data-stu-id="67ee4-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="67ee4-109">El [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) elemento define el método extendido como un método de código.</span><span class="sxs-lookup"><span data-stu-id="67ee4-109">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="67ee4-110">El [nombre](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) elemento especifica el nombre del método extendido.</span><span class="sxs-lookup"><span data-stu-id="67ee4-110">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="67ee4-111">Y, el [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) elemento especifica el método estático.</span><span class="sxs-lookup"><span data-stu-id="67ee4-111">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="67ee4-112">(También puede agregar el [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) elemento a los miembros de la [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) elemento.)</span><span class="sxs-lookup"><span data-stu-id="67ee4-112">(You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="67ee4-113">Métodos de script</span><span class="sxs-lookup"><span data-stu-id="67ee4-113">Script Methods</span></span>

<span data-ttu-id="67ee4-114">Un método de secuencia de comandos define un método cuyo valor es el resultado de una secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="67ee4-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="67ee4-115">¿En el ejemplo siguiente, la **ConvertToDateTime** método se agrega a la [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) tipo.</span><span class="sxs-lookup"><span data-stu-id="67ee4-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="67ee4-116">El [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) elemento define el método extendido como un método de secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="67ee4-116">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="67ee4-117">El [nombre](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) elemento especifica el nombre del método extendido.</span><span class="sxs-lookup"><span data-stu-id="67ee4-117">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="67ee4-118">Y, el [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) elemento especifica el script que genera el valor del método.</span><span class="sxs-lookup"><span data-stu-id="67ee4-118">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="67ee4-119">(También puede agregar el [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) elemento a los miembros de la [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) elemento.)</span><span class="sxs-lookup"><span data-stu-id="67ee4-119">(You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="67ee4-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="67ee4-120">See Also</span></span>

[<span data-ttu-id="67ee4-121">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="67ee4-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
