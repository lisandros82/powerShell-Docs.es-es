---
title: Conjuntos de cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bcf0739e-920e-4dd8-afca-2c6d6927bc2a
caps.latest.revision: 10
ms.openlocfilehash: ef3b5bab5dcafc578397bcb4f071776bbdeaced1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058273"
---
# <a name="cmdlet-sets"></a><span data-ttu-id="d9b1e-102">Conjuntos de cmdlets</span><span class="sxs-lookup"><span data-stu-id="d9b1e-102">Cmdlet Sets</span></span>

<span data-ttu-id="d9b1e-103">Al diseñar sus cmdlets, podría encontrar casos en que necesite realizar varias acciones en el mismo elemento de datos.</span><span class="sxs-lookup"><span data-stu-id="d9b1e-103">When you design your cmdlets, you might encounter cases in which you need to perform several actions on the same piece of data.</span></span> <span data-ttu-id="d9b1e-104">Por ejemplo, deberá obtener y establecer los datos o iniciar y detener un proceso.</span><span class="sxs-lookup"><span data-stu-id="d9b1e-104">For example, you might need to get and set data or start and stop a process.</span></span> <span data-ttu-id="d9b1e-105">Aunque se necesita crear cmdlets independientes para llevar a cabo cada acción, el diseño del cmdlet debe incluir una clase base que se derivan las clases para los cmdlets individuales.</span><span class="sxs-lookup"><span data-stu-id="d9b1e-105">Although you will need to create separate cmdlets to perform each action, your cmdlet design should include a base class from which the classes for the individual cmdlets are derived.</span></span>

<span data-ttu-id="d9b1e-106">Tenga en cuenta lo siguiente al implementar una clase base.</span><span class="sxs-lookup"><span data-stu-id="d9b1e-106">Keep the following things in mind when implementing a base class.</span></span>

- <span data-ttu-id="d9b1e-107">Declare los parámetros comunes utilizados por todos los cmdlets derivados de la clase base.</span><span class="sxs-lookup"><span data-stu-id="d9b1e-107">Declare any common parameters used by all the derived cmdlets in the base class.</span></span>

- <span data-ttu-id="d9b1e-108">Agregar parámetros de cmdlet específico a la clase cmdlet correspondiente.</span><span class="sxs-lookup"><span data-stu-id="d9b1e-108">Add cmdlet-specific parameters to the appropriate cmdlet class.</span></span>

- <span data-ttu-id="d9b1e-109">Invalide el método de la clase base de procesamiento de entrada adecuada.</span><span class="sxs-lookup"><span data-stu-id="d9b1e-109">Override the appropriate input processing method in the base class.</span></span>

- <span data-ttu-id="d9b1e-110">Declare el [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo en todas las clases de cmdlet, pero no se ha declarado en la clase base.</span><span class="sxs-lookup"><span data-stu-id="d9b1e-110">Declare the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute on all cmdlet classes, but do not declare it on the base class.</span></span>

- <span data-ttu-id="d9b1e-111">Implemente un [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) o [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) cuyo nombre de clase y descripción refleja el conjunto de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d9b1e-111">Implement a [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class whose name and description reflects the set of cmdlets.</span></span>

## <a name="example"></a><span data-ttu-id="d9b1e-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d9b1e-112">Example</span></span>

<span data-ttu-id="d9b1e-113">El ejemplo siguiente muestra la implementación de una clase base que se usa por Get-Proc y el cmdlet Stop-Proc que derivan de la misma clase base.</span><span class="sxs-lookup"><span data-stu-id="d9b1e-113">The following example shows the implementation of a base class that is used by Get-Proc and Stop-Proc cmdlet that derive from the same base class.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace.

namespace Microsoft.Samples.PowerShell.Commands
{

  #region ProcessCommands

  /// <summary>
  /// This class implements a Stop-Proc cmdlet. The parameters
  /// for this cmdlet are defined by the BaseProcCommand class.
  /// </summary>
  [Cmdlet(VerbsLifecycle.Stop, "Proc", SupportsShouldProcess = true)]
  public class StopProcCommand : BaseProcCommand
  {
    public override void ProcessObject(Process process)
    {
      if (ShouldProcess(process.ProcessName, "Stop-Proc"))
      {
        process.Kill();
      }
    }
  }

  /// <summary>
  /// This class implements a Get-Proc cmdlet. The parameters
  /// for this cmdlet are defined by the BaseProcCommand class.
  /// </summary>

  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : BaseProcCommand
  {
    public override void ProcessObject(Process process)
    {
      WriteObject(process);
    }
  }

  /// <summary>
  /// This class is the base class that defines the common
  /// functionality used by the Get-Proc and Stop-Proc
  /// cmdlets.
  /// </summary>
  public class BaseProcCommand : Cmdlet
  {
    #region Parameters

    // Defines the Name parameter that is used to
    // specify a process by its name.
    [Parameter(
               Position = 0,
               Mandatory = true,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true
    )]
    public string[] Name
    {
      get { return processNames; }
      set { processNames = value; }
    }
    private string[] processNames;

    // Defines the Exclude parameter that is used to
    // specify which processes should be excluded when
    // the cmdlet performs its action.
    [Parameter()]
    public string[] Exclude
    {
      get { return excludeNames; }
      set { excludeNames = value; }
    }
    private string[] excludeNames = new string[0];
    #endregion Parameters

    public virtual void ProcessObject(Process process)
    {
      throw new NotImplementedException("This method should be overridden.");
    }

    #region Cmdlet Overrides
    // <summary>
    // For each of the requested process names, retrieve and write
    // the associated processes.
    // </summary>
    protected override void ProcessRecord()
    {
      // Set up the wildcard characters used in resolving
      // the process names.
      WildcardOptions options = WildcardOptions.IgnoreCase |
                                WildcardOptions.Compiled;

      WildcardPattern[] include = new WildcardPattern[Name.Length];
      for (int i = 0; i < Name.Length; i++)
      {
        include[i] = new WildcardPattern(Name[i], options);
      }

      WildcardPattern[] exclude = new WildcardPattern[Exclude.Length];
      for (int i = 0; i < Exclude.Length; i++)
      {
        exclude[i] = new WildcardPattern(Exclude[i], options);
      }

      foreach (Process p in Process.GetProcesses())
      {
        foreach (WildcardPattern wIn in include)
        {
          if (wIn.IsMatch(p.ProcessName))
          {
            bool processThisOne = true;
            foreach (WildcardPattern wOut in exclude)
            {
              if (wOut.IsMatch(p.ProcessName))
              {
                processThisOne = false;
                break;
              }
            }
            if (processThisOne)
            {
              ProcessObject(p);
            }
            break;
          }
        }
      }
    }
    #endregion Cmdlet Overrides
  }
    #endregion ProcessCommands
}
```

## <a name="see-also"></a><span data-ttu-id="d9b1e-114">Véase también</span><span class="sxs-lookup"><span data-stu-id="d9b1e-114">See Also</span></span>

[<span data-ttu-id="d9b1e-115">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d9b1e-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
