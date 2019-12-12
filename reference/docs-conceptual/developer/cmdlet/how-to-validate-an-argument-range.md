---
title: Cómo validar un intervalo de argumentos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365524"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="a7c0a-102">Cómo validar un rango de argumentos</span><span class="sxs-lookup"><span data-stu-id="a7c0a-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="a7c0a-103">En este ejemplo se muestra cómo especificar una regla de validación que el tiempo de ejecución de Windows PowerShell puede usar para comprobar los valores mínimo y máximo del argumento de parámetro antes de que se ejecute el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7c0a-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="a7c0a-104">Esta regla de validación se establece declarando el atributo ValidateRange.</span><span class="sxs-lookup"><span data-stu-id="a7c0a-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="a7c0a-105">Para obtener más información sobre la clase que define este atributo, vea [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="a7c0a-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="a7c0a-106">Para validar un intervalo de argumentos</span><span class="sxs-lookup"><span data-stu-id="a7c0a-106">To validate an argument range</span></span>

- <span data-ttu-id="a7c0a-107">Agregue el atributo ValidateRange como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="a7c0a-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="a7c0a-108">Este ejemplo especifica un intervalo de 0 a 5 para el parámetro `InputData`.</span><span class="sxs-lookup"><span data-stu-id="a7c0a-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

<span data-ttu-id="a7c0a-109">Para obtener más información sobre cómo declarar este atributo, vea [declaración de atributos ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a7c0a-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a7c0a-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="a7c0a-110">See Also</span></span>

[<span data-ttu-id="a7c0a-111">Declaración de atributos de ValidateRange</span><span class="sxs-lookup"><span data-stu-id="a7c0a-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="a7c0a-112">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a7c0a-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
