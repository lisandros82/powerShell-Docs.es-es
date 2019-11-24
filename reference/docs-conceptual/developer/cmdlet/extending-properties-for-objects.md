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
# <a name="extending-properties-for-objects"></a><span data-ttu-id="be321-102">Extensión de las propiedades de los objetos</span><span class="sxs-lookup"><span data-stu-id="be321-102">Extending Properties for Objects</span></span>

<span data-ttu-id="be321-103">Al extender .NET Framework objetos, puede Agregar propiedades de alias, propiedades de código, propiedades de notas, propiedades de script y conjuntos de propiedades a los objetos.</span><span class="sxs-lookup"><span data-stu-id="be321-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="be321-104">El XML que define estas propiedades se describe en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="be321-104">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="be321-105">Los ejemplos de las secciones siguientes son del archivo de tipos de `Types.ps1xml` predeterminado en el directorio de instalación de PowerShell (`$PSHOME`).</span><span class="sxs-lookup"><span data-stu-id="be321-105">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="be321-106">Para obtener más información, vea [About Types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="be321-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="be321-107">Propiedades de alias</span><span class="sxs-lookup"><span data-stu-id="be321-107">Alias properties</span></span>

<span data-ttu-id="be321-108">Una propiedad de alias define un nuevo nombre para una propiedad existente.</span><span class="sxs-lookup"><span data-stu-id="be321-108">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="be321-109">En el ejemplo siguiente, la propiedad **Count** se agrega al tipo [System. Array](/dotnet/api/System.Array) .</span><span class="sxs-lookup"><span data-stu-id="be321-109">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="be321-110">El elemento [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) define la propiedad extendida como una propiedad de alias.</span><span class="sxs-lookup"><span data-stu-id="be321-110">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="be321-111">El elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica el nuevo nombre.</span><span class="sxs-lookup"><span data-stu-id="be321-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="be321-112">Y el elemento [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) especifica la propiedad existente a la que hace referencia el alias.</span><span class="sxs-lookup"><span data-stu-id="be321-112">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="be321-113">También puede Agregar el elemento `AliasProperty` a los miembros del elemento [MemberSets](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="be321-113">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="be321-114">Propiedades de código</span><span class="sxs-lookup"><span data-stu-id="be321-114">Code properties</span></span>

<span data-ttu-id="be321-115">Una propiedad de código hace referencia a una propiedad estática de un objeto .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be321-115">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="be321-116">En el ejemplo siguiente, la propiedad **mode** se agrega al tipo [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="be321-116">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="be321-117">El elemento [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) define la propiedad extendida como una propiedad de código.</span><span class="sxs-lookup"><span data-stu-id="be321-117">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="be321-118">El elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica el nombre de la propiedad extendida.</span><span class="sxs-lookup"><span data-stu-id="be321-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="be321-119">Y el elemento [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) define el método estático al que hace referencia la propiedad extendida.</span><span class="sxs-lookup"><span data-stu-id="be321-119">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="be321-120">También puede Agregar el elemento `CodeProperty` a los miembros del elemento [MemberSets](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="be321-120">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="be321-121">Propiedades de nota</span><span class="sxs-lookup"><span data-stu-id="be321-121">Note properties</span></span>

<span data-ttu-id="be321-122">Una propiedad note define una propiedad que tiene un valor estático.</span><span class="sxs-lookup"><span data-stu-id="be321-122">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="be321-123">En el ejemplo siguiente, la propiedad **status** , cuyo valor es siempre **Success**, se agrega al tipo [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="be321-123">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="be321-124">El elemento [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) define la propiedad extendida como una propiedad de nota.</span><span class="sxs-lookup"><span data-stu-id="be321-124">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="be321-125">El elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica el nombre de la propiedad extendida.</span><span class="sxs-lookup"><span data-stu-id="be321-125">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="be321-126">El elemento [Value](/dotnet/api/system.management.automation.psnoteproperty.value) especifica el valor estático de la propiedad extendida.</span><span class="sxs-lookup"><span data-stu-id="be321-126">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="be321-127">También se puede Agregar el elemento `NoteProperty` a los miembros del elemento [MemberSets](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="be321-127">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="be321-128">Propiedades del script</span><span class="sxs-lookup"><span data-stu-id="be321-128">Script properties</span></span>

<span data-ttu-id="be321-129">Una propiedad de script define una propiedad cuyo valor es la salida de un script.</span><span class="sxs-lookup"><span data-stu-id="be321-129">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="be321-130">En el ejemplo siguiente, la propiedad **versionInfo** se agrega al tipo [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) .</span><span class="sxs-lookup"><span data-stu-id="be321-130">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="be321-131">El elemento [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) define la propiedad extendida como una propiedad de script.</span><span class="sxs-lookup"><span data-stu-id="be321-131">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="be321-132">El elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica el nombre de la propiedad extendida.</span><span class="sxs-lookup"><span data-stu-id="be321-132">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="be321-133">Y el elemento [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) especifica el script que genera el valor de propiedad.</span><span class="sxs-lookup"><span data-stu-id="be321-133">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="be321-134">También puede Agregar el elemento `ScriptProperty` a los miembros del elemento [MemberSets](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="be321-134">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="be321-135">Conjuntos de propiedades</span><span class="sxs-lookup"><span data-stu-id="be321-135">Property sets</span></span>

<span data-ttu-id="be321-136">Un conjunto de propiedades define un grupo de propiedades extendidas al que se puede hacer referencia mediante el nombre del conjunto.</span><span class="sxs-lookup"><span data-stu-id="be321-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="be321-137">Por ejemplo, el parámetro de **propiedad** [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
puede especificar un conjunto de propiedades específico que se mostrará.</span><span class="sxs-lookup"><span data-stu-id="be321-137">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="be321-138">Cuando se especifica un conjunto de propiedades, solo se muestran las propiedades que pertenecen al conjunto.</span><span class="sxs-lookup"><span data-stu-id="be321-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="be321-139">No hay ninguna restricción en el número de conjuntos de propiedades que se pueden definir para un objeto.</span><span class="sxs-lookup"><span data-stu-id="be321-139">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="be321-140">Sin embargo, los conjuntos de propiedades que se usan para definir las propiedades de presentación predeterminadas de un objeto deben especificarse en el conjunto de miembros **PSStandardMembers** .</span><span class="sxs-lookup"><span data-stu-id="be321-140">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="be321-141">En el archivo de tipos de `Types.ps1xml`, los nombres de los conjuntos de propiedades predeterminados son **DefaultDisplayProperty**, **DefaultDisplayPropertySet**y **DefaultKeyPropertySet**.</span><span class="sxs-lookup"><span data-stu-id="be321-141">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="be321-142">Se omiten los conjuntos de propiedades adicionales que se agreguen al conjunto de miembros **PSStandardMembers** .</span><span class="sxs-lookup"><span data-stu-id="be321-142">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="be321-143">En el ejemplo siguiente, el conjunto de propiedades **DefaultDisplayPropertySet** se agrega al conjunto de miembros **PSStandardMembers** del tipo [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="be321-143">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="be321-144">El elemento [PropertySet](/dotnet/api/system.management.automation.pspropertyset) define el grupo de propiedades.</span><span class="sxs-lookup"><span data-stu-id="be321-144">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="be321-145">El elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica el nombre del conjunto de propiedades.</span><span class="sxs-lookup"><span data-stu-id="be321-145">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="be321-146">Y el elemento [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) especifica las propiedades del conjunto.</span><span class="sxs-lookup"><span data-stu-id="be321-146">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="be321-147">También puede Agregar el elemento `PropertySet` a los miembros del elemento [Type](/dotnet/api/system.management.automation.pstypename) .</span><span class="sxs-lookup"><span data-stu-id="be321-147">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="be321-148">Vea también</span><span class="sxs-lookup"><span data-stu-id="be321-148">See also</span></span>

[<span data-ttu-id="be321-149">Acerca de types. ps1xml</span><span class="sxs-lookup"><span data-stu-id="be321-149">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="be321-150">System. Management. Automation</span><span class="sxs-lookup"><span data-stu-id="be321-150">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

[<span data-ttu-id="be321-151">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="be321-151">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
