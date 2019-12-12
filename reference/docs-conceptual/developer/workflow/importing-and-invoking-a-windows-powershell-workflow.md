---
title: Importar e invocar un flujo de trabajo de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50e6f9b1-2678-4f53-9250-7c48843a9549
caps.latest.revision: 5
ms.openlocfilehash: 1113c0d1cd68bb97d2f96b529f755b62137d1f40
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366044"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>Importación e invocación de un flujo de trabajo de Windows PowerShell

Windows PowerShell 3 le permite importar e invocar un flujo de trabajo empaquetado como módulo de Windows PowerShell. Para obtener información acerca de los módulos de Windows PowerShell, consulte [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).

La clase [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)se usa como proxy de cliente para los objetos de flujo de trabajo en el servidor. En el procedimiento siguiente se explica cómo usar un objeto [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)para invocar un flujo de trabajo.

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>Crear un objeto PSJobProxy para ejecutar comandos de flujo de trabajo en un servidor remoto.

1. Cree un objeto [System. Management. Automation. runspace. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)para crear una conexión a un espacio de ejecución remoto.

2. Establezca la propiedad [System. Management. Automation. espacios de Wsmanconnectioninfo. Shelluri *](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) del objeto [System. Management. Automation. espacios](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)de. Wsmanconnectioninfo en `Microsoft.PowerShell.Workflow` para especificar un punto de conexión de Windows PowerShell.

3. Cree un espacio de ejecución que use la conexión creada al completar los pasos anteriores.

4. Cree un objeto [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell)y establezca su propiedad [System. Management. Automation. PowerShell. Runspace *](/dotnet/api/System.Management.Automation.PowerShell.Runspace) en el espacio de ejecución creado en el paso anterior.

5. Importe el módulo de flujo de trabajo y sus comandos en [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell).

6. Cree un objeto [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) y úselo para ejecutar comandos de flujo de trabajo en el servidor remoto.

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra cómo invocar un flujo de trabajo mediante Windows PowerShell.

Este ejemplo requiere Windows PowerShell 3.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;
using System.Management.Automation.Runspaces;

namespace WorkflowHostTest
{

class Program
    {
        static void Main(string[] args)
        {
            if (args.Length == 0)
            {
                Console.WriteLine("Specify path to Workflow module");
                return;
            }

            string moduleFile = args[0];

            Console.Write("Creating Remote runspace connection...");
            WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

            //Set the shellURI to workflow endpoint Microsoft.PowerShell.Workflow
            connectionInfo.ShellUri = "Microsoft.PowerShell.Workflow";

            //Create and open a runspace.
            Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo);
            runspace.Open();
            Console.WriteLine("done");

            PowerShell powershell = PowerShell.Create();
            powershell.Runspace = runspace;
            Console.Write("Setting $VerbosePreference=\"Continue\"...");
            powershell.AddScript("$VerbosePreference=\"Continue\"");
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Importing Workflow module...");
            powershell.Commands.Clear();

            //Import the module in to the PowerShell runspace. A XAML file could also be imported directly by using Import-Module.
            powershell.AddCommand("Import-Module").AddArgument(moduleFile);
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Creating job proxy...");
            powershell.Commands.Clear();
            powershell.AddCommand("Get-Proc").AddArgument("*");
            PSJobProxy job = powershell.AsJobProxy();
            Console.WriteLine("done");

                Console.WriteLine();
                Console.WriteLine("Using job proxy and performing operations...");
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine("Starting job...");
                job.StartJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());

                // use blocking enumerator to wait for objects until job finishes
                job.Output.BlockingEnumerator = true;
                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                // wait for a random time before attempting to stop job
                Random random = new Random();
                int time = random.Next(1, 10);
                Console.Write("Sleeping for {0} seconds when job is running on another thread...", time);
                System.Threading.Thread.Sleep(time * 1000);
                Console.WriteLine("done");
                Console.WriteLine("Stopping job...");
                job.StopJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine();
                job.Finished.WaitOne();
                Console.WriteLine("Output from job");
                Console.WriteLine("---------------");

                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                Console.WriteLine();
                Console.WriteLine("Verbose messages from job");
                Console.WriteLine("-------------------------");
                foreach (VerboseRecord v in job.Verbose)
                {
                    Console.WriteLine(v.Message);
                }

            runspace.Close();
        }
    }
}

```