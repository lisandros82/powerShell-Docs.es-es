---
title: Ejemplo de GetProcessSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364574"
---
# <a name="getprocesssample02-sample"></a><span data-ttu-id="ff3ac-102">Ejemplo GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="ff3ac-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="ff3ac-103">Este ejemplo muestra cómo escribir un cmdlet que recupere los procesos en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="ff3ac-104">Proporciona un parámetro `Name` que se puede utilizar para especificar los procesos que se van a recuperar.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="ff3ac-105">Este cmdlet es una versión simplificada del cmdlet `Get-Process` proporcionado por Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="ff3ac-106">Cómo compilar el ejemplo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="ff3ac-107">Con el SDK de Windows PowerShell 2,0 instalado, vaya a la carpeta GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="ff3ac-108">La ubicación predeterminada es C:\Archivos de programa (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="ff3ac-109">Haga doble clic en el icono del archivo de solución (. sln).</span><span class="sxs-lookup"><span data-stu-id="ff3ac-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="ff3ac-110">Se abrirá el proyecto de ejemplo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="ff3ac-111">En el menú **Compilar**, seleccione **Compilar solución**.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="ff3ac-112">La biblioteca del ejemplo se generará en las carpetas \Bin o \bin\debug predeterminadas.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="ff3ac-113">Ejecución del ejemplo</span><span class="sxs-lookup"><span data-stu-id="ff3ac-113">How to run the sample</span></span>

1. <span data-ttu-id="ff3ac-114">Cree la siguiente carpeta de módulo:</span><span class="sxs-lookup"><span data-stu-id="ff3ac-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="ff3ac-115">Copie el ensamblado de ejemplo en la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="ff3ac-116">Inicie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="ff3ac-117">Ejecute el siguiente comando para cargar el ensamblado en Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ff3ac-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="ff3ac-118">Ejecute el siguiente comando para ejecutar el cmdlet:</span><span class="sxs-lookup"><span data-stu-id="ff3ac-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="ff3ac-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ff3ac-119">Requirements</span></span>

<span data-ttu-id="ff3ac-120">Este ejemplo requiere Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ff3ac-121">Demuestra</span><span class="sxs-lookup"><span data-stu-id="ff3ac-121">Demonstrates</span></span>

<span data-ttu-id="ff3ac-122">Este ejemplo muestra lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="ff3ac-123">Declarar una clase de cmdlet mediante el atributo de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="ff3ac-124">Declarar un parámetro de cmdlet mediante el atributo Parameter.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="ff3ac-125">Que especifica la posición del parámetro.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="ff3ac-126">Declarar un atributo de validación para la entrada de parámetro.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="ff3ac-127">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ff3ac-127">Example</span></span>

<span data-ttu-id="ff3ac-128">En este ejemplo se muestra una implementación del cmdlet Get-proc que incluye un parámetro `Name`.</span><span class="sxs-lookup"><span data-stu-id="ff3ac-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
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
    /// associated process objects to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="ff3ac-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="ff3ac-129">See Also</span></span>

[<span data-ttu-id="ff3ac-130">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff3ac-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
