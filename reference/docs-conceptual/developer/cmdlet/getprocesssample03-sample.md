---
title: Ejemplo de GetProcessSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369714"
---
# <a name="getprocesssample03-sample"></a><span data-ttu-id="ead3a-102">Ejemplo GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="ead3a-102">GetProcessSample03 Sample</span></span>

<span data-ttu-id="ead3a-103">Este ejemplo muestra cómo implementar un cmdlet que recupera los procesos en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="ead3a-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="ead3a-104">Proporciona un parámetro `Name` que puede aceptar un objeto de la canalización o un valor de una propiedad de un objeto cuyo nombre de propiedad es el mismo que el nombre del parámetro.</span><span class="sxs-lookup"><span data-stu-id="ead3a-104">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="ead3a-105">Este cmdlet es una versión simplificada del cmdlet `Get-Process` proporcionado por Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="ead3a-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="ead3a-106">Cómo compilar el ejemplo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ead3a-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="ead3a-107">Con el SDK de Windows PowerShell 2,0 instalado, vaya a la carpeta GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="ead3a-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="ead3a-108">La ubicación predeterminada es C:\Archivos de programa (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="ead3a-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="ead3a-109">Haga doble clic en el icono del archivo de solución (. sln).</span><span class="sxs-lookup"><span data-stu-id="ead3a-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="ead3a-110">Se abrirá el proyecto de ejemplo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ead3a-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="ead3a-111">En el menú **Compilar**, seleccione **Compilar solución**.</span><span class="sxs-lookup"><span data-stu-id="ead3a-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="ead3a-112">La biblioteca del ejemplo se generará en las carpetas \Bin o \bin\debug predeterminadas.</span><span class="sxs-lookup"><span data-stu-id="ead3a-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="ead3a-113">Ejecución del ejemplo</span><span class="sxs-lookup"><span data-stu-id="ead3a-113">How to run the sample</span></span>

1. <span data-ttu-id="ead3a-114">Cree la siguiente carpeta de módulo:</span><span class="sxs-lookup"><span data-stu-id="ead3a-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="ead3a-115">Copie el ensamblado de ejemplo en la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="ead3a-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="ead3a-116">Inicie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ead3a-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="ead3a-117">Ejecute el siguiente comando para cargar el ensamblado en Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ead3a-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="ead3a-118">Ejecute el siguiente comando para ejecutar el cmdlet:</span><span class="sxs-lookup"><span data-stu-id="ead3a-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="ead3a-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ead3a-119">Requirements</span></span>

<span data-ttu-id="ead3a-120">Este ejemplo requiere Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="ead3a-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ead3a-121">Demuestra</span><span class="sxs-lookup"><span data-stu-id="ead3a-121">Demonstrates</span></span>

<span data-ttu-id="ead3a-122">Este ejemplo muestra lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="ead3a-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="ead3a-123">Declarar una clase de cmdlet mediante el atributo de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ead3a-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="ead3a-124">Declarar un parámetro de cmdlet mediante el atributo Parameter.</span><span class="sxs-lookup"><span data-stu-id="ead3a-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="ead3a-125">Que especifica la posición del parámetro.</span><span class="sxs-lookup"><span data-stu-id="ead3a-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="ead3a-126">Especificar que el parámetro toma la entrada de la canalización.</span><span class="sxs-lookup"><span data-stu-id="ead3a-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="ead3a-127">La entrada se puede tomar de un objeto o un valor de una propiedad de un objeto cuyo nombre de propiedad es el mismo que el nombre del parámetro.</span><span class="sxs-lookup"><span data-stu-id="ead3a-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="ead3a-128">Declarar un atributo de validación para la entrada de parámetro.</span><span class="sxs-lookup"><span data-stu-id="ead3a-128">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="ead3a-129">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ead3a-129">Example</span></span>

<span data-ttu-id="ead3a-130">Este ejemplo muestra una implementación del cmdlet Get-proc que incluye un parámetro `Name` que acepta la entrada de la canalización.</span><span class="sxs-lookup"><span data-stu-id="ead3a-130">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
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
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
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
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="ead3a-131">Véase también</span><span class="sxs-lookup"><span data-stu-id="ead3a-131">See Also</span></span>

[<span data-ttu-id="ead3a-132">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ead3a-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
