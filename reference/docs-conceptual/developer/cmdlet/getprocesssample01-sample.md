---
title: Ejemplo de GetProcessSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369734"
---
# <a name="getprocesssample01-sample"></a>Ejemplo GetProcessSample01

Este ejemplo muestra cómo implementar un cmdlet que recupera los procesos en el equipo local. Este cmdlet es una versión simplificada del cmdlet `Get-Process` proporcionado por Windows PowerShell 2,0.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Cómo compilar el ejemplo mediante Visual Studio.

1. Con el SDK de Windows PowerShell 2,0 instalado, vaya a la carpeta GetProcessSample01. La ubicación predeterminada es C:\Archivos de programa (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.

2. Haga doble clic en el icono del archivo de solución (. sln). Se abrirá el proyecto de ejemplo en Microsoft Visual Studio.

3. En el menú **Compilar**, seleccione **Compilar solución**.

  La biblioteca del ejemplo se generará en las carpetas \Bin o \bin\debug predeterminadas.

### <a name="how-to-run-the-sample"></a>Ejecución del ejemplo

1. Abra una ventana del símbolo del sistema.

2. Navegue hasta el directorio que contiene el archivo. dll de ejemplo.

3. Ejecute InstallUtil "GetProcessSample01. dll".

4. Inicie Windows PowerShell.

5. Ejecute el siguiente comando para agregar el complemento al shell.

   `Add-PSSnapin GetProcPSSnapIn01`

6. Escriba el siguiente comando para ejecutar el cmdlet. `get-proc`

   `get-proc`

   Esta es una salida de ejemplo que se obtiene al seguir estos pasos.

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

## <a name="requirements"></a>Requisitos

Este ejemplo requiere Windows PowerShell 1,0 o posterior.

## <a name="demonstrates"></a>Demuestra

Este ejemplo muestra lo siguiente.

- Crear un cmdlet de ejemplo básico.

- Definir una clase de cmdlet mediante el atributo de cmdlet.

- Crear un complemento que funcione con Windows PowerShell 1,0 y Windows PowerShell 2,0. Los ejemplos siguientes usan módulos en lugar de complementos para que requieran Windows PowerShell 2,0.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo crear un cmdlet simple y su complemento.

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

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)