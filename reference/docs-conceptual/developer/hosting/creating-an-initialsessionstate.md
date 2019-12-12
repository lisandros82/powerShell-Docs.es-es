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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367624"
---
# <a name="creating-an-initialsessionstate"></a>Creación de un InitialSessionState

Los comandos de PowerShell se ejecutan en un espacio de ejecución.
Para hospedar PowerShell en la aplicación, debe crear un objeto [System. Management. Automation. Runspace. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) .
Cada espacio de ejecución tiene un objeto [System. Management. Automation. runspace. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) asociado a él.
InitialSessionState especifica características del espacio de ejecución, como qué comandos, variables y módulos están disponibles para ese espacio de ejecución.

## <a name="create-a-default-initialsessionstate"></a>Crear un InitialSessionState predeterminado

Los métodos [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) y [createdefault2)](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) de la clase **InitialSessionState** se pueden usar para crear un objeto **InitialSessionState** .
El método **CreateDefault** crea una **InitialSessionState** con todos los comandos integrados cargados, mientras que el método **createdefault2)** solo carga los comandos necesarios para hospedar PowerShell (los comandos del módulo Microsoft. PowerShell. Core).

Si desea limitar aún más los comandos disponibles en la aplicación host, debe crear un espacio de ejecución restringido.
Para obtener más información, vea [crear un espacio de ejecución restringido](creating-a-constrained-runspace.md).

En el código siguiente se muestra cómo crear un **InitialSessionState**, asignarlo a un espacio de ejecución, agregar comandos a la canalización en ese espacio de ejecución e invocar los comandos.
Para obtener más información sobre cómo agregar e invocar comandos, vea [Agregar e invocar comandos](adding-and-invoking-commands.md).

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

## <a name="see-also"></a>Véase también

[Crear un espacio de ejecución restringido](creating-a-constrained-runspace.md)

[Agregar e invocar comandos](adding-and-invoking-commands.md)
