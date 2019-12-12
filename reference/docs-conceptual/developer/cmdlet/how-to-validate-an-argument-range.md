---
title: Cómo validar un intervalo de argumentos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365524"
---
# <a name="how-to-validate-an-argument-range"></a>Cómo validar un rango de argumentos

En este ejemplo se muestra cómo especificar una regla de validación que el tiempo de ejecución de Windows PowerShell puede usar para comprobar los valores mínimo y máximo del argumento de parámetro antes de que se ejecute el cmdlet. Esta regla de validación se establece declarando el atributo ValidateRange.

> [!NOTE]
> Para obtener más información sobre la clase que define este atributo, vea [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>Para validar un intervalo de argumentos

- Agregue el atributo ValidateRange como se muestra en el código siguiente. Este ejemplo especifica un intervalo de 0 a 5 para el parámetro `InputData`.

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

Para obtener más información sobre cómo declarar este atributo, vea [declaración de atributos ValidateRange](./validaterange-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[Declaración de atributos de ValidateRange](./validaterange-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
