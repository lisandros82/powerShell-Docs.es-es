---
title: Ejemplo de Runspace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4f7bf81e-4f95-4150-afc3-c0872b24d026
caps.latest.revision: 7
ms.openlocfilehash: 3205286fbbc823d21e29a328b3ba9c4c1459d9ff
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360874"
---
# <a name="runspace07-sample"></a>Ejemplo Runspace07

En este ejemplo se muestra cómo crear un espacio de ejecución y, a continuación, usar ese espacio de ejecución para ejecutar dos cmdlets de forma sincrónica mediante un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

## <a name="requirements"></a>Requisitos

Este ejemplo requiere Windows PowerShell 2,0.

## <a name="demonstrates"></a>Demuestra

Este ejemplo muestra lo siguiente.

- Crear un objeto [System. Management. Automation. Runspace. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) mediante la clase [System. Management. Automation. runspace. Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) .

- Creación de un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) que utiliza el espacio de ejecución.

- Agregar cmdlets a la canalización del objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

- Ejecutar los cmdlets sincrónicamente.

- Extracción de propiedades de los objetos [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) devueltos por el comando.

## <a name="example"></a>Ejemplo

En este ejemplo se crea un espacio de ejecución que usa un objeto [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) para ejecutar los cmdlets [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) y [Measure-Object](/powershell/module/microsoft.powershell.utility/measure-object) .

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
  internal class Runspace07
  {
    /// <summary>
    /// This sample shows how to create a runspace and how to run commands
    /// using a PowerShell object. It builds a pipeline that runs the
    /// get-process cmdlet, which is piped to the measure-object
    /// cmdlet to count the number of processes running on the system.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a runspace using the RunspaceFactory class.
    /// 2. Creating a PowerShell object that uses the runspace.
    /// 3. Adding cmdlets to the pipeline of the PowerShell object.
    /// 4. Running the cmdlets synchronously.
    /// 5. Working with PSObject objects to extract properties
    ///    from the objects returned by the cmdlets.
    /// </remarks>
    private static void Main(string[] args)
    {
      Collection<PSObject> result;     // Will hold the result
                                       // of running the cmdlets.

      // Create a runspace. We can not use the RunspaceInvoke class
      // because we need to get at the underlying runspace to
      // explicitly add the commands. Notice that no PSHost object is
      // supplied to the CreateRunspace method so the default host is
      // used. See the Host samples for more information on creating
      // your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace())
      {
        myRunSpace.Open();

        // Create a PowerShell object and specify the runspace.
        PowerShell powershell = PowerShell.Create();
        powershell.Runspace = myRunSpace;

        // Use the using statement so we dispose of the PowerShell object
        // when we're done.
        using (powershell)
        {
          // Add the get-process cmdlet to the PowerShell object. Notice
          // we are specify the name of the cmdlet, not a script.
          powershell.AddCommand("get-process");

          // Add the measure-object cmdlet to count the number
          // of objects being returned. Commands are always added to the end
          // of the pipeline.
          powershell.AddCommand("measure-object");

          // Run the cmdlets synchronously and save the objects returned.
          result = powershell.Invoke();
        }

        // Even after disposing of the pipeLine, we still need to set
        // the powershell variable to null so that the garbage collector
        // can clean it up.
        powershell = null;

        // Display the results of running the commands (checking that
        // everything is ok first.
        if (result == null || result.Count != 1)
        {
          throw new InvalidOperationException(
                    "pipeline.Invoke() returned the wrong number of objects");
        }

        PSMemberInfo count = result[0].Properties["Count"];
        if (count == null)
        {
          throw new InvalidOperationException(
                    "The object returned doesn't have a 'count' property");
        }

        Console.WriteLine(
                   "Runspace07: The Get-Process cmdlet returned {0} objects",
                   count.Value);

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>Véase también

[Escritura de una aplicación host de Windows PowerShell](./writing-a-windows-powershell-host-application.md)