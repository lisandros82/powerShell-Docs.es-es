---
title: Guía de inicio rápido de Windows PowerShell Host | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: cc014487a680747ad59437052f79d4576154a1cb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059684"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="9bc38-102">Inicio rápido de Host de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bc38-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="9bc38-103">Para hospedar Windows PowerShell en la aplicación, usa el [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) clase.</span><span class="sxs-lookup"><span data-stu-id="9bc38-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span> <span data-ttu-id="9bc38-104">Esta clase proporciona métodos que se creación una canalización de comandos y, a continuación, ejecutan esos comandos en un espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="9bc38-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span> <span data-ttu-id="9bc38-105">La manera más sencilla de crear una aplicación host es usar el espacio de ejecución predeterminado.</span><span class="sxs-lookup"><span data-stu-id="9bc38-105">The simplest way to create a host application is to use the default runspace.</span></span> <span data-ttu-id="9bc38-106">El espacio de ejecución predeterminada contiene todos los comandos de Windows PowerShell core.</span><span class="sxs-lookup"><span data-stu-id="9bc38-106">The default runspace contains all of the core Windows PowerShell commands.</span></span> <span data-ttu-id="9bc38-107">Si desea que la aplicación para exponer solo un subconjunto de los comandos de Windows PowerShell, debe crear un espacio de ejecución personalizado.</span><span class="sxs-lookup"><span data-stu-id="9bc38-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="9bc38-108">Uso de espacio de ejecución predeterminado</span><span class="sxs-lookup"><span data-stu-id="9bc38-108">Using the default runspace</span></span>

<span data-ttu-id="9bc38-109">Para empezar, se utilizará el espacio de ejecución de forma predeterminada y utilice los métodos de la [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) clase para agregar los comandos, parámetros, instrucciones y secuencias de comandos a una canalización.</span><span class="sxs-lookup"><span data-stu-id="9bc38-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="9bc38-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="9bc38-110">AddCommand</span></span>

<span data-ttu-id="9bc38-111">Usa el [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) método de la [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) clase para agregar comandos a la canalización.</span><span class="sxs-lookup"><span data-stu-id="9bc38-111">You use the [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands to the pipeline.</span></span> <span data-ttu-id="9bc38-112">Por ejemplo, suponga que desea obtener la lista de procesos en ejecución en el equipo.</span><span class="sxs-lookup"><span data-stu-id="9bc38-112">For example, suppose you want to get the list of running processes on the machine.</span></span> <span data-ttu-id="9bc38-113">La forma de ejecutar este comando es como sigue.</span><span class="sxs-lookup"><span data-stu-id="9bc38-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="9bc38-114">Crear un [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) objeto.</span><span class="sxs-lookup"><span data-stu-id="9bc38-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="9bc38-115">Agregue el comando que desea ejecutar.</span><span class="sxs-lookup"><span data-stu-id="9bc38-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="9bc38-116">Invoque el comando.</span><span class="sxs-lookup"><span data-stu-id="9bc38-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="9bc38-117">Si se llama a la [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) más de una vez antes de llamar al método el [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método, el resultado de la primer comando se canaliza hacia el segundo y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="9bc38-117">If you call the [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="9bc38-118">Si no desea canalizar el resultado de un comando a un comando anterior, puede agregarlo mediante una llamada a la [System.Management.Automation.Powershell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) en su lugar.</span><span class="sxs-lookup"><span data-stu-id="9bc38-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="9bc38-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="9bc38-119">AddParameter</span></span>

<span data-ttu-id="9bc38-120">El ejemplo anterior ejecuta un comando único sin ningún parámetro.</span><span class="sxs-lookup"><span data-stu-id="9bc38-120">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="9bc38-121">Puede agregar parámetros al comando mediante el [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) método, por ejemplo, el código siguiente obtiene una lista de todos los procesos que se denominan `PowerShell` que se ejecutan en el máquina.</span><span class="sxs-lookup"><span data-stu-id="9bc38-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="9bc38-122">Puede agregar parámetros adicionales mediante una llamada a [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repetidamente.</span><span class="sxs-lookup"><span data-stu-id="9bc38-122">You can add additional parameters by calling [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

<span data-ttu-id="9bc38-123">También puede agregar un diccionario de nombres de parámetros y valores mediante una llamada a la [System.Management.Automation.PowerShell.AddParameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) método.</span><span class="sxs-lookup"><span data-stu-id="9bc38-123">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="9bc38-124">AddStatement</span><span class="sxs-lookup"><span data-stu-id="9bc38-124">AddStatement</span></span>

<span data-ttu-id="9bc38-125">Puede simular el procesamiento por lotes utilizando el [System.Management.Automation.PowerShell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) método, que agrega una instrucción adicional al final de la canalización en el código siguiente obtiene una lista de procesos en ejecución con el nombre `PowerShell`y, a continuación, obtiene la lista de servicios en ejecución.</span><span class="sxs-lookup"><span data-stu-id="9bc38-125">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="9bc38-126">AddScript</span><span class="sxs-lookup"><span data-stu-id="9bc38-126">AddScript</span></span>

<span data-ttu-id="9bc38-127">Puede ejecutar un script existente mediante una llamada a la [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método.</span><span class="sxs-lookup"><span data-stu-id="9bc38-127">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="9bc38-128">El ejemplo siguiente agrega una secuencia de comandos a la canalización y lo ejecuta.</span><span class="sxs-lookup"><span data-stu-id="9bc38-128">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="9bc38-129">En este ejemplo se da por supuesto que ya hay un script denominado `MyScript.ps1` en una carpeta denominada `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="9bc38-129">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="9bc38-130">También hay una versión de la [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método que toma un parámetro booleano denominado `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="9bc38-130">There is also a version of the [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="9bc38-131">Si este parámetro se establece en `true`, a continuación, el script se ejecuta en el ámbito local.</span><span class="sxs-lookup"><span data-stu-id="9bc38-131">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="9bc38-132">El siguiente código ejecutará el script en el ámbito local.</span><span class="sxs-lookup"><span data-stu-id="9bc38-132">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="9bc38-133">Creación de un espacio de ejecución personalizado</span><span class="sxs-lookup"><span data-stu-id="9bc38-133">Creating a custom runspace</span></span>

<span data-ttu-id="9bc38-134">Mientras todos los comandos de Windows PowerShell core carga en el espacio de ejecución predeterminado utilizado en los ejemplos anteriores, puede crear un espacio de ejecución personalizado que solo un subconjunto especificado de todos los comandos de carga.</span><span class="sxs-lookup"><span data-stu-id="9bc38-134">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span> <span data-ttu-id="9bc38-135">Es posible que desee hacer esto para mejorar el rendimiento (cargando un mayor número de comandos es una disminución del rendimiento), o para restringir la capacidad del usuario para realizar operaciones.</span><span class="sxs-lookup"><span data-stu-id="9bc38-135">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span> <span data-ttu-id="9bc38-136">Un espacio de ejecución que expone sólo un número limitado de comandos se llama a un espacio de ejecución restringido.</span><span class="sxs-lookup"><span data-stu-id="9bc38-136">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span> <span data-ttu-id="9bc38-137">Para crear un espacio de ejecución restringido, utilice el [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) y [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) clases.</span><span class="sxs-lookup"><span data-stu-id="9bc38-137">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="9bc38-138">Creación de un objeto InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="9bc38-138">Creating an InitialSessionState object</span></span>

<span data-ttu-id="9bc38-139">Para crear un espacio de ejecución personalizado, debe crear primero un [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto.</span><span class="sxs-lookup"><span data-stu-id="9bc38-139">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span> <span data-ttu-id="9bc38-140">En el ejemplo siguiente, usamos el [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) para crear un espacio de ejecución después de crear el valor predeterminado es [System.Management.Automation.Runspaces.InitialSessionState ](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto.</span><span class="sxs-lookup"><span data-stu-id="9bc38-140">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="9bc38-141">Restringir el espacio de ejecución</span><span class="sxs-lookup"><span data-stu-id="9bc38-141">Constraining the runspace</span></span>

<span data-ttu-id="9bc38-142">En el ejemplo anterior, creamos un valor predeterminado [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto que se carga todo el núcleo integrado de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9bc38-142">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span> <span data-ttu-id="9bc38-143">Llamamos también podríamos haber a la [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) método para crear un objeto InitialSessionState que se pueda cargar solo los comandos en el Microsoft.PowerShell.Core complemento.</span><span class="sxs-lookup"><span data-stu-id="9bc38-143">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span> <span data-ttu-id="9bc38-144">Para crear un espacio de ejecución más restringido, debe crear vacío [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto mediante una llamada a la [ System.Management.Automation.Runspaces.InitialSessionState.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) método y, a continuación, agregar comandos a la InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="9bc38-144">To create a more constrained runspace, you must create an empty [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="9bc38-145">Uso de un espacio de ejecución que carga únicamente los comandos que especifique proporciona mejora significativa del rendimiento.</span><span class="sxs-lookup"><span data-stu-id="9bc38-145">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="9bc38-146">Utilice los métodos de la [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) clase para definir los cmdlets de para el estado de sesión inicial.</span><span class="sxs-lookup"><span data-stu-id="9bc38-146">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span> <span data-ttu-id="9bc38-147">En el ejemplo siguiente se crea un estado de sesión inicial vacío, a continuación, define y agrega el `Get-Command` y `Import-Module` comandos para el estado de sesión inicial.</span><span class="sxs-lookup"><span data-stu-id="9bc38-147">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span> <span data-ttu-id="9bc38-148">A continuación, crear un espacio de ejecución restringido por ese estado de sesión inicial y ejecute los comandos en ese espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="9bc38-148">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="9bc38-149">Crear el estado de sesión inicial.</span><span class="sxs-lookup"><span data-stu-id="9bc38-149">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="9bc38-150">Definir y agregar comandos para el estado de sesión inicial.</span><span class="sxs-lookup"><span data-stu-id="9bc38-150">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="9bc38-151">Crear y abrir el espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="9bc38-151">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="9bc38-152">Ejecutar un comando y muestra el resultado.</span><span class="sxs-lookup"><span data-stu-id="9bc38-152">Execute a command and show the result.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

<span data-ttu-id="9bc38-153">Cuando se ejecuta, el resultado de este código tendrá un aspecto como sigue.</span><span class="sxs-lookup"><span data-stu-id="9bc38-153">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
