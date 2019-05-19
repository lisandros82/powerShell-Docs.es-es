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
ms.openlocfilehash: 4d3cdccc0fe3e24b1221e41beef4821b613aab93
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855162"
---
# <a name="validatelength-attribute-declaration"></a>Declaración de atributo ValidateLength

El atributo ValidateLength especifica el número mínimo y máximo de caracteres para un argumento de parámetro de cmdlet. Este atributo también se puede usar las funciones de Windows PowerShell.

## <a name="syntax"></a>Sintaxis

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parámetros

`MinLength` ([System.Integer](/dotnet/api/System.Integer)) necesarios. Especifica el número mínimo de caracteres permitidos.

`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) necesarios. Especifica el número máximo de caracteres permitidos.

## <a name="remarks"></a>Observaciones

- Para obtener más información acerca de cómo declarar este atributo, vea [cómo declarar las reglas de validación de entrada](./how-to-validate-parameter-input.md).

- Cuando no se usa este atributo, el argumento correspondiente del parámetro puede tener cualquier longitud.

- El tiempo de ejecución de Windows PowerShell, produce un error en las siguientes condiciones:

    - Cuando el valor de la `MaxLength` parámetro de atributo es menor que el valor de la `MinLength` parámetro de atributo.

    - Cuando el `MaxLength` parámetro de atributo se establece en 0.

    - Cuando el argumento no es una cadena.

- El atributo ValidateLength está definido por el [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) clase.

## <a name="see-also"></a>Véase también

[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
