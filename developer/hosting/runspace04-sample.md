---
title: Ejemplo Runspace04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6a04f15-b5d8-475b-ac9c-e75c58ec8933
caps.latest.revision: 8
ms.openlocfilehash: 9e8123e9b1068e0fd6efec8508eacf594ff22301
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854751"
---
# <a name="runspace04-sample"></a><span data-ttu-id="3cbd2-102">Ejemplo Runspace04</span><span class="sxs-lookup"><span data-stu-id="3cbd2-102">Runspace04 Sample</span></span>

<span data-ttu-id="3cbd2-103">En este ejemplo se muestra cómo usar el [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) clase para ejecutar comandos y cómo capturar los errores de terminación que se producen al ejecutar los comandos.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span> <span data-ttu-id="3cbd2-104">Se ejecutan dos comandos; al último, se le pasa un argumento de parámetro que no es válido.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-104">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span> <span data-ttu-id="3cbd2-105">Como resultado, no se devuelve ningún objeto y se produce un error de terminación.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-105">As a result, no objects are returned and a terminating error is thrown.</span></span>

## <a name="requirements"></a><span data-ttu-id="3cbd2-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3cbd2-106">Requirements</span></span>

<span data-ttu-id="3cbd2-107">Este ejemplo requiere Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3cbd2-108">Demostraciones</span><span class="sxs-lookup"><span data-stu-id="3cbd2-108">Demonstrates</span></span>

<span data-ttu-id="3cbd2-109">Este ejemplo muestra lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="3cbd2-110">Creación de un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="3cbd2-111">Agregar comandos a la canalización de la [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-111">Adding commands to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="3cbd2-112">Adición de argumentos de parámetro a la canalización.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-112">Adding parameter arguments to the pipeline.</span></span>

- <span data-ttu-id="3cbd2-113">Invocar los comandos de forma sincrónica.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-113">Invoking the commands synchronously.</span></span>

- <span data-ttu-id="3cbd2-114">Uso de [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objetos para extraer y mostrar las propiedades de los objetos devueltos por los comandos.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-114">Using [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the commands.</span></span>

- <span data-ttu-id="3cbd2-115">Recuperar y mostrar los registros de error que se generaron durante la ejecución de los comandos.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-115">Retrieving and displaying error records that were generated during the running of the commands.</span></span>

- <span data-ttu-id="3cbd2-116">Detectar y mostrar la terminación de las excepciones producidas por los comandos.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-116">Catching and displaying terminating exceptions thrown by the commands.</span></span>

## <a name="example"></a><span data-ttu-id="3cbd2-117">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3cbd2-117">Example</span></span>

<span data-ttu-id="3cbd2-118">Este ejemplo ejecuta los comandos de forma sincrónica en el espacio de ejecución predeterminada proporcionada por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-118">This sample runs commands synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="3cbd2-119">El último comando produce un error de terminación, ya que se pasa un argumento de parámetro que no es válido para el comando.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-119">The last command throws a terminating error because a parameter argument that is not valid is passed to the command.</span></span> <span data-ttu-id="3cbd2-120">Se capturan y se muestra el error de terminación.</span><span class="sxs-lookup"><span data-stu-id="3cbd2-120">The terminating error is trapped and displayed.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace04
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands.
    /// The commands generate a terminating exception that the caller
    /// should catch and process.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run commands.
    /// 2. Adding commands to the pipeline of  the PowerShell object.
    /// 3. Passing input objects to the commands from the calling program.
    /// 4. Using PSObject objects to extract and display properties from the
    ///    objects returned by the commands.
    /// 5. Retrieving and displaying error records that were generated
    ///    while running the commands.
    /// 6. Catching and displaying terminating exceptions generated
    ///    while running the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object.
      using (PowerShell powershell = PowerShell.Create())
      {
        // Add the commands to the PowerShell object.
        powershell.AddCommand("Get-ChildItem").AddCommand("Select-String").AddArgument("*");

        // Run the commands synchronously. Because of the bad regular expression,
        // no objects will be returned. Instead, an exception will be thrown.
        try
        {
          foreach (PSObject result in powershell.Invoke())
          {
            Console.WriteLine("'{0}'", result.ToString());
          }

          // Process any error records that were generated while running the commands.
          Console.WriteLine("\nThe following non-terminating errors occurred:\n");
          PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
          if (errors != null && errors.Count > 0)
          {
            foreach (ErrorRecord err in errors)
            {
              System.Console.WriteLine("    error: {0}", err.ToString());
            }
          }
        }
        catch (RuntimeException runtimeException)
        {
          // Trap any exception generated by the commands. These exceptions
          // will all be derived from the RuntimeException exception.
          System.Console.WriteLine(
                        "Runtime exception: {0}: {1}\n{2}",
                        runtimeException.ErrorRecord.InvocationInfo.InvocationName,
                        runtimeException.Message,
                        runtimeException.ErrorRecord.InvocationInfo.PositionMessage);
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="3cbd2-121">Véase también</span><span class="sxs-lookup"><span data-stu-id="3cbd2-121">See Also</span></span>

[<span data-ttu-id="3cbd2-122">Escribir una aplicación de Host de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="3cbd2-122">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)