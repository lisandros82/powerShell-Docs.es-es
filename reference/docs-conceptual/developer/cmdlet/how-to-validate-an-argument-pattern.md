---
title: Cómo validar un patrón de argumentos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365564"
---
# <a name="how-to-validate-an-argument-pattern"></a>Cómo validar un patrón de argumentos

En este ejemplo se muestra cómo especificar una regla de validación que el tiempo de ejecución de Windows PowerShell puede usar para comprobar el patrón de caracteres del argumento de parámetro antes de que se ejecute el cmdlet. Esta regla de validación se establece declarando el atributo ValidatePattern.

> [!NOTE]
> Para obtener más información sobre la clase que define este atributo, vea [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>Para validar un patrón de argumentos

- Agregue el atributo Validate tal como se muestra en el código siguiente. Este ejemplo especifica un patrón de cuatro dígitos, donde cada dígito tiene un valor de 0 a 9.

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

Para obtener más información sobre cómo declarar este atributo, vea [declaración de atributos ValidatePattern](./validatepattern-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[Declaración de atributos de ValidatePattern](./validatepattern-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
