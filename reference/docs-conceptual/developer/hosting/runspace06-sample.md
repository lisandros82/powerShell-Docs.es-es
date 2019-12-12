---
title: Ejemplo de Runspace06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 471c85f3-9287-45c2-b4bc-833caa1b7634
caps.latest.revision: 8
ms.openlocfilehash: 3850aec88bc800718a82f51c91fbd0cb3c705089
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367594"
---
# <a name="runspace06-sample"></a><span data-ttu-id="b60b7-102">Ejemplo Runspace06</span><span class="sxs-lookup"><span data-stu-id="b60b7-102">Runspace06 Sample</span></span>

<span data-ttu-id="b60b7-103">En este ejemplo se muestra cómo agregar un módulo a un objeto [System. Management. Automation. runspace. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) para que el módulo se cargue cuando se abra el espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="b60b7-103">This sample shows how to add a module to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the module is loaded when the runspace is opened.</span></span> <span data-ttu-id="b60b7-104">El módulo proporciona un cmdlet Get-proc (definido por el [ejemplo GetProcessSample02](../cmdlet/getprocesssample02-sample.md)) que se ejecuta de forma sincrónica mediante un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="b60b7-104">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](../cmdlet/getprocesssample02-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="b60b7-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b60b7-105">Requirements</span></span>

<span data-ttu-id="b60b7-106">Este ejemplo requiere Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="b60b7-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b60b7-107">Demuestra</span><span class="sxs-lookup"><span data-stu-id="b60b7-107">Demonstrates</span></span>

<span data-ttu-id="b60b7-108">Este ejemplo muestra lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="b60b7-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="b60b7-109">Crear un objeto [System. Management. Automation. espacios de Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="b60b7-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="b60b7-110">Agregar el módulo al objeto [System. Management. Automation. espacios de Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="b60b7-110">Adding the module to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="b60b7-111">Crear un objeto [System. Management. Automation. Runspace. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) que use el objeto [System. Management. Automation. runspace. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="b60b7-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="b60b7-112">Creación de un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) que utiliza el espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="b60b7-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="b60b7-113">Agregar el cmdlet Get-proc del módulo a la canalización del objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="b60b7-113">Adding the module's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="b60b7-114">Ejecutar el comando sincrónicamente.</span><span class="sxs-lookup"><span data-stu-id="b60b7-114">Running the command synchronously.</span></span>

- <span data-ttu-id="b60b7-115">Extracción de propiedades de los objetos [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) devueltos por el comando.</span><span class="sxs-lookup"><span data-stu-id="b60b7-115">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="b60b7-116">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b60b7-116">Example</span></span>

<span data-ttu-id="b60b7-117">En este ejemplo se crea un espacio de ejecución que usa un objeto [System. Management. Automation. runspace. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) para definir los elementos que están disponibles cuando se abre el espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="b60b7-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="b60b7-118">En este ejemplo, se agrega un módulo que define un cmdlet Get-proc al estado de sesión inicial.</span><span class="sxs-lookup"><span data-stu-id="b60b7-118">In this sample, a module that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace06
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a binary module that is loaded by the initial session state.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample02.dll
    /// that is produced by the GetProcessSample02 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a module to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the module's get-proc cmdlet to the PowerShell object.
    /// 6. Running the command synchronously.
    /// 7. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
        // Create the default initial session state and add the module.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      iss.ImportPSModule(new string[] { @".\GetProcessSample02.dll" });

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the cmdlet and specify the runspace.
          powershell.AddCommand(@"GetProcessSample02\get-proc");
          powershell.Runspace = myRunSpace;

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="b60b7-119">Véase también</span><span class="sxs-lookup"><span data-stu-id="b60b7-119">See Also</span></span>

[<span data-ttu-id="b60b7-120">Escritura de una aplicación host de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b60b7-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)