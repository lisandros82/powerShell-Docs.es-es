---
title: Declaración de atributo ValidatePattern | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369164"
---
# <a name="validatepattern-attribute-declaration"></a>Declaración de atributo ValidatePattern

El atributo ValidatePattern especifica un patrón de expresión regular que valida el argumento de un parámetro de cmdlet. Este atributo también se puede usar en las funciones de Windows PowerShell.

Cuando se invoca ValidatePattern dentro de un cmdlet, el tiempo de ejecución de Windows PowerShell convierte el argumento del parámetro de cmdlet en una cadena y, a continuación, compara esa cadena con el patrón proporcionado por el atributo ValidatePattern. El cmdlet se ejecuta solo si la representación de cadena convertida del argumento y el patrón proporcionado coinciden. Si no coinciden, el tiempo de ejecución de Windows PowerShell produce un error.

## <a name="syntax"></a>Sintaxis

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Parámetros

`RegexString` ([System. String](/dotnet/api/System.String)) requerido. Especifica una expresión regular que valida el argumento del parámetro.

Options ([System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) opcional parámetro con nombre. Especifica una combinación bit a bit de las marcas [System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) que especifican las opciones de expresión regular.

## <a name="remarks"></a>Observaciones

- Este atributo solo se puede usar una vez por parámetro.

- Puede usar el parámetro `Option` del atributo para definir más el patrón. Por ejemplo, puede hacer que el patrón distinga mayúsculas de minúsculas.

- Si este atributo se aplica a una colección, cada elemento de la colección debe coincidir con el patrón.

- La clase [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) define el atributo ValidatePattern.

## <a name="see-also"></a>Véase también

[System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
