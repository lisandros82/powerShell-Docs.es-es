---
title: Declaración de atributo de parámetro | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365364"
---
# <a name="parameter-attribute-declaration"></a>Declaración de atributo de parámetro

El atributo Parameter identifica una propiedad pública de la clase cmdlet como un parámetro de cmdlet.

## <a name="syntax"></a>Sintaxis

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parámetros

parámetro con nombre opcional `Mandatory` ([System. Boolean](/dotnet/api/System.Boolean)). `True` indica que se requiere el parámetro del cmdlet. Si no se proporciona un parámetro necesario cuando se invoca el cmdlet, Windows PowerShell solicita al usuario un valor de parámetro. El valor predeterminado es `false`.

parámetro con nombre opcional `ParameterSetName` ([System. String](/dotnet/api/System.String)). Especifica el conjunto de parámetros al que pertenece este parámetro de cmdlet. Si no se especifica ningún conjunto de parámetros, el parámetro pertenece a todos los conjuntos de parámetros.

parámetro con nombre opcional `Position` ([System. Int32](/dotnet/api/System.Int32)). Especifica la posición del parámetro en un comando de Windows PowerShell.

parámetro con nombre opcional `ValueFromPipeline` ([System. Boolean](/dotnet/api/System.Boolean)). `True` indica que el parámetro del cmdlet toma su valor de un objeto de canalización. Especifique esta palabra clave si el cmdlet tiene acceso al objeto completo, no solo a una propiedad del objeto. El valor predeterminado es `false`.

parámetro con nombre opcional `ValueFromPipelineByPropertyName` ([System. Boolean](/dotnet/api/System.Boolean)). `True` indica que el parámetro del cmdlet toma su valor de una propiedad de un objeto de canalización que tiene el mismo nombre o el mismo alias que este parámetro. Por ejemplo, si el cmdlet tiene un parámetro `Name` y el objeto de canalización también tiene una propiedad `Name`, el valor de la propiedad `Name` se asigna al parámetro `Name` del cmdlet. El valor predeterminado es `false`.

parámetro con nombre opcional `ValueFromRemainingArguments` ([System. Boolean](/dotnet/api/System.Boolean)). `True` indica que el parámetro del cmdlet acepta todos los argumentos restantes que se pasan al cmdlet. El valor predeterminado es `false`.

`HelpMessage` parámetro con nombre opcional. Especifica una breve descripción del parámetro. Windows PowerShell muestra este mensaje cuando se ejecuta un cmdlet y no se especifica un parámetro obligatorio.

`HelpMessageBaseName` parámetro con nombre opcional. Especifica la ubicación donde residen los identificadores de recursos. Por ejemplo, este parámetro puede especificar un ensamblado de recursos que contiene los mensajes de ayuda que desea localizar.

`HelpMessageResourceId` parámetro con nombre opcional. Especifica el identificador de recurso de un mensaje de ayuda.

## <a name="remarks"></a>Observaciones

- Para obtener más información sobre cómo declarar este atributo, vea [cómo declarar parámetros de cmdlet](./how-to-declare-cmdlet-parameters.md).

- Un cmdlet puede tener cualquier número de parámetros. Sin embargo, para una mejor experiencia de usuario, limite el número de parámetros.

- Los parámetros se deben declarar en campos o propiedades públicos no estáticos. Los parámetros se deben declarar en las propiedades. La propiedad debe tener un descriptor de acceso set público y, si se especifica la palabra clave `ValueFromPipeline` o `ValueFromPipelineByPropertyName`, la propiedad debe tener un descriptor de acceso get público.

- Al especificar parámetros posicionales, limite el número de parámetros posicionales en un parámetro establecido en un valor inferior a cinco. Y, los parámetros posicionales no tienen que ser contiguos. Las posiciones 5, 100 y 250 funcionan igual que las posiciones 0, 1 y 2.

- Cuando no se especifica la palabra clave `Position`, se debe hacer referencia al parámetro del cmdlet por su nombre.

- Cuando use conjuntos de parámetros, tenga en cuenta lo siguiente:

    - Cada conjunto de parámetros debe tener al menos un parámetro único. Un buen diseño de cmdlet indica que este parámetro único también debe ser obligatorio si es posible. Si el cmdlet está diseñado para ejecutarse sin parámetros, el parámetro único no puede ser obligatorio.

    - Ningún conjunto de parámetros debe contener más de un parámetro posicional con la misma posición.

    - Solo un parámetro de un conjunto de parámetros debe declarar `ValueFromPipeline = true`. Varios parámetros pueden definir `ValueFromPipelineByPropertyName = true`.

    - Varios parámetros pueden definir `ValueFromPipelineByPropertyName = true`.

- Para obtener más información sobre las directrices para los nombres de parámetro, consulte [nombres de parámetros de cmdlet](standard-cmdlet-parameter-names-and-types.md).

- El atributo Parameter se define mediante la clase [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .

## <a name="see-also"></a>Véase también

[System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Nombres de parámetros de cmdlet](standard-cmdlet-parameter-names-and-types.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
