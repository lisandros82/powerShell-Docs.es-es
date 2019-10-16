---
title: Declaración de atributo ValidateCount | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369234"
---
# <a name="validatecount-attribute-declaration"></a>Declaración de atributo ValidateCount

El atributo ValidateCount especifica el número mínimo y máximo de argumentos permitidos para un parámetro de cmdlet.

## <a name="syntax"></a>Sintaxis

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parámetros

se requiere `MinLength` ([System. Int32][]). Especifica el número mínimo de argumentos.

se requiere `MaxLength` ([System. Int32][]). Especifica el número máximo de argumentos.

## <a name="remarks"></a>Observaciones

- Para obtener más información sobre cómo declarar este atributo, vea [cómo validar un número de argumentos][].

- Cuando no se invoca este atributo, el parámetro de cmdlet correspondiente puede tener cualquier número de argumentos.

- El tiempo de ejecución de Windows PowerShell genera un error en las siguientes condiciones:

    - Los parámetros de atributo `MinLength` y `MaxLength` no son del tipo [System. Int32][].

    - El valor del parámetro del atributo `MaxLength` es menor que el valor del parámetro del atributo `MinLength`.

- La clase [System. Management. Automation. ValidateCountAttribute][] define el atributo ValidateCount.

## <a name="see-also"></a>Véase también

[System. Management. Automation. ValidateCountAttribute][]

[Cómo validar un número de argumentos][]

[Escribir un cmdlet de Windows PowerShell][]

[Cómo validar un número de argumentos]: how-to-validate-an-argument-count.md
[Escribir un cmdlet de Windows PowerShell]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
