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
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="43e45-102">Cómo validar la longitud del argumento</span><span class="sxs-lookup"><span data-stu-id="43e45-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="43e45-103">En este ejemplo se muestra cómo especificar una regla de validación que el tiempo de ejecución de Windows PowerShell puede usar para comprobar el número de caracteres (longitud) del argumento de parámetro antes de que se ejecute el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="43e45-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="43e45-104">Esta regla de validación se establece declarando el atributo ValidateLength.</span><span class="sxs-lookup"><span data-stu-id="43e45-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="43e45-105">Para obtener más información sobre la clase que define este atributo, vea [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span><span class="sxs-lookup"><span data-stu-id="43e45-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="43e45-106">Para validar la longitud del argumento</span><span class="sxs-lookup"><span data-stu-id="43e45-106">To validate the argument length</span></span>

- <span data-ttu-id="43e45-107">Agregue el atributo Validate tal como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="43e45-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="43e45-108">Este ejemplo especifica que la longitud del argumento debe tener una longitud de 0 a 10 caracteres.</span><span class="sxs-lookup"><span data-stu-id="43e45-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="43e45-109">Para obtener más información sobre cómo declarar este atributo, vea [declaración de atributos ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="43e45-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43e45-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="43e45-110">See Also</span></span>

[<span data-ttu-id="43e45-111">Declaración de atributos de ValidateLength</span><span class="sxs-lookup"><span data-stu-id="43e45-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="43e45-112">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="43e45-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
