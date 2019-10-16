---
title: Crear un InitialSessionState | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 9140d03e046def2fbbcc2a842b9ea1b9e1fa2985
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367624"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="a4672-102">Creación de un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="a4672-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="a4672-103">Los comandos de PowerShell se ejecutan en un espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="a4672-103">PowerShell commands run in a runspace.</span></span>
<span data-ttu-id="a4672-104">Para hospedar PowerShell en la aplicación, debe crear un objeto [System. Management. Automation. Runspace. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) .</span><span class="sxs-lookup"><span data-stu-id="a4672-104">To host PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>
<span data-ttu-id="a4672-105">Cada espacio de ejecución tiene un objeto [System. Management. Automation. runspace. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) asociado a él.</span><span class="sxs-lookup"><span data-stu-id="a4672-105">Every runspace has an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span>
<span data-ttu-id="a4672-106">InitialSessionState especifica características del espacio de ejecución, como qué comandos, variables y módulos están disponibles para ese espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="a4672-106">The InitialSessionState specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="a4672-107">Crear un InitialSessionState predeterminado</span><span class="sxs-lookup"><span data-stu-id="a4672-107">Create a default InitialSessionState</span></span>

<span data-ttu-id="a4672-108">Los métodos [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) y [createdefault2)](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) de la clase **InitialSessionState** se pueden usar para crear un objeto **InitialSessionState** .</span><span class="sxs-lookup"><span data-stu-id="a4672-108">The [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) and [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods of the **InitialSessionState** class can be used to create an **InitialSessionState** object.</span></span>
<span data-ttu-id="a4672-109">El método **CreateDefault** crea una **InitialSessionState** con todos los comandos integrados cargados, mientras que el método **createdefault2)** solo carga los comandos necesarios para hospedar PowerShell (los comandos de la Módulo Microsoft. PowerShell. Core).</span><span class="sxs-lookup"><span data-stu-id="a4672-109">The **CreateDefault** method creates an **InitialSessionState** with all of the built-in commands loaded, while the **CreateDefault2** method loads only the commands required to host PowerShell (the commands from the Microsoft.PowerShell.Core module).</span></span>

<span data-ttu-id="a4672-110">Si desea limitar aún más los comandos disponibles en la aplicación host, debe crear un espacio de ejecución restringido.</span><span class="sxs-lookup"><span data-stu-id="a4672-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span>
<span data-ttu-id="a4672-111">Para obtener más información, vea [crear un espacio de ejecución restringido](creating-a-constrained-runspace.md).</span><span class="sxs-lookup"><span data-stu-id="a4672-111">For information, see [Creating a constrained runspace](creating-a-constrained-runspace.md).</span></span>

<span data-ttu-id="a4672-112">En el código siguiente se muestra cómo crear un **InitialSessionState**, asignarlo a un espacio de ejecución, agregar comandos a la canalización en ese espacio de ejecución e invocar los comandos.</span><span class="sxs-lookup"><span data-stu-id="a4672-112">The following code shows how to create an **InitialSessionState**, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span>
<span data-ttu-id="a4672-113">Para obtener más información sobre cómo agregar e invocar comandos, vea [Agregar e invocar comandos](adding-and-invoking-commands.md).</span><span class="sxs-lookup"><span data-stu-id="a4672-113">For more information about adding and invoking commands, see [Adding and invoking commands](adding-and-invoking-commands.md).</span></span>

```csharp
namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell object,
      // and then specify the runspace and commands to the pipeline.
      // and create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
      foreach (PSObject result in ps.Invoke())
      {
        Console.WriteLine("{0,-20}{1}",
            result.Members["Name"].Value,
            result.Members["Value"].Value);
      } // End foreach.

      // Close the runspace to free resources.
      rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a><span data-ttu-id="a4672-114">Véase también</span><span class="sxs-lookup"><span data-stu-id="a4672-114">See Also</span></span>

[<span data-ttu-id="a4672-115">Crear un espacio de ejecución restringido</span><span class="sxs-lookup"><span data-stu-id="a4672-115">Creating a constrained runspace</span></span>](creating-a-constrained-runspace.md)

[<span data-ttu-id="a4672-116">Agregar e invocar comandos</span><span class="sxs-lookup"><span data-stu-id="a4672-116">Adding and invoking commands</span></span>](adding-and-invoking-commands.md)
