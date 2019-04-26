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
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067831"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="02f9a-102">Cómo invocar un cmdlet desde dentro de un cmdlet</span><span class="sxs-lookup"><span data-stu-id="02f9a-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="02f9a-103">En este ejemplo se muestra cómo invocar un cmdlet desde dentro de otro cmdlet, que le permite agregar la funcionalidad del cmdlet invocado al cmdlet que está desarrollando.</span><span class="sxs-lookup"><span data-stu-id="02f9a-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="02f9a-104">En este ejemplo, el `Get-Process` se invoca el cmdlet para obtener los procesos que se ejecutan en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="02f9a-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="02f9a-105">La llamada a la `Get-Process` cmdlet es equivalente al comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="02f9a-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="02f9a-106">Este comando recupera todos los procesos cuyos nombres empiezan por los caracteres "a" a "t".</span><span class="sxs-lookup"><span data-stu-id="02f9a-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="02f9a-107">Puede invocar solo esos cmdlets que se derivan directamente de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase.</span><span class="sxs-lookup"><span data-stu-id="02f9a-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="02f9a-108">No se puede invocar un cmdlet que se deriva el [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) clase.</span><span class="sxs-lookup"><span data-stu-id="02f9a-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="02f9a-109">Para invocar un cmdlet desde dentro de un cmdlet</span><span class="sxs-lookup"><span data-stu-id="02f9a-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="02f9a-110">Asegúrese de que se hace referencia el ensamblado que define el cmdlet para invocar y que adecuado `using` se agrega la instrucción.</span><span class="sxs-lookup"><span data-stu-id="02f9a-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="02f9a-111">En este ejemplo, se agregan los siguientes espacios de nombres.</span><span class="sxs-lookup"><span data-stu-id="02f9a-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="02f9a-112">En el método del cmdlet de procesamiento de entrada, cree una nueva instancia del cmdlet que se debe invocar.</span><span class="sxs-lookup"><span data-stu-id="02f9a-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="02f9a-113">En este ejemplo, un objeto de tipo [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) se crea junto con la cadena que contiene los argumentos que se usan cuando se invoca el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="02f9a-113">In this example, an object of type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="02f9a-114">Llame a la [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método para invocar el `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="02f9a-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="02f9a-115">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="02f9a-115">Example</span></span>

<span data-ttu-id="02f9a-116">En este ejemplo, el `Get-Process` cmdlet se invoca desde el [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método de un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="02f9a-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="02f9a-117">Véase también</span><span class="sxs-lookup"><span data-stu-id="02f9a-117">See Also</span></span>

[<span data-ttu-id="02f9a-118">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="02f9a-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
