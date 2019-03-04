---
title: Cómo validar un argumento de intervalo | Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859741"
---
# <a name="how-to-validate-an-argument-range"></a>Cómo validar un rango de argumentos

En este ejemplo se muestra cómo especificar una regla de validación que puede usar el tiempo de ejecución de Windows PowerShell para comprobar los valores mínimos y máximo del argumento del parámetro antes de ejecuta el cmdlet. Establezca esta regla de validación al declarar el atributo ValidateRange.

> [!NOTE]
> Para obtener más información acerca de la clase que define este atributo, vea [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>Para validar un argumento de intervalo

- Agregue el atributo ValidateRange tal como se muestra en el código siguiente. En este ejemplo se especifica un intervalo de 0 a 5 para el `InputData` parámetro.

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

Para obtener más información acerca de cómo declarar este atributo, vea [ValidateRange la declaración de atributo](./validaterange-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[Declaración de atributo ValidateRange](./validaterange-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
