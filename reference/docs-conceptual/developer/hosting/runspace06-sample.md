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
# <a name="runspace06-sample"></a>Ejemplo Runspace06

En este ejemplo se muestra cómo agregar un módulo a un objeto [System. Management. Automation. runspace. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) para que el módulo se cargue cuando se abra el espacio de ejecución. El módulo proporciona un cmdlet Get-proc (definido por el [ejemplo GetProcessSample02](../cmdlet/getprocesssample02-sample.md)) que se ejecuta de forma sincrónica mediante un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

## <a name="requirements"></a>Requisitos

Este ejemplo requiere Windows PowerShell 2,0.

## <a name="demonstrates"></a>Demuestra

Este ejemplo muestra lo siguiente.

- Crear un objeto [System. Management. Automation. espacios de Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

- Agregar el módulo al objeto [System. Management. Automation. espacios de Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

- Crear un objeto [System. Management. Automation. Runspace. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) que use el objeto [System. Management. Automation. runspace. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

- Creación de un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) que utiliza el espacio de ejecución.

- Agregar el cmdlet Get-proc del módulo a la canalización del objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

- Ejecutar el comando sincrónicamente.

- Extracción de propiedades de los objetos [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) devueltos por el comando.

## <a name="example"></a>Ejemplo

En este ejemplo se crea un espacio de ejecución que usa un objeto [System. Management. Automation. runspace. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) para definir los elementos que están disponibles cuando se abre el espacio de ejecución. En este ejemplo, se agrega un módulo que define un cmdlet Get-proc al estado de sesión inicial.

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

## <a name="see-also"></a>Véase también

[Escritura de una aplicación host de Windows PowerShell](./writing-a-windows-powershell-host-application.md)