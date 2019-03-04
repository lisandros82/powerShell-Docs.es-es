---
title: Agregar mensajes de usuario al Cmdlet | Microsoft Docs
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
ms.openlocfilehash: ffc08d2713c4bfc0938b2e07146102af8b5467d2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855991"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Adición de mensajes de usuario al cmdlet

Cmdlets puede escribir varios tipos de mensajes que se pueden mostrar al usuario el tiempo de ejecución de Windows PowerShell. Estos mensajes incluyen los siguientes tipos:

- Mensajes detallados que contengan información general del usuario.

- Los mensajes que contienen información de solución de problemas de depuración.

- Los mensajes de advertencia que contienen una notificación de que el cmdlet que se va a realizar una operación que puede tener resultados inesperados.

- Informe de progreso de los mensajes que contienen información sobre la cantidad funcionar el cmdlet se ha completado cuando se realiza una operación que tarda mucho tiempo.

No hay ningún límite al número de mensajes que puede escribir el cmdlet o el tipo de mensajes que el cmdlet escribe. Cada mensaje se escribe mediante una llamada específica desde dentro de la entrada que procesar el método de su cmdlet.

## <a name="the-stopproc-cmdlet"></a>El StopProc Cmdlet

Temas de esta sección incluyen lo siguiente:

- [Definir el Cmdlet](#Defining-the-Cmdlet)

- [Definir parámetros para la modificación del sistema](#Defining-Parameters-for-System-Modification)

- [Reemplazar una método de procesamiento de entrada](#Overriding-an-Input-Processing-Method)

- [Escribir un mensaje detallado](#Writing-a-Verbose-Message)

- [Escribir un mensaje de depuración](#Writing-a-Debug-Message)

- [Escribir un mensaje de advertencia](#Writing-a-Warning-Message)

- [Escribir un mensaje de progreso](#Writing-a-Progress-Message)

- [Ejemplo de código](#Code-Sample)

- [Definir tipos de objeto y el formato](#Define-Object-Types-and-Formatting)

- [Compilar el Cmdlet](#Building-the-Cmdlet)

- [Probar el Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definir el Cmdlet

El primer paso en la creación de cmdlet siempre es el cmdlet de nomenclatura y declarar la clase de .NET que implementa el cmdlet. Cualquier tipo de cmdlet puede escribir las notificaciones de usuario desde su entrada de procesamiento de los métodos; en general, por lo tanto, puede asignar este cmdlet con cualquier verbo que indica qué modificaciones en el sistema realiza el cmdlet. Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

El cmdlet Stop-Proc está diseñado para modificar el sistema; por lo tanto, el [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) debe incluir la declaración de la clase .NET del `SupportsShouldProcess` palabra clave de atributo y se puede establecer en `true`.

El código siguiente es la definición para esta clase de cmdlet Stop-Proc. Para obtener más información acerca de esta definición, consulte [creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definir parámetros para la modificación del sistema

El cmdlet Stop-Proc define tres parámetros: `Name`, `Force`, y `PassThru`. Para obtener más información acerca de cómo definir estos parámetros, vea [creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md).

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

El cmdlet debe invalidar una método de procesamiento de entrada, con más frecuencia será [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Este cmdlet Stop-Proc invalida la [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método de procesamiento de entrada. En esta implementación del cmdlet Stop-Proc, se realizan llamadas a escribir los mensajes detallados, mensajes de depuración y los mensajes de advertencia.

> [!NOTE]
> Para obtener más información acerca de cómo este método llama a la [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos, vea [Creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>Escribir un mensaje detallado

El [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método se utiliza para escribir información general de nivel de usuario que no está relacionado con las condiciones de error específico. El administrador del sistema, a continuación, puede usar esa información para continuar procesando otros comandos. Además, toda la información escrita con este método se debe traducir, según sea necesario.

El siguiente código de este cmdlet Stop-Proc muestra dos llamadas a la [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método desde el reemplazo de la [System.Management.Automation.Cmdlet.Processrecord* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.

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

El [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método se utiliza para escribir mensajes de depuración que se pueden usar para solucionar problemas de funcionamiento del cmdlet. La llamada se realiza desde una método de procesamiento de entrada.

> [!NOTE]
> Windows PowerShell también define un `Debug` parámetro que presenta ambos detallado y la información de depuración. Si el cmdlet es compatible con este parámetro, no necesita llamar a [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) en el mismo código que llama a [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).

Las dos secciones de código desde el cmdlet Stop-Proc de ejemplo siguientes muestran las llamadas a la [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método desde el reemplazo de la [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.

Este mensaje de depuración se escribe inmediatamente antes de [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) se llama.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Este mensaje de depuración se escribe inmediatamente antes de [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) se llama.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell se enruta automáticamente cualquier [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) las llamadas a los cmdlets y la infraestructura de seguimiento. Esto permite que las llamadas de método realizar un seguimiento a un depurador, un archivo o la aplicación de hospedaje sin tener que realizar ningún trabajo de desarrollo adicional en el cmdlet. La entrada de línea de comandos siguiente implementa una operación de seguimiento.

**PS > Detener seguimiento-expression-proc-archivo proc.log-Bloc de notas de comando stop-proc**

## <a name="writing-a-warning-message"></a>Escribir un mensaje de advertencia

El [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método se utiliza para escribir una advertencia cuando el cmdlet que se va a realizar una operación que podría tener un resultado inesperado, por ejemplo, sobrescribir un archivo de solo lectura.

El siguiente código desde el cmdlet Stop-Proc de ejemplo muestra la llamada a la [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método desde el reemplazo de la [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.

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

El [System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) se utiliza para escribir mensajes de progreso cuando las operaciones de cmdlet tienen un período prolongado de tiempo en completarse. Una llamada a [System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) pasa un [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) objeto que se envía a la aplicación de hospedaje para representar al usuario.

> [!NOTE]
> Este cmdlet Stop-Proc no incluye una llamada a la [System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) método.

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

## <a name="code-sample"></a>Ejemplo de código

Para la completa C# código de ejemplo, vea [StopProcessSample02 ejemplo](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Definir tipos de objeto y el formato

Windows PowerShell pasa información entre cmdlets mediante objetos. NET. Por lo tanto, un cmdlet es posible que deba definir su propio tipo o el cmdlet que tenga que ampliar un tipo existente proporcionado por otro cmdlet. Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Compilar el Cmdlet

Después de implementar un cmdlet, se debe registrar con Windows PowerShell a través de un complemento de Windows PowerShell. Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Probar el Cmdlet

Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarla mediante la ejecución de la línea de comandos. Vamos a probar el cmdlet Stop-Proc de ejemplo. Para obtener más información sobre el uso de cmdlets de la línea de comandos, consulte el [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- La siguiente entrada de línea de comandos utiliza Stop-Proc para detener el proceso denominado "NOTEPAD", proporcionan notificaciones detalladas e imprimir la información de depuración.

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

[Crear un Cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Creación de un Cmdlet de Windows PowerShell](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Extensión de tipos de objeto y el formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
