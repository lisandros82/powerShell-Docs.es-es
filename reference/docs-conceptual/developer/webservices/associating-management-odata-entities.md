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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359814"
---
# <a name="associating-management-odata-entities"></a>Asociación de las entidades de Management OData

A menudo resulta útil crear una asociación entre dos entidades de OData de administración diferentes. Por ejemplo, un servicio de administración de OData podría tener entidades que administren un catálogo de productos organizados en categorías y definir las entidades `Product` y `Category`. Al asociar estas dos entidades, un cliente puede obtener información sobre todos los productos de una categoría con una única solicitud al servicio Web.

Un ejemplo que muestra cómo crear asociaciones entre entidades se puede descargar en el [ejemplo de asociación](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>Crear la asociación en el archivo de esquema de recursos

El siguiente MOF define dos entidades. Se creará una asociación entre ellos.

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

La clase `Category` define una propiedad que es una matriz de los nombres de los productos que pertenecen a esa categoría.

Para asociar dos entidades, debe definir una clase con el `Association` atributo en el archivo MOF del esquema de recursos para el servicio. La clase debe definir las dos entidades que se van a asociar, llamadas `ends` de la asociación. En el ejemplo siguiente se muestra una definición de una clase que define una asociación entre las entidades Category y Products.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

También debe cambiar la declaración de la propiedad Products en la clase Category. La palabra clave `AssociationClass` se usa para especificar que la propiedad es un extremo de la asociación. La propiedad también se debe definir como una referencia a una entidad independiente, en lugar de una matriz de cadenas. Para ello, use la palabra clave `ref`. En el ejemplo siguiente se muestra la definición de la propiedad para la asociación.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Por último, debe declarar el otro extremo de la Asociación agregando una definición de propiedad a la clase `Product`. Se trata de una referencia a una matriz o a una sola entidad. Suponiendo que cada producto pertenece a una sola categoría, la definición sería como se indica a continuación.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

Las propiedades que representan los dos extremos de la asociación se denominan propiedades de navegación.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Pasos para asociar entidades en el archivo de esquema de recursos

- Defina la Asociación como una clase mediante la palabra clave `Association`.

- Defina los extremos de la asociación mediante la palabra clave AssociationClass para calificar las propiedades de las entidades asociadas.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Crear la asociación en el archivo XML de asignación de recursos

Hay tres casos diferentes que se deben tener en cuenta al asignar una asociación en el archivo XML de asignación de recursos.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Determinar cómo asociar entidades en el archivo de asignación de recursos

- Si la propiedad de navegación está presente en el subyacente. .NET Framework tipo, y esa propiedad contiene claves externas, no es necesario realizar ninguna asignación explícita.

- Si la propiedad de navegación no existe en el tipo de .NET Framework subyacente, debe especificar un cmdlet que recupere la lista de claves de las instancias asociadas. Para ello, agregue un elemento `Association` anidado bajo el elemento `CmdletImplementation`, siguiendo los elementos que definen los `cmdlets` para los demás comandos CRUD.

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

- Si la propiedad de navegación existe en el tipo de .NET Framework subyacente, pero contiene instancias de objeto en lugar de claves externas, debe crear un cmdlet (escribiendo una función o un script de Windows PowerShell) para recuperar las claves externas. A continuación, especifique ese cmdlet en el archivo de asignación de recursos. Por ejemplo, el script para recuperar las claves tendría un aspecto similar al siguiente.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  Y el código XML del archivo de asignación de recursos tendría el aspecto siguiente.

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

- Además de especificar un cmdlet para recuperar las entidades asociadas, también puede especificar cmdlets para agregar y quitar referencias de la colección. En el ejemplo siguiente se supone que existen los cmdlets Add-ProductToCategory y Remove-ProductFromCategory (también se pueden definir en un script o en una función como en el ejemplo anterior).

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

#### <a name="constructing-queries-for-associated-entities"></a>Construir consultas para entidades asociadas

- Un cliente puede solicitar los detalles de una categoría sin recuperar sus productos asociados. Por ejemplo, la siguiente solicitud obtiene detalles de la categoría `food`.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Para obtener los productos asociados de la categoría (pero no los detalles de la propia categoría, el cliente especifica la propiedad de navegación en la solicitud.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Para recuperar solo las direcciones URL de los productos, use el calificador `$links` en la solicitud.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- El cliente puede obtener los detalles de la categoría y sus productos asociados mediante el calificador `$expand`.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Véase también

[Creación de un servicio Web de extensión de IIS Management OData](./creating-a-management-odata-web-service.md)