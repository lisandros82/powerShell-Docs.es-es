---
title: Declaración de atributo ValidateSet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364284"
---
# <a name="validateset-attribute-declaration"></a>Declaración de atributo ValidateSet

El atributo ValidateSetAttribute especifica un conjunto de valores posibles para un argumento de parámetro de cmdlet. Este atributo también se puede usar en las funciones de Windows PowerShell.

Cuando se especifica este atributo, el tiempo de ejecución de Windows PowerShell determina si el argumento proporcionado para el parámetro de cmdlet coincide con un elemento del conjunto de elementos proporcionado. El cmdlet se ejecuta solo si el argumento de parámetro coincide con un elemento del conjunto. Si no se encuentra ninguna coincidencia, el tiempo de ejecución de Windows PowerShell produce un error.

## <a name="syntax"></a>Sintaxis

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Parámetros

`ValidValues` ([System. String](/dotnet/api/System.String)) requerido. Especifica los valores de elemento de parámetro válidos. En el ejemplo siguiente se muestra cómo especificar un elemento o varios elementos.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

parámetro con nombre opcional `IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)). El valor predeterminado de `true` indica que se omite el caso. Un valor de `false` hace que el cmdlet distinga mayúsculas de minúsculas.

## <a name="remarks"></a>Observaciones

- Este atributo solo se puede usar una vez por parámetro.

- Si el valor del parámetro es una matriz, cada elemento de la matriz debe coincidir con un elemento del conjunto de atributos.

- La clase [System. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) define el atributo ValidateSetAttribute.

## <a name="see-also"></a>Véase también

[System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
