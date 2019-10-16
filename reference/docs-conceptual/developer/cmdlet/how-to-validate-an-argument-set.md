---
title: Cómo validar un conjunto de argumentos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365514"
---
# <a name="how-to-validate-an-argument-set"></a>Cómo validar un conjunto de argumentos

En este ejemplo se muestra cómo especificar una regla de validación que el tiempo de ejecución de Windows PowerShell puede usar para comprobar el argumento de parámetro antes de que se ejecute el cmdlet. Esta regla de validación proporciona un conjunto de valores válidos para el argumento de parámetro.

> [!NOTE]
> Para obtener más información sobre la clase que define este atributo, vea [System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).

## <a name="to-validate-an-argument-set"></a>Para validar un conjunto de argumentos

- Agregue el atributo ValidateSet como se muestra en el código siguiente. Este ejemplo especifica un conjunto de tres valores posibles para el parámetro `UserName`.

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

Para obtener más información sobre cómo declarar este atributo, vea [declaración de atributos ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Declaración de atributos de ValidateSet](./validateset-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
