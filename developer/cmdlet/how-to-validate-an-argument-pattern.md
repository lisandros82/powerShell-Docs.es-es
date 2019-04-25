---
title: Cómo validar un patrón de argumento | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067780"
---
# <a name="how-to-validate-an-argument-pattern"></a>Cómo validar un patrón de argumentos

En este ejemplo se muestra cómo especificar una regla de validación que puede usar el tiempo de ejecución de Windows PowerShell para comprobar el patrón de caracteres del argumento del parámetro antes de ejecuta el cmdlet. Establezca esta regla de validación al declarar el atributo ValidatePattern.

> [!NOTE]
> Para obtener más información acerca de la clase que define este atributo, vea [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>Para validar un patrón de argumento

- Agregue el atributo de validación tal como se muestra en el código siguiente. En este ejemplo se especifica un patrón de cuatro dígitos, donde cada dígito tiene un valor de 0 a 9.

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

Para obtener más información acerca de cómo declarar este atributo, vea [ValidatePattern la declaración de atributo](./validatepattern-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[Declaración de atributo ValidatePattern](./validatepattern-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
