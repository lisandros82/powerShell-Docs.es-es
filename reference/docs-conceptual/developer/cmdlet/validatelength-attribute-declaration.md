---
title: Declaración de atributo ValidateLength | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369184"
---
# <a name="validatelength-attribute-declaration"></a>Declaración de atributo ValidateLength

El atributo ValidateLength especifica el número mínimo y máximo de caracteres para un argumento de parámetro de cmdlet. Este atributo también se puede usar en las funciones de Windows PowerShell.

## <a name="syntax"></a>Sintaxis

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parámetros

se requiere `MinLength` ([System. Int32](/dotnet/api/System.Int32)). Especifica el número mínimo de caracteres permitidos.

se requiere `MaxLength` ([System. Int32](/dotnet/api/System.Int32)). Especifica el número máximo de caracteres permitidos.

## <a name="remarks"></a>Observaciones

- Para obtener más información sobre cómo declarar este atributo, vea [cómo declarar reglas de validación de entrada](./how-to-validate-parameter-input.md).

- Cuando no se utiliza este atributo, el argumento de parámetro correspondiente puede tener cualquier longitud.

- El tiempo de ejecución de Windows PowerShell genera un error en las siguientes condiciones:

    - Cuando el valor del parámetro del atributo `MaxLength` es menor que el valor del parámetro del atributo `MinLength`.

    - Cuando el parámetro del atributo `MaxLength` está establecido en 0.

    - Cuando el argumento no es una cadena.

- La clase [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) define el atributo ValidateLength.

## <a name="see-also"></a>Véase también

[System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
