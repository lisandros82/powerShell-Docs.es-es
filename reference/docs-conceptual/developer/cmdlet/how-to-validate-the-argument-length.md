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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365494"
---
# <a name="how-to-validate-the-argument-length"></a>Cómo validar la longitud del argumento

En este ejemplo se muestra cómo especificar una regla de validación que el tiempo de ejecución de Windows PowerShell puede usar para comprobar el número de caracteres (longitud) del argumento de parámetro antes de que se ejecute el cmdlet. Esta regla de validación se establece declarando el atributo ValidateLength.

> [!NOTE]
> Para obtener más información sobre la clase que define este atributo, vea [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).

## <a name="to-validate-the-argument-length"></a>Para validar la longitud del argumento

- Agregue el atributo Validate tal como se muestra en el código siguiente. Este ejemplo especifica que la longitud del argumento debe tener una longitud de 0 a 10 caracteres.

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

Para obtener más información sobre cómo declarar este atributo, vea [declaración de atributos ValidateLength](./validatelength-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[Declaración de atributos de ValidateLength](./validatelength-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
