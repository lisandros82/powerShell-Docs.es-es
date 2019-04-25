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
ms.openlocfilehash: 3cb370cd1bfe9ce7198980cc1c26fafb126d00a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082689"
---
# <a name="runspace04-sample"></a><span data-ttu-id="42949-102">Ejemplo Runspace04</span><span class="sxs-lookup"><span data-stu-id="42949-102">Runspace04 Sample</span></span>

<span data-ttu-id="42949-103">En este ejemplo se muestra cómo usar el [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) clase para ejecutar comandos y cómo capturar los errores de terminación que se producen al ejecutar los comandos.</span><span class="sxs-lookup"><span data-stu-id="42949-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span> <span data-ttu-id="42949-104">Se ejecutan dos comandos; al último, se le pasa un argumento de parámetro que no es válido.</span><span class="sxs-lookup"><span data-stu-id="42949-104">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span> <span data-ttu-id="42949-105">Como resultado, no se devuelve ningún objeto y se produce un error de terminación.</span><span class="sxs-lookup"><span data-stu-id="42949-105">As a result, no objects are returned and a terminating error is thrown.</span></span>

## <a name="requirements"></a><span data-ttu-id="42949-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="42949-106">Requirements</span></span>

<span data-ttu-id="42949-107">Este ejemplo requiere Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="42949-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="42949-108">Muestra</span><span class="sxs-lookup"><span data-stu-id="42949-108">Demonstrates</span></span>

<span data-ttu-id="42949-109">Este ejemplo muestra lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="42949-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="42949-110">Creación de un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="42949-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="42949-111">Agregar comandos a la canalización de la [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="42949-111">Adding commands to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="42949-112">Adición de argumentos de parámetro a la canalización.</span><span class="sxs-lookup"><span data-stu-id="42949-112">Adding parameter arguments to the pipeline.</span></span>

- <span data-ttu-id="42949-113">Invocar los comandos de forma sincrónica.</span><span class="sxs-lookup"><span data-stu-id="42949-113">Invoking the commands synchronously.</span></span>

- <span data-ttu-id="42949-114">Uso de [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objetos para extraer y mostrar las propiedades de los objetos devueltos por los comandos.</span><span class="sxs-lookup"><span data-stu-id="42949-114">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the commands.</span></span>

- <span data-ttu-id="42949-115">Recuperar y mostrar los registros de error que se generaron durante la ejecución de los comandos.</span><span class="sxs-lookup"><span data-stu-id="42949-115">Retrieving and displaying error records that were generated during the running of the commands.</span></span>

- <span data-ttu-id="42949-116">Detectar y mostrar la terminación de las excepciones producidas por los comandos.</span><span class="sxs-lookup"><span data-stu-id="42949-116">Catching and displaying terminating exceptions thrown by the commands.</span></span>

## <a name="example"></a><span data-ttu-id="42949-117">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="42949-117">Example</span></span>

<span data-ttu-id="42949-118">Este ejemplo ejecuta los comandos de forma sincrónica en el espacio de ejecución predeterminada proporcionada por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42949-118">This sample runs commands synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="42949-119">El último comando produce un error de terminación, ya que se pasa un argumento de parámetro que no es válido para el comando.</span><span class="sxs-lookup"><span data-stu-id="42949-119">The last command throws a terminating error because a parameter argument that is not valid is passed to the command.</span></span> <span data-ttu-id="42949-120">Se capturan y se muestra el error de terminación.</span><span class="sxs-lookup"><span data-stu-id="42949-120">The terminating error is trapped and displayed.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="42949-121">Véase también</span><span class="sxs-lookup"><span data-stu-id="42949-121">See Also</span></span>

[<span data-ttu-id="42949-122">Escribir una aplicación de Host de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="42949-122">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)