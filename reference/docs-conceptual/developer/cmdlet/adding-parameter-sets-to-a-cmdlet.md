---
title: Agregar conjuntos de parámetros a un cmdlet | Microsoft Docs
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
ms.openlocfilehash: 59db96cf03ff7086e8c89fb45bc96fd805078ac8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364594"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Adición de conjuntos de parámetros a un cmdlet

## <a name="things-to-know-about-parameter-sets"></a>Aspectos que se deben conocer acerca de los conjuntos de parámetros

Windows PowerShell define un conjunto de parámetros como un grupo de parámetros que operan juntos. Mediante la agrupación de los parámetros de un cmdlet, puede crear un cmdlet único que pueda cambiar su funcionalidad en función del grupo de parámetros que especifique el usuario.

Un ejemplo de un cmdlet que usa dos conjuntos de parámetros para definir funcionalidades diferentes es el cmdlet `Get-EventLog` proporcionado por Windows PowerShell. Este cmdlet devuelve información diferente cuando el usuario especifica el parámetro `List` o `LogName`. Si se especifica el parámetro `LogName`, el cmdlet devuelve información sobre los eventos de un registro de eventos determinado. Si se especifica el parámetro `List`, el cmdlet devuelve información sobre los propios archivos de registro (no la información de evento que contienen). En este caso, los parámetros `List` y `LogName` identifican dos conjuntos de parámetros independientes.

Dos aspectos importantes que hay que recordar sobre los conjuntos de parámetros es que el tiempo de ejecución de Windows PowerShell solo usa un conjunto de parámetros para una entrada determinada, y que cada conjunto de parámetros debe tener al menos un parámetro que sea único para ese conjunto de parámetros.

Para ilustrar ese último punto, este cmdlet Stop-proc usa tres conjuntos de parámetros: `ProcessName`, `ProcessId` y `InputObject`. Cada uno de estos conjuntos de parámetros tiene un parámetro que no está en los otros conjuntos de parámetros. Los conjuntos de parámetros podrían compartir otros parámetros, pero el cmdlet usa los parámetros únicos `ProcessName`, `ProcessId` y `InputObject` para identificar qué conjunto de parámetros debe usar el tiempo de ejecución de Windows PowerShell.

## <a name="declaring-the-cmdlet-class"></a>Declarar la clase de cmdlet

El primer paso en la creación de un cmdlet es siempre nombrar el cmdlet y declarar la clase .NET que implementa el cmdlet. Para este cmdlet, se usa el verbo de ciclo de vida "STOP" porque el cmdlet detiene los procesos del sistema. El nombre de sustantivo "proc" se usa porque el cmdlet funciona en procesos. En la declaración siguiente, tenga en cuenta que el verbo de cmdlet y el nombre de sustantivo se reflejan en el nombre de la clase de cmdlet.

> [!NOTE]
> Para obtener más información sobre los nombres de verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).

El código siguiente es la definición de clase para este cmdlet Stop-proc.

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Declarar los parámetros del cmdlet

Este cmdlet define tres parámetros necesarios como entrada para el cmdlet (estos parámetros también definen los conjuntos de parámetros), así como un parámetro `Force` que administra lo que hace el cmdlet y un parámetro `PassThru` que determina si el cmdlet envía un objeto de salida. a través de la canalización. De forma predeterminada, este cmdlet no pasa un objeto a través de la canalización. Para obtener más información sobre estos dos últimos parámetros, consulte [crear un cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>Declarar el parámetro name

Este parámetro de entrada permite al usuario especificar los nombres de los procesos que se van a detener. Tenga en cuenta que la palabra clave del atributo `ParameterSetName` del atributo [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) especifica el conjunto de parámetros `ProcessName` para este parámetro.

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

Tenga en cuenta también que el alias "processName" se asigna a este parámetro.

### <a name="declaring-the-id-parameter"></a>Declarar el parámetro id

Este parámetro de entrada permite al usuario especificar los identificadores de los procesos que se van a detener. Tenga en cuenta que la palabra clave del atributo `ParameterSetName` del atributo [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) especifica el conjunto de parámetros `ProcessId`.

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

Este parámetro de entrada permite al usuario especificar un objeto de entrada que contiene información sobre los procesos que se van a detener. Tenga en cuenta que la palabra clave del atributo `ParameterSetName` del atributo [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) especifica el conjunto de parámetros `InputObject` para este parámetro.

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

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Declarar parámetros en varios conjuntos de parámetros

Aunque debe haber un parámetro único para cada conjunto de parámetros, los parámetros pueden pertenecer a más de un conjunto de parámetros. En estos casos, asigne al parámetro compartido una declaración de atributo [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) para cada conjunto al que pertenece el parámetro. Si un parámetro está en todos los conjuntos de parámetros, solo tiene que declarar el atributo Parameter una vez y no es necesario especificar el nombre del conjunto de parámetros.

## <a name="overriding-an-input-processing-method"></a>Reemplazar un método de procesamiento de entrada

Cada cmdlet debe invalidar un método de procesamiento de entrada, lo que suele ser el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . En este cmdlet, el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) se invalida para que el cmdlet pueda procesar cualquier número de procesos. Contiene una instrucción SELECT que llama a un método diferente en función del conjunto de parámetros especificado por el usuario.

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

Los métodos auxiliares a los que llama la instrucción SELECT no se describen aquí, pero puede ver su implementación en el ejemplo de código completo en la sección siguiente.

## <a name="code-sample"></a>Código de ejemplo

Para obtener el C# código de ejemplo completo, vea el [ejemplo de StopProcessSample04](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto y formato

Windows PowerShell pasa información entre cmdlets mediante objetos .NET. Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que el cmdlet tenga que extender un tipo existente proporcionado por otro cmdlet. Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Compilación del cmdlet

Después de implementar un cmdlet, debe registrarlo con Windows PowerShell a través de un complemento de Windows PowerShell. Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Prueba del cmdlet

Cuando el cmdlet se haya registrado con Windows PowerShell, pruébelo en la línea de comandos. Estas son algunas pruebas que muestran cómo se pueden usar los parámetros `ProcessId` y `InputObject` para probar sus conjuntos de parámetros para detener un proceso.

- Con Windows PowerShell iniciado, ejecute el cmdlet Stop-proc con el parámetro `ProcessId` establecido para detener un proceso en función de su identificador. En este caso, el cmdlet usa el parámetro `ProcessId` establecido para detener el proceso.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Con Windows PowerShell iniciado, ejecute el cmdlet Stop-proc con el parámetro `InputObject` establecido para detener los procesos en el objeto de Bloc de notas recuperado por el comando `Get-Process`.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Véase también

[Creación de un cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Cómo crear un cmdlet de Windows PowerShell](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85))

[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
