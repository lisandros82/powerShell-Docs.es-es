---
title: Cómo validar un número de argumentos | Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859141"
---
# <a name="how-to-validate-an-argument-count"></a>Cómo validar un recuento de argumentos

En este ejemplo se muestra cómo especificar una regla de validación que puede usar el tiempo de ejecución de Windows PowerShell para comprobar el número de argumentos (el recuento) que acepta un parámetro antes de ejecuta el cmdlet. Establezca esta regla de validación al declarar el atributo ValidateCount.

> [!NOTE]
> Para obtener más información acerca de la clase que define este atributo, vea [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>Para validar un número de argumentos

- Agregue el atributo de validación tal como se muestra en el código siguiente. Este ejemplo especifica que el parámetro aceptará un argumento o hasta tres argumentos.

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

Para obtener más información acerca de cómo declarar este atributo, vea [ValidateCount la declaración de atributo](./validatecount-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[Declaración de atributo ValidateCount](./validatecount-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
