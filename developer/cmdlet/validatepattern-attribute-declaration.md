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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858881"
---
# <a name="validatepattern-attribute-declaration"></a>Declaración de atributo ValidatePattern

El atributo ValidatePattern especifica un patrón de expresión regular que valide el argumento de un parámetro de cmdlet. Este atributo también se puede usar las funciones de Windows PowerShell.

Cuando se invoca ValidatePattern dentro de un cmdlet, el tiempo de ejecución de Windows PowerShell convierte el argumento del parámetro de cmdlet en una cadena y, a continuación, compara dicha cadena en el patrón proporcionado por el atributo ValidatePattern. El cmdlet se ejecuta solo si coincide con la representación de cadena convertida del argumento y el patrón proporcionado. Si no coinciden, se produce un error por el tiempo de ejecución de Windows PowerShell.

## <a name="syntax"></a>Sintaxis

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Parámetros

`RegexString` ([System.String](/dotnet/api/System.String)) necesarios. Especifica una expresión regular que valide el argumento del parámetro.

Opciones ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) con el nombre de parámetro opcional. Especifica una combinación bit a bit de [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) marcadores que especifican opciones de expresiones regulares.

## <a name="remarks"></a>Observaciones

- Este atributo se puede usar una sola vez por cada parámetro.

- Puede usar el `Option` parámetro del atributo para definir el modelo. Por ejemplo, puede hacer que el modelo distingue mayúsculas de minúsculas.

- Si este atributo se aplica a una colección, cada elemento de la colección debe coincidir con el patrón.

- El atributo ValidatePattern está definido por el [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) clase.

## <a name="see-also"></a>Véase también

[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
