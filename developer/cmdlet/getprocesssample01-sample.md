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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859841"
---
# <a name="getprocesssample01-sample"></a>Ejemplo GetProcessSample01

En este ejemplo se muestra cómo implementar un cmdlet que recupera los procesos en el equipo local. Este cmdlet es una versión simplificada de la `Get-Process` cmdlet proporcionada por Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Cómo generar el ejemplo mediante Visual Studio.

1. Con Windows PowerShell 2.0 instalado el SDK, vaya a la carpeta GetProcessSample01. La ubicación predeterminada es C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.

2. Haga doble clic en el icono del archivo de solución (.sln). Se abre el proyecto de ejemplo en Microsoft Visual Studio.

3. En el **compilar** menú, seleccione **compilar solución**.

  En las carpetas \bin o \bin\debug de forma predeterminada, se compilará la biblioteca para el ejemplo.

### <a name="how-to-run-the-sample"></a>Cómo ejecutar el ejemplo

1. Abra una ventana del símbolo del sistema.

2. Navegue hasta el directorio que contiene el archivo .dll de ejemplo.

3. Ejecute installutil "GetProcessSample01.dll".

4. Inicie Windows PowerShell.

5. Ejecute el siguiente comando para agregar el complemento en el shell.

   `Add-PSSnapin GetProcPSSnapIn01`

6. Escriba el siguiente comando para ejecutar el cmdlet. `get-proc`

   `get-proc`

   Se trata de una salida de ejemplo que da como resultado de los siguientes pasos.

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

Este ejemplo requiere Windows PowerShell 1.0 o posterior.

## <a name="demonstrates"></a>Demostraciones

Este ejemplo muestra lo siguiente.

- Creación de un cmdlet de ejemplo básica.

- Definir una clase de cmdlet mediante el atributo de Cmdlet.

- Crear un complemento que funciona con Windows PowerShell 1.0 y 2.0 de Windows PowerShell. Los ejemplos siguientes muestran usan módulos en lugar de complementos, por lo que requieren Windows PowerShell 2.0.

## <a name="example"></a>Ejemplo

Este ejemplo muestra cómo crear un cmdlet sencillo y su complemento.

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