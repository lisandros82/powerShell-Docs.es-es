---
title: Ejemplo GetProcessSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861881"
---
# <a name="getprocesssample04-sample"></a><span data-ttu-id="17037-102">Ejemplo GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="17037-102">GetProcessSample04 Sample</span></span>

<span data-ttu-id="17037-103">En este ejemplo se muestra cómo implementar un cmdlet que recupera los procesos en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="17037-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="17037-104">Si se produce un error al recuperar un proceso genera un error de no terminación.</span><span class="sxs-lookup"><span data-stu-id="17037-104">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="17037-105">Este cmdlet es una versión simplificada de la `Get-Process` cmdlet proporcionado por Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="17037-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="17037-106">Cómo generar el ejemplo desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17037-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="17037-107">Con Windows PowerShell 2.0 instalado el SDK, vaya a la carpeta GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="17037-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="17037-108">La ubicación predeterminada es C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="17037-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="17037-109">Haga doble clic en el icono del archivo de solución (.sln).</span><span class="sxs-lookup"><span data-stu-id="17037-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="17037-110">Se abrirá el proyecto de ejemplo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17037-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="17037-111">En el **compilar** menú, seleccione **compilar solución**.</span><span class="sxs-lookup"><span data-stu-id="17037-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="17037-112">En las carpetas \bin o \bin\debug de forma predeterminada, se compilará la biblioteca para el ejemplo.</span><span class="sxs-lookup"><span data-stu-id="17037-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="17037-113">Cómo ejecutar el ejemplo</span><span class="sxs-lookup"><span data-stu-id="17037-113">How to run the sample</span></span>

1. <span data-ttu-id="17037-114">Cree la siguiente carpeta del módulo:</span><span class="sxs-lookup"><span data-stu-id="17037-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="17037-115">Copie el ensamblado de ejemplo en la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="17037-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="17037-116">Inicie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17037-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="17037-117">Ejecute el siguiente comando para cargar el ensamblado en Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="17037-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="17037-118">Ejecute el siguiente comando para ejecutar el cmdlet:</span><span class="sxs-lookup"><span data-stu-id="17037-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="17037-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17037-119">Requirements</span></span>

<span data-ttu-id="17037-120">Este ejemplo requiere Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="17037-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="17037-121">Demostraciones</span><span class="sxs-lookup"><span data-stu-id="17037-121">Demonstrates</span></span>

<span data-ttu-id="17037-122">Este ejemplo muestra lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="17037-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="17037-123">Declarar una clase de cmdlet mediante el atributo de Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="17037-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="17037-124">Declarar un parámetro de cmdlet mediante el atributo de parámetro.</span><span class="sxs-lookup"><span data-stu-id="17037-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="17037-125">Especifica la posición del parámetro.</span><span class="sxs-lookup"><span data-stu-id="17037-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="17037-126">Especifica que el parámetro toma como entrado de la canalización.</span><span class="sxs-lookup"><span data-stu-id="17037-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="17037-127">La entrada se puede obtener de un objeto o un valor de una propiedad de un objeto cuyo nombre de propiedad es el mismo que el nombre del parámetro.</span><span class="sxs-lookup"><span data-stu-id="17037-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="17037-128">Declarar un atributo de validación para el parámetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="17037-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="17037-129">Interceptar un error de no terminación y escribir un mensaje de error en la secuencia de error.</span><span class="sxs-lookup"><span data-stu-id="17037-129">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="17037-130">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17037-130">Example</span></span>

<span data-ttu-id="17037-131">En este ejemplo se muestra cómo crear un cmdlet que controla los errores de no terminación y escribe los mensajes de error en la secuencia de error.</span><span class="sxs-lookup"><span data-stu-id="17037-131">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes specified by the Name
      /// parameter. Then, the WriteObject method writes the
      /// associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="17037-132">Véase también</span><span class="sxs-lookup"><span data-stu-id="17037-132">See Also</span></span>

[<span data-ttu-id="17037-133">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="17037-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
