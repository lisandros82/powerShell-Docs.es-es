---
title: Validar la entrada del parámetro | Microsoft Docs
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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858851"
---
# <a name="validating-parameter-input"></a>Validación de la entrada de parámetros

Windows PowerShell puede validar los argumentos pasados a los parámetros de cmdlet de varias maneras. Windows PowerShell puede validar la longitud, el intervalo y el patrón de los caracteres del argumento. Puede validar el número de argumentos disponibles (el recuento). Estas reglas de validación se definen mediante atributos de validación que se declaran con el atributo de parámetro en las propiedades públicas de la clase del cmdlet.

Para validar un argumento de parámetro, el tiempo de ejecución de Windows PowerShell usa la información proporcionada por los atributos de validación para confirmar el valor del parámetro antes de ejecuta el cmdlet. Si la entrada de parámetro no es válida, el usuario recibe un mensaje de error. Cada parámetro de validación define una regla de validación que se aplica mediante Windows PowerShell.

Windows PowerShell aplica las reglas de validación en función de los siguientes atributos.

ValidateCount especifica el número mínimo y máximo de argumentos que puede aceptar un parámetro. Para obtener más información sobre la sintaxis que se utiliza para declarar este atributo, vea [ValidateCount la declaración de atributo](./validatecount-attribute-declaration.md).

ValidateLength especifica el número mínimo y máximo de caracteres en el argumento del parámetro. Para obtener más información sobre la sintaxis que se utiliza para declarar este atributo, vea [declaración de atributo ValidateLength](./validatelength-attribute-declaration.md).

ValidatePattern especifica una expresión regular que valide el argumento del parámetro. Para obtener más información sobre la sintaxis que se utiliza para declarar este atributo, vea [ValidatePattern la declaración de atributo](./validatepattern-attribute-declaration.md).

ValidateRange especifica los valores mínimos y máximo del argumento del parámetro. Para obtener más información sobre la sintaxis que se utiliza para declarar este atributo, vea [ValidateRange la declaración de atributo](./validaterange-attribute-declaration.md).

ValidateSet especifica los valores válidos para el argumento del parámetro. Para obtener más información sobre la sintaxis que se utiliza para declarar este atributo, vea [ValidateSet la declaración de atributo](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[Cómo validar entrada de parámetros](./how-to-validate-parameter-input.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
