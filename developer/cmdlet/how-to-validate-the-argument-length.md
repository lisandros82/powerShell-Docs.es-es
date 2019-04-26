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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067726"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="3721b-102">Cómo validar la longitud del argumento</span><span class="sxs-lookup"><span data-stu-id="3721b-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="3721b-103">En este ejemplo se muestra cómo especificar una regla de validación que puede usar el tiempo de ejecución de Windows PowerShell para comprobar el número de caracteres (longitud) del argumento del parámetro antes de ejecuta el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3721b-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="3721b-104">Establezca esta regla de validación al declarar el atributo ValidateLength.</span><span class="sxs-lookup"><span data-stu-id="3721b-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="3721b-105">Para obtener más información acerca de la clase que define este atributo, vea [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span><span class="sxs-lookup"><span data-stu-id="3721b-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="3721b-106">Para validar la longitud del argumento</span><span class="sxs-lookup"><span data-stu-id="3721b-106">To validate the argument length</span></span>

- <span data-ttu-id="3721b-107">Agregue el atributo de validación tal como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="3721b-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="3721b-108">En este ejemplo especifica que la longitud del argumento debe tener una longitud de 0 a 10 caracteres.</span><span class="sxs-lookup"><span data-stu-id="3721b-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="3721b-109">Para obtener más información acerca de cómo declarar este atributo, vea [declaración de atributo ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="3721b-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3721b-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="3721b-110">See Also</span></span>

[<span data-ttu-id="3721b-111">Declaración de atributo ValidateLength</span><span class="sxs-lookup"><span data-stu-id="3721b-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="3721b-112">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3721b-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
