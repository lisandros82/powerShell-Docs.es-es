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
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: 10c347a8c3dcbf8962295601834f5ba85342a87b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "56863621"
---
# <a name="parameter-attribute-declaration"></a>Declaración de atributo de parámetro

El atributo de parámetro identifica una propiedad pública de la clase de cmdlet como un parámetro de cmdlet.

## <a name="syntax"></a>Sintaxis

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parámetros

`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) con el nombre de parámetro opcional. `True` indica que el parámetro de cmdlet es necesario. Si no se proporciona un parámetro obligatorio cuando se invoca el cmdlet, Windows PowerShell solicita al usuario para un valor de parámetro. El valor predeterminado es `false`.

`ParameterSetName` ([System.String](/dotnet/api/System.String)) con el nombre de parámetro opcional. Especifica que el parámetro establecido que pertenece este parámetro de cmdlet. Si no se especifica ningún conjunto de parámetros, el parámetro pertenece a todos los conjuntos de parámetros.

`Position` ([System.Integer](/dotnet/api/System.Integer)) con el nombre de parámetro opcional. Especifica la posición del parámetro dentro de un comando de Windows PowerShell.

`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) con el nombre de parámetro opcional. `True` indica que el parámetro de cmdlet toma su valor de un objeto de canalización. Especifique esta palabra clave si el cmdlet obtiene acceso a la completa de objetos, no solo una propiedad del objeto. El valor predeterminado es `false`.

`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) con el nombre de parámetro opcional. `True` indica que el parámetro de cmdlet toma su valor de una propiedad de un objeto de canalización que tiene el mismo nombre o el mismo alias como este parámetro. Por ejemplo, si el cmdlet tiene un `Name` parámetro y el objeto de canalización también tiene un `Name` propiedad, el valor de la `Name` propiedad se asigna a la `Name` parámetro del cmdlet. El valor predeterminado es `false`.

`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) con el nombre de parámetro opcional. `True` indica que el parámetro de cmdlet acepta todos los argumentos restantes que se pasan al cmdlet. El valor predeterminado es `false`.

`HelpMessage` Parámetro con nombre opcional. Especifica una breve descripción del parámetro. Windows PowerShell muestra este mensaje cuando se ejecuta un cmdlet y no se especifica un parámetro obligatorio.

`HelpMessageBaseName` Parámetro con nombre opcional. Especifica la ubicación donde residen los identificadores de recursos. Por ejemplo, este parámetro podría especificar un ensamblado de recursos que contiene mensajes de ayuda que desee localizar.

`HelpMessageResourceId` Parámetro con nombre opcional. Especifica el identificador de recurso para un mensaje de ayuda.

## <a name="remarks"></a>Observaciones

- Para obtener más información acerca de cómo declarar este atributo, vea [cómo declarar los parámetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).

- Un cmdlet puede tener cualquier número de parámetros. Sin embargo, para una mejor experiencia de usuario, limite el número de parámetros.

- Parámetros se deben declarar en los campos no estáticos públicos o propiedades. Se deben declarar como parámetros en Propiedades. La propiedad debe tener un descriptor de acceso set público y si el `ValueFromPipeline` o `ValueFromPipelineByPropertyName` se especifica la palabra clave, la propiedad debe tener un descriptor de acceso get público.

- Cuando se especifican parámetros posicionales, limitar el número de parámetros posicionales en un parámetro establecido en menos de cinco. Y los parámetros posicionales no tiene que ser contiguas. Las posiciones 5, 100 y 250 funcionan igual que las posiciones 0, 1 y 2.

- Cuando el `Position` palabra clave no se especifica, el parámetro de cmdlet debe hacer referencia a su nombre.

- Al usar conjuntos de parámetros, tenga en cuenta lo siguiente:

    - Cada conjunto de parámetros debe tener al menos un parámetro único. Cmdlet de buen diseño indica que este parámetro único también debería obligatorio si es posible. Si el cmdlet está diseñado para ejecutarse sin parámetros, el único parámetro no puede ser obligatorio.

    - Ningún conjunto de parámetros debe contener más de un parámetro de posición con la misma posición.

    - Solo un parámetro en un conjunto de parámetros debe declarar `ValueFromPipeline = true`. Pueden definir varios parámetros `ValueFromPipelineByPropertyName = true`.

    - Pueden definir varios parámetros `ValueFromPipelineByPropertyName = true`.

- Para obtener más información sobre las directrices para los nombres de parámetros, vea [los nombres de parámetro de Cmdlet](standard-cmdlet-parameter-names-and-types.md).

- El atributo de parámetro está definido por el [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) clase.

## <a name="see-also"></a>Véase también

[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Nombres de parámetro de cmdlet](standard-cmdlet-parameter-names-and-types.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
