---
title: Adición e invocación de comandos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: f776f13fe743a3f5f67de0d94883e3f754040ffc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367644"
---
# <a name="adding-and-invoking-commands"></a>Adición e invocación de comandos

Después de crear un espacio de ejecución, puede Agregar PowerShellcommands de Windows y scripts a una canalización y, a continuación, invocar la canalización de forma sincrónica o asincrónica.

## <a name="creating-a-pipeline"></a>Creación de una canalización

 La clase [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) proporciona varios métodos para agregar comandos, parámetros y scripts a la canalización. Puede invocar la canalización sincrónicamente mediante una llamada a una sobrecarga del método [System. Management. Automation. PowerShell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) o de forma asincrónica llamando a una sobrecarga de [System. Management. Automation. PowerShell. BeginInvoke *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) y, a continuación, el método [System. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .

### <a name="addcommand"></a>AddCommand

1. Cree un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

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

 Si llama al método [System. Management. Automation. PowerShell. addCommand *](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) más de una vez antes de llamar al método [System. Management. Automation. PowerShell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , el resultado del primer comando se canaliza al segundo, y así sucesivamente. Si no desea canalizar el resultado de un comando anterior a un comando, agréguelo llamando a [System. Management. Automation. PowerShell. Addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) en su lugar.

### <a name="addparameter"></a>AddParameter

 En el ejemplo anterior se ejecuta un solo comando sin parámetros. Puede agregar parámetros al comando mediante el método [System. Management. Automation. Pscommand. Addparameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) por ejemplo, el código siguiente obtiene una lista de todos los procesos denominados `PowerShell` que se ejecutan en la máquina.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 Puede agregar parámetros adicionales llamando a [System. Management. Automation. Pscommand. Addparameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) varias veces.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 También puede Agregar un diccionario de nombres y valores de parámetros llamando al método [System. Management. Automation. PowerShell. AddParameters *](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 Puede simular el procesamiento por lotes mediante el método [System. Management. Automation. PowerShell. Addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , que agrega una instrucción adicional al final de la canalización. el código siguiente obtiene una lista de los procesos en ejecución con el nombre `PowerShell` y, a continuación, Obtiene la lista de servicios en ejecución.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 Puede ejecutar un script existente llamando al método [System. Management. Automation. PowerShell. addScript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript) . En el ejemplo siguiente se agrega un script a la canalización y se ejecuta. En este ejemplo se da por supuesto que ya existe un script denominado `MyScript.ps1` en una carpeta denominada `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 También hay una versión del método [System. Management. Automation. PowerShell. addScript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript) que toma un parámetro booleano denominado `useLocalScope`. Si este parámetro se establece en `true`, el script se ejecuta en el ámbito local. En el código siguiente se ejecutará el script en el ámbito local.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Invocar una canalización de forma sincrónica

 Después de agregar elementos a la canalización, se invoca. Para invocar la canalización sincrónicamente, llame a una sobrecarga del método [System. Management. Automation. PowerShell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) . En el ejemplo siguiente se muestra cómo invocar una canalización de forma sincrónica.

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

 Una canalización se invoca de forma asincrónica mediante una llamada a una sobrecarga de [System. Management. Automation. PowerShell. BeginInvoke *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) para crear un objeto [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) y, a continuación, llamar a [System. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) método.

 En el ejemplo siguiente se muestra cómo invocar una canalización de forma asincrónica.

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

 [Crear un espacio de ejecución restringido](./creating-a-constrained-runspace.md)
