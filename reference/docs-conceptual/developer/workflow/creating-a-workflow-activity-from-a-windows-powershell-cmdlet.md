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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359664"
---
# <a name="creating-a-workflow-activity-from-a-windows-powershell-cmdlet"></a>Creación de una actividad de flujo de trabajo desde un cmdlet de Windows PowerShell

Cualquier cmdlet o módulo de Windows PowerShell se puede empaquetar como una actividad de flujo de trabajo mediante los métodos de la clase [Microsoft. PowerShell. Activities. Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) . Use [Microsoft. PowerShell. Activities. Activitygenerator. Generatefrommoduleinfo *](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromModuleInfo), [Microsoft. PowerShell. Activities. Activitygenerator. Generatefromcommandinfo *](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromCommandInfo)y [ Métodos Microsoft. PowerShell. Activities. Activitygenerator. Generatefromname *](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromName) de la clase [Microsoft. PowerShell. Activities. Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) para generar C# código que representa una actividad. Después, puede compilar C# el código resultante en un ensamblado que se puede Agregar a un proyecto como una actividad.

Después, puede compilar C# el código resultante en un ensamblado que se puede Agregar a un proyecto como una actividad mediante una línea de comandos con el siguiente formato.

**CSC/nologo/out: AssemblyName/target: Library/Reference: System. Activities. Activity/Reference: Microsoft. PowerShell. Activities codefile.cs**

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo C# generar código para una actividad desde un módulo de Windows PowerShell.

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

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo C# generar código para una actividad desde un cmdlet de Windows PowerShell.

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