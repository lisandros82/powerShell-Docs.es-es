---
title: Validando entrada de parámetro | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363514"
---
# <a name="validating-parameter-input"></a>Validación de la entrada de parámetros

PowerShell puede validar los argumentos que se pasan a los parámetros de cmdlet de varias maneras.
PowerShell puede validar la longitud, el intervalo y el patrón de los caracteres del argumento.
Puede validar el número de argumentos disponibles (el recuento).
Estas reglas de validación se definen mediante atributos de validación que se declaran con el atributo Parameter en las propiedades públicas de la clase cmdlet.

Para validar un argumento de parámetro, el tiempo de ejecución de PowerShell usa la información proporcionada por los atributos de validación para confirmar el valor del parámetro antes de que se ejecute el cmdlet.
Si la entrada del parámetro no es válida, el usuario recibe un mensaje de error.
Cada parámetro de validación define una regla de validación que se aplica mediante PowerShell.

PowerShell aplica las reglas de validación en función de los siguientes atributos.

### <a name="validatecount"></a>ValidateCount

Especifica el número mínimo y máximo de argumentos que puede aceptar un parámetro.
Para obtener más información, vea [declaración de atributos de ValidateCount](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Especifica el número mínimo y máximo de caracteres en el argumento de parámetro.
Para obtener más información, vea [declaración de atributos de ValidateLength](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Especifica una expresión regular que valida el argumento del parámetro.
Para obtener más información, vea [declaración de atributos de ValidatePattern](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Especifica los valores mínimo y máximo del argumento de parámetro.
Para obtener más información, vea [declaración de atributos de ValidateRange](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Especifica los valores válidos para el argumento del parámetro.
Para obtener más información, vea [declaración de atributos de ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[Cómo validar la entrada de parámetros](./how-to-validate-parameter-input.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
