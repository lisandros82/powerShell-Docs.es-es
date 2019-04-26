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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068035"
---
# <a name="getprocesssample04-sample"></a>Ejemplo GetProcessSample04

En este ejemplo se muestra cómo implementar un cmdlet que recupera los procesos en el equipo local. Si se produce un error al recuperar un proceso genera un error de no terminación. Este cmdlet es una versión simplificada de la `Get-Process` cmdlet proporcionado por Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Cómo generar el ejemplo desde Visual Studio.

1. Con Windows PowerShell 2.0 instalado el SDK, vaya a la carpeta GetProcessSample04. La ubicación predeterminada es C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.

2. Haga doble clic en el icono del archivo de solución (.sln). Se abrirá el proyecto de ejemplo en Visual Studio.

3. En el **compilar** menú, seleccione **compilar solución**.

    En las carpetas \bin o \bin\debug de forma predeterminada, se compilará la biblioteca para el ejemplo.

### <a name="how-to-run-the-sample"></a>Cómo ejecutar el ejemplo

1. Cree la siguiente carpeta del módulo:

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. Copie el ensamblado de ejemplo en la carpeta del módulo.

3. Inicie Windows PowerShell.

4. Ejecute el siguiente comando para cargar el ensamblado en Windows PowerShell:

    `Import-module getprossessample04`

5. Ejecute el siguiente comando para ejecutar el cmdlet:

    `get-proc`

## <a name="requirements"></a>Requisitos

Este ejemplo requiere Windows PowerShell 2.0.

## <a name="demonstrates"></a>Muestra

Este ejemplo muestra lo siguiente.

- Declarar una clase de cmdlet mediante el atributo de Cmdlet.

- Declarar un parámetro de cmdlet mediante el atributo de parámetro.

- Especifica la posición del parámetro.

- Especifica que el parámetro toma como entrado de la canalización. La entrada se puede obtener de un objeto o un valor de una propiedad de un objeto cuyo nombre de propiedad es el mismo que el nombre del parámetro.

- Declarar un atributo de validación para el parámetro de entrada.

- Interceptar un error de no terminación y escribir un mensaje de error en la secuencia de error.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo crear un cmdlet que controla los errores de no terminación y escribe los mensajes de error en la secuencia de error.

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

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
