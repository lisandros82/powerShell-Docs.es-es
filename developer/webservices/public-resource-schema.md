---
title: Esquema de recursos públicos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080584"
---
# <a name="public-resource-schema"></a><span data-ttu-id="71b12-102">Esquema de recursos públicos</span><span class="sxs-lookup"><span data-stu-id="71b12-102">Public Resource Schema</span></span>

<span data-ttu-id="71b12-103">IIS Management OData utiliza MOF para definir los recursos y sus propiedades.</span><span class="sxs-lookup"><span data-stu-id="71b12-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="71b12-104">Las propiedades de una entidad de administración OData corresponden directamente a las propiedades del tipo administrado que se devuelve mediante el cmdlet subyacente.</span><span class="sxs-lookup"><span data-stu-id="71b12-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="71b12-105">Definir un recurso</span><span class="sxs-lookup"><span data-stu-id="71b12-105">Defining a resource</span></span>

<span data-ttu-id="71b12-106">Cada recurso corresponde a un objeto devuelto por un cmdlet de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71b12-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="71b12-107">En el archivo MOF de recurso público, definir un recurso mediante la declaración de una clase.</span><span class="sxs-lookup"><span data-stu-id="71b12-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="71b12-108">La clase tiene propiedades que corresponden a las propiedades del objeto.</span><span class="sxs-lookup"><span data-stu-id="71b12-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="71b12-109">Por ejemplo, en el ejemplo siguiente, la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) clase está representada por el siguiente MOF.</span><span class="sxs-lookup"><span data-stu-id="71b12-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

<span data-ttu-id="71b12-110">Cada nombre de propiedad está precedido por un tipo de datos.</span><span class="sxs-lookup"><span data-stu-id="71b12-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="71b12-111">Los tipos de datos en este ejemplo se corresponden con los tipos de datos primitivos de CLR en las versiones de .NET Framework, pero las propiedades también pueden ser referencias a otros recursos o tipos complejos, que son ambos se describen más adelante.</span><span class="sxs-lookup"><span data-stu-id="71b12-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="71b12-112">El `Key` calificador indica que una propiedad se utiliza para identificar de forma exclusiva una instancia de recursos.</span><span class="sxs-lookup"><span data-stu-id="71b12-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="71b12-113">Un recurso puede tener más de una clave.</span><span class="sxs-lookup"><span data-stu-id="71b12-113">A resource can have more than one key.</span></span>

<span data-ttu-id="71b12-114">El `Required` calificador indica que la propiedad es obligatoria.</span><span class="sxs-lookup"><span data-stu-id="71b12-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="71b12-115">Si una propiedad se etiqueta con el `Key` calificador, se considera que es requerida y el `Required` calificador no es necesario.</span><span class="sxs-lookup"><span data-stu-id="71b12-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="71b12-116">Tipos de datos complejos</span><span class="sxs-lookup"><span data-stu-id="71b12-116">Complex data types</span></span>

<span data-ttu-id="71b12-117">Las propiedades de entidades pueden tener tipos de datos complejos.</span><span class="sxs-lookup"><span data-stu-id="71b12-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="71b12-118">Tipos de datos complejos son tipos que están formados por otros tipos, similares a las estructuras en el lenguaje de programación de C.</span><span class="sxs-lookup"><span data-stu-id="71b12-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="71b12-119">Un tipo complejo se declara en el archivo MOF como una clase con el `ComplexType` calificador, como en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="71b12-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="71b12-120">Para declarar una propiedad de entidad como un tipo complejo, se declara como un `string` tipo con el `EmbeddedInstance` calificador, incluido el nombre del tipo complejo.</span><span class="sxs-lookup"><span data-stu-id="71b12-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="71b12-121">El ejemplo siguiente muestra la declaración de una propiedad de la `PswsTest_ProcessModule` tipo declarado en el ejemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="71b12-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="71b12-122">Asociación de entidades</span><span class="sxs-lookup"><span data-stu-id="71b12-122">Associating entities</span></span>

<span data-ttu-id="71b12-123">Puede asociar dos entidades mediante los calificadores de asociación y AssociationClass.</span><span class="sxs-lookup"><span data-stu-id="71b12-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="71b12-124">Para obtener más información, consulte [asociar entidades de OData Management](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="71b12-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="71b12-125">Tipos derivados</span><span class="sxs-lookup"><span data-stu-id="71b12-125">Derived types</span></span>

<span data-ttu-id="71b12-126">Puede derivar un tipo de otro tipo.</span><span class="sxs-lookup"><span data-stu-id="71b12-126">You can derive a type from another type.</span></span> <span data-ttu-id="71b12-127">El tipo derivado hereda todas las propiedades del tipo del que se deriva además de cualquier propiedad derivada explícitamente.</span><span class="sxs-lookup"><span data-stu-id="71b12-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="71b12-128">El ejemplo siguiente muestra una declaración de tipo y, a continuación, en una declaración de dos tipos derivados de ese tipo.</span><span class="sxs-lookup"><span data-stu-id="71b12-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

```csharp
Class Product {

    [Key] String ProductName;

};

Class DairyProduct : Product {

    Uint16 PercentFat;
};
Class POPProduct : Product {

    Boolean IsCarbonated;
};
```