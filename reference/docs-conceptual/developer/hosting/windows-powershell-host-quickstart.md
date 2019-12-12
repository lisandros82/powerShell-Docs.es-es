---
title: Inicio rápido de host de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 390eb2d0153c65967d8c0711c852aa6e13fe4660
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360824"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="51005-102">Inicio rápido de Host de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="51005-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="51005-103">Para hospedar Windows PowerShell en la aplicación, se usa la clase [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) .</span><span class="sxs-lookup"><span data-stu-id="51005-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="51005-104">Esta clase proporciona métodos que crean una canalización de comandos y, a continuación, ejecutan esos comandos en un espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="51005-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="51005-105">La manera más sencilla de crear una aplicación host es usar el espacio de ejecución predeterminado.</span><span class="sxs-lookup"><span data-stu-id="51005-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="51005-106">El espacio de ejecución predeterminado contiene todos los comandos principales de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51005-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="51005-107">Si desea que la aplicación exponga solo un subconjunto de los comandos de Windows PowerShell, debe crear un espacio de ejecución personalizado.</span><span class="sxs-lookup"><span data-stu-id="51005-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="51005-108">Usar el espacio de ejecución predeterminado</span><span class="sxs-lookup"><span data-stu-id="51005-108">Using the default runspace</span></span>

<span data-ttu-id="51005-109">Para empezar, usaremos el espacio de ejecución predeterminado y usaremos los métodos de la clase [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) para agregar comandos, parámetros, instrucciones y scripts a una canalización.</span><span class="sxs-lookup"><span data-stu-id="51005-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="51005-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="51005-110">AddCommand</span></span>

<span data-ttu-id="51005-111">El método [System. Management. Automation. PowerShell. AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) se usa para agregar comandos a la canalización.</span><span class="sxs-lookup"><span data-stu-id="51005-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="51005-112">Por ejemplo, supongamos que desea obtener la lista de procesos en ejecución en la máquina.</span><span class="sxs-lookup"><span data-stu-id="51005-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="51005-113">La forma de ejecutar este comando es la siguiente.</span><span class="sxs-lookup"><span data-stu-id="51005-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="51005-114">Cree un objeto [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) .</span><span class="sxs-lookup"><span data-stu-id="51005-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="51005-115">Agregue el comando que desea ejecutar.</span><span class="sxs-lookup"><span data-stu-id="51005-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="51005-116">Invoque el comando.</span><span class="sxs-lookup"><span data-stu-id="51005-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="51005-117">Si llama al método AddCommand más de una vez antes de llamar al método [System. Management. Automation. PowerShell. Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , el resultado del primer comando se canaliza al segundo, y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="51005-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="51005-118">Si no desea canalizar el resultado de un comando anterior a un comando, agréguelo llamando a [System. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) en su lugar.</span><span class="sxs-lookup"><span data-stu-id="51005-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="51005-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="51005-119">AddParameter</span></span>

<span data-ttu-id="51005-120">En el ejemplo anterior se ejecuta un solo comando sin parámetros.</span><span class="sxs-lookup"><span data-stu-id="51005-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="51005-121">Puede agregar parámetros al comando mediante el método [System. Management. Automation. PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) .</span><span class="sxs-lookup"><span data-stu-id="51005-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="51005-122">Por ejemplo, en el código siguiente se obtiene una lista de todos los procesos denominados `PowerShell` que se ejecutan en el equipo.</span><span class="sxs-lookup"><span data-stu-id="51005-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="51005-123">Puede agregar parámetros adicionales mediante una llamada repetida al método AddParameter.</span><span class="sxs-lookup"><span data-stu-id="51005-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

<span data-ttu-id="51005-124">También puede Agregar un diccionario de nombres y valores de parámetros llamando al método [System. Management. Automation. PowerShell. AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .</span><span class="sxs-lookup"><span data-stu-id="51005-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="51005-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="51005-125">AddStatement</span></span>

<span data-ttu-id="51005-126">Puede simular el procesamiento por lotes mediante el método [System. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , que agrega una instrucción adicional al final de la canalización.</span><span class="sxs-lookup"><span data-stu-id="51005-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="51005-127">En el código siguiente se obtiene una lista de los procesos en ejecución con el nombre `PowerShell`y, a continuación, se obtiene la lista de servicios en ejecución.</span><span class="sxs-lookup"><span data-stu-id="51005-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="51005-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="51005-128">AddScript</span></span>

<span data-ttu-id="51005-129">Puede ejecutar un script existente llamando al método [System. Management. Automation. PowerShell. AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) .</span><span class="sxs-lookup"><span data-stu-id="51005-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="51005-130">En el ejemplo siguiente se agrega un script a la canalización y se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="51005-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="51005-131">En este ejemplo se da por supuesto que ya existe un script denominado `MyScript.ps1` en una carpeta denominada `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="51005-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="51005-132">También hay una versión del método AddScript que toma un parámetro booleano denominado `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="51005-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="51005-133">Si este parámetro se establece en `true`, el script se ejecuta en el ámbito local.</span><span class="sxs-lookup"><span data-stu-id="51005-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="51005-134">En el código siguiente se ejecutará el script en el ámbito local.</span><span class="sxs-lookup"><span data-stu-id="51005-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="51005-135">Crear un espacio de ejecución personalizado</span><span class="sxs-lookup"><span data-stu-id="51005-135">Creating a custom runspace</span></span>

<span data-ttu-id="51005-136">Mientras que el espacio de ejecución predeterminado que se usa en los ejemplos anteriores carga todos los comandos principales de Windows PowerShell, puede crear un espacio de ejecución personalizado que cargue solo un subconjunto especificado de todos los comandos.</span><span class="sxs-lookup"><span data-stu-id="51005-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="51005-137">Puede que desee hacer esto para mejorar el rendimiento (la carga de un número mayor de comandos es una disminución del rendimiento) o para restringir la capacidad del usuario para realizar operaciones.</span><span class="sxs-lookup"><span data-stu-id="51005-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="51005-138">Un espacio de ejecución que exponga solo un número limitado de comandos se denomina espacio de ejecución restringido.</span><span class="sxs-lookup"><span data-stu-id="51005-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="51005-139">Para crear un espacio de ejecución restringido, use las clases [System. Management. Automation. runspace. runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) y [System. Management. Automation. runspace. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="51005-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="51005-140">Creación de un objeto InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="51005-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="51005-141">Para crear un espacio de ejecución personalizado, primero debe crear un objeto [System. Management. Automation. runspace. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="51005-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="51005-142">En el ejemplo siguiente, usamos [System. Management. Automation. runspace. RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) para crear un espacio de ejecución después de crear un objeto InitialSessionState predeterminado.</span><span class="sxs-lookup"><span data-stu-id="51005-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="51005-143">Restricción del espacio de ejecución</span><span class="sxs-lookup"><span data-stu-id="51005-143">Constraining the runspace</span></span>

<span data-ttu-id="51005-144">En el ejemplo anterior, creamos un objeto [System. Management. Automation. espacios de InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) predeterminado que carga todo el núcleo integrado de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51005-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="51005-145">También podríamos haber llamado al método [System. Management. Automation. espacios de nombre. InitialSessionState. createdefault2)](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) para crear un objeto InitialSessionState que cargara solo los comandos en el complemento Microsoft. PowerShell. Core.</span><span class="sxs-lookup"><span data-stu-id="51005-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="51005-146">Para crear un espacio de ejecución más restringido, debe crear un objeto InitialSessionState vacío llamando al método [System. Management. Automation. runspace. InitialSessionState. Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) y, a continuación, agregue comandos a InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="51005-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="51005-147">El uso de un espacio de ejecución que solo carga los comandos especificados proporciona un rendimiento significativamente mejorado.</span><span class="sxs-lookup"><span data-stu-id="51005-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="51005-148">Los métodos de la clase [System. Management. Automation. espacios de SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) se usan para definir cmdlets para el estado de sesión inicial.</span><span class="sxs-lookup"><span data-stu-id="51005-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="51005-149">En el ejemplo siguiente se crea un estado de sesión inicial vacío y, a continuación, se definen y agregan los comandos `Get-Command` y `Import-Module` al estado de sesión inicial.</span><span class="sxs-lookup"><span data-stu-id="51005-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="51005-150">A continuación, se crea un espacio de ejecución restringido por ese estado de sesión inicial y se ejecutan los comandos en ese espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="51005-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="51005-151">Cree el estado de sesión inicial.</span><span class="sxs-lookup"><span data-stu-id="51005-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="51005-152">Defina y agregue comandos al estado de sesión inicial.</span><span class="sxs-lookup"><span data-stu-id="51005-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="51005-153">Cree y abra el espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="51005-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="51005-154">Ejecutar un comando y mostrar el resultado.</span><span class="sxs-lookup"><span data-stu-id="51005-154">Execute a command and show the result.</span></span>

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

<span data-ttu-id="51005-155">Cuando se ejecute, la salida de este código tendrá el siguiente aspecto.</span><span class="sxs-lookup"><span data-stu-id="51005-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
