---
title: Creación de un espacio de ejecución restringido | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59125e65-7030-40bb-9926-756120b2d952
caps.latest.revision: 5
ms.openlocfilehash: 3c70296cb22c325ace10dc04c8b1fd941742857b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863001"
---
# <a name="creating-a-constrained-runspace"></a><span data-ttu-id="33ad4-102">Creación de un espacio de ejecución restringido</span><span class="sxs-lookup"><span data-stu-id="33ad4-102">Creating a constrained runspace</span></span>

<span data-ttu-id="33ad4-103">Por motivos de seguridad o rendimiento, puede restringir los comandos de Windows PowerShell disponibles para su aplicación host.</span><span class="sxs-lookup"><span data-stu-id="33ad4-103">For performance or security reasons, you might want to restrict the Windows PowerShell commands available to your host application.</span></span> <span data-ttu-id="33ad4-104">Para ello, crear vacío [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) mediante una llamada a la [System.Management.Automation.Runspaces.Initialsessionstate.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) método, y, a continuación, agregue únicamente los comandos que desee que estén disponibles.</span><span class="sxs-lookup"><span data-stu-id="33ad4-104">To do this you create an empty [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) by calling the [System.Management.Automation.Runspaces.Initialsessionstate.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add only the commands you want available.</span></span>

 <span data-ttu-id="33ad4-105">Uso de un espacio de ejecución que carga únicamente los comandos que especifique proporciona mejora significativa del rendimiento.</span><span class="sxs-lookup"><span data-stu-id="33ad4-105">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

 <span data-ttu-id="33ad4-106">Utilice los métodos de la [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) clase para definir los cmdlets de para el estado de sesión inicial.</span><span class="sxs-lookup"><span data-stu-id="33ad4-106">You use the methods of the [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>

 <span data-ttu-id="33ad4-107">También puede hacer que los comandos privadas.</span><span class="sxs-lookup"><span data-stu-id="33ad4-107">You can also make commands private.</span></span> <span data-ttu-id="33ad4-108">Comandos privados pueden usarse por la aplicación host, pero no por los usuarios de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="33ad4-108">Private commands can be used by the host application, but not by users of the application.</span></span>

## <a name="adding-commands-to-an-empty-runspace"></a><span data-ttu-id="33ad4-109">Agregar comandos a un espacio de ejecución vacío</span><span class="sxs-lookup"><span data-stu-id="33ad4-109">Adding commands to an empty runspace</span></span>

 <span data-ttu-id="33ad4-110">El ejemplo siguiente muestra cómo crear un InitialSessionState vacía y agregar comandos a él.</span><span class="sxs-lookup"><span data-stu-id="33ad4-110">The following example demonstrates how to create an empty InitialSessionState and add commands to it.</span></span>

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

## <a name="making-commands-private"></a><span data-ttu-id="33ad4-111">Poner comandos privada</span><span class="sxs-lookup"><span data-stu-id="33ad4-111">Making commands private</span></span>

 <span data-ttu-id="33ad4-112">También puede realizar un comando privada, si se establece de [System.Management.Automation.Commandinfo.Visibility\*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) propiedad [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private) .</span><span class="sxs-lookup"><span data-stu-id="33ad4-112">You can also make a command private, by setting it's [System.Management.Automation.Commandinfo.Visibility\*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) property to [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private).</span></span> <span data-ttu-id="33ad4-113">Otros comandos y la aplicación host pueden llamar a ese comando, pero no el usuario de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="33ad4-113">The host application and other commands can call that command, but the user of the application cannot.</span></span> <span data-ttu-id="33ad4-114">En el ejemplo siguiente, la [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) comando es privado.</span><span class="sxs-lookup"><span data-stu-id="33ad4-114">In the following example, the [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) command is private.</span></span>
<span data-ttu-id="33ad4-115">También puede realizar un comando privada, si se establece de [System.Management.Automation.Commandinfo.Visibility\*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) propiedad [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private) .</span><span class="sxs-lookup"><span data-stu-id="33ad4-115">You can also make a command private, by setting it's [System.Management.Automation.Commandinfo.Visibility\*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) property to [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private).</span></span> <span data-ttu-id="33ad4-116">Otros comandos y la aplicación host pueden llamar a ese comando, pero no el usuario de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="33ad4-116">The host application and other commands can call that command, but the user of the application cannot.</span></span> <span data-ttu-id="33ad4-117">En el ejemplo siguiente, la [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) comando es privado.</span><span class="sxs-lookup"><span data-stu-id="33ad4-117">In the following example, the [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) command is private.</span></span>

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a><span data-ttu-id="33ad4-118">Véase también</span><span class="sxs-lookup"><span data-stu-id="33ad4-118">See Also</span></span>

 [<span data-ttu-id="33ad4-119">Creación de un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="33ad4-119">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)