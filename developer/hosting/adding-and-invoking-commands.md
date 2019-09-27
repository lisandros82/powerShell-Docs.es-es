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
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323479"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="e2ed2-102">Adición e invocación de comandos</span><span class="sxs-lookup"><span data-stu-id="e2ed2-102">Adding and invoking commands</span></span>

<span data-ttu-id="e2ed2-103">Después de crear un espacio de ejecución, puede Agregar PowerShellcommands de Windows y scripts a una canalización y, a continuación, invocar la canalización de forma sincrónica o asincrónica.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="e2ed2-104">Creación de una canalización</span><span class="sxs-lookup"><span data-stu-id="e2ed2-104">Creating a pipeline</span></span>

 <span data-ttu-id="e2ed2-105">La clase [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) proporciona varios métodos para agregar comandos, parámetros y scripts a la canalización.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="e2ed2-106">Puede invocar la canalización sincrónicamente mediante una llamada a una sobrecarga del método [System. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) o de forma asincrónica llamando a una sobrecarga de [System. Management. Automation. PowerShell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) y, a continuación, el método [System. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="e2ed2-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="e2ed2-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="e2ed2-107">AddCommand</span></span>

1. <span data-ttu-id="e2ed2-108">Cree un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="e2ed2-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="e2ed2-109">Agregue el comando que desea ejecutar.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="e2ed2-110">Invoque el comando.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="e2ed2-111">Si llama al método [System. Management. Automation. PowerShell. addCommand \*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) más de una vez antes de llamar al método [System. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , el resultado del primer comando se canaliza al segundo, y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="e2ed2-112">Si no desea canalizar el resultado de un comando anterior a un comando, agréguelo llamando a [System. Management. Automation. PowerShell. Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) en su lugar.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="e2ed2-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="e2ed2-113">AddParameter</span></span>

 <span data-ttu-id="e2ed2-114">En el ejemplo anterior se ejecuta un solo comando sin parámetros.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="e2ed2-115">Puede agregar parámetros al comando mediante el método [System. Management. Automation. Pscommand. Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) por ejemplo, el código siguiente obtiene una lista de todos los procesos denominados `PowerShell` que se ejecutan en la máquina.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="e2ed2-116">Puede agregar parámetros adicionales llamando a [System. Management. Automation. Pscommand. Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) varias veces.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="e2ed2-117">También puede Agregar un diccionario de nombres y valores de parámetros llamando al método [System. Management. Automation. PowerShell. AddParameters \*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .</span><span class="sxs-lookup"><span data-stu-id="e2ed2-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="e2ed2-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="e2ed2-118">AddStatement</span></span>

 <span data-ttu-id="e2ed2-119">Puede simular el procesamiento por lotes mediante el método [System. Management. Automation. PowerShell. Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , que agrega una instrucción adicional al final de la canalización. el código siguiente obtiene una lista de los procesos en ejecución `PowerShell`con el nombre y Obtiene la lista de servicios en ejecución.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="e2ed2-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="e2ed2-120">AddScript</span></span>

 <span data-ttu-id="e2ed2-121">Puede ejecutar un script existente llamando al método [System. Management. Automation. PowerShell. addScript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) .</span><span class="sxs-lookup"><span data-stu-id="e2ed2-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="e2ed2-122">En el ejemplo siguiente se agrega un script a la canalización y se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="e2ed2-123">En este ejemplo se da por supuesto que ya `MyScript.ps1` existe un script denominado `D:\PSScripts`en una carpeta denominada.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="e2ed2-124">También hay una versión del método [System. Management. Automation. PowerShell. addScript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) que toma un parámetro booleano denominado `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="e2ed2-125">Si este parámetro se establece en `true`, el script se ejecuta en el ámbito local.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="e2ed2-126">En el código siguiente se ejecutará el script en el ámbito local.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="e2ed2-127">Invocar una canalización de forma sincrónica</span><span class="sxs-lookup"><span data-stu-id="e2ed2-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="e2ed2-128">Después de agregar elementos a la canalización, se invoca.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="e2ed2-129">Para invocar la canalización sincrónicamente, llame a una sobrecarga del método [System. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) .</span><span class="sxs-lookup"><span data-stu-id="e2ed2-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="e2ed2-130">En el ejemplo siguiente se muestra cómo invocar una canalización de forma sincrónica.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-130">The following example shows how to synchronously invoke a pipeline.</span></span>

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

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="e2ed2-131">Invocar una canalización de forma asincrónica</span><span class="sxs-lookup"><span data-stu-id="e2ed2-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="e2ed2-132">Una canalización se invoca de forma asincrónica mediante una llamada a una sobrecarga de [System. Management. Automation. PowerShell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) para crear un objeto [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) y, a continuación, llamar a [System. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) método.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="e2ed2-133">En el ejemplo siguiente se muestra cómo invocar una canalización de forma asincrónica.</span><span class="sxs-lookup"><span data-stu-id="e2ed2-133">The following example shows how to invoke a pipeline asynchronously.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e2ed2-134">Vea también</span><span class="sxs-lookup"><span data-stu-id="e2ed2-134">See Also</span></span>

 [<span data-ttu-id="e2ed2-135">Creación de un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="e2ed2-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="e2ed2-136">Crear un espacio de ejecución restringido</span><span class="sxs-lookup"><span data-stu-id="e2ed2-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
