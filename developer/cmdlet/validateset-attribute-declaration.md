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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861211"
---
# <a name="validateset-attribute-declaration"></a>Declaración de atributo ValidateSet

El atributo ValidateSetAttribute especifica un conjunto de valores posibles para un argumento de parámetro de cmdlet. Este atributo también se puede usar las funciones de Windows PowerShell.

Cuando se especifica este atributo, el tiempo de ejecución de Windows PowerShell determina si el argumento proporcionado para el parámetro de cmdlet coincide con un elemento en el conjunto de elemento proporcionada. El cmdlet se ejecuta solo si el argumento del parámetro coincide con un elemento del conjunto. Si no se encuentra ninguna coincidencia, se produce un error por el tiempo de ejecución de Windows PowerShell.

## <a name="syntax"></a>Sintaxis

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Parámetros

`ValidValues` ([System.String](/dotnet/api/System.String)) necesarios. Especifica los valores de elemento de parámetro válido. El ejemplo siguiente muestra cómo especificar un elemento o varios elementos.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) con el nombre de parámetro opcional. El valor predeterminado de `true` indica que las mayúsculas y minúsculas se ignoran. Un valor de `false` hace que el cmdlet que distingue mayúsculas de minúsculas.

## <a name="remarks"></a>Observaciones

- Este atributo se puede usar una sola vez por cada parámetro.

- Si el valor del parámetro es una matriz, cada elemento de la matriz debe coincidir con un elemento del conjunto de atributos.

- El atributo ValidateSetAttribute está definido por el [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) clase.

## <a name="see-also"></a>Véase también

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
