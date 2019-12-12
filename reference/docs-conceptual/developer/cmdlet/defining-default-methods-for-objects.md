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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365694"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="eb1e9-102">Definición de métodos predeterminados para los objetos</span><span class="sxs-lookup"><span data-stu-id="eb1e9-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="eb1e9-103">Al extender .NET Framework objetos, puede Agregar métodos de código y métodos de script a los objetos.</span><span class="sxs-lookup"><span data-stu-id="eb1e9-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span>
<span data-ttu-id="eb1e9-104">El XML que se usa para definir estos métodos se describe en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="eb1e9-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="eb1e9-105">Los ejemplos de las secciones siguientes proceden del archivo de tipos de `Types.ps1xml` en el directorio de instalación de Windows PowerShell (`$PSHOME`).</span><span class="sxs-lookup"><span data-stu-id="eb1e9-105">The examples in the following sections are from the `Types.ps1xml` types file in the Windows PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="eb1e9-106">Para obtener más información, vea [About Types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="eb1e9-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="code-methods"></a><span data-ttu-id="eb1e9-107">Métodos de código</span><span class="sxs-lookup"><span data-stu-id="eb1e9-107">Code methods</span></span>

<span data-ttu-id="eb1e9-108">Un método de código hace referencia a un método estático de un objeto .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb1e9-108">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="eb1e9-109">En el ejemplo siguiente, el método **ToString** se agrega al tipo [System. Xml. XmlNode](/dotnet/api/System.Xml.XmlNode) .</span><span class="sxs-lookup"><span data-stu-id="eb1e9-109">In the following example, the **ToString** method is added to the [System.Xml.XmlNode](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="eb1e9-110">El elemento [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) define el método extendido como un método de código.</span><span class="sxs-lookup"><span data-stu-id="eb1e9-110">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="eb1e9-111">El elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) especifica el nombre del método extendido.</span><span class="sxs-lookup"><span data-stu-id="eb1e9-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="eb1e9-112">Y el elemento [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) especifica el método estático.</span><span class="sxs-lookup"><span data-stu-id="eb1e9-112">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="eb1e9-113">También puede Agregar el elemento [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) a los miembros del elemento [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .</span><span class="sxs-lookup"><span data-stu-id="eb1e9-113">You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="eb1e9-114">Métodos de script</span><span class="sxs-lookup"><span data-stu-id="eb1e9-114">Script methods</span></span>

<span data-ttu-id="eb1e9-115">Un método de script define un método cuyo valor es la salida de un script.</span><span class="sxs-lookup"><span data-stu-id="eb1e9-115">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="eb1e9-116">En el ejemplo siguiente, el método **ConvertToDateTime** se agrega al tipo [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) .</span><span class="sxs-lookup"><span data-stu-id="eb1e9-116">In the following example, the **ConvertToDateTime** method is added to the [System.Management.ManagementObject](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="eb1e9-117">El elemento [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) define el método extendido como un método de script.</span><span class="sxs-lookup"><span data-stu-id="eb1e9-117">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="eb1e9-118">El elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) especifica el nombre del método extendido.</span><span class="sxs-lookup"><span data-stu-id="eb1e9-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="eb1e9-119">Y el elemento [script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) especifica el script que genera el valor del método.</span><span class="sxs-lookup"><span data-stu-id="eb1e9-119">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="eb1e9-120">También puede Agregar el elemento [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) a los miembros del elemento [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .</span><span class="sxs-lookup"><span data-stu-id="eb1e9-120">You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eb1e9-121">Consulta también</span><span class="sxs-lookup"><span data-stu-id="eb1e9-121">See also</span></span>

[<span data-ttu-id="eb1e9-122">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb1e9-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
