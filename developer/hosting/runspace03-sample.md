---
title: Ejemplo Runspace03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31df99d7-6954-4fdc-b6f5-06ecba094f43
caps.latest.revision: 8
ms.openlocfilehash: 39495f7813aecf5d0210866fc11f94557fdb0cd9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059004"
---
# <a name="runspace03-sample"></a>Ejemplo Runspace03

En este ejemplo se muestra cómo usar el [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) clase para ejecutar un script de forma sincrónica y cómo controlar errores de no terminación. El script recibe una lista de nombres de procesos y después los recupera. Los resultados del script, incluidos los errores de no terminación generados al ejecutarlo, se muestran en una ventana de consola.

## <a name="requirements"></a>Requisitos

Este ejemplo requiere Windows PowerShell 2.0.

## <a name="demonstrates"></a>Demostraciones

Este ejemplo muestra lo siguiente.

- Creación de un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) que se ejecute un script de objeto.

- Agregar un script a la canalización de la [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

- Pasar objetos de entrada a la secuencia de comandos del programa que realiza la llamada.

- Ejecutar el script de forma sincrónica.

- Uso de [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objetos para extraer y mostrar las propiedades de los objetos devueltos por la secuencia de comandos.

- Recuperar y mostrar los registros de error que se generaron cuando se ejecutó la secuencia de comandos.

## <a name="example"></a>Ejemplo

Este ejemplo ejecuta una secuencia de comandos de forma sincrónica en el espacio de ejecución predeterminada proporcionada por Windows PowerShell. La salida de la secuencia de comandos y los errores de no terminación generados se muestran en una ventana de consola.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace03
  {
    /// <summary>
    /// This sample shows how to use the PowerShell class to run a
    /// script that retrieves process information for the list of
    /// process names passed to the script. It shows how to pass input
    /// objects to a script and how to retrieve error objects as well
    /// as the output objects.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerSHell object to run a script.
    /// 2. Adding a script to the pipeline of the PowerShell object.
    /// 3. Passing input objects to the script from the calling program.
    /// 4. Running the script synchronously.
    /// 5. Using PSObject objects to extract and display properties from
    ///    the objects returned by the script.
    /// 6. Retrieving and displaying error records that were generated
    ///    when the script was run.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Define a list of processes to look for.
      string[] processNames = new string[]
      {
        "lsass", "nosuchprocess", "services", "nosuchprocess2"
      };

      // The script to run to get these processes. Input passed
      // to the script will be available in the $input variable.
      string script = "$input | get-process -name {$_}";

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the script.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddScript(script);

        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the script synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke(processNames))
        {
          Console.WriteLine(
                            "{0,-20} {1}",
                            result.Members["ProcessName"].Value,
                            result.Members["HandleCount"].Value);
        }

        // Process any error records that were generated while running
        //  the script.
        Console.WriteLine("\nThe following non-terminating errors occurred:\n");
        PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
        if (errors != null && errors.Count > 0)
        {
          foreach (ErrorRecord err in errors)
          {
            System.Console.WriteLine("    error: {0}", err.ToString());
          }
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>Véase también

[Escribir una aplicación de Host de PowerShell de Windows](./writing-a-windows-powershell-host-application.md)