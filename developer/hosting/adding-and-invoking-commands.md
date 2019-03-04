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
ms.openlocfilehash: 31371797ee57f07075da3436e0b42b2ca01aaffd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857351"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="872c6-102">Adición e invocación de comandos</span><span class="sxs-lookup"><span data-stu-id="872c6-102">Adding and invoking commands</span></span>

<span data-ttu-id="872c6-103">Después de crear un espacio de ejecución, puede agregar Windows PowerShellcommands y scripts en una canalización y, a continuación, invocar la canalización de forma sincrónica o asincrónica.</span><span class="sxs-lookup"><span data-stu-id="872c6-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="872c6-104">Creación de una canalización</span><span class="sxs-lookup"><span data-stu-id="872c6-104">Creating a pipeline</span></span>

 <span data-ttu-id="872c6-105">El [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) clase proporciona varios métodos para agregar secuencias de comandos, parámetros y comandos a la canalización.</span><span class="sxs-lookup"><span data-stu-id="872c6-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="872c6-106">Puede invocar la canalización de forma sincrónica mediante una llamada a una sobrecarga de la [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método, o de forma asincrónica mediante una llamada a una sobrecarga de la [ System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) y, a continuación, el [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) método.</span><span class="sxs-lookup"><span data-stu-id="872c6-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="872c6-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="872c6-107">AddCommand</span></span>

1. <span data-ttu-id="872c6-108">Crear un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="872c6-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="872c6-109">Agregue el comando que desea ejecutar.</span><span class="sxs-lookup"><span data-stu-id="872c6-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="872c6-110">Invoque el comando.</span><span class="sxs-lookup"><span data-stu-id="872c6-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="872c6-111">Si se llama a la [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) más de una vez antes de llamar al método el [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método, el resultado de la primer comando se canaliza hacia el segundo y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="872c6-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="872c6-112">Si no desea canalizar el resultado de un comando a un comando anterior, puede agregarlo mediante una llamada a la [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) en su lugar.</span><span class="sxs-lookup"><span data-stu-id="872c6-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="872c6-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="872c6-113">AddParameter</span></span>

 <span data-ttu-id="872c6-114">El ejemplo anterior ejecuta un comando único sin ningún parámetro.</span><span class="sxs-lookup"><span data-stu-id="872c6-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="872c6-115">Puede agregar parámetros al comando mediante el [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) método, por ejemplo, el código siguiente obtiene una lista de todos los procesos que se denominan `PowerShell` que se ejecutan en el máquina.</span><span class="sxs-lookup"><span data-stu-id="872c6-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="872c6-116">Puede agregar parámetros adicionales mediante una llamada a [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repetidamente.</span><span class="sxs-lookup"><span data-stu-id="872c6-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="872c6-117">También puede agregar un diccionario de nombres de parámetros y valores mediante una llamada a la [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) método.</span><span class="sxs-lookup"><span data-stu-id="872c6-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="872c6-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="872c6-118">AddStatement</span></span>

 <span data-ttu-id="872c6-119">Puede simular el procesamiento por lotes utilizando el [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) método, que agrega una instrucción adicional al final de la canalización en el código siguiente obtiene una lista de procesos en ejecución con el nombre `PowerShell`y, a continuación, obtiene la lista de servicios en ejecución.</span><span class="sxs-lookup"><span data-stu-id="872c6-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="872c6-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="872c6-120">AddScript</span></span>

 <span data-ttu-id="872c6-121">Puede ejecutar un script existente mediante una llamada a la [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método.</span><span class="sxs-lookup"><span data-stu-id="872c6-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="872c6-122">El ejemplo siguiente agrega una secuencia de comandos a la canalización y lo ejecuta.</span><span class="sxs-lookup"><span data-stu-id="872c6-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="872c6-123">En este ejemplo se da por supuesto que ya hay un script denominado `MyScript.ps1` en una carpeta denominada `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="872c6-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="872c6-124">También hay una versión de la [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método que toma un parámetro booleano denominado `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="872c6-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="872c6-125">Si este parámetro se establece en `true`, a continuación, el script se ejecuta en el ámbito local.</span><span class="sxs-lookup"><span data-stu-id="872c6-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="872c6-126">El siguiente código ejecutará el script en el ámbito local.</span><span class="sxs-lookup"><span data-stu-id="872c6-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="872c6-127">Invocar una canalización de forma sincrónica</span><span class="sxs-lookup"><span data-stu-id="872c6-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="872c6-128">Después de agregar elementos a la canalización, se invoca.</span><span class="sxs-lookup"><span data-stu-id="872c6-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="872c6-129">Para invocar la canalización de forma sincrónica, llame a una sobrecarga de la [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método.</span><span class="sxs-lookup"><span data-stu-id="872c6-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="872c6-130">El ejemplo siguiente muestra cómo invocar una canalización de forma sincrónica.</span><span class="sxs-lookup"><span data-stu-id="872c6-130">The following example shows how to synchronously invoke a pipeline.</span></span>

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

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="872c6-131">Invocar una canalización de forma asincrónica</span><span class="sxs-lookup"><span data-stu-id="872c6-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="872c6-132">Invocar una canalización de forma asincrónica mediante una llamada a una sobrecarga de la [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) para crear un [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) objeto y, a continuación, llamar a la [ System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) método.</span><span class="sxs-lookup"><span data-stu-id="872c6-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="872c6-133">El ejemplo siguiente muestra cómo invocar un asynchronoulsy de canalización.</span><span class="sxs-lookup"><span data-stu-id="872c6-133">The following example shows how to invoke a pipeline asynchronoulsy.</span></span>

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
      // Get-Process cmdlet. Do not include spaces immediatly
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

## <a name="see-also"></a><span data-ttu-id="872c6-134">Véase también</span><span class="sxs-lookup"><span data-stu-id="872c6-134">See Also</span></span>

 [<span data-ttu-id="872c6-135">Creación de un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="872c6-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="872c6-136">Creación de un espacio de ejecución restringida</span><span class="sxs-lookup"><span data-stu-id="872c6-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
