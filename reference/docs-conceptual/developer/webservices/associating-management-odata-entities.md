---
title: Asociar entidades OData de administración | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359814"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="60b04-102">Asociación de las entidades de Management OData</span><span class="sxs-lookup"><span data-stu-id="60b04-102">Associating Management OData Entities</span></span>

<span data-ttu-id="60b04-103">A menudo resulta útil crear una asociación entre dos entidades de OData de administración diferentes.</span><span class="sxs-lookup"><span data-stu-id="60b04-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="60b04-104">Por ejemplo, un servicio de administración de OData podría tener entidades que administren un catálogo de productos organizados en categorías y definir las entidades `Product` y `Category`.</span><span class="sxs-lookup"><span data-stu-id="60b04-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="60b04-105">Al asociar estas dos entidades, un cliente puede obtener información sobre todos los productos de una categoría con una única solicitud al servicio Web.</span><span class="sxs-lookup"><span data-stu-id="60b04-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="60b04-106">Un ejemplo que muestra cómo crear asociaciones entre entidades se puede descargar en el [ejemplo de asociación](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span><span class="sxs-lookup"><span data-stu-id="60b04-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="60b04-107">Crear la asociación en el archivo de esquema de recursos</span><span class="sxs-lookup"><span data-stu-id="60b04-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="60b04-108">El siguiente MOF define dos entidades.</span><span class="sxs-lookup"><span data-stu-id="60b04-108">The following MOF defines two entities.</span></span> <span data-ttu-id="60b04-109">Se creará una asociación entre ellos.</span><span class="sxs-lookup"><span data-stu-id="60b04-109">We will create an association between them.</span></span>

```csharp
class Product {

[key] string ProductName;

// other fields ...
};

class Category {

[key] string CategoryName;

string Products[];

// other fields
}
```

<span data-ttu-id="60b04-110">La clase `Category` define una propiedad que es una matriz de los nombres de los productos que pertenecen a esa categoría.</span><span class="sxs-lookup"><span data-stu-id="60b04-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="60b04-111">Para asociar dos entidades, debe definir una clase con el atributo `Association` en el archivo MOF del esquema de recursos para el servicio.</span><span class="sxs-lookup"><span data-stu-id="60b04-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="60b04-112">La clase debe definir las dos entidades que se van a asociar, llamadas `ends` de la asociación.</span><span class="sxs-lookup"><span data-stu-id="60b04-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="60b04-113">En el ejemplo siguiente se muestra una definición de una clase que define una asociación entre las entidades Category y Products.</span><span class="sxs-lookup"><span data-stu-id="60b04-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="60b04-114">También debe cambiar la declaración de la propiedad Products en la clase Category.</span><span class="sxs-lookup"><span data-stu-id="60b04-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="60b04-115">Use la palabra clave `AssociationClass` para especificar que la propiedad es un extremo de la asociación.</span><span class="sxs-lookup"><span data-stu-id="60b04-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="60b04-116">La propiedad también se debe definir como una referencia a una entidad independiente, en lugar de una matriz de cadenas.</span><span class="sxs-lookup"><span data-stu-id="60b04-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="60b04-117">Para ello, use la palabra clave `ref`.</span><span class="sxs-lookup"><span data-stu-id="60b04-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="60b04-118">En el ejemplo siguiente se muestra la definición de la propiedad para la asociación.</span><span class="sxs-lookup"><span data-stu-id="60b04-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="60b04-119">Por último, debe declarar el otro extremo de la Asociación agregando una definición de propiedad a la clase `Product`.</span><span class="sxs-lookup"><span data-stu-id="60b04-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="60b04-120">Se trata de una referencia a una matriz o a una sola entidad.</span><span class="sxs-lookup"><span data-stu-id="60b04-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="60b04-121">Suponiendo que cada producto pertenece a una sola categoría, la definición sería como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="60b04-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="60b04-122">Las propiedades que representan los dos extremos de la asociación se denominan propiedades de navegación.</span><span class="sxs-lookup"><span data-stu-id="60b04-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="60b04-123">Pasos para asociar entidades en el archivo de esquema de recursos</span><span class="sxs-lookup"><span data-stu-id="60b04-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="60b04-124">Defina la Asociación como una clase mediante la palabra clave `Association`.</span><span class="sxs-lookup"><span data-stu-id="60b04-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="60b04-125">Defina los extremos de la asociación mediante la palabra clave AssociationClass para calificar las propiedades de las entidades asociadas.</span><span class="sxs-lookup"><span data-stu-id="60b04-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="60b04-126">Crear la asociación en el archivo XML de asignación de recursos</span><span class="sxs-lookup"><span data-stu-id="60b04-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="60b04-127">Hay tres casos diferentes que se deben tener en cuenta al asignar una asociación en el archivo XML de asignación de recursos.</span><span class="sxs-lookup"><span data-stu-id="60b04-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="60b04-128">Determinar cómo asociar entidades en el archivo de asignación de recursos</span><span class="sxs-lookup"><span data-stu-id="60b04-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="60b04-129">Si la propiedad de navegación está presente en el subyacente.</span><span class="sxs-lookup"><span data-stu-id="60b04-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="60b04-130">.NET Framework tipo, y esa propiedad contiene claves externas, no es necesario realizar ninguna asignación explícita.</span><span class="sxs-lookup"><span data-stu-id="60b04-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="60b04-131">Si la propiedad de navegación no existe en el tipo de .NET Framework subyacente, debe especificar un cmdlet que recupere la lista de claves de las instancias asociadas.</span><span class="sxs-lookup"><span data-stu-id="60b04-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="60b04-132">Para ello, agregue un elemento `Association` anidado bajo el elemento `CmdletImplementation`, siguiendo los elementos que definen el `cmdlets` para los demás comandos CRUD.</span><span class="sxs-lookup"><span data-stu-id="60b04-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="60b04-133">Si la propiedad de navegación existe en el tipo de .NET Framework subyacente, pero contiene instancias de objeto en lugar de claves externas, debe crear un cmdlet (escribiendo una función o un script de Windows PowerShell) para recuperar las claves externas.</span><span class="sxs-lookup"><span data-stu-id="60b04-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="60b04-134">A continuación, especifique ese cmdlet en el archivo de asignación de recursos.</span><span class="sxs-lookup"><span data-stu-id="60b04-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="60b04-135">Por ejemplo, el script para recuperar las claves tendría un aspecto similar al siguiente.</span><span class="sxs-lookup"><span data-stu-id="60b04-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="60b04-136">Y el código XML del archivo de asignación de recursos tendría el aspecto siguiente.</span><span class="sxs-lookup"><span data-stu-id="60b04-136">And the XML in the resource mapping file would look like the following.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory.ps1</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="60b04-137">Además de especificar un cmdlet para recuperar las entidades asociadas, también puede especificar cmdlets para agregar y quitar referencias de la colección.</span><span class="sxs-lookup"><span data-stu-id="60b04-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="60b04-138">En el ejemplo siguiente se supone que existen los cmdlets Add-ProductToCategory y Remove-ProductFromCategory (también se pueden definir en un script o en una función como en el ejemplo anterior).</span><span class="sxs-lookup"><span data-stu-id="60b04-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

  ```xml
  Class Name="Sample.Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
  ...
              </GetReference>
        <AddReference>
     <CmdletName>"Add-ProductToCategory"</>
     <ParameterForThisObject>"Product"</>
     <ParameterForReferredObject>"Category"</>
        </AddReference>
        <RemoveReference>
     <CmdletName="Remove-ProductFromCategory"/>
     <ParameterForThisObject >"Product"</>
     <ParameterForReferredObject >"Category"</>
        </RemoveReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

## <a name="querying-associated-entities"></a><span data-ttu-id="60b04-139">Consultar entidades asociadas</span><span class="sxs-lookup"><span data-stu-id="60b04-139">Querying associated entities</span></span>

<span data-ttu-id="60b04-140">El cliente puede recuperar una lista de las instancias asociadas a una entidad mediante la creación de consultas específicas.</span><span class="sxs-lookup"><span data-stu-id="60b04-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="60b04-141">Construir consultas para entidades asociadas</span><span class="sxs-lookup"><span data-stu-id="60b04-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="60b04-142">Un cliente puede solicitar los detalles de una categoría sin recuperar sus productos asociados.</span><span class="sxs-lookup"><span data-stu-id="60b04-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="60b04-143">Por ejemplo, la siguiente solicitud obtiene detalles de la categoría `food`.</span><span class="sxs-lookup"><span data-stu-id="60b04-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="60b04-144">Para obtener los productos asociados de la categoría (pero no los detalles de la propia categoría, el cliente especifica la propiedad de navegación en la solicitud.</span><span class="sxs-lookup"><span data-stu-id="60b04-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="60b04-145">Para recuperar solo las direcciones URL de los productos, use el calificador `$links` en la solicitud.</span><span class="sxs-lookup"><span data-stu-id="60b04-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="60b04-146">El cliente puede obtener los detalles de la categoría y sus productos asociados mediante el calificador `$expand`.</span><span class="sxs-lookup"><span data-stu-id="60b04-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="60b04-147">Véase también</span><span class="sxs-lookup"><span data-stu-id="60b04-147">See Also</span></span>

[<span data-ttu-id="60b04-148">Creación de un servicio Web de extensión de IIS Management OData</span><span class="sxs-lookup"><span data-stu-id="60b04-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)