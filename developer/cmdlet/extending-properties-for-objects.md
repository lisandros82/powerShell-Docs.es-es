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
ms.openlocfilehash: 496e363b041194563d46c09eee67a12055bb54b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068154"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="a7bca-102">Extensión de las propiedades de los objetos</span><span class="sxs-lookup"><span data-stu-id="a7bca-102">Extending Properties for Objects</span></span>

<span data-ttu-id="a7bca-103">Al extender los objetos de .NET Framework, puede agregar alias propiedades, propiedades de código, las propiedades de nota, las propiedades de la secuencia de comandos y conjuntos de propiedades a los objetos.</span><span class="sxs-lookup"><span data-stu-id="a7bca-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="a7bca-104">El XML que se usa para definir estas propiedades se describe en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="a7bca-104">The XML that is used to define these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="a7bca-105">Los ejemplos de las siguientes secciones son desde el archivo de tipos predeterminado Types.ps1xml en el directorio de instalación de Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="a7bca-105">The examples in the following sections are from the default Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="a7bca-106">Propiedades del alias</span><span class="sxs-lookup"><span data-stu-id="a7bca-106">Alias Properties</span></span>

<span data-ttu-id="a7bca-107">Una propiedad de alias define un nombre nuevo para una propiedad existente.</span><span class="sxs-lookup"><span data-stu-id="a7bca-107">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="a7bca-108">¿En el ejemplo siguiente, la `Count` propiedad se agrega a la [System.Array? Displayproperty = Fullname](/dotnet/api/System.Array) tipo.</span><span class="sxs-lookup"><span data-stu-id="a7bca-108">In the following example, the `Count` property is added to the [System.Array?Displayproperty=Fullname](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="a7bca-109">El [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) elemento define la propiedad extendida como una propiedad de alias.</span><span class="sxs-lookup"><span data-stu-id="a7bca-109">The [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element defines the extended property as an alias property.</span></span> <span data-ttu-id="a7bca-110">El [nombre](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento especifica el nuevo nombre.</span><span class="sxs-lookup"><span data-stu-id="a7bca-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the new name.</span></span> <span data-ttu-id="a7bca-111">Y, el [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) elemento especifica la propiedad existente al que hace referencia el alias.</span><span class="sxs-lookup"><span data-stu-id="a7bca-111">And, the [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="a7bca-112">(También puede agregar el [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) elemento a los miembros de la [conjuntos de miembros](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="a7bca-112">(You can also add the [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="a7bca-113">Propiedades de código</span><span class="sxs-lookup"><span data-stu-id="a7bca-113">Code Properties</span></span>

<span data-ttu-id="a7bca-114">Una propiedad de código hace referencia a una propiedad estática de un objeto de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a7bca-114">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="a7bca-115">¿En el ejemplo siguiente, la `Node` propiedad se agrega a la [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) tipo.</span><span class="sxs-lookup"><span data-stu-id="a7bca-115">In the following example, the `Node` property is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="a7bca-116">El [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) elemento define la propiedad extendida como una propiedad de código.</span><span class="sxs-lookup"><span data-stu-id="a7bca-116">The [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element defines the extended property as a code property.</span></span> <span data-ttu-id="a7bca-117">El [nombre](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento especifica el nombre de la propiedad extendida.</span><span class="sxs-lookup"><span data-stu-id="a7bca-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="a7bca-118">Y, el [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) elemento define el método estático al que hace referencia la propiedad extendida.</span><span class="sxs-lookup"><span data-stu-id="a7bca-118">And, the [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="a7bca-119">(También puede agregar el [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) elemento a los miembros de la [conjuntos de miembros](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="a7bca-119">(You can also add the [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="a7bca-120">Propiedades de nota</span><span class="sxs-lookup"><span data-stu-id="a7bca-120">Note Properties</span></span>

<span data-ttu-id="a7bca-121">Una propiedad de nota define una propiedad que tiene un valor estático.</span><span class="sxs-lookup"><span data-stu-id="a7bca-121">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="a7bca-122">¿En el ejemplo siguiente, la `Status` propiedad (cuyo valor siempre es "Correcto") se agrega a la [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) tipo.</span><span class="sxs-lookup"><span data-stu-id="a7bca-122">In the following example, the `Status` property (whose value is always "Success") is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="a7bca-123">El [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elemento define la propiedad extendida como una propiedad de nota; el [nombre](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento especifica el nombre de la propiedad extendida; y la [valor](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) elemento Especifica el valor estático de la propiedad extendida.</span><span class="sxs-lookup"><span data-stu-id="a7bca-123">The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element defines the extended property as a note property; the [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property; and the [Value](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the static value of the extended property.</span></span> <span data-ttu-id="a7bca-124">(El [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elemento también se puede agregar a los miembros de la [conjuntos de miembros](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="a7bca-124">(The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element can also be added to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="a7bca-125">Propiedades de script</span><span class="sxs-lookup"><span data-stu-id="a7bca-125">Script Properties</span></span>

<span data-ttu-id="a7bca-126">Una propiedad de secuencia de comandos define una propiedad cuyo valor es el resultado de una secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="a7bca-126">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="a7bca-127">¿En el ejemplo siguiente, la `VersionInfo` propiedad se agrega a la [System.IO.FileInfo? Displayproperty = Fullname](/dotnet/api/System.IO.FileInfo) tipo.</span><span class="sxs-lookup"><span data-stu-id="a7bca-127">In the following example, the `VersionInfo` property is added to the [System.IO.FileInfo?Displayproperty=Fullname](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="a7bca-128">El [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) elemento define la propiedad extendida como una propiedad de secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="a7bca-128">The [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element defines the extended property as a script property.</span></span> <span data-ttu-id="a7bca-129">El [nombre](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento especifica el nombre de la propiedad extendida.</span><span class="sxs-lookup"><span data-stu-id="a7bca-129">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="a7bca-130">Y, el [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) elemento especifica el script que genera el valor de propiedad.</span><span class="sxs-lookup"><span data-stu-id="a7bca-130">And, the [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the script that generates the property value.</span></span> <span data-ttu-id="a7bca-131">(También puede agregar el [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) elemento a los miembros de la [conjuntos de miembros](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="a7bca-131">(You can also add the [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="a7bca-132">Conjuntos de propiedades</span><span class="sxs-lookup"><span data-stu-id="a7bca-132">Property Sets</span></span>

<span data-ttu-id="a7bca-133">Un conjunto de propiedades define un grupo de propiedades extendidas que se puede hacer referencia por el nombre del conjunto.</span><span class="sxs-lookup"><span data-stu-id="a7bca-133">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="a7bca-134">Por ejemplo, el `Property` parámetro de la [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet puede especificar una propiedad específica establecida en mostrarse.</span><span class="sxs-lookup"><span data-stu-id="a7bca-134">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="a7bca-135">Cuando se especifica un conjunto de propiedades, se muestran solo las propiedades que pertenecen al conjunto.</span><span class="sxs-lookup"><span data-stu-id="a7bca-135">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="a7bca-136">No hay ninguna restricción en el número de conjuntos de propiedades que se pueden definir para un objeto.</span><span class="sxs-lookup"><span data-stu-id="a7bca-136">There is no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="a7bca-137">Sin embargo, se deben especificar los conjuntos de propiedades que se usan para definir las propiedades de presentación predeterminada de un objeto en el conjunto de miembros PSStandardMembers.</span><span class="sxs-lookup"><span data-stu-id="a7bca-137">However, the property sets used to define the default display properties of an object must be specified within the PSStandardMembers member set.</span></span> <span data-ttu-id="a7bca-138">En el archivo Types.ps1xml tipos, los nombres de conjunto de propiedades predeterminada incluyen DefaultDisplayProperty, DefaultDisplayPropertySet y DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="a7bca-138">In the Types.ps1xml types file, the default property set names include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="a7bca-139">Se omiten los conjuntos de propiedades adicionales que agregue al conjunto de miembros PSStandardMembers.</span><span class="sxs-lookup"><span data-stu-id="a7bca-139">Any additional property sets that you add to the PSStandardMembers member set are ignored.</span></span>

<span data-ttu-id="a7bca-140">¿En el ejemplo siguiente, el conjunto de propiedades DefaultDisplayPropertySet se agrega al conjunto de miembros de PSStandardMembers el [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) tipo.</span><span class="sxs-lookup"><span data-stu-id="a7bca-140">In the following example, the DefaultDisplayPropertySet property set is added to the PSStandardMembers member set of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="a7bca-141">El [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) elemento define el grupo de propiedades.</span><span class="sxs-lookup"><span data-stu-id="a7bca-141">The [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element defines the group of properties.</span></span> <span data-ttu-id="a7bca-142">El [nombre](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento especifica el nombre del conjunto de propiedades.</span><span class="sxs-lookup"><span data-stu-id="a7bca-142">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the property set.</span></span> <span data-ttu-id="a7bca-143">Y, el [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) elemento especifica las propiedades del conjunto.</span><span class="sxs-lookup"><span data-stu-id="a7bca-143">And, the [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element specifies the properties of the set.</span></span> <span data-ttu-id="a7bca-144">(También puede agregar el [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) elemento a los miembros de la [tipo](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) elemento.)</span><span class="sxs-lookup"><span data-stu-id="a7bca-144">(You can also add the [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element to the members of the [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a7bca-145">Véase también</span><span class="sxs-lookup"><span data-stu-id="a7bca-145">See Also</span></span>

[<span data-ttu-id="a7bca-146">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a7bca-146">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
