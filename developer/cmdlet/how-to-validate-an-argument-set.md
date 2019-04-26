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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067727"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="81efc-102">Cómo validar un conjunto de argumentos</span><span class="sxs-lookup"><span data-stu-id="81efc-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="81efc-103">En este ejemplo se muestra cómo especificar una regla de validación que puede usar el tiempo de ejecución de Windows PowerShell para comprobar el argumento del parámetro antes de ejecuta el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="81efc-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="81efc-104">Esta regla de validación proporciona un conjunto de los valores válidos para el argumento del parámetro.</span><span class="sxs-lookup"><span data-stu-id="81efc-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="81efc-105">Para obtener más información acerca de la clase que define este atributo, vea [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="81efc-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="81efc-106">Para validar un conjunto de argumentos</span><span class="sxs-lookup"><span data-stu-id="81efc-106">To validate an argument set</span></span>

- <span data-ttu-id="81efc-107">Agregue el atributo ValidateSet tal como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="81efc-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="81efc-108">En este ejemplo se especifica un conjunto de tres valores posibles para el `UserName` parámetro.</span><span class="sxs-lookup"><span data-stu-id="81efc-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="81efc-109">Para obtener más información acerca de cómo declarar este atributo, vea [ValidateSet la declaración de atributo](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="81efc-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="81efc-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="81efc-110">See Also</span></span>

[<span data-ttu-id="81efc-111">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="81efc-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="81efc-112">Declaración de atributo ValidateSet</span><span class="sxs-lookup"><span data-stu-id="81efc-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="81efc-113">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="81efc-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
