---
title: Ejemplo de Runspace09 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f19f12c0-82e9-42f6-a7df-76c45b733855
caps.latest.revision: 8
ms.openlocfilehash: d78c865b869f802c7ebe2743942b6f21681de4b3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360864"
---
# <a name="runspace09-sample"></a><span data-ttu-id="da13b-102">Ejemplo Runspace09</span><span class="sxs-lookup"><span data-stu-id="da13b-102">Runspace09 Sample</span></span>

<span data-ttu-id="da13b-103">En este ejemplo se muestra cómo agregar un script a la canalización de un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) y cómo ejecutar el script de forma asincrónica.</span><span class="sxs-lookup"><span data-stu-id="da13b-103">This sample shows how to add a script to the pipeline of a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object and how to run the script asynchronously.</span></span> <span data-ttu-id="da13b-104">Los eventos se usan para controlar la salida del script.</span><span class="sxs-lookup"><span data-stu-id="da13b-104">Events are used to handle the output of the script.</span></span>

## <a name="requirements"></a><span data-ttu-id="da13b-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da13b-105">Requirements</span></span>

<span data-ttu-id="da13b-106">Este ejemplo requiere Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="da13b-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="da13b-107">Demuestra</span><span class="sxs-lookup"><span data-stu-id="da13b-107">Demonstrates</span></span>

<span data-ttu-id="da13b-108">Este ejemplo muestra lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="da13b-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="da13b-109">Creación de un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) que utiliza el espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="da13b-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="da13b-110">Adición de un script de la canalización del objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="da13b-110">Adding a script the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="da13b-111">Usar el método [System. Management. Automation. PowerShell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) para ejecutar la canalización de forma asincrónica.</span><span class="sxs-lookup"><span data-stu-id="da13b-111">Using the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) method to run the pipeline asynchronously.</span></span>

- <span data-ttu-id="da13b-112">Usar los eventos del objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) para procesar la salida del script.</span><span class="sxs-lookup"><span data-stu-id="da13b-112">Using the events of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to process the output of the script.</span></span>

- <span data-ttu-id="da13b-113">Usar el método [System. Management. Automation. PowerShell. Stop \*](/dotnet/api/System.Management.Automation.PowerShell.Stop) para interrumpir la invocación de la canalización.</span><span class="sxs-lookup"><span data-stu-id="da13b-113">Using the [System.Management.Automation.Powershell.Stop\*](/dotnet/api/System.Management.Automation.PowerShell.Stop) method to interrupt the invocation of the pipeline.</span></span>

## <a name="example"></a><span data-ttu-id="da13b-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="da13b-114">Example</span></span>

<span data-ttu-id="da13b-115">Este ejemplo se ejecuta para ejecutar un script que genera los números del 1 al 10 con retrasos entre cada número.</span><span class="sxs-lookup"><span data-stu-id="da13b-115">This sample runs to run a script that generates the numbers from 1 to 10 with delays between each number.</span></span> <span data-ttu-id="da13b-116">El script se ejecuta de forma asincrónica y los eventos se utilizan para controlar la salida.</span><span class="sxs-lookup"><span data-stu-id="da13b-116">The script is run asynchronously and events are used to handle the output.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Collections.ObjectModel;
  using System.Diagnostics;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace09
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run a
    /// script that generates the numbers from 1 to 10 with delays
    /// between each number. The pipeline of the PowerShell object
    /// is run asynchronously and events are used to handle the output.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding a script to the pipeline of the PowerShell object.
    /// 3. Using the BeginInvoke method to run the pipeline asynchronously.
    /// 4. Using the events of the PowerShell object to process the
    ///    output of the script.
    /// 5. Using the PowerShell.Stop() method to interrupt the invocation of
    ///    the pipeline.
    /// </remarks>
    private static void Main(string[] args)
    {
      Console.WriteLine("Print the numbers from 1 to 10. Hit any key to halt processing\n");

      using (PowerShell powershell = PowerShell.Create())
      {
        // Add a script to the PowerShell object. The script generates the
        // numbers from 1 to 10 in half second intervals.
        powershell.AddScript("1..10 | foreach {$_ ; start-sleep -milli 500}");

        // Add the event handlers.  If we did not care about hooking the DataAdded
        // event, we would let BeginInvoke create the output stream for us.
        PSDataCollection<PSObject> output = new PSDataCollection<PSObject>();
        output.DataAdded += new EventHandler<DataAddedEventArgs>(Output_DataAdded);
        powershell.InvocationStateChanged += new EventHandler<PSInvocationStateChangedEventArgs>(Powershell_InvocationStateChanged);

        // Invoke the pipeline asynchronously.
        IAsyncResult asyncResult = powershell.BeginInvoke<PSObject, PSObject>(null, output);

        // Wait for things to happen. If the user hits a key before the
        // script has completed, then call the PowerShell Stop() method
        // to halt processing.
        Console.ReadKey();
        if (powershell.InvocationStateInfo.State != PSInvocationState.Completed)
        {
          // Stop the invocation of the pipeline.
          Console.WriteLine("\nStopping the pipeline!\n");
          powershell.Stop();

          // Wait for the Windows PowerShell state change messages to be displayed.
          System.Threading.Thread.Sleep(500);
          Console.WriteLine("\nPress a key to exit");
          Console.ReadKey();
        }
      }
    }

    /// <summary>
    /// The output data added event handler. This event is called when
    /// data is added to the output pipe. It reads the data that is
    /// available and displays it on the console.
    /// </summary>
    /// <param name="sender">The output pipe this event is associated with.</param>
    /// <param name="e">Parameter is not used.</param>
    private static void Output_DataAdded(object sender, DataAddedEventArgs e)
    {
      PSDataCollection<PSObject> myp = (PSDataCollection<PSObject>)sender;

      Collection<PSObject> results = myp.ReadAll();
      foreach (PSObject result in results)
      {
        Console.WriteLine(result.ToString());
      }
    }

    /// <summary>
    /// This event handler is called when the pipeline state is changed.
    /// If the state change is to Completed, the handler issues a message
    /// asking the user to exit the program.
    /// </summary>
    /// <param name="sender">This parameter is not used.</param>
    /// <param name="e">The PowerShell state information.</param>
    private static void Powershell_InvocationStateChanged(object sender, PSInvocationStateChangedEventArgs e)
    {
      Console.WriteLine("PowerShell object state changed: state: {0}\n", e.InvocationStateInfo.State);
      if (e.InvocationStateInfo.State == PSInvocationState.Completed)
      {
        Console.WriteLine("Processing completed, press a key to exit!");
      }
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="da13b-117">Véase también</span><span class="sxs-lookup"><span data-stu-id="da13b-117">See Also</span></span>

[<span data-ttu-id="da13b-118">Escritura de una aplicación host de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="da13b-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)