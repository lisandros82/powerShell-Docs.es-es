---
title: Crear una actividad de flujo de trabajo desde un cmdlet de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4174e84f-d516-4aca-b418-273047dcfb07
caps.latest.revision: 7
ms.openlocfilehash: 5761ed2168a46d6ed9a2e50554d459f5b93223ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359664"
---
# <a name="creating-a-workflow-activity-from-a-windows-powershell-cmdlet"></a><span data-ttu-id="5c78a-102">Creación de una actividad de flujo de trabajo desde un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c78a-102">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>

<span data-ttu-id="5c78a-103">Cualquier cmdlet o módulo de Windows PowerShell se puede empaquetar como una actividad de flujo de trabajo mediante los métodos de la clase [Microsoft. PowerShell. Activities. Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) .</span><span class="sxs-lookup"><span data-stu-id="5c78a-103">Any Windows PowerShell module or cmdlet can be packaged as a Workflow activity by using the methods of the [Microsoft.Powershell.Activities.Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) class.</span></span> <span data-ttu-id="5c78a-104">Use los métodos [Microsoft. PowerShell. Activities. Activitygenerator. Generatefrommoduleinfo \*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromModuleInfo), [Microsoft. PowerShell. Activities. Activitygenerator. Generatefromcommandinfo \*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromCommandInfo)y [Microsoft. PowerShell. Activities. Activitygenerator. Generatefromname \*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromName) de la clase [Microsoft. PowerShell. Activities. Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) para generar C# código que representa una actividad.</span><span class="sxs-lookup"><span data-stu-id="5c78a-104">Use the [Microsoft.Powershell.Activities.Activitygenerator.Generatefrommoduleinfo\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromModuleInfo), [Microsoft.Powershell.Activities.Activitygenerator.Generatefromcommandinfo\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromCommandInfo), and [Microsoft.Powershell.Activities.Activitygenerator.Generatefromname\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromName) methods of the [Microsoft.Powershell.Activities.Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) class to generate C# code that represents an activity.</span></span> <span data-ttu-id="5c78a-105">Después, puede compilar C# el código resultante en un ensamblado que se puede Agregar a un proyecto como una actividad.</span><span class="sxs-lookup"><span data-stu-id="5c78a-105">You can then compile the resulting C# code into an assembly that can be added to a project as an activity.</span></span>

<span data-ttu-id="5c78a-106">Después, puede compilar C# el código resultante en un ensamblado que se puede Agregar a un proyecto como una actividad mediante una línea de comandos con el siguiente formato.</span><span class="sxs-lookup"><span data-stu-id="5c78a-106">You can then compile the resulting C# code into an assembly that can be added to a project as an activity by using a command line with the following form.</span></span>

<span data-ttu-id="5c78a-107">**CSC/nologo/out: AssemblyName/target: Library/Reference: System. Activities. Activity/Reference: Microsoft. PowerShell. Activities codefile.cs**</span><span class="sxs-lookup"><span data-stu-id="5c78a-107">**csc /nologo /out:AssemblyName /target:library /reference:System.Activities.Activity /reference:Microsoft.PowerShell.Activities codefile.cs**</span></span>

## <a name="example"></a><span data-ttu-id="5c78a-108">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5c78a-108">Example</span></span>

<span data-ttu-id="5c78a-109">En el ejemplo siguiente se muestra cómo C# generar código para una actividad desde un módulo de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5c78a-109">The following example demonstrates how to generate C# code for an activity from a Windows PowerShell module.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Management.Automation;
using System.Collections.ObjectModel;
using Microsoft.PowerShell.Activities;

namespace MakeActivity
{
    class Program
    {
        static void Main(string[] args)

        {
            StreamWriter CodeFile = new StreamWriter("c:\\\\testmodule\\codefile.cs");
            Collection<PSModuleInfo> ModuleInfos = new Collection<PSModuleInfo> { };
            PSModuleInfo ModuleInfo;
            string ActivityCode = "";
            string ModulePath = "";
            Console.Write("Type the full path and filename of the module to process:");
            ModulePath = Console.ReadLine();

            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Import-Module").AddArgument(ModulePath);
            ps.AddParameter("PassThru");
            ModuleInfos = ps.Invoke<PSModuleInfo>();

            ModuleInfo = (PSModuleInfo)ModuleInfos[0];

            ActivityCode = ActivityGenerator.GenerateFromModuleInfo(ModuleInfo, "MyNamespace").First<String>();

           CodeFile.Write(ActivityCode);
            Console.ReadLine();

        }
    }
}

```

## <a name="example"></a><span data-ttu-id="5c78a-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5c78a-110">Example</span></span>

<span data-ttu-id="5c78a-111">En el ejemplo siguiente se muestra cómo C# generar código para una actividad desde un cmdlet de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5c78a-111">The following example demonstrates how to generate C# code for an activity from a Windows PowerShell cmdlet.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Management.Automation;
using System.Collections.ObjectModel;
using Microsoft.PowerShell.Activities;

namespace MakeActivity
{
    class Program
    {
        static void Main(string[] args)

        {
            StreamWriter CodeFile = new StreamWriter("c:\\\\testmodule\\codefile.cs");
            Collection<PSModuleInfo> ModuleInfos = new Collection<PSModuleInfo> { };
            PSModuleInfo ModuleInfo;
            Collection<CommandInfo> CommandInfos = new Collection<CommandInfo> { };
            CommandInfo MyCommand;
            string ActivityCode = "";
            string ModulePath = "";
            Console.Write("Type the full path and filename of the module to process:");
            ModulePath = Console.ReadLine();

            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Import-Module").AddArgument(ModulePath);
            ps.AddParameter("PassThru");
            ModuleInfos = ps.Invoke<PSModuleInfo>();

            ModuleInfo = (PSModuleInfo)ModuleInfos[0];

            ps.AddCommand("Get-Command").AddArgument(ModuleInfo);
            CommandInfos = ps.Invoke<CommandInfo>();

            MyCommand = CommandInfos[0];

            ActivityCode = ActivityGenerator.GenerateFromCommandInfo(MyCommand, "MyNamespace");

           CodeFile.Write(ActivityCode);
            Console.ReadLine();

        }
    }
}

```