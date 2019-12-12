---
title: Ejemplo de Runspace01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c1c59c-6da5-4cda-9562-e8059177fee1
caps.latest.revision: 11
ms.openlocfilehash: eec9c616fc6d5240db185f764a3ea2c8f9575d03
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367424"
---
# <a name="runspace01-sample"></a>Ejemplo Runspace01

En este ejemplo se muestra cómo usar la clase [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) para ejecutar el cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) sincrónicamente. El cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) devuelve objetos [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) para cada proceso que se ejecuta en el equipo local. Los valores de las propiedades [System. Diagnostics. Process. processName *](/dotnet/api/System.Diagnostics.Process.ProcessName) y [System. Diagnostics. Process. Handlecount *](/dotnet/api/System.Diagnostics.Process.Handlecount) se extraen de los objetos devueltos y se muestran en una ventana de la consola.

## <a name="requirements"></a>Requisitos

 Este ejemplo requiere Windows PowerShell 2,0.

## <a name="demonstrates"></a>Demuestra

- Crear un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) para ejecutar un comando.

- Agregar un comando a la canalización del objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

- Ejecutar el comando sincrónicamente.

- Usar objetos [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) para extraer propiedades de los objetos devueltos por el comando.

## <a name="example"></a>Ejemplo

 Este ejemplo ejecuta el cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) sincrónicamente en el espacio de ejecución predeterminado proporcionado por Windows PowerShell.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace01
  {
    /// <summary>
    /// This sample uses the PowerShell class to execute
    /// the get-process cmdlet synchronously. The name and
    /// handlecount are then extracted from the PSObjects
    /// returned and displayed.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run a command.
    /// 2. Adding a command to the pipeline of the PowerShell object.
    /// 3. Running the command synchronously.
    /// 4. Using PSObject objects to extract properties from the objects
    ///    returned by the command.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create().AddCommand("get-process"))
      {
        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the command synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke())
        {
          Console.WriteLine(
                      "{0,-20} {1}",
                      result.Members["ProcessName"].Value,
                      result.Members["HandleCount"].Value);
        }
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>Véase también
