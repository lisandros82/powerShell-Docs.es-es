---
title: Ejemplo GetProcessSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068069"
---
# <a name="getprocesssample01-sample"></a><span data-ttu-id="7b7d3-102">Ejemplo GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="7b7d3-102">GetProcessSample01 Sample</span></span>

<span data-ttu-id="7b7d3-103">En este ejemplo se muestra cómo implementar un cmdlet que recupera los procesos en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="7b7d3-104">Este cmdlet es una versión simplificada de la `Get-Process` cmdlet proporcionada por Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-104">This cmdlet is a simplified version of the `Get-Process` cmdlet that is provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="7b7d3-105">Cómo generar el ejemplo mediante Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="7b7d3-106">Con Windows PowerShell 2.0 instalado el SDK, vaya a la carpeta GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample01 folder.</span></span> <span data-ttu-id="7b7d3-107">La ubicación predeterminada es C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span></span>

2. <span data-ttu-id="7b7d3-108">Haga doble clic en el icono del archivo de solución (.sln).</span><span class="sxs-lookup"><span data-stu-id="7b7d3-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="7b7d3-109">Se abre el proyecto de ejemplo en Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="7b7d3-110">En el **compilar** menú, seleccione **compilar solución**.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-110">In the **Build** menu, select **Build Solution**.</span></span>

  <span data-ttu-id="7b7d3-111">En las carpetas \bin o \bin\debug de forma predeterminada, se compilará la biblioteca para el ejemplo.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="7b7d3-112">Cómo ejecutar el ejemplo</span><span class="sxs-lookup"><span data-stu-id="7b7d3-112">How to run the sample</span></span>

1. <span data-ttu-id="7b7d3-113">Abra una ventana del símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-113">Open a Command Prompt window.</span></span>

2. <span data-ttu-id="7b7d3-114">Navegue hasta el directorio que contiene el archivo .dll de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-114">Navigate to the directory containing the sample .dll file.</span></span>

3. <span data-ttu-id="7b7d3-115">Ejecute installutil "GetProcessSample01.dll".</span><span class="sxs-lookup"><span data-stu-id="7b7d3-115">Run installutil "GetProcessSample01.dll".</span></span>

4. <span data-ttu-id="7b7d3-116">Inicie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-116">Start Windows PowerShell.</span></span>

5. <span data-ttu-id="7b7d3-117">Ejecute el siguiente comando para agregar el complemento en el shell.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-117">Run the following command to add the snap-in to the shell.</span></span>

   `Add-PSSnapin GetProcPSSnapIn01`

6. <span data-ttu-id="7b7d3-118">Escriba el siguiente comando para ejecutar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-118">Enter the following command to run the cmdlet.</span></span> `get-proc`

   `get-proc`

   <span data-ttu-id="7b7d3-119">Se trata de una salida de ejemplo que da como resultado de los siguientes pasos.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-119">This is a sample output that results from following these steps.</span></span>

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a><span data-ttu-id="7b7d3-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b7d3-120">Requirements</span></span>

<span data-ttu-id="7b7d3-121">Este ejemplo requiere Windows PowerShell 1.0 o posterior.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-121">This sample requires Windows PowerShell 1.0 or later.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7b7d3-122">Muestra</span><span class="sxs-lookup"><span data-stu-id="7b7d3-122">Demonstrates</span></span>

<span data-ttu-id="7b7d3-123">Este ejemplo muestra lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="7b7d3-124">Creación de un cmdlet de ejemplo básica.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-124">Creating a basic sample cmdlet.</span></span>

- <span data-ttu-id="7b7d3-125">Definir una clase de cmdlet mediante el atributo de Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-125">Defining a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="7b7d3-126">Crear un complemento que funciona con Windows PowerShell 1.0 y 2.0 de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-126">Creating a snap-in that works with both Windows PowerShell 1.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="7b7d3-127">Los ejemplos siguientes muestran usan módulos en lugar de complementos, por lo que requieren Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-127">Subsequent samples use modules instead of snap-ins so they require Windows PowerShell 2.0.</span></span>

## <a name="example"></a><span data-ttu-id="7b7d3-128">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7b7d3-128">Example</span></span>

<span data-ttu-id="7b7d3-129">Este ejemplo muestra cómo crear un cmdlet sencillo y su complemento.</span><span class="sxs-lookup"><span data-stu-id="7b7d3-129">This sample shows how to create a simple cmdlet and its snap-in.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a><span data-ttu-id="7b7d3-130">Véase también</span><span class="sxs-lookup"><span data-stu-id="7b7d3-130">See Also</span></span>

[<span data-ttu-id="7b7d3-131">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7b7d3-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)