---
title: Ejemplo GetProcessSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856481"
---
# <a name="getprocesssample03-sample"></a>Ejemplo GetProcessSample03

En este ejemplo se muestra cómo implementar un cmdlet que recupera los procesos en el equipo local. Proporciona un `Name` parámetro que puede aceptar un objeto de la canalización o un valor de una propiedad de un objeto cuyo nombre de propiedad es el mismo que el nombre del parámetro. Este cmdlet es una versión simplificada de la `Get-Process` cmdlet proporcionado por Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Cómo generar el ejemplo desde Visual Studio.

1. Con Windows PowerShell 2.0 instalado el SDK, vaya a la carpeta GetProcessSample03. La ubicación predeterminada es C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.

2. Haga doble clic en el icono del archivo de solución (.sln). Se abrirá el proyecto de ejemplo en Visual Studio.

3. En el **compilar** menú, seleccione **compilar solución**.

    En las carpetas \bin o \bin\debug de forma predeterminada, se compilará la biblioteca para el ejemplo.

### <a name="how-to-run-the-sample"></a>Cómo ejecutar el ejemplo

1. Cree la siguiente carpeta del módulo:

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. Copie el ensamblado de ejemplo en la carpeta del módulo.

3. Inicie Windows PowerShell.

4. Ejecute el siguiente comando para cargar el ensamblado en Windows PowerShell:

    `Import-module getprossessample03`

5. Ejecute el siguiente comando para ejecutar el cmdlet:

    `get-proc`

## <a name="requirements"></a>Requisitos

Este ejemplo requiere Windows PowerShell 2.0.

## <a name="demonstrates"></a>Demostraciones

Este ejemplo muestra lo siguiente.

- Declarar una clase de cmdlet mediante el atributo de Cmdlet.

- Declarar un parámetro de cmdlet mediante el atributo de parámetro.

- Especifica la posición del parámetro.

- Especifica que el parámetro toma como entrado de la canalización. La entrada se puede obtener de un objeto o un valor de una propiedad de un objeto cuyo nombre de propiedad es el mismo que el nombre del parámetro.

- Declarar un atributo de validación para el parámetro de entrada.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra una implementación del cmdlet Get-Proc que incluye un `Name` parámetro que acepta la entrada de la canalización.

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

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
