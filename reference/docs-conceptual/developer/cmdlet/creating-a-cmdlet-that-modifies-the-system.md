---
title: Creación de un cmdlet que modifica el sistema | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365764"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Creación de un cmdlet que modifica el sistema

A veces, un cmdlet debe modificar el estado de ejecución del sistema, no solo el estado del tiempo de ejecución de Windows PowerShell. En estos casos, el cmdlet debe permitir que el usuario tenga la oportunidad de confirmar si se realiza el cambio.

Para admitir la confirmación, un cmdlet debe hacer dos cosas.

- Declare que el cmdlet admita la confirmación cuando especifique el atributo [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) estableciendo la palabra clave SupportsShouldProcess en `true`.

- Llame a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) durante la ejecución del cmdlet (como se muestra en el ejemplo siguiente).

Al admitir la confirmación, un cmdlet expone los parámetros `Confirm` y `WhatIf` proporcionados por Windows PowerShell y también cumple las directrices de desarrollo para cmdlets de (para obtener más información sobre las directrices de desarrollo de cmdlets, consulte [cmdlet Instrucciones de desarrollo](./cmdlet-development-guidelines.md)).

## <a name="changing-the-system"></a>Cambiar el sistema

La acción de "cambiar el sistema" hace referencia a cualquier cmdlet que pueda cambiar el estado del sistema fuera de Windows PowerShell. Por ejemplo, la detención de un proceso, la habilitación o deshabilitación de una cuenta de usuario o la adición de una fila a una tabla de base de datos son cambios en el sistema que deben confirmarse. Por el contrario, las operaciones que leen datos o establecen conexiones transitorias no cambian el sistema y, por lo general, no requieren confirmación. La confirmación tampoco es necesaria para las acciones cuyo efecto está limitado a dentro del tiempo de ejecución de Windows PowerShell, como `set-variable`. Los cmdlets que pueden o no hacer un cambio persistente deben declarar `SupportsShouldProcess` y llamar a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solo si están a punto de hacer un cambio persistente.

> [!NOTE]
> La confirmación de ShouldProcess solo se aplica a los cmdlets de. Si un comando o script modifica el estado de ejecución de un sistema llamando directamente a métodos o propiedades de .NET o llamando a aplicaciones fuera de Windows PowerShell, esta forma de confirmación no estará disponible.

## <a name="the-stopproc-cmdlet"></a>El cmdlet StopProc

En este tema se describe un cmdlet Stop-proc que intenta detener los procesos que se recuperan con el cmdlet Get-proc (descrito en [creación del primer cmdlet](./creating-a-cmdlet-without-parameters.md)).

## <a name="defining-the-cmdlet"></a>Definición del cmdlet

El primer paso en la creación de un cmdlet es siempre nombrar el cmdlet y declarar la clase .NET que implementa el cmdlet. Dado que está escribiendo un cmdlet para cambiar el sistema, debe denominarse en consecuencia. Este cmdlet detiene los procesos del sistema, por lo que el nombre del verbo elegido aquí es "STOP", definido por la clase [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , con el nombre "proc" para indicar que el cmdlet detiene los procesos. Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).

A continuación se encuentra la definición de clase para este cmdlet Stop-proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

Tenga en cuenta que en la declaración de [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) , la palabra clave del atributo `SupportsShouldProcess` está establecida en `true` para permitir que el cmdlet realice llamadas a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [ System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Sin esta palabra clave establecida, los parámetros `Confirm` y `WhatIf` no estarán disponibles para el usuario.

### <a name="extremely-destructive-actions"></a>Acciones extremadamente destructivas

Algunas operaciones son extremadamente destructivas, como volver a formatear una partición del disco duro activo. En estos casos, el cmdlet debe establecer `ConfirmImpact` @ no__t-1 @ no__t-2 al declarar el atributo [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) . Esta configuración obliga al cmdlet a solicitar la confirmación del usuario incluso cuando el usuario no ha especificado el parámetro `Confirm`. Sin embargo, los desarrolladores de cmdlets deben evitar sobreutilizar `ConfirmImpact` para las operaciones que son potencialmente destructivas, como eliminar una cuenta de usuario. Recuerde que si `ConfirmImpact` está establecido en [System. Management. Automation. ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.

De forma similar, es poco probable que algunas operaciones sean destructivas, aunque en teoría modifican el estado de ejecución de un sistema fuera de Windows PowerShell. Estos cmdlets pueden establecer `ConfirmImpact` en [System. Management. Automation. Confirmimpact. Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). Esto omitirá las solicitudes de confirmación en las que el usuario ha solicitado confirmar solo las operaciones de impacto medio y alto impacto.

## <a name="defining-parameters-for-system-modification"></a>Definir parámetros para la modificación del sistema

En esta sección se describe cómo definir los parámetros del cmdlet, incluidos los que son necesarios para admitir la modificación del sistema. Consulte [agregar parámetros que procesan la entrada de línea de comandos](./adding-parameters-that-process-command-line-input.md) si necesita información general sobre la definición de parámetros.

El cmdlet Stop-proc define tres parámetros: `Name`, `Force` y `PassThru`.

El parámetro `Name` corresponde a la propiedad `Name` del objeto de entrada del proceso. Tenga en cuenta que el parámetro `Name` de este ejemplo es obligatorio, ya que se producirá un error en el cmdlet si no tiene un proceso con nombre para detenerse.

El parámetro `Force` permite al usuario invalidar las llamadas a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). De hecho, cualquier cmdlet que llame a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) debe tener un parámetro `Force` para que cuando se especifique `Force`, el cmdlet omita la llamada a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) y continúa con la operación. Tenga en cuenta que esto no afecta a las llamadas a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).

El parámetro `PassThru` permite al usuario indicar si el cmdlet pasa un objeto de salida a través de la canalización, en este caso, después de que se detenga un proceso. Tenga en cuenta que este parámetro está asociado al propio cmdlet en lugar de a una propiedad del objeto de entrada.

Esta es la declaración de parámetro para el cmdlet Stop-proc.

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a>Reemplazar un método de procesamiento de entrada

El cmdlet debe invalidar un método de procesamiento de entrada. En el código siguiente se muestra la invalidación [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) usada en el cmdlet Stop-proc de ejemplo. Para cada nombre de proceso solicitado, este método garantiza que el proceso no es un proceso especial, intenta detener el proceso y, a continuación, envía un objeto de salida si se especifica el parámetro `PassThru`.

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a>Llamar al método ShouldProcess

El método de procesamiento de entrada del cmdlet debe llamar al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) para confirmar la ejecución de una operación antes de que se realice un cambio (por ejemplo, la eliminación de archivos) en el estado de ejecución del sistema. Esto permite que el tiempo de ejecución de Windows PowerShell proporcione el comportamiento correcto de "WhatIf" y "CONFIRM" dentro del shell.

> [!NOTE]
> Si un cmdlet indica que admite debe procesar y no puede realizar la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , el usuario podría modificar el sistema de forma inesperada.

La llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) envía el nombre del recurso que se va a cambiar al usuario, con el tiempo de ejecución de Windows PowerShell teniendo en cuenta cualquier configuración de línea de comandos o variables de preferencia para determinar qué debe mostrarse al usuario.

En el ejemplo siguiente se muestra la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) desde la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) en el cmdlet Stop-proc de ejemplo.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>Llamar al método ShouldContinue

La llamada al método [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) envía un mensaje secundario al usuario. Esta llamada se realiza después de que la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) devuelve `true` y si el parámetro `Force` no se estableció en `true`. A continuación, el usuario puede proporcionar comentarios para indicar si la operación debe continuar. El cmdlet llama a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) como una comprobación adicional para las modificaciones potencialmente peligrosas del sistema o cuando desea proporcionar al usuario opciones de sí a todo y de no a todos.

En el ejemplo siguiente se muestra la llamada a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) desde la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) en el cmdlet Stop-proc de ejemplo.

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a>Detener el procesamiento de la entrada

El método de procesamiento de entrada de un cmdlet que realiza modificaciones en el sistema debe proporcionar una manera de detener el procesamiento de la entrada. En el caso de este cmdlet Stop-proc, se realiza una llamada desde el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) al método [System. Diagnostics. Process. Kill *](/dotnet/api/System.Diagnostics.Process.Kill) . Dado que el parámetro `PassThru` se establece en `true`, [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) también llama a [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) para enviar el objeto de proceso a la canalización.

## <a name="code-sample"></a>Código de ejemplo

Para obtener el C# código de ejemplo completo, vea el [ejemplo de StopProcessSample01](./stopprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto y formato

Windows PowerShell pasa información entre cmdlets mediante objetos .net. Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que el cmdlet tenga que extender un tipo existente proporcionado por otro cmdlet. Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Compilación del cmdlet

Después de implementar un cmdlet, debe registrarse con Windows PowerShell a través de un complemento de Windows PowerShell. Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Prueba del cmdlet

Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarlo mediante su ejecución en la línea de comandos. A continuación se muestran varias pruebas que prueban el cmdlet Stop-proc. Para obtener más información sobre el uso de cmdlets desde la línea de comandos, consulte la [Introducción con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Inicie Windows PowerShell y use el cmdlet Stop-proc para detener el procesamiento, como se muestra a continuación. Dado que el cmdlet especifica el parámetro `Name` como obligatorio, el cmdlet consulta el parámetro.

    ```powershell
    PS> stop-proc
    ```

Aparece el siguiente resultado.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- Ahora vamos a usar el cmdlet para detener el proceso denominado "NOTEPAD". El cmdlet le pide que confirme la acción.

    ```powershell
    PS> stop-proc -Name notepad
    ```

Aparece el siguiente resultado.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Use STOP-proc como se muestra para detener el proceso crítico denominado "WINLOGON". Se le pedirá que le avise sobre cómo realizar esta acción porque hará que el sistema operativo se reinicie.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

Aparece el siguiente resultado.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- Ahora vamos a intentar detener el proceso WINLOGON sin recibir una advertencia. Tenga en cuenta que esta entrada de comando usa el parámetro `Force` para invalidar la advertencia.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

Aparece el siguiente resultado.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Véase también

[Agregar parámetros que procesan la entrada de la línea de comandos](./adding-parameters-that-process-command-line-input.md)

[Extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85))

[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Ejemplos de cmdlet](./cmdlet-samples.md)