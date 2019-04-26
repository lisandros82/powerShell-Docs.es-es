---
title: Creación de un Cmdlet que modifica el sistema | Microsoft Docs
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
ms.openlocfilehash: bbe9f0213754d1cc47e0fd9a7a898bde916c0636
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068453"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Creación de un cmdlet que modifica el sistema

A veces, un cmdlet debe modificar el estado de ejecución del sistema, no solo el estado del tiempo de ejecución de Windows PowerShell. En estos casos, el cmdlet debe permitir al usuario una oportunidad de confirmar si desea realizar el cambio o no.

Para admitir la confirmación de un cmdlet debe hacer dos cosas.

- Declarar que el cmdlet admite confirmación cuando se especifica la [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo estableciendo la palabra clave SupportsShouldProcess en `true`.

- Llame a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) durante la ejecución del cmdlet (como se muestra en el ejemplo siguiente).

Admitiendo la confirmación, se expone un cmdlet el `Confirm` y `WhatIf` parámetros que se proporcionan mediante Windows PowerShell y también con las directrices de desarrollo de cmdlets (para obtener más información acerca de las instrucciones de desarrollo de cmdlet, consulte [ Las instrucciones de desarrollo de cmdlet](./cmdlet-development-guidelines.md).).

## <a name="changing-the-system"></a>Cambio del sistema

El acto de "cambiar el sistema" hace referencia a cualquier cmdlet que potencialmente se cambia el estado del sistema fuera de Windows PowerShell. Por ejemplo, detener un proceso, habilitar o deshabilitar una cuenta de usuario o agregar una fila a una tabla de base de datos son todos los cambios en el sistema que se debe confirmar. En cambio, las operaciones que leerán los datos o establecer las conexiones transitorias no cambian el sistema y generalmente no requieren confirmación. Confirmación también no es necesaria para las acciones cuyo efecto se limita a dentro del tiempo de ejecución de Windows PowerShell, como `set-variable`. Debe declarar los cmdlets que puede o no se puede hacer un cambio definitivo `SupportsShouldProcess` y llamar a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solo si va a realizar un cambio definitivo.

> [!NOTE]
> Confirmación de ShouldProcess se aplica únicamente a los cmdlets. Si un comando o script modifica el estado de ejecución de un sistema llamando directamente a propiedades o métodos. NET, o por aplicaciones que realizan llamadas fuera de Windows PowerShell, esta forma de confirmación no estará disponible.

## <a name="the-stopproc-cmdlet"></a>El StopProc Cmdlet

Este tema describe un cmdlet Stop-Proc que intenta detener los procesos que se recuperan mediante el cmdlet Get-Proc (se describe en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Temas de esta sección incluyen lo siguiente:

- [Definir el Cmdlet](#Defining-the-Cmdlet)

- [Definir parámetros para la modificación del sistema](#Defining-Parameters-for-System-Modification)

- [Reemplazar una método de procesamiento de entrada](#Overriding-an-Input-Processing-Method)

- [Una llamada al método ShouldProcess](#Calling-the-ShouldProcess-Method)

- [Una llamada al método ShouldContinue](#Calling-the-ShouldContinue-Method)

- [Detener procesamiento de entrada](#Stopping-Input-Processing)

- [Ejemplo de código](#Code-Sample)

- [Definir los tipos de objeto y el formato](#Defining-Object-Types-and-Formatting)

- [Compilar el Cmdlet](#Building-the-Cmdlet)

- [Probar el Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definir el Cmdlet

El primer paso en la creación de cmdlet siempre es el cmdlet de nomenclatura y declarar la clase de .NET que implementa el cmdlet. Dado que está escribiendo un cmdlet para cambiar el sistema, debe llamarse en consecuencia. Este procesos del sistema se detiene de cmdlet, por lo que el nombre del verbo seleccionado aquí es "Stop" definen por el [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) (clase), con el sustantivo "Proc" para indicar que el cmdlet detiene los procesos. Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

La siguiente es la definición de clase para este cmdlet Stop-Proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

Tenga en cuenta que, en el [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaración, el `SupportsShouldProcess` palabra clave de atributo está establecido en `true` para habilitar el cmdlet realizar llamadas a [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Sin este conjunto de palabra clave, el `Confirm` y `WhatIf` parámetros no estarán disponibles para el usuario.

### <a name="extremely-destructive-actions"></a>Acciones destructivas extremadamente

Algunas operaciones son extremadamente destructivas, como volver a formatear una partición de disco duro activo. En estos casos, debe establecer el cmdlet `ConfirmImpact`  =  `ConfirmImpact.High` al declarar el [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo. Esta opción fuerza el cmdlet para solicitar la confirmación de usuario incluso cuando el usuario no ha especificado el `Confirm` parámetro. Sin embargo, los desarrolladores de cmdlets deben evitar el uso excesivo `ConfirmImpact` para las operaciones que son simplemente potencialmente destructivas, como la eliminación de una cuenta de usuario. Recuerde que si `ConfirmImpact` está establecido en [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).

De forma similar, algunas operaciones suelen ser destructivo, aunque en teoría modifican el estado de ejecución de un sistema fuera de Windows PowerShell. Puede establecer estos cmdlets `ConfirmImpact` a [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). Esto pasará por alto las solicitudes de confirmación que ha solicitado el usuario para confirmar las operaciones solo impacto medio y alto impacto.

## <a name="defining-parameters-for-system-modification"></a>Definir parámetros para la modificación del sistema

En esta sección se describe cómo definir los parámetros del cmdlet, las que son necesarios para la modificación del sistema de soporte técnico incluidas. Consulte [agregar parámetros esa entrada de línea de comandos de proceso](./adding-parameters-that-process-command-line-input.md) si necesita obtener información general acerca de cómo definir parámetros.

El cmdlet Stop-Proc define tres parámetros: `Name`, `Force`, y `PassThru`.

El `Name` parámetro corresponde a la `Name` propiedad del objeto de entrada de proceso. Tenga en cuenta que el `Name` parámetro en este ejemplo es obligatorio, como el cmdlet se producirá un error si no tiene un proceso con nombre a detener.

El `Force` parámetro permite al usuario reemplazar las llamadas a [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). De hecho, cualquier cmdlet que llama [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) debe tener un `Force` parámetro para que cuando `Force` se especifica, el cmdlet omite la llamada a [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) y continúa con la operación. Tenga en cuenta que esto no afecta a las llamadas a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).

El `PassThru` parámetro permite al usuario indicar si el cmdlet pasa un objeto de salida a través de la canalización, en este caso, cuando se haya detenido un proceso. Tenga en cuenta que este parámetro está relacionado con el cmdlet propia en lugar de a una propiedad del objeto de entrada.

Aquí es la declaración de parámetro para el cmdlet Stop-Proc.

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

## <a name="overriding-an-input-processing-method"></a>Reemplazar una método de procesamiento de entrada

El cmdlet debe invalidar una método de procesamiento de entrada. El código siguiente ilustra la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) invalidación que se usa en el cmdlet Stop-Proc de ejemplo. Para cada uno solicita el nombre del proceso, este método garantiza que el proceso no es un proceso especial, intenta detener el proceso y, a continuación, envía un objeto de salida si el `PassThru` se especifica el parámetro.

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

## <a name="calling-the-shouldprocess-method"></a>Una llamada al método ShouldProcess

El método de su cmdlet de procesamiento de entrada debe llamar a la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para confirmar la ejecución de una operación antes de que se realiza un cambio (por ejemplo, la eliminación de archivos) en el estado de ejecución del sistema. Esto permite que el tiempo de ejecución de Windows PowerShell proporcionar el comportamiento correcto de "WhatIf" y "Confirmar" en el shell.

> [!NOTE]
> Si un cmdlet indica que es compatible con debe procesar y se produce un error al realizar la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) llamar a, el usuario podría modificar el sistema de forma inesperada.

La llamada a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) envía el nombre del recurso que se puede cambiar para el usuario, con el tiempo de ejecución de Windows PowerShell teniendo en cuenta cualquier configuración de línea de comandos o variables de preferencia determinar lo que debe mostrarse al usuario.

El ejemplo siguiente muestra la llamada a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) de reemplazar el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método en el ejemplo Cmdlet Stop-Proc.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>Una llamada al método ShouldContinue

La llamada a la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método envía un mensaje secundario para el usuario. Esta llamada se realiza después de llamar a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) devuelve `true` y si el `Force` parámetro no se estableció en `true`. El usuario, a continuación, puede proporcionar comentarios para indicar si se debe continuar la operación. Las llamadas de cmdlet [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) como una comprobación adicional para las modificaciones del sistema potencialmente peligroso o cuando desee proporcionar opciones sí a todo y no a todo al usuario.

El ejemplo siguiente muestra la llamada a [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) de reemplazar el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método en el ejemplo Cmdlet Stop-Proc.

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

## <a name="stopping-input-processing"></a>Detener procesamiento de entrada

El método de un cmdlet que realiza modificaciones en el sistema de procesamiento de entrada debe proporcionar una manera de detener el procesamiento de entrada. En el caso de este cmdlet Stop-Proc, se realiza una llamada desde el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método a la [System.Diagnostics.Process.Kill*](/dotnet/api/System.Diagnostics.Process.Kill) método. Dado que el `PassThru` parámetro está establecido en `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) también llama a [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) para enviar el objeto de proceso a la canalización.

## <a name="code-sample"></a>Ejemplo de código

Para la completa C# código de ejemplo, vea [StopProcessSample01 ejemplo](./stopprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir los tipos de objeto y el formato

Windows PowerShell pasa información entre cmdlets mediante objetos. NET. Por lo tanto, un cmdlet que deba definir su propio tipo o el cmdlet puede necesitar extender un tipo existente proporcionado por otro cmdlet. Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Compilar el Cmdlet

Después de implementar un cmdlet, se debe registrar con Windows PowerShell a través de un complemento de Windows PowerShell. Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Probar el Cmdlet

Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarla mediante la ejecución de la línea de comandos. Estas son varias pruebas que comprueban el cmdlet Stop-Proc. Para obtener más información sobre el uso de cmdlets de la línea de comandos, consulte el [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Inicie Windows PowerShell y use el cmdlet Stop-Proc para detener el procesamiento, como se muestra a continuación. Dado que el cmdlet especifica la `Name` parámetro como obligatorios, las consultas de cmdlet para el parámetro.

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

- Use Stop-Proc tal como se muestra para detener el proceso crítico denominado "WINLOGON". Se le pida y advierte acerca de cómo realizar esta acción porque hará que el sistema operativo se reinicie.

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

- Vamos a probar ahora detener el proceso WINLOGON sin recibir una advertencia. Tenga en cuenta que esta entrada de comando utiliza el `Force` parámetro para invalidar la advertencia.

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

[Adición de parámetros que procesa la entrada de línea de comandos](./adding-parameters-that-process-command-line-input.md)

[Extensión de tipos de objeto y el formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Ejemplos de cmdlet](./cmdlet-samples.md)