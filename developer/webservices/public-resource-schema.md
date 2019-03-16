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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057253"
---
# <a name="public-resource-schema"></a>Esquema de recursos públicos

IIS Management OData utiliza MOF para definir los recursos y sus propiedades. Las propiedades de una entidad de administración OData corresponden directamente a las propiedades del tipo administrado que se devuelve mediante el cmdlet subyacente.

## <a name="defining-a-resource"></a>Definir un recurso

Cada recurso corresponde a un objeto devuelto por un cmdlet de Windows PowerShell. En el archivo MOF de recurso público, definir un recurso mediante la declaración de una clase. La clase tiene propiedades que corresponden a las propiedades del objeto. Por ejemplo, en el ejemplo siguiente, la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) clase está representada por el siguiente MOF.

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

Cada nombre de propiedad está precedido por un tipo de datos. Los tipos de datos en este ejemplo se corresponden con los tipos de datos primitivos de CLR en las versiones de .NET Framework, pero las propiedades también pueden ser referencias a otros recursos o tipos complejos, que son ambos se describen más adelante.

El `Key` calificador indica que una propiedad se utiliza para identificar de forma exclusiva una instancia de recursos. Un recurso puede tener más de una clave.

El `Required` calificador indica que la propiedad es obligatoria. Si una propiedad se etiqueta con el `Key` calificador, se considera que es requerida y el `Required` calificador no es necesario.

### <a name="complex-data-types"></a>Tipos de datos complejos

Las propiedades de entidades pueden tener tipos de datos complejos. Tipos de datos complejos son tipos que están formados por otros tipos, similares a las estructuras en el lenguaje de programación de C. Un tipo complejo se declara en el archivo MOF como una clase con el `ComplexType` calificador, como en el ejemplo siguiente.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Para declarar una propiedad de entidad como un tipo complejo, se declara como un `string` tipo con el `EmbeddedInstance` calificador, incluido el nombre del tipo complejo. El ejemplo siguiente muestra la declaración de una propiedad de la `PswsTest_ProcessModule` tipo declarado en el ejemplo anterior.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Asociación de entidades

Puede asociar dos entidades mediante los calificadores de asociación y AssociationClass. Para obtener más información, consulte [asociar entidades de OData Management](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Tipos derivados

Puede derivar un tipo de otro tipo. El tipo derivado hereda todas las propiedades del tipo del que se deriva además de cualquier propiedad derivada explícitamente. El ejemplo siguiente muestra una declaración de tipo y, a continuación, en una declaración de dos tipos derivados de ese tipo.

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