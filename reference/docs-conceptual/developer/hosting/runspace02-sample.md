---
title: Ejemplo de Runspace02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7630bb63-ef39-4abd-b795-8000f984c1e5
caps.latest.revision: 9
ms.openlocfilehash: 6352169cffbb8a8bf59a42f79979f5003c150fa4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360984"
---
# <a name="runspace02-sample"></a><span data-ttu-id="7a0ff-102">Ejemplo Runspace02</span><span class="sxs-lookup"><span data-stu-id="7a0ff-102">Runspace02 Sample</span></span>

<span data-ttu-id="7a0ff-103">En este ejemplo se muestra cómo usar la clase [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) para ejecutar los cmdlets [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) y [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) sincrónicamente.</span><span class="sxs-lookup"><span data-stu-id="7a0ff-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="7a0ff-104">El cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) devuelve objetos [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) para cada proceso que se ejecuta en el equipo local y el `Sort-Object` ordena los objetos basándose en su propiedad [System.Diagnostics.Process.ID \*](/dotnet/api/System.Diagnostics.Process.Id) .</span><span class="sxs-lookup"><span data-stu-id="7a0ff-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="7a0ff-105">Los resultados de estos comandos se muestran mediante un control [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) .</span><span class="sxs-lookup"><span data-stu-id="7a0ff-105">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="7a0ff-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a0ff-106">Requirements</span></span>

<span data-ttu-id="7a0ff-107">Este ejemplo requiere Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="7a0ff-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7a0ff-108">Demuestra</span><span class="sxs-lookup"><span data-stu-id="7a0ff-108">Demonstrates</span></span>

<span data-ttu-id="7a0ff-109">Este ejemplo muestra lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="7a0ff-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="7a0ff-110">Crear un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) para ejecutar comandos.</span><span class="sxs-lookup"><span data-stu-id="7a0ff-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="7a0ff-111">Agregar comandos a la canalización del objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="7a0ff-111">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="7a0ff-112">Ejecutar los comandos sincrónicamente.</span><span class="sxs-lookup"><span data-stu-id="7a0ff-112">Running the commands synchronously.</span></span>

- <span data-ttu-id="7a0ff-113">Usar un control [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) para mostrar el resultado de los comandos en una aplicación Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7a0ff-113">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="7a0ff-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7a0ff-114">Example</span></span>

<span data-ttu-id="7a0ff-115">En este ejemplo se ejecutan los cmdlets [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) y [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) sincrónicamente en el espacio de ejecución predeterminado proporcionado por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a0ff-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="7a0ff-116">El resultado se muestra en un formulario con un control [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) .</span><span class="sxs-lookup"><span data-stu-id="7a0ff-116">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using System.Windows.Forms;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace02
  {
    /// <summary>
    /// This method creates the form where the output is displayed.
    /// </summary>
    private static void CreateForm()
    {
      Form form = new Form();
      DataGridView grid = new DataGridView();
      form.Controls.Add(grid);
      grid.Dock = DockStyle.Fill;

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddCommand("get-process").AddCommand("sort-object").AddArgument("ID");
        if (Runspace.DefaultRunspace == null)
        {
          Runspace.DefaultRunspace = powershell.Runspace;
        }

        Collection<PSObject> results = powershell.Invoke();

        // The generic collection needs to be re-wrapped in an ArrayList
        // for data-binding to work.
        ArrayList objects = new ArrayList();
        objects.AddRange(results);

        // The DataGridView will use the PSObjectTypeDescriptor type
        // to retrieve the properties.
        grid.DataSource = objects;
      }

      form.ShowDialog();
    }

    /// <summary>
    /// This sample uses a PowerShell object to run the Get-Process
    /// and Sort-Object cmdlets synchronously. Windows Forms and
    /// data binding are then used to display the results in a
    /// DataGridView control.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding commands and arguments to the pipeline of
    ///    the PowerShell object.
    /// 3. Running the commands synchronously.
    /// 4. Using a DataGridView control to display the output
    ///    of the commands in a Windows Forms application.
    /// </remarks>
    private static void Main(string[] args)
    {
      Runspace02.CreateForm();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="7a0ff-117">Vea también</span><span class="sxs-lookup"><span data-stu-id="7a0ff-117">See Also</span></span>

[<span data-ttu-id="7a0ff-118">Escritura de una aplicación host de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a0ff-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)