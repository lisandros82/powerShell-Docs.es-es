---
title: Agregar e invocar comandos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 9a01f948c5b474b4f9068030907601543e13cc7e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057661"
---
# <a name="adding-and-invoking-commands"></a>Adición e invocación de comandos

Después de crear un espacio de ejecución, puede agregar Windows PowerShellcommands y scripts en una canalización y, a continuación, invocar la canalización de forma sincrónica o asincrónica.

## <a name="creating-a-pipeline"></a>Creación de una canalización

 El [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) clase proporciona varios métodos para agregar secuencias de comandos, parámetros y comandos a la canalización. Puede invocar la canalización de forma sincrónica mediante una llamada a una sobrecarga de la [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método, o de forma asincrónica mediante una llamada a una sobrecarga de la [ System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) y, a continuación, el [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) método.

### <a name="addcommand"></a>AddCommand

1. Crear un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Agregue el comando que desea ejecutar.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Invoque el comando.

   ```csharp
   ps.Invoke();
   ```

 Si se llama a la [System.Management.Automation.Powershell.Addcommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) más de una vez antes de llamar al método el [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método, el resultado de la primer comando se canaliza hacia el segundo y así sucesivamente. Si no desea canalizar el resultado de un comando a un comando anterior, puede agregarlo mediante una llamada a la [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) en su lugar.

### <a name="addparameter"></a>AddParameter

 El ejemplo anterior ejecuta un comando único sin ningún parámetro. Puede agregar parámetros al comando mediante el [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) método, por ejemplo, el código siguiente obtiene una lista de todos los procesos que se denominan `PowerShell` que se ejecutan en el máquina.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 Puede agregar parámetros adicionales mediante una llamada a [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repetidamente.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 También puede agregar un diccionario de nombres de parámetros y valores mediante una llamada a la [System.Management.Automation.Powershell.Addparameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) método.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 Puede simular el procesamiento por lotes utilizando el [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) método, que agrega una instrucción adicional al final de la canalización en el código siguiente obtiene una lista de procesos en ejecución con el nombre `PowerShell`y, a continuación, obtiene la lista de servicios en ejecución.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 Puede ejecutar un script existente mediante una llamada a la [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método. El ejemplo siguiente agrega una secuencia de comandos a la canalización y lo ejecuta. En este ejemplo se da por supuesto que ya hay un script denominado `MyScript.ps1` en una carpeta denominada `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 También hay una versión de la [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método que toma un parámetro booleano denominado `useLocalScope`. Si este parámetro se establece en `true`, a continuación, el script se ejecuta en el ámbito local. El siguiente código ejecutará el script en el ámbito local.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Invocar una canalización de forma sincrónica

 Después de agregar elementos a la canalización, se invoca. Para invocar la canalización de forma sincrónica, llame a una sobrecarga de la [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método. El ejemplo siguiente muestra cómo invocar una canalización de forma sincrónica.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a>Invocar una canalización de forma asincrónica

 Invocar una canalización de forma asincrónica mediante una llamada a una sobrecarga de la [System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) para crear un [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) objeto y, a continuación, llamar a la [ System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) método.

 El ejemplo siguiente muestra cómo invocar una canalización de forma asincrónica.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a>Véase también

 [Creación de un InitialSessionState](./creating-an-initialsessionstate.md)

 [Creación de un espacio de ejecución restringida](./creating-a-constrained-runspace.md)
