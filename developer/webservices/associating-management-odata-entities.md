---
title: Asociar las entidades de OData de administración | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860831"
---
# <a name="associating-management-odata-entities"></a>Asociación de las entidades de Management OData

A menudo resulta útil crear una asociación entre dos entidades de OData de administración diferentes. Por ejemplo, un servicio OData de administración podría tener entidades que administran un catálogo de productos que se organizan en categorías y definir las entidades `Product` y `Category`. Al asociar estas dos entidades, un cliente puede obtener información acerca de todos los productos en una categoría con una única solicitud al servicio web.

Se puede descargar un ejemplo que muestra cómo crear asociaciones entre entidades en [ejemplo asociación](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>Creación de la asociación en el archivo de esquema de recursos

El MOF siguiente define dos entidades. Se creará una asociación entre ellos.

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

La `Category` clase define una propiedad que es una matriz de los nombres de los productos que pertenecen a esa categoría.

Para asociar dos entidades, debe definir una clase con el `Association` atributo del archivo de recursos esquema MOF para el servicio. La clase debe definir las dos entidades asociadas, llamado `ends` de la asociación. El ejemplo siguiente muestra una definición de una clase que define una asociación entre las entidades productos y categoría.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

También debe cambiar la declaración de la propiedad Products de la clase de categoría. Usa el `AssociationClass` palabra clave para especificar que la propiedad es un extremo de la asociación. La propiedad también se debe definir como una referencia a una entidad independiente, en lugar de una matriz de cadenas. Para ello, uso el `ref` palabra clave. El ejemplo siguiente muestra la definición de propiedad para la asociación.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Por último, debe declarar el otro extremo de la asociación mediante la adición de una definición de propiedad para el `Product` clase. Se trata de una referencia a una matriz o a una sola entidad. Suponiendo que cada producto pertenece únicamente a una categoría, la definición sería como sigue.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

Las propiedades que representan los dos extremos de la asociación se denominan propiedades de navegación.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Pasos para asociar las entidades en el archivo de esquema de recursos

- Definir la asociación como una clase mediante el `Association` palabra clave.

- Definir los extremos de la asociación con la palabra clave AssociationClass para calificar las propiedades de las entidades asociadas.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Creación de la asociación en el archivo XML de asignación de recursos

Existen tres casos diferentes que tener en cuenta al asignar una asociación en el archivo XML de asignación de recursos.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Determinación de cómo asociar entidades en el archivo de asignación de recursos

- Si la propiedad de navegación está presente en subyacente. Tipo de .NET framework y esa propiedad contiene las claves externas, no es necesaria ninguna asignación explícita.

- Si la propiedad de navegación no existe en el tipo subyacente de .NET Framework, debe especificar un cmdlet que recupera la lista de claves de las instancias asociadas. Hacer esto agregando un `Association` elemento anidado en el `CmdletImplementation` elemento, siguiendo los elementos que definen el `cmdlets` para los demás comandos CRUD.

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

- Si existe la propiedad de navegación en el tipo subyacente de .NET Framework, pero contiene las instancias de objeto en lugar de las claves externas, debe crear un cmdlet (escribiendo una función de Windows PowerShell o la secuencia de comandos) para recuperar las claves externas. A continuación, especificará ese cmdlet en el archivo de asignación de recursos. Por ejemplo, la secuencia de comandos para recuperar las claves tendría un aspecto similar al siguiente.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  Y tendría un aspecto similar al siguiente XML en el archivo de asignación de recursos.

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

- Además de especificar un cmdlet para recuperar las entidades asociadas, también puede especificar los cmdlets de para agregar y quitar las referencias de la colección. El siguiente ejemplo se supone que existen los cmdlets Add-ProductToCategory y Remove-ProductFromCategory (también pueden definirse en un script o una función del ejemplo anterior).

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

## <a name="querying-associated-entities"></a>Consultar entidades asociadas

El cliente puede recuperar una lista de las instancias asociadas a una entidad mediante la creación de consultas específicas.

#### <a name="constructing-queries-for-associated-entities"></a>Construir consultas para las entidades asociadas

- Un cliente puede solicitar los detalles de una categoría sin tener que recuperar sus productos asociados. Por ejemplo, la siguiente solicitud obtiene detalles de la `food` categoría.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Para obtener los productos de la categoría asociados (pero no los detalles de la categoría, el cliente especifica la propiedad de navegación en la solicitud.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Para recuperar únicamente las direcciones URL de los productos, utilice el `$links` calificador en la solicitud.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- El cliente puede obtener los detalles de la categoría y sus productos asociados con el `$expand` calificador.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Véase también

[Creación de un servicio Web de administración IIS OData extensión](./creating-a-management-odata-web-service.md)