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
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="233fa-102">Cómo validar un conjunto de argumentos</span><span class="sxs-lookup"><span data-stu-id="233fa-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="233fa-103">En este ejemplo se muestra cómo especificar una regla de validación que el tiempo de ejecución de Windows PowerShell puede usar para comprobar el argumento de parámetro antes de que se ejecute el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="233fa-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="233fa-104">Esta regla de validación proporciona un conjunto de valores válidos para el argumento de parámetro.</span><span class="sxs-lookup"><span data-stu-id="233fa-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="233fa-105">Para obtener más información sobre la clase que define este atributo, vea [System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="233fa-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="233fa-106">Para validar un conjunto de argumentos</span><span class="sxs-lookup"><span data-stu-id="233fa-106">To validate an argument set</span></span>

- <span data-ttu-id="233fa-107">Agregue el atributo ValidateSet como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="233fa-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="233fa-108">Este ejemplo especifica un conjunto de tres valores posibles para el parámetro `UserName`.</span><span class="sxs-lookup"><span data-stu-id="233fa-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="233fa-109">Para obtener más información sobre cómo declarar este atributo, vea [declaración de atributos ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="233fa-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="233fa-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="233fa-110">See Also</span></span>

[<span data-ttu-id="233fa-111">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="233fa-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="233fa-112">Declaración de atributos de ValidateSet</span><span class="sxs-lookup"><span data-stu-id="233fa-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="233fa-113">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="233fa-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
