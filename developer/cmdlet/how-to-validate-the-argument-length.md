---
title: Cómo validar la longitud del argumento | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857131"
---
# <a name="how-to-validate-the-argument-length"></a>Cómo validar la longitud del argumento

En este ejemplo se muestra cómo especificar una regla de validación que puede usar el tiempo de ejecución de Windows PowerShell para comprobar el número de caracteres (longitud) del argumento del parámetro antes de ejecuta el cmdlet. Establezca esta regla de validación al declarar el atributo ValidateLength.

> [!NOTE]
> Para obtener más información acerca de la clase que define este atributo, vea [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).

## <a name="to-validate-the-argument-length"></a>Para validar la longitud del argumento

- Agregue el atributo de validación tal como se muestra en el código siguiente. En este ejemplo especifica que la longitud del argumento debe tener una longitud de 0 a 10 caracteres.

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Para obtener más información acerca de cómo declarar este atributo, vea [declaración de atributo ValidateLength](./validatelength-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[Declaración de atributo ValidateLength](./validatelength-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
