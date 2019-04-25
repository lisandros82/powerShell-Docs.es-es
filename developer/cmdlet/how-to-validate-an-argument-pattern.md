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
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="ab0ee-102">Cómo validar un patrón de argumentos</span><span class="sxs-lookup"><span data-stu-id="ab0ee-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="ab0ee-103">En este ejemplo se muestra cómo especificar una regla de validación que puede usar el tiempo de ejecución de Windows PowerShell para comprobar el patrón de caracteres del argumento del parámetro antes de ejecuta el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab0ee-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="ab0ee-104">Establezca esta regla de validación al declarar el atributo ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="ab0ee-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="ab0ee-105">Para obtener más información acerca de la clase que define este atributo, vea [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span><span class="sxs-lookup"><span data-stu-id="ab0ee-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="ab0ee-106">Para validar un patrón de argumento</span><span class="sxs-lookup"><span data-stu-id="ab0ee-106">To validate an argument pattern</span></span>

- <span data-ttu-id="ab0ee-107">Agregue el atributo de validación tal como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="ab0ee-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="ab0ee-108">En este ejemplo se especifica un patrón de cuatro dígitos, donde cada dígito tiene un valor de 0 a 9.</span><span class="sxs-lookup"><span data-stu-id="ab0ee-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

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

<span data-ttu-id="ab0ee-109">Para obtener más información acerca de cómo declarar este atributo, vea [ValidatePattern la declaración de atributo](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ab0ee-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab0ee-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="ab0ee-110">See Also</span></span>

[<span data-ttu-id="ab0ee-111">Declaración de atributo ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="ab0ee-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="ab0ee-112">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab0ee-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
