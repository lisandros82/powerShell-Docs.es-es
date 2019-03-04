---
title: Creación de un InitialSessionState | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: c23640b69d1e71a343e2bef2c6b3f8ffe19826d7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855691"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="0a000-102">Creación de un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="0a000-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="0a000-103">Ejecutan los comandos de Windows PowerShell en un espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="0a000-103">Windows PowerShell commands run in a runspace.</span></span> <span data-ttu-id="0a000-104">Para hospedar Windows PowerShell en la aplicación, debe crear un [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) objeto.</span><span class="sxs-lookup"><span data-stu-id="0a000-104">To host Windows PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span> <span data-ttu-id="0a000-105">Cada espacio de ejecución tiene un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto asociado a él.</span><span class="sxs-lookup"><span data-stu-id="0a000-105">Every runspace has an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span> <span data-ttu-id="0a000-106">El [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) especifica las características del espacio de ejecución, por ejemplo, qué módulos, variables y comandos están disponibles para ese espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="0a000-106">The [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="0a000-107">Crear un valor predeterminado InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="0a000-107">Create a default InitialSessionState</span></span>

 <span data-ttu-id="0a000-108">El [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)y [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) pueden usarse métodos Para crear [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objetos.</span><span class="sxs-lookup"><span data-stu-id="0a000-108">The [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)and [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods can be used to create [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objects.</span></span> <span data-ttu-id="0a000-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) crea un InitialSessionState con todos los comandos integrados cargado al [ System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) carga únicamente los comandos necesarios para el host de Windows PowerShell (los comandos desde el módulo Microsoft.PowerShell.Core.</span><span class="sxs-lookup"><span data-stu-id="0a000-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) creates an InitialSessionState with all of the built-in commands loaded, while [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) loads only the commands required to host Windows PowerShell (the commands from the Microsoft.PowerShell.Core module.</span></span>

 <span data-ttu-id="0a000-110">Si desea limitar aún más los comandos disponibles en la aplicación host necesita crear un espacio de ejecución restringido.</span><span class="sxs-lookup"><span data-stu-id="0a000-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span> <span data-ttu-id="0a000-111">Para obtener información, vea Crear un espacio de ejecución restringido.</span><span class="sxs-lookup"><span data-stu-id="0a000-111">For information, see Creating a constrained runspace.</span></span>

 <span data-ttu-id="0a000-112">El código siguiente muestra cómo crear un InitialSessionState, asignarla a un espacio de ejecución, agregar comandos a la canalización en ese espacio de ejecución e invocar los comandos.</span><span class="sxs-lookup"><span data-stu-id="0a000-112">The following code shows how to create an InitialSessionState, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span> <span data-ttu-id="0a000-113">Para obtener más información sobre cómo agregar e invocar comandos, vea Agregar e invocar comandos.</span><span class="sxs-lookup"><span data-stu-id="0a000-113">For more information about adding and invoking commands, see Adding and invoking commands.</span></span>

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
      // Call the InitailSessionState.CreateDefault method to create
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

      // Call the PowerShell.Create() method to create the PowerShell
      // object,and then specify the runspace and commands to the pipeline.
      // and  create the command pipeline.
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

## <a name="see-also"></a><span data-ttu-id="0a000-114">Véase también</span><span class="sxs-lookup"><span data-stu-id="0a000-114">See Also</span></span>

 [<span data-ttu-id="0a000-115">Creación de un espacio de ejecución restringida</span><span class="sxs-lookup"><span data-stu-id="0a000-115">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
