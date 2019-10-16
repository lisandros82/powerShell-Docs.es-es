---
title: Crear espacios de creación remotos | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 057a666f-731b-423d-9d80-7be6b1836244
caps.latest.revision: 5
ms.openlocfilehash: c97b0dfc12d96f99c53383d3578579f1988efd52
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367684"
---
# <a name="creating-remote-runspaces"></a>Creación de espacios de ejecución remotos

Los comandos de PowerShell que toman un parámetro **ComputerName** se pueden ejecutar en cualquier equipo que ejecute PowerShell. Para ejecutar comandos que no toman un parámetro **ComputerName** , puede usar WS-Management para configurar un espacio de ejecución que se conecta a un equipo especificado y ejecutar comandos en dicho equipo.

## <a name="using-a-wsmanconnection-to-create-a-remote-runspace"></a>Usar un WSManConnection para crear un espacio de ejecución remoto

 Para crear un espacio de ejecución que se conecte a un equipo remoto, cree un objeto [System. Management. Automation. runspace. WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) . Para especificar el extremo de destino de la conexión, establezca la propiedad [System. Management. Automation. espacios de WSManConnectionInfo. ConnectionUri](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) del objeto. A continuación, cree un espacio de ejecución llamando al método [System. Management. Automation. runspace. RunspaceFactory. CreateRunspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) , especificando el objeto [System. Management. Automation. runspace. WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) como `connectionInfo` parámetro.

 En el ejemplo siguiente se muestra cómo crear un espacio de ejecución que se conecta a un equipo remoto. En el ejemplo, `RemoteComputerUri` se usa como marcador de posición para el URI real de un equipo remoto.

```csharp
namespace Samples
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;            // PowerShell namespace.
  using System.Management.Automation.Runspaces;  // PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class RemoteRunspace02
  {
    /// <summary>
    /// This sample shows how to create a remote runspace that
    /// runs commands on the local computer.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor
      // to connect to the "localHost". The WSManConnectionInfo object can
      // also be used to specify connections to remote computers.
      Uri RemoteComputerUri = new uri("http://Server01:5985/WSMAN");
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo(RemoteComputerUri);

      // Set the OperationTimeout property and OpenTimeout properties.
      // The OperationTimeout property is used to tell PowerShell
      // how long to wait (in milliseconds) before timing out for an
      // operation. The OpenTimeout property is used to tell Windows
      // PowerShell how long to wait (in milliseconds) before timing out
      // while establishing a remote connection.
      connectionInfo.OperationTimeout = 4 * 60 * 1000; // 4 minutes.
      connectionInfo.OpenTimeout = 1 * 60 * 1000; // 1 minute.

      // Create a remote runspace using the connection information.
      //using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace())
      using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace(connectionInfo))
      {
        // Establish the connection by calling the Open() method to open the runspace.
        // The OpenTimeout value set previously will be applied while establishing
        // the connection. Establishing a remote connection involves sending and
        // receiving some data, so the OperationTimeout will also play a role in this process.
          remoteRunspace.Open();

        // Create a PowerShell object to run commands in the remote runspace.
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = remoteRunspace;
          powershell.AddCommand("get-process");
          powershell.Invoke();

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

        // Close the connection. Call the Close() method to close the remote
        // runspace. The Dispose() method (called by using primitive) will call
        // the Close() method if it is not already called.
        remoteRunspace.Close();
      }
    }
  }
}
```
