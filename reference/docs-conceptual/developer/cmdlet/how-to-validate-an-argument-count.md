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
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="29f4c-102">Cómo validar un recuento de argumentos</span><span class="sxs-lookup"><span data-stu-id="29f4c-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="29f4c-103">En este ejemplo se muestra cómo especificar una regla de validación que el tiempo de ejecución de Windows PowerShell puede usar para comprobar el número de argumentos (el recuento) que un parámetro acepta antes de que se ejecute el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29f4c-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="29f4c-104">Esta regla de validación se establece declarando el atributo ValidateCount.</span><span class="sxs-lookup"><span data-stu-id="29f4c-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="29f4c-105">Para obtener más información sobre la clase que define este atributo, vea [System. Management. Automation. Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span><span class="sxs-lookup"><span data-stu-id="29f4c-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="29f4c-106">Para validar un recuento de argumentos</span><span class="sxs-lookup"><span data-stu-id="29f4c-106">To validate an argument count</span></span>

- <span data-ttu-id="29f4c-107">Agregue el atributo Validate tal como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="29f4c-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="29f4c-108">En este ejemplo se especifica que el parámetro aceptará un argumento o un máximo de tres argumentos.</span><span class="sxs-lookup"><span data-stu-id="29f4c-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

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

<span data-ttu-id="29f4c-109">Para obtener más información sobre cómo declarar este atributo, vea [declaración de atributos ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="29f4c-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29f4c-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="29f4c-110">See Also</span></span>

[<span data-ttu-id="29f4c-111">Declaración de atributos de ValidateCount</span><span class="sxs-lookup"><span data-stu-id="29f4c-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="29f4c-112">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="29f4c-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
