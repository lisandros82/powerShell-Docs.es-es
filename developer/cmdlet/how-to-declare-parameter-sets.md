---
title: Cómo declarar los conjuntos de parámetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859701"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="92b7f-102">Cómo declarar los conjuntos de parámetros</span><span class="sxs-lookup"><span data-stu-id="92b7f-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="92b7f-103">En este ejemplo se muestra cómo se definen dos conjuntos de parámetros al declarar los parámetros para un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="92b7f-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="92b7f-104">Cada conjunto de parámetros tiene un parámetro único y un parámetro compartido que está usando ambos conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="92b7f-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="92b7f-105">Para obtener más información acerca de los conjuntos de parámetros, incluida la forma de especificar el conjunto de parámetros predeterminados, consulte [conjuntos de parámetros de Cmdlet](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="92b7f-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="92b7f-106">Siempre que sea posible, defina el parámetro unique de un parámetro establecido como un parámetro necesario.</span><span class="sxs-lookup"><span data-stu-id="92b7f-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="92b7f-107">Sin embargo, si desea que el cmdlet se ejecuten sin especificar ningún parámetro, el único parámetro puede ser un parámetro opcional.</span><span class="sxs-lookup"><span data-stu-id="92b7f-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="92b7f-108">Por ejemplo, el parámetro unique de la `Get-Command` cmdlet es opcional.</span><span class="sxs-lookup"><span data-stu-id="92b7f-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="92b7f-109">Cómo se definen dos conjuntos de parámetros</span><span class="sxs-lookup"><span data-stu-id="92b7f-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="92b7f-110">Agregar el `ParameterSet` palabra clave para el atributo de parámetro para el parámetro único del primer conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="92b7f-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. <span data-ttu-id="92b7f-111">Agregar el `ParameterSet` palabra clave para el atributo de parámetro para el parámetro único del segundo conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="92b7f-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. <span data-ttu-id="92b7f-112">Para el parámetro al que pertenece a ambos conjuntos de parámetros, agregue un atributo de parámetro para cada conjunto de parámetros y, a continuación, agregue el `ParameterSet` palabra clave para cada conjunto.</span><span class="sxs-lookup"><span data-stu-id="92b7f-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="92b7f-113">En cada atributo de parámetro, puede especificar cómo se define ese parámetro.</span><span class="sxs-lookup"><span data-stu-id="92b7f-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="92b7f-114">Puede ser un parámetro opcional en un conjunto y obligatoria en otro.</span><span class="sxs-lookup"><span data-stu-id="92b7f-114">A parameter can be optional in one set and mandatory in another.</span></span>

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a><span data-ttu-id="92b7f-115">Véase también</span><span class="sxs-lookup"><span data-stu-id="92b7f-115">See Also</span></span>

[<span data-ttu-id="92b7f-116">Conjuntos de parámetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="92b7f-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="92b7f-117">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="92b7f-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)