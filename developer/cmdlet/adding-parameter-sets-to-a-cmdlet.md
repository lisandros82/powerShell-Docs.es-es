---
title: Adición de parámetro se establece en un Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: f0bff11618c18bf53b9c2a185445795a17306fa3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054992"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Adición de conjuntos de parámetros a un cmdlet

En esta sección se describe cómo agregar el parámetro se establece en el cmdlet Stop-Proc (se describe en [creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md)). Al igual que los otros cmdlets de parada de proceso se describe en esta guía del programador, intentos de este cmdlet detener los procesos que se recuperan mediante el cmdlet Get-Proc (se describe en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Temas de esta sección incluyen lo siguiente:

- [Cosas que saber acerca de conjuntos de parámetros](#Adding-Parameter-Sets-to-a-Cmdlet)

- [Declarar la clase de Cmdlet](#Declaring-the-Cmdlet-Class)

- [Declarar los parámetros del Cmdlet](#Declaring-the-Parameters-of-the-Cmdlet)

- [Reemplazar una método de procesamiento de entrada](#Overriding-an-Input-Processing-Method)

- [Ejemplo de código](#Declaring-the-Parameters-of-the-Cmdlet)

- [Definir los tipos de objeto y el formato](#Defining-Object-Types-and-Formatting)

- [Compilar el Cmdlet](#Building-the-Cmdlet)

- [Probar el Cmdlet](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a>Cosas que saber acerca de conjuntos de parámetros

Windows PowerShell define un parámetro establecido como un grupo de parámetros que operan conjuntamente. Mediante la agrupación de los parámetros de un cmdlet, puede crear un solo cmdlet que puede cambiar su funcionalidad basada en el usuario especifica a qué grupo de parámetros.

Un ejemplo de un cmdlet que usa dos conjuntos de parámetros para definir distintas funcionalidades es la `Get-EventLog` cmdlet proporcionada por Windows PowerShell. Este cmdlet devuelve información diferente cuando el usuario especifica la `List` o `LogName` parámetro. Si el `LogName` parámetro se especifica, el cmdlet devuelve información acerca de los eventos en un determinado registro de eventos. Si el `List` parámetro se especifica, el cmdlet devuelve información acerca del registro de archivos (no la información de evento que contienen). En este caso, el `List` y `LogName` parámetros identifican dos conjuntos de parámetros independiente.

Dos aspectos importantes que recordar sobre los conjuntos de parámetros es que el tiempo de ejecución de Windows PowerShell usa un único conjunto de parámetros para una entrada determinada, y que cada conjunto de parámetros debe tener al menos un parámetro que es único para ese conjunto de parámetros.

Para ilustrar este último punto, este cmdlet Stop-Proc utiliza tres conjuntos de parámetros: `ProcessName`, `ProcessId`, y `InputObject`. Cada uno de estos conjuntos de parámetros tiene un parámetro que no está en los otros conjuntos de parámetros. Los conjuntos de parámetros podrían compartir otros parámetros, pero el cmdlet usa los parámetros únicos `ProcessName`, `ProcessId`, y `InputObject` para identificar qué conjunto de parámetros que debe usar el tiempo de ejecución de Windows PowerShell.

## <a name="declaring-the-cmdlet-class"></a>Declarar la clase de Cmdlet

El primer paso en la creación de cmdlet siempre es el cmdlet de nomenclatura y declarar la clase de .NET que implementa el cmdlet. Para este cmdlet, se utiliza el verbo de ciclo de vida "Stop" porque el cmdlet detiene los procesos del sistema. Se usa el nombre de sustantivo "Proc" porque el cmdlet funciona en los procesos. En la siguiente declaración, tenga en cuenta que el nombre del verbo y sustantivo cmdlet se reflejan en el nombre de la clase del cmdlet.

> [!NOTE]
> Para obtener más información acerca de los nombres de verbo del cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

El código siguiente es la definición de clase para este cmdlet Stop-Proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Declarar los parámetros del Cmdlet

Este cmdlet define tres parámetros necesarios como entrada al cmdlet (estos parámetros también definen los conjuntos de parámetros), así como un `Force` parámetro que administra lo que hace el cmdlet y una `PassThru` parámetro que determina si el cmdlet envía un objeto de salida a través de la canalización. De forma predeterminada, este cmdlet no pasa un objeto a través de la canalización. Para obtener más información acerca de estos dos últimos parámetros, vea [creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>Declarar el parámetro Name

Este parámetro de entrada permite al usuario especificar los nombres de los procesos que se va a detener. Tenga en cuenta que el `ParameterSetName` atributo palabra clave de la [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica el `ProcessName` conjunto de parámetros para este parámetro.

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

Tenga en cuenta también que el alias "ProcessName" se asigna a este parámetro.

### <a name="declaring-the-id-parameter"></a>Declarar el parámetro Id

Este parámetro de entrada permite al usuario especificar los identificadores de los procesos que se va a detener. Tenga en cuenta que el `ParameterSetName` atributo palabra clave de la [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica el `ProcessId` conjunto de parámetros.

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

Tenga en cuenta también que el alias "ProcessId" se asigna a este parámetro.

### <a name="declaring-the-inputobject-parameter"></a>Declarar el parámetro InputObject

Este parámetro de entrada permite al usuario especificar un objeto de entrada que contiene información sobre los procesos que se va a detener. Tenga en cuenta que el `ParameterSetName` atributo palabra clave de la [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica el `InputObject` conjunto de parámetros para este parámetro.

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

Tenga en cuenta también que este parámetro no tiene ningún alias.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Declarar parámetros de varios conjuntos de parámetros

Aunque debe haber un parámetro único para cada conjunto de parámetros, los parámetros pueden pertenecer a más de un conjunto de parámetros. En estos casos, asigne el parámetro compartido una [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaración de atributo para cada conjunto en los que el parámetro pertenece. Si es un parámetro en todos los conjuntos de parámetros, solo tiene que declarar el atributo de parámetro de una vez y no es necesario especificar que el parámetro establece el nombre.

## <a name="overriding-an-input-processing-method"></a>Reemplazar una método de procesamiento de entrada

Todos los cmdlets deben invalidar una método de procesamiento de entrada, con más frecuencia esto será la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método. En este cmdlet, el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método se reemplaza para que el cmdlet puede procesar cualquier número de procesos. Contiene una instrucción Select que llama a un método diferente basándose en qué conjunto de parámetros, el usuario ha especificado.

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

Los métodos auxiliares llamados por la instrucción Select no se describen aquí, pero puede ver su implementación en el ejemplo de código completo en la sección siguiente.

## <a name="code-sample"></a>Ejemplo de código

Para la completa C# código de ejemplo, vea [StopProcessSample04 ejemplo](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir los tipos de objeto y el formato

Windows PowerShell pasa información entre cmdlets mediante objetos. NET. Por lo tanto, un cmdlet es posible que deba definir su propio tipo o el cmdlet que tenga que ampliar un tipo existente proporcionado por otro cmdlet. Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Compilar el Cmdlet

Después de implementar un cmdlet, debe registrarlo con Windows PowerShell a través de un complemento de Windows PowerShell. Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Probar el Cmdlet

Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarla mediante la ejecución de la línea de comandos. Estas son algunas pruebas que demuestran cómo la `ProcessId` y `InputObject` parámetros se pueden usar para probar sus conjuntos de parámetros para detener un proceso.

- Con Windows PowerShell iniciado, ejecute el cmdlet Stop-Proc con el `ProcessId` establecido para detener un proceso según su identificador. En este caso, el cmdlet usa el `ProcessId` establecido para detener el proceso.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Con Windows PowerShell iniciado, ejecute el cmdlet Stop-Proc con el `InputObject` establecido para detener procesos en el objeto el Bloc de notas recuperado por el `Get-Process` comando.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Véase también

[Creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Creación de un Cmdlet de Windows PowerShell](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Extensión de tipos de objeto y el formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
