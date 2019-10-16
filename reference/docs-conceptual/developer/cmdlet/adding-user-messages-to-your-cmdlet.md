---
title: Agregando mensajes de usuario al cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 1e048f6ae94ac226218c18c8f8f7590a4db26226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370074"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Adición de mensajes de usuario al cmdlet

Los cmdlets pueden escribir varios tipos de mensajes que el tiempo de ejecución de Windows PowerShell puede mostrar al usuario. Estos mensajes incluyen los siguientes tipos:

- Mensajes detallados que contienen información general del usuario.

- Depure mensajes que contengan información de solución de problemas.

- Mensajes de advertencia que contienen una notificación de que el cmdlet está a punto de realizar una operación que puede tener resultados inesperados.

- Progreso de los mensajes de informe que contienen información sobre cuánto trabajo ha completado el cmdlet al realizar una operación que tarda mucho tiempo.

No hay ningún límite en cuanto al número de mensajes que el cmdlet puede escribir o el tipo de mensajes que escribe el cmdlet. Cada mensaje se escribe realizando una llamada específica desde el método de procesamiento de entrada del cmdlet.

## <a name="defining-the-cmdlet"></a>Definición del cmdlet

El primer paso en la creación de un cmdlet es siempre nombrar el cmdlet y declarar la clase .NET que implementa el cmdlet. Cualquier tipo de cmdlet puede escribir notificaciones de usuario desde sus métodos de procesamiento de entrada; por lo tanto, en general, puede asignar un nombre a este cmdlet con cualquier verbo que indique qué modificaciones del sistema realiza el cmdlet. Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).

El cmdlet Stop-proc está diseñado para modificar el sistema; por lo tanto, la declaración [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) de la clase .net debe incluir la palabra clave de atributo `SupportsShouldProcess` y establecerse en `true`.

El código siguiente es la definición de esta clase de cmdlet Stop-proc. Para obtener más información acerca de esta definición, consulte [crear un cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definir parámetros para la modificación del sistema

El cmdlet Stop-proc define tres parámetros: `Name`, `Force` y `PassThru`. Para obtener más información sobre cómo definir estos parámetros, consulte [crear un cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md).

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

El cmdlet debe invalidar un método de procesamiento de entrada. a menudo, será [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Este cmdlet Stop-proc invalida el método de procesamiento de entrada [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . En esta implementación del cmdlet Stop-proc, se realizan llamadas para escribir mensajes detallados, mensajes de depuración y mensajes de advertencia.

> [!NOTE]
> Para obtener más información sobre cómo este método llama a los métodos [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , consulte [crear un cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>Escribir un mensaje detallado

El método [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) se usa para escribir información general de nivel de usuario que no está relacionada con condiciones de error específicas. A continuación, el administrador del sistema puede usar esa información para continuar procesando otros comandos. Además, toda la información escrita con este método debe localizarse según sea necesario.

El siguiente código de este cmdlet Stop-proc muestra dos llamadas al método [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) desde la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>Escribir un mensaje de depuración

El método [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) se usa para escribir mensajes de depuración que se pueden usar para solucionar problemas del funcionamiento del cmdlet. La llamada se realiza desde un método de procesamiento de entrada.

> [!NOTE]
> Windows PowerShell también define un parámetro `Debug` que presenta información detallada y de depuración. Si el cmdlet admite este parámetro, no es necesario llamar a [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) en el mismo código que llama a [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).

Las dos secciones siguientes del código del cmdlet Stop-proc de ejemplo muestran llamadas al método [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) desde la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

Este mensaje de depuración se escribe inmediatamente antes de que se llame a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Este mensaje de depuración se escribe inmediatamente antes de que se llame a [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell enruta automáticamente cualquier llamada a [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) a la infraestructura de seguimiento y a los cmdlets. Esto permite realizar el seguimiento de las llamadas de método a la aplicación de hospedaje, a un archivo o a un depurador sin necesidad de realizar ningún trabajo de desarrollo adicional en el cmdlet. La entrada de línea de comandos siguiente implementa una operación de seguimiento.

**PS > trace-Expression STOP-proc-File proc. log-comando STOP-proc Notepad**

## <a name="writing-a-warning-message"></a>Escribir un mensaje de advertencia

El método [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) se usa para escribir una advertencia cuando el cmdlet está a punto de realizar una operación que podría tener un resultado inesperado, por ejemplo, sobrescribir un archivo de solo lectura.

El siguiente código del cmdlet Stop-proc de ejemplo muestra la llamada al método [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) de la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Escribir un mensaje de progreso

[System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) se usa para escribir mensajes de progreso cuando las operaciones de cmdlet tardan mucho tiempo en completarse. Una llamada a [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) pasa un objeto [System. Management. Automation. Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) que se envía a la aplicación de hospedaje para su representación al usuario.

> [!NOTE]
> Este cmdlet Stop-proc no incluye una llamada al método [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .

El código siguiente es un ejemplo de un mensaje de progreso escrito por un cmdlet que está intentando copiar un elemento.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>Código de ejemplo

Para obtener el C# código de ejemplo completo, vea el [ejemplo de StopProcessSample02](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Definir tipos de objeto y formato

Windows PowerShell pasa información entre cmdlets mediante objetos .NET. Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que el cmdlet tenga que extender un tipo existente proporcionado por otro cmdlet. Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Compilación del cmdlet

Después de implementar un cmdlet, debe registrarse con Windows PowerShell a través de un complemento de Windows PowerShell. Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Prueba del cmdlet

Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarlo mediante su ejecución en la línea de comandos. Vamos a probar el cmdlet Stop-proc de ejemplo. Para obtener más información sobre el uso de cmdlets desde la línea de comandos, consulte la [Introducción con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- La siguiente entrada de línea de comandos usa STOP-proc para detener el proceso denominado "Bloc de notas", proporcionar notificaciones detalladas e imprimir información de depuración.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

Aparece el siguiente resultado.

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a>Véase también

[Crear un cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Cómo crear un cmdlet de Windows PowerShell](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85))

[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
