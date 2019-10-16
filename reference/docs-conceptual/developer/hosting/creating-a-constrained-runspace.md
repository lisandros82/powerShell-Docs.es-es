---
title: Crear un espacio de ejecución restringido | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59125e65-7030-40bb-9926-756120b2d952
caps.latest.revision: 5
ms.openlocfilehash: 20ac1e2af8e047b8b572d86a55439676aa8df25c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367654"
---
# <a name="creating-a-constrained-runspace"></a>Creación de un espacio de ejecución restringido

Por motivos de rendimiento o seguridad, es posible que desee restringir los comandos de Windows PowerShell disponibles para la aplicación host. Para ello, cree una vacía [System. Management. Automation. espacios de Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) llamando al método [System. Management. Automation. espacios de Initialsessionstate. Create *](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) y, a continuación, agregue únicamente los comandos que desee. disponible.

 El uso de un espacio de ejecución que solo carga los comandos especificados proporciona un rendimiento significativamente mejorado.

 Los métodos de la clase [System. Management. Automation. espacios de Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) se usan para definir cmdlets para el estado de sesión inicial.

 También puede hacer que los comandos sean privados. Los comandos privados se pueden usar en la aplicación host, pero no en los usuarios de la aplicación.

## <a name="adding-commands-to-an-empty-runspace"></a>Agregar comandos a un espacio de ejecución vacío

 En el ejemplo siguiente se muestra cómo crear un InitialSessionState vacío y cómo agregarle comandos.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using Microsoft.PowerShell.Commands;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class Runspace10b
  {
    /// <summary>
    /// This sample shows how to create an empty initial session state,
    /// how to add commands to the session state, and then how to create a
    /// runspace that has only those two commands. A PowerShell object
    /// is used to run the Get-Command cmdlet to show that only two commands
    /// are available.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create an empty InitialSessionState and then add two commands.
      InitialSessionState iss = InitialSessionState.Create();

      // Add the Get-Process and Get-Command cmdlets to the session state.
      SessionStateCmdletEntry ssce1 = new SessionStateCmdletEntry(
                                                            "get-process",
                                                            typeof(GetProcessCommand),
                                                            null);
      iss.Commands.Add(ssce1);

      SessionStateCmdletEntry ssce2 = new SessionStateCmdletEntry(
                                                            "get-command",
                                                            typeof(GetCommandCommand),
                                                            null);
      iss.Commands.Add(ssce2);

      // Create a runspace.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Create a pipeline with the Get-Command command.
          powershell.AddCommand("get-command");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Verb                 Noun");
          Console.WriteLine("----------------------------");

          // Display each result object.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                             "{0,-20} {1}",
                             result.Members["verb"].Value,
                             result.Members["Noun"].Value);
          }
        }

        // Close the runspace and release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="making-commands-private"></a>Convertir comandos en privados

 También puede hacer que un comando sea privado, estableciendo su propiedad [System. Management. Automation. Commandinfo. Visibility](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) en [System. Management. Automation. SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **Private**. La aplicación host y otros comandos pueden llamar a ese comando, pero el usuario de la aplicación no puede. En el ejemplo siguiente, el comando [Get-childitem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) es privado.

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a>Véase también

 [Creación de un InitialSessionState](./creating-an-initialsessionstate.md)
