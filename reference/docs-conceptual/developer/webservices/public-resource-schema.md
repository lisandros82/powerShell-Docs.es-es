---
title: Esquema de recursos público | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366274"
---
# <a name="public-resource-schema"></a><span data-ttu-id="0fbbd-102">Esquema de recursos públicos</span><span class="sxs-lookup"><span data-stu-id="0fbbd-102">Public Resource Schema</span></span>

<span data-ttu-id="0fbbd-103">Management OData usa MOF para definir recursos y sus propiedades.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="0fbbd-104">Las propiedades de una entidad de administración de OData corresponden directamente a las propiedades del tipo administrado devuelto por el cmdlet subyacente.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="0fbbd-105">Definición de un recurso</span><span class="sxs-lookup"><span data-stu-id="0fbbd-105">Defining a resource</span></span>

<span data-ttu-id="0fbbd-106">Cada recurso corresponde a un objeto devuelto por un cmdlet de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="0fbbd-107">En el archivo MOF de recursos públicos, se define un recurso mediante la declaración de una clase.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="0fbbd-108">La clase consta de las propiedades que corresponden a las propiedades del objeto.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="0fbbd-109">Por ejemplo, en el ejemplo siguiente, la clase [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) está representada por el MOF siguiente.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

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

<span data-ttu-id="0fbbd-110">Cada nombre de propiedad está precedido por un tipo de datos.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="0fbbd-111">Los tipos de datos de este ejemplo se corresponden con los tipos de datos CLR primitivos de .NET Framework, pero las propiedades también pueden ser referencias a otros recursos o tipos complejos, que se describen más adelante.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="0fbbd-112">El calificador `Key` indica que una propiedad se utiliza para identificar de forma única una instancia de recurso.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="0fbbd-113">Un recurso puede tener más de una clave.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-113">A resource can have more than one key.</span></span>

<span data-ttu-id="0fbbd-114">El calificador `Required` indica que la propiedad es obligatoria.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="0fbbd-115">Si una propiedad se etiqueta con el calificador `Key`, se considera necesaria y el calificador `Required` no es necesario.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="0fbbd-116">Tipos de datos complejos</span><span class="sxs-lookup"><span data-stu-id="0fbbd-116">Complex data types</span></span>

<span data-ttu-id="0fbbd-117">Las propiedades de las entidades pueden tener tipos de datos complejos.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="0fbbd-118">Los tipos de datos complejos son tipos que se componen de otros tipos, similares a los Structs del lenguaje de programación C.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="0fbbd-119">Un tipo complejo se declara en el archivo MOF como una clase con el calificador `ComplexType`, como en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="0fbbd-120">Para declarar una propiedad de entidad como un tipo complejo, se declara como un tipo `string` con el calificador `EmbeddedInstance`, incluido el nombre del tipo complejo.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="0fbbd-121">En el ejemplo siguiente se muestra la declaración de una propiedad del tipo `PswsTest_ProcessModule` declarado en el ejemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="0fbbd-122">Asociar entidades</span><span class="sxs-lookup"><span data-stu-id="0fbbd-122">Associating entities</span></span>

<span data-ttu-id="0fbbd-123">Puede asociar dos entidades mediante los calificadores Association y AssociationClass.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="0fbbd-124">Para obtener más información, consulte [asociar entidades de administración de oData](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="0fbbd-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="0fbbd-125">Tipos derivados</span><span class="sxs-lookup"><span data-stu-id="0fbbd-125">Derived types</span></span>

<span data-ttu-id="0fbbd-126">Puede derivar un tipo de otro tipo.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-126">You can derive a type from another type.</span></span> <span data-ttu-id="0fbbd-127">El tipo derivado hereda todas las propiedades del tipo del que deriva además de cualquier propiedad derivada explícitamente.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="0fbbd-128">En el ejemplo siguiente se muestra una declaración de tipos y, a continuación, una declaración de dos tipos derivados de ese tipo.</span><span class="sxs-lookup"><span data-stu-id="0fbbd-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

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