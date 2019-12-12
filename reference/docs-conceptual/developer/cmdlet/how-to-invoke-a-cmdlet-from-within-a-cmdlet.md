---
title: Cómo invocar un cmdlet desde un cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365554"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Cómo invocar un cmdlet desde dentro de un cmdlet

En este ejemplo se muestra cómo invocar un cmdlet desde otro cmdlet, lo que le permite agregar la funcionalidad del cmdlet invocado al cmdlet que está desarrollando. En este ejemplo, se invoca el cmdlet `Get-Process` para obtener los procesos que se están ejecutando en el equipo local. La llamada al cmdlet `Get-Process` es equivalente al comando siguiente. Este comando recupera todos los procesos cuyos nombres comienzan con los caracteres "a" a "t".

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> Solo puede invocar los cmdlets que derivan directamente de la clase [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . No se puede invocar un cmdlet derivado de la clase [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Para invocar un cmdlet desde un cmdlet

1. Asegúrese de que se hace referencia al ensamblado que define el cmdlet que se va a invocar y que se ha agregado la instrucción `using` adecuada. En este ejemplo, se agregan los siguientes espacios de nombres.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. En el método de procesamiento de entrada del cmdlet, cree una nueva instancia del cmdlet que se va a invocar. En este ejemplo, se crea un objeto de tipo [Microsoft. PowerShell. Commands. Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) junto con la cadena que contiene los argumentos que se usan cuando se invoca el cmdlet.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Llame al método [System. Management. Automation. cmdlet. Invoke *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) para invocar el cmdlet `Get-Process`.

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>Ejemplo

En este ejemplo, el cmdlet `Get-Process` se invoca desde el método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) de un cmdlet.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
