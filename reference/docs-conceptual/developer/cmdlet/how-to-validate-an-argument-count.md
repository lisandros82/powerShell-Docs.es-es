---
title: Cómo validar un recuento de argumentos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365534"
---
# <a name="how-to-validate-an-argument-count"></a>Cómo validar un recuento de argumentos

En este ejemplo se muestra cómo especificar una regla de validación que el tiempo de ejecución de Windows PowerShell puede usar para comprobar el número de argumentos (el recuento) que un parámetro acepta antes de que se ejecute el cmdlet. Esta regla de validación se establece declarando el atributo ValidateCount.

> [!NOTE]
> Para obtener más información sobre la clase que define este atributo, vea [System. Management. Automation. Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>Para validar un recuento de argumentos

- Agregue el atributo Validate tal como se muestra en el código siguiente. En este ejemplo se especifica que el parámetro aceptará un argumento o un máximo de tres argumentos.

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

Para obtener más información sobre cómo declarar este atributo, vea [declaración de atributos ValidateCount](./validatecount-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[Declaración de atributos de ValidateCount](./validatecount-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
