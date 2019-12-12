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
# <a name="windows-powershell-host-quickstart"></a>Inicio rápido de Host de Windows PowerShell

Para hospedar Windows PowerShell en la aplicación, se usa la clase [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) .
Esta clase proporciona métodos que crean una canalización de comandos y, a continuación, ejecutan esos comandos en un espacio de ejecución.
La manera más sencilla de crear una aplicación host es usar el espacio de ejecución predeterminado.
El espacio de ejecución predeterminado contiene todos los comandos principales de Windows PowerShell.
Si desea que la aplicación exponga solo un subconjunto de los comandos de Windows PowerShell, debe crear un espacio de ejecución personalizado.

## <a name="using-the-default-runspace"></a>Usar el espacio de ejecución predeterminado

Para empezar, usaremos el espacio de ejecución predeterminado y usaremos los métodos de la clase [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) para agregar comandos, parámetros, instrucciones y scripts a una canalización.

### <a name="addcommand"></a>AddCommand

El método [System. Management. Automation. PowerShell. AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) se usa para agregar comandos a la canalización.
Por ejemplo, supongamos que desea obtener la lista de procesos en ejecución en la máquina.
La forma de ejecutar este comando es la siguiente.

1. Cree un objeto [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) .

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

Si llama al método AddCommand más de una vez antes de llamar al método [System. Management. Automation. PowerShell. Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , el resultado del primer comando se canaliza al segundo, y así sucesivamente.
Si no desea canalizar el resultado de un comando anterior a un comando, agréguelo llamando a [System. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) en su lugar.

### <a name="addparameter"></a>AddParameter

En el ejemplo anterior se ejecuta un solo comando sin parámetros.
Puede agregar parámetros al comando mediante el método [System. Management. Automation. PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) .
Por ejemplo, en el código siguiente se obtiene una lista de todos los procesos denominados `PowerShell` que se ejecutan en el equipo.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

Puede agregar parámetros adicionales mediante una llamada repetida al método AddParameter.

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

También puede Agregar un diccionario de nombres y valores de parámetros llamando al método [System. Management. Automation. PowerShell. AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

Puede simular el procesamiento por lotes mediante el método [System. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , que agrega una instrucción adicional al final de la canalización.
En el código siguiente se obtiene una lista de los procesos en ejecución con el nombre `PowerShell`y, a continuación, se obtiene la lista de servicios en ejecución.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

Puede ejecutar un script existente llamando al método [System. Management. Automation. PowerShell. AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) .
En el ejemplo siguiente se agrega un script a la canalización y se ejecuta.
En este ejemplo se da por supuesto que ya existe un script denominado `MyScript.ps1` en una carpeta denominada `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

También hay una versión del método AddScript que toma un parámetro booleano denominado `useLocalScope`.
Si este parámetro se establece en `true`, el script se ejecuta en el ámbito local.
En el código siguiente se ejecutará el script en el ámbito local.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Crear un espacio de ejecución personalizado

Mientras que el espacio de ejecución predeterminado que se usa en los ejemplos anteriores carga todos los comandos principales de Windows PowerShell, puede crear un espacio de ejecución personalizado que cargue solo un subconjunto especificado de todos los comandos.
Puede que desee hacer esto para mejorar el rendimiento (la carga de un número mayor de comandos es una disminución del rendimiento) o para restringir la capacidad del usuario para realizar operaciones.
Un espacio de ejecución que exponga solo un número limitado de comandos se denomina espacio de ejecución restringido.
Para crear un espacio de ejecución restringido, use las clases [System. Management. Automation. runspace. runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) y [System. Management. Automation. runspace. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

### <a name="creating-an-initialsessionstate-object"></a>Creación de un objeto InitialSessionState

Para crear un espacio de ejecución personalizado, primero debe crear un objeto [System. Management. Automation. runspace. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .
En el ejemplo siguiente, usamos [System. Management. Automation. runspace. RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) para crear un espacio de ejecución después de crear un objeto InitialSessionState predeterminado.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>Restricción del espacio de ejecución

En el ejemplo anterior, creamos un objeto [System. Management. Automation. espacios de InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) predeterminado que carga todo el núcleo integrado de Windows PowerShell.
También podríamos haber llamado al método [System. Management. Automation. espacios de nombre. InitialSessionState. createdefault2)](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) para crear un objeto InitialSessionState que cargara solo los comandos en el complemento Microsoft. PowerShell. Core.
Para crear un espacio de ejecución más restringido, debe crear un objeto InitialSessionState vacío llamando al método [System. Management. Automation. runspace. InitialSessionState. Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) y, a continuación, agregue comandos a InitialSessionState.

El uso de un espacio de ejecución que solo carga los comandos especificados proporciona un rendimiento significativamente mejorado.

Los métodos de la clase [System. Management. Automation. espacios de SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) se usan para definir cmdlets para el estado de sesión inicial.
En el ejemplo siguiente se crea un estado de sesión inicial vacío y, a continuación, se definen y agregan los comandos `Get-Command` y `Import-Module` al estado de sesión inicial.
A continuación, se crea un espacio de ejecución restringido por ese estado de sesión inicial y se ejecutan los comandos en ese espacio de ejecución.

Cree el estado de sesión inicial.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Defina y agregue comandos al estado de sesión inicial.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Cree y abra el espacio de ejecución.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

Ejecutar un comando y mostrar el resultado.

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

Cuando se ejecute, la salida de este código tendrá el siguiente aspecto.

```powershell
Get-Command
Import-Module
```
