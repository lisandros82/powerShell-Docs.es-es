---
title: Cómo validar un argumento de intervalo | Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859741"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="63394-102">Cómo validar un rango de argumentos</span><span class="sxs-lookup"><span data-stu-id="63394-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="63394-103">En este ejemplo se muestra cómo especificar una regla de validación que puede usar el tiempo de ejecución de Windows PowerShell para comprobar los valores mínimos y máximo del argumento del parámetro antes de ejecuta el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="63394-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="63394-104">Establezca esta regla de validación al declarar el atributo ValidateRange.</span><span class="sxs-lookup"><span data-stu-id="63394-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="63394-105">Para obtener más información acerca de la clase que define este atributo, vea [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="63394-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="63394-106">Para validar un argumento de intervalo</span><span class="sxs-lookup"><span data-stu-id="63394-106">To validate an argument range</span></span>

- <span data-ttu-id="63394-107">Agregue el atributo ValidateRange tal como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="63394-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="63394-108">En este ejemplo se especifica un intervalo de 0 a 5 para el `InputData` parámetro.</span><span class="sxs-lookup"><span data-stu-id="63394-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="63394-109">Para obtener más información acerca de cómo declarar este atributo, vea [ValidateRange la declaración de atributo](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="63394-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63394-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="63394-110">See Also</span></span>

[<span data-ttu-id="63394-111">Declaración de atributo ValidateRange</span><span class="sxs-lookup"><span data-stu-id="63394-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="63394-112">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="63394-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
