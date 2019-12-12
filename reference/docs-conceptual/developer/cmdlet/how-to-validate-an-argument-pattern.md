---
title: Cómo validar un patrón de argumentos | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365564"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="687df-102">Cómo validar un patrón de argumentos</span><span class="sxs-lookup"><span data-stu-id="687df-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="687df-103">En este ejemplo se muestra cómo especificar una regla de validación que el tiempo de ejecución de Windows PowerShell puede usar para comprobar el patrón de caracteres del argumento de parámetro antes de que se ejecute el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="687df-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="687df-104">Esta regla de validación se establece declarando el atributo ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="687df-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="687df-105">Para obtener más información sobre la clase que define este atributo, vea [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span><span class="sxs-lookup"><span data-stu-id="687df-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="687df-106">Para validar un patrón de argumentos</span><span class="sxs-lookup"><span data-stu-id="687df-106">To validate an argument pattern</span></span>

- <span data-ttu-id="687df-107">Agregue el atributo Validate tal como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="687df-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="687df-108">Este ejemplo especifica un patrón de cuatro dígitos, donde cada dígito tiene un valor de 0 a 9.</span><span class="sxs-lookup"><span data-stu-id="687df-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

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

<span data-ttu-id="687df-109">Para obtener más información sobre cómo declarar este atributo, vea [declaración de atributos ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="687df-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="687df-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="687df-110">See Also</span></span>

[<span data-ttu-id="687df-111">Declaración de atributos de ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="687df-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="687df-112">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="687df-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
