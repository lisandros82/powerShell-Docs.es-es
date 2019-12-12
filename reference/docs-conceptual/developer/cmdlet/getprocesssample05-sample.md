---
title: Ejemplo de GetProcessSample05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6aebd53f-0610-4959-88b2-42339588c859
caps.latest.revision: 6
ms.openlocfilehash: ad4300937c10652b677346a62c42fa4f6e8513cf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365704"
---
# <a name="getprocesssample05-sample"></a><span data-ttu-id="ad850-102">Ejemplo GetProcessSample05</span><span class="sxs-lookup"><span data-stu-id="ad850-102">GetProcessSample05 Sample</span></span>

<span data-ttu-id="ad850-103">En este ejemplo se muestra una versión completa del cmdlet Get-proc.</span><span class="sxs-lookup"><span data-stu-id="ad850-103">This sample shows a complete version of the Get-Proc cmdlet.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="ad850-104">Cómo compilar el ejemplo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ad850-104">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="ad850-105">Abra el explorador de Windows y navegue hasta el directorio GetProcessSample05 en el directorio Samples.</span><span class="sxs-lookup"><span data-stu-id="ad850-105">Open Windows Explorer and navigate to the GetProcessSample05 directory under the Samples directory.</span></span>

   <span data-ttu-id="ad850-106">Con el SDK de Windows PowerShell 2,0 instalado, vaya a la carpeta GetProcessSample05.</span><span class="sxs-lookup"><span data-stu-id="ad850-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample05 folder.</span></span> <span data-ttu-id="ad850-107">La ubicación predeterminada es C:\Archivos de programa (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample05.</span><span class="sxs-lookup"><span data-stu-id="ad850-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample05.</span></span>

2. <span data-ttu-id="ad850-108">Haga doble clic en el icono del archivo de solución (. sln).</span><span class="sxs-lookup"><span data-stu-id="ad850-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="ad850-109">Se abrirá el proyecto de ejemplo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ad850-109">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="ad850-110">En el menú **Compilar**, seleccione **Compilar solución**.</span><span class="sxs-lookup"><span data-stu-id="ad850-110">In the **Build** menu, select **Build Solution**.</span></span>

   <span data-ttu-id="ad850-111">La biblioteca del ejemplo se compilará en los directorios \Bin o \bin\debug predeterminados.</span><span class="sxs-lookup"><span data-stu-id="ad850-111">The library for the sample will be built in the default \bin or \bin\debug directories.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="ad850-112">Ejecución del ejemplo</span><span class="sxs-lookup"><span data-stu-id="ad850-112">How to run the sample</span></span>

1. <span data-ttu-id="ad850-113">Cree la siguiente carpeta de módulo:</span><span class="sxs-lookup"><span data-stu-id="ad850-113">Create the following module folder:</span></span>

   `[user]/documents/windowspowershell/modules/GetProcessSample05`

2. <span data-ttu-id="ad850-114">Copie el ensamblado de ejemplo en la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="ad850-114">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="ad850-115">Inicie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad850-115">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="ad850-116">Ejecute el siguiente comando para cargar el ensamblado en Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ad850-116">Run the following command to load the assembly into Windows PowerShell:</span></span>

   `Import-module getprossessample05`

5. <span data-ttu-id="ad850-117">Ejecute el siguiente comando para ejecutar el cmdlet:</span><span class="sxs-lookup"><span data-stu-id="ad850-117">Run the following command to run the cmdlet:</span></span>

   `get-proc`

## <a name="requirements"></a><span data-ttu-id="ad850-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad850-118">Requirements</span></span>

<span data-ttu-id="ad850-119">Este ejemplo requiere Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="ad850-119">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ad850-120">Demuestra</span><span class="sxs-lookup"><span data-stu-id="ad850-120">Demonstrates</span></span>

<span data-ttu-id="ad850-121">Este ejemplo muestra lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="ad850-121">This sample demonstrates the following.</span></span>

- <span data-ttu-id="ad850-122">Declarar una clase de cmdlet mediante el atributo de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ad850-122">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="ad850-123">Declarar un parámetro de cmdlet mediante el atributo Parameter.</span><span class="sxs-lookup"><span data-stu-id="ad850-123">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="ad850-124">Especificar las posiciones de los parámetros.</span><span class="sxs-lookup"><span data-stu-id="ad850-124">Specifying positions for parameters.</span></span>

- <span data-ttu-id="ad850-125">Especificar que los parámetros pueden tomar entradas de la canalización.</span><span class="sxs-lookup"><span data-stu-id="ad850-125">Specifying that parameters can take input from the pipeline.</span></span> <span data-ttu-id="ad850-126">La entrada se puede tomar de un objeto o un valor de una propiedad de un objeto cuyo nombre de propiedad es el mismo que el nombre del parámetro.</span><span class="sxs-lookup"><span data-stu-id="ad850-126">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="ad850-127">Declarar un atributo de validación para la entrada de parámetro.</span><span class="sxs-lookup"><span data-stu-id="ad850-127">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="ad850-128">Control de errores y excepciones.</span><span class="sxs-lookup"><span data-stu-id="ad850-128">Handling errors and exceptions.</span></span>

- <span data-ttu-id="ad850-129">Escritura de mensajes de depuración.</span><span class="sxs-lookup"><span data-stu-id="ad850-129">Writing debug messages.</span></span>

## <a name="example"></a><span data-ttu-id="ad850-130">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ad850-130">Example</span></span>

<span data-ttu-id="ad850-131">En este ejemplo se muestra cómo crear un cmdlet que muestre una lista de los procesos especificados.</span><span class="sxs-lookup"><span data-stu-id="ad850-131">This sample shows how to create a cmdlet that displays a list of specified processes.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Collections.Generic;
    using System.Diagnostics;
    using System.Management.Automation;    // Windows PowerShell namespace.
    using System.Security.Permissions;
    using Win32Exception = System.ComponentModel.Win32Exception;
    #region GetProcCommand

    /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc",
      DefaultParameterSetName = "ProcessName")]
   public class GetProcCommand : PSCmdlet
   {
       #region Fields
       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

       /// <summary>
       /// The identifiers of the processes to act on.
       /// </summary>
       private int[] processIds;

       /// <summary>
       /// The process objects to act on.
       /// </summary>
       private Process[] inputObjects;

       #endregion Fields

       #region Parameters

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ParameterSetName = "ProcessName",
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      /// <summary>
      /// Gets or sets the list of process identifiers on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         ParameterSetName = "Id",
         Mandatory = true,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true,
         HelpMessage = "The unique id of the process to get.")]
      public int[] Id
      {
         get { return this.processIds; }
         set { this.processIds = value; }
      }

      /// <summary>
      /// Gets or sets Process objects directly. If the input is a
      /// stream of [collection of] Process objects, the cmdlet bypasses the
      /// ProcessName and Id parameters and reads the Process objects
      /// directly.  This allows the cmdlet to deal with processes that have
      /// wildcard characters in their name.
      /// <value>Process objects</value>
      /// </summary>
      [Parameter(
         ParameterSetName = "InputObject",
         Mandatory = true,
         ValueFromPipeline = true)]
      public Process[] Input
      {
         get { return this.inputObjects; }
         set { this.inputObjects = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes. Then, the WriteObject
      /// method writes the associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         List<Process> matchingProcesses;

         WriteDebug("Obtaining the list of matching process objects.");

         switch (ParameterSetName)
         {
            case "Id":
               matchingProcesses = this.GetMatchingProcessesById();
               break;
            case "ProcessName":
               matchingProcesses = this.GetMatchingProcessesByName();
               break;
            case "InputObject":
               matchingProcesses = this.GetProcessesByInput();
               break;
            default:
               ThrowTerminatingError(
                   new ErrorRecord(
                       new ArgumentException("Bad ParameterSetName"),
                       "UnableToAccessProcessList",
                       ErrorCategory.InvalidOperation,
                       null));
               return;
         } // switch (ParameterSetName)

         WriteDebug("Outputting the matching process objects.");

         matchingProcesses.Sort(ProcessComparison);

         foreach (Process process in matchingProcesses)
         {
            WriteObject(process);
         }
      } // ProcessRecord

      #endregion Overrides

      #region protected Methods and Data

      /// <summary>
      /// Retrieves the list of all processes matching the ProcessName
      /// parameter and generates a nonterminating error for each
      /// specified process name which is not found even though the name
      /// contains no wildcards.
      /// </summary>
      /// <returns>The matching processes.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetMatchingProcessesByName()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> allProcesses =
            new List<Process>(Process.GetProcesses());

         // The keys dictionary is used for rapid lookup of
         // processes that are already in the matchingProcesses list.
         Dictionary<int, byte> keys = new Dictionary<int, byte>();

         List<Process> matchingProcesses = new List<Process>();

         if (null == this.processNames)
         {
             matchingProcesses.AddRange(allProcesses);
         }
         else
         {
             foreach (string pattern in this.processNames)
             {
                 WriteVerbose("Finding matches for process name \""
                    + pattern + "\".");

                 // WildCard search on the available processes
                 WildcardPattern wildcard =
                    new WildcardPattern(
                        pattern,
                        WildcardOptions.IgnoreCase);

                 bool found = false;

                 foreach (Process process in allProcesses)
                 {
                     if (!keys.ContainsKey(process.Id))
                     {
                         string processName = SafeGetProcessName(process);

                         // Remove the process from the allProcesses list
                         // so that it is not tested again.
                         if (processName.Length == 0)
                         {
                             allProcesses.Remove(process);
                         }

                         // Perform a wildcard search on this particular
                         // process name and check whether it matches the
                         // pattern specified.
                         if (!wildcard.IsMatch(processName))
                         {
                             continue;
                         }

                         WriteDebug("Found matching process id "
                            + process.Id + ".");

                         // A match is found.
                         found = true;

                         // Store the process identifier so that the same process
                         // is not added twice.
                         keys.Add(process.Id, 0);

                         // Add the process to the processes list.
                         matchingProcesses.Add(process);
                     }
                 } // foreach (Process...

                 if (!found &&
                   !WildcardPattern.ContainsWildcardCharacters(pattern))
                 {
                     WriteError(new ErrorRecord(
                        new ArgumentException("Cannot find process name "
                           + "\"" + pattern + "\"."),
                        "ProcessNameNotFound",
                        ErrorCategory.ObjectNotFound,
                        pattern));
                 }
             } // foreach (string...
         } // if (null...

         return matchingProcesses;
      } // GetMatchingProcessesByName

      /// <summary>
      /// Returns the name of a process.  If an error occurs, a blank
      /// string is returned.
      /// </summary>
      /// <param name="process">The process whose name is
      /// returned.</param>
      /// <returns>The name of the process.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand, Unrestricted = true)]
      protected static string SafeGetProcessName(Process process)
      {
         new EnvironmentPermission(PermissionState.Unrestricted).Assert();
         string name = String.Empty;

         if (process != null)
         {
            try
            {
                return process.ProcessName;
            }
            catch (Win32Exception)
            {
            }
            catch (InvalidOperationException)
            {
            }
         }

         return name;
     } // SafeGetProcessName

      #endregion Cmdlet Overrides

      #region Private Methods

      /// <summary>
      /// Function to sort by process name first, and then by
      /// the process identifier.
      /// </summary>
      /// <param name="x">First process object.</param>
      /// <param name="y">Second process object.</param>
      /// <returns>
      /// Returns less than zero if x is less than y,
      /// greater than 0 if x is greater than y, and 0 if x == y.
      /// </returns>
      private static int ProcessComparison(Process x, Process y)
      {
         int diff = String.Compare(
            SafeGetProcessName(x),
            SafeGetProcessName(y),
            StringComparison.CurrentCultureIgnoreCase);

         if (0 != diff)
         {
             return diff;
         }
         else
         {
             return x.Id.CompareTo(y.Id);
         }
      }

      /// <summary>
      /// Retrieves the list of all processes matching the Id
      /// parameter and generates a nonterminating error for
      /// each specified process identifier which is not found.
      /// </summary>
      /// <returns>
      /// An array of processes that match the given identifier.
      /// </returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetMatchingProcessesById()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> matchingProcesses = new List<Process>();

         if (null != this.processIds)
         {
            // The keys dictionary is used for rapid lookup of the
            // processes already in the matchingProcesses list.
            Dictionary<int, byte> keys = new Dictionary<int, byte>();

            foreach (int processId in this.processIds)
            {
               WriteVerbose("Finding match for process id "
                  + processId + ".");

               if (!keys.ContainsKey(processId))
               {
                  Process process;
                  try
                  {
                      process = Process.GetProcessById(processId);
                  }
                  catch (ArgumentException ex)
                  {
                     WriteError(new ErrorRecord(
                        ex,
                        "ProcessIdNotFound",
                        ErrorCategory.ObjectNotFound,
                        processId));
                     continue;
                  }

                  WriteDebug("Found matching process.");

                  matchingProcesses.Add(process);
                  keys.Add(processId, 0);
               }
            }
         }

         return matchingProcesses;
      } // GetMatchingProcessesById

      /// <summary>
      /// Retrieves the list of all processes matching the InputObject
      /// parameter.
      /// </summary>
      /// <returns>The matching processes.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetProcessesByInput()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> matchingProcesses = new List<Process>();

         if (null != this.Input)
         {
            // The keys dictionary is used for rapid lookup of the
            // processes already in the matchingProcesses list.
            Dictionary<int, byte> keys = new Dictionary<int, byte>();

            foreach (Process process in this.Input)
            {
               WriteVerbose("Refreshing process object.");

               if (!keys.ContainsKey(process.Id))
               {
                  try
                  {
                      process.Refresh();
                  }
                  catch (Win32Exception)
                  {
                  }
                  catch (InvalidOperationException)
                  {
                  }

                  matchingProcesses.Add(process);
               }
            }
         }

         return matchingProcesses;
      } // GetProcessesByInput
      #endregion Private Methods
    } // End GetProcCommand class.

    #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="ad850-132">Véase también</span><span class="sxs-lookup"><span data-stu-id="ad850-132">See Also</span></span>

[<span data-ttu-id="ad850-133">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad850-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
