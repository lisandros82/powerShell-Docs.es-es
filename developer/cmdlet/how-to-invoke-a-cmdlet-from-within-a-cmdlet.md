---
title: Cómo invocar un Cmdlet desde dentro de un Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: d4564b51b74422cdaec3878b227ffc6be7c97949
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855891"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Cómo invocar un cmdlet desde dentro de un cmdlet

En este ejemplo se muestra cómo invocar un cmdlet desde dentro de otro cmdlet, que le permite agregar la funcionalidad del cmdlet invocado al cmdlet que está desarrollando. En este ejemplo, el `Get-Process` se invoca el cmdlet para obtener los procesos que se ejecutan en el equipo local. La llamada a la `Get-Process` cmdlet es equivalente al comando siguiente. Este comando recupera todos los procesos cuyos nombres empiezan por los caracteres "a" a "t".

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> Puede invocar solo esos cmdlets que se derivan directamente de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase. No se puede invocar un cmdlet que se deriva el [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) clase.

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Para invocar un cmdlet desde dentro de un cmdlet

1. Asegúrese de que se hace referencia el ensamblado que define el cmdlet para invocar y que adecuado `using` se agrega la instrucción. En este ejemplo, se agregan los siguientes espacios de nombres.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. En el método del cmdlet de procesamiento de entrada, cree una nueva instancia del cmdlet que se debe invocar. En este ejemplo, un objeto de tipo [Microsoft.Powershell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) se crea junto con la cadena que contiene los argumentos que se usan cuando se invoca el cmdlet.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Llame a la [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método para invocar el `Get-Process` cmdlet.

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>Ejemplo

En este ejemplo, el `Get-Process` cmdlet se invoca desde el [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método de un cmdlet.

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
