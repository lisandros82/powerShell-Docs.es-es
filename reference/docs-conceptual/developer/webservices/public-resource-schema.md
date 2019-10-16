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
# <a name="public-resource-schema"></a>Esquema de recursos públicos

Management OData usa MOF para definir recursos y sus propiedades. Las propiedades de una entidad de administración de OData corresponden directamente a las propiedades del tipo administrado devuelto por el cmdlet subyacente.

## <a name="defining-a-resource"></a>Definición de un recurso

Cada recurso corresponde a un objeto devuelto por un cmdlet de Windows PowerShell. En el archivo MOF de recursos públicos, se define un recurso mediante la declaración de una clase. La clase consta de las propiedades que corresponden a las propiedades del objeto. Por ejemplo, en el ejemplo siguiente, la clase [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) está representada por el MOF siguiente.

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

Cada nombre de propiedad está precedido por un tipo de datos. Los tipos de datos de este ejemplo se corresponden con los tipos de datos CLR primitivos de .NET Framework, pero las propiedades también pueden ser referencias a otros recursos o tipos complejos, que se describen más adelante.

El calificador `Key` indica que una propiedad se utiliza para identificar de forma única una instancia de recurso. Un recurso puede tener más de una clave.

El calificador `Required` indica que la propiedad es obligatoria. Si una propiedad se etiqueta con el calificador `Key`, se considera necesaria y el calificador `Required` no es necesario.

### <a name="complex-data-types"></a>Tipos de datos complejos

Las propiedades de las entidades pueden tener tipos de datos complejos. Los tipos de datos complejos son tipos que se componen de otros tipos, similares a los Structs del lenguaje de programación C. Un tipo complejo se declara en el archivo MOF como una clase con el calificador `ComplexType`, como en el ejemplo siguiente.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Para declarar una propiedad de entidad como un tipo complejo, se declara como un tipo `string` con el calificador `EmbeddedInstance`, incluido el nombre del tipo complejo. En el ejemplo siguiente se muestra la declaración de una propiedad del tipo `PswsTest_ProcessModule` declarado en el ejemplo anterior.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Asociar entidades

Puede asociar dos entidades mediante los calificadores Association y AssociationClass. Para obtener más información, consulte [asociar entidades de administración de oData](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Tipos derivados

Puede derivar un tipo de otro tipo. El tipo derivado hereda todas las propiedades del tipo del que deriva además de cualquier propiedad derivada explícitamente. En el ejemplo siguiente se muestra una declaración de tipos y, a continuación, una declaración de dos tipos derivados de ese tipo.

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