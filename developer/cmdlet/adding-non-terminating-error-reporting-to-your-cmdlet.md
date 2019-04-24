---
title: Agregar informes de errores para el Cmdlet de no terminación | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 3741982f81efa04d8fe7ab448fba5f2fdf4b0c01
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984245"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Adición de informes de errores de no terminación al cmdlet

Cmdlets puede notificar los errores de no terminación mediante una llamada a la [System.Management.Automation.Cmdlet.WriteError][] método y continuar funcionando en el objeto de entrada actual o en la entrada más objetos de canalización.
Esta sección explica cómo crear un cmdlet que informa de errores de no terminación de sus métodos de procesamiento de entrada.

Para errores de no terminación (así como los errores de terminación), el cmdlet debe pasar un [System.Management.Automation.ErrorRecord][] objeto que identifica el error.
Cada registro de error se identifica mediante una cadena única denominada "identificador de error".
Además, el identificador de la categoría de cada error se especifica mediante constantes definidas por un [System.Management.Automation.ErrorCategory][] enumeración.
El usuario puede ver los errores según su categoría estableciendo el `$ErrorView` variable a "CategoryView".

Para obtener más información acerca de los registros de error, consulte [registros de Error de Windows PowerShell](./windows-powershell-error-records.md).

## <a name="defining-the-cmdlet"></a>Definir el Cmdlet

El primer paso en la creación de cmdlet siempre es el cmdlet de nomenclatura y declarar la clase de .NET que implementa el cmdlet.
Este cmdlet recupera información de proceso, por lo que el nombre del verbo seleccionado aquí es "Get".
(Casi cualquier tipo de cmdlet que es capaz de recuperar la información puede procesar la entrada de línea de comandos). Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](approved-verbs-for-windows-powershell-commands.md).

La siguiente es la definición de este cmdlet Get-Proc.
Se proporcionan detalles de esta definición [crear su primer Cmdlet](creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>Definición de parámetros

Si es necesario, el cmdlet debe definir parámetros para el procesamiento de entrada.
Este cmdlet Get-Proc define un **nombre** parámetro tal y como se describe en [agregar parámetros que procesan datos de línea de comandos](adding-parameters-that-process-command-line-input.md).

Esta es la declaración de parámetros para el **nombre** parámetro de este cmdlet Get-Proc.

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a>Invalidar los métodos de procesamiento de entrada

Debe invalidar todos los cmdlets de al menos uno de los métodos proporcionados por procesamiento de entrada la [System.Management.Automation.Cmdlet][] clase.
Estos métodos se describen en [crear su primer Cmdlet](creating-a-cmdlet-without-parameters.md).

> [!NOTE]
> El cmdlet debe controlar cada registro que de manera independiente como sea posible.

Este cmdlet Get-Proc invalida la [System.Management.Automation.Cmdlet.ProcessRecord][] método para controlar la **nombre** parámetro de entrada proporcionada por el usuario o una secuencia de comandos.
Este método obtiene los procesos para cada nombre de proceso solicitado o todos los procesos si se proporciona ningún nombre.
Se proporcionan detalles de esta invalidación [crear su primer Cmdlet](creating-a-cmdlet-without-parameters.md).

### <a name="things-to-remember-when-reporting-errors"></a>Cosas que recordar al informar de errores

El [System.Management.Automation.ErrorRecord][] objeto que el cmdlet pasa al escribir un error requiere una excepción en su núcleo.
Siga las instrucciones de .NET al determinar la excepción a usar.
Básicamente, si el error semánticamente es igual que una excepción existente, debe usar el cmdlet o se derivan de esa excepción.
En caso contrario, debe derivar una nueva excepción o la jerarquía de excepciones directamente desde el [System.Exception][] clase.

Al crear identificadores de errores (que tiene accesibles a través de la propiedad FullyQualifiedErrorId de la clase ErrorRecord) tenga en cuenta lo siguiente.

- Utilice las cadenas que tienen como destino para fines de diagnóstico para que al inspeccionar el identificador completo puede determinar qué el error es y donde procede el error.

- Un identificador de error completo con formato correcto podría ser como sigue.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

Tenga en cuenta que en el ejemplo anterior, el identificador de error (el primer token) designa el error y la parte restante indica de dónde procede el error.

- Para escenarios más complejos, el identificador de error puede ser un token de punto separado que se puede analizar de inspección.
  Esto permite que bifurca demasiado en las partes del identificador del error, así como la categoría de error y el identificador de error.

El cmdlet debe asignar identificadores de error específico a diferentes rutas de código.
Tenga en cuenta para la asignación de identificadores de errores de la información siguiente:

- Un identificador de error debe permanecer constante a lo largo del ciclo de vida del cmdlet.
  No se cambia la semántica de un identificador de error entre las versiones de cmdlet.

- Use el texto para un identificador de error que lacónicamente corresponde a la que se informa del error.
  No use signos de puntuación o espacios en blanco.

- Tener su cmdlet generar identificadores de errores que son reproducibles.
  Por ejemplo, no debe generar un identificador que incluye un identificador de proceso.
  Los identificadores de error son útiles para un usuario solo cuando se corresponden con los identificadores que ven otros usuarios que experimentan el problema.

PowerShell no detecta las excepciones no controladas en las siguientes condiciones:

- Si un cmdlet crea un nuevo subproceso y el código que se ejecuta en ese subproceso produce una excepción no controlada, PowerShell no detectará el error y finalizará el proceso.

- Si un objeto tiene código en su destructor o los métodos Dispose que produce una excepción no controlada, PowerShell no detectará el error y finalizará el proceso.

## <a name="reporting-nonterminating-errors"></a>Informes de errores de no terminación

Uno de los métodos de procesamiento de entrada puede notificar un error de no terminación en el flujo de salida mediante la [System.Management.Automation.Cmdlet.WriteError][] método.

Este es un ejemplo de código de este cmdlet Get-Proc que ilustra la llamada a [System.Management.Automation.Cmdlet.WriteError][] desde dentro de la invalidación de la [System.Management.Automation.Cmdlet.ProcessRecord][] método.
En este caso, se realiza la llamada si el cmdlet no encuentra un proceso para un identificador de proceso especificado.

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
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
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Cosas que recordar acerca de cómo escribir los errores de no terminación

Un error de no terminación, el cmdlet debe generar un identificador de error específico para cada objeto de entrada específico.

Con frecuencia necesita un cmdlet modificar la acción de PowerShell generada por un error de no terminación.
Puede hacerlo mediante la definición de la `ErrorAction` y `ErrorVariable` parámetros.
Si la definición de la `ErrorAction` parámetro, el cmdlet presenta las opciones de usuario [System.Management.Automation.ActionPreference][], directamente también pueden influir en la acción estableciendo el `$ErrorActionPreference` variable.

El cmdlet puede guardar los errores de no terminación en una variable mediante el `ErrorVariable` parámetro, que no se ve afectado por el valor de `ErrorAction`.
Errores se pueden anexar a una variable de error existente mediante la adición de un signo más (+) al principio del nombre de la variable.

## <a name="code-sample"></a>Ejemplo de código

Para la completa C# código de ejemplo, vea [GetProcessSample04 ejemplo](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Definir tipos de objeto y el formato

PowerShell pasa información entre cmdlets mediante objetos. NET.
Por lo tanto, un cmdlet es posible que deba definir su propio tipo o el cmdlet que tenga que ampliar un tipo existente proporcionado por otro cmdlet.
Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Compilar el Cmdlet

Después de implementar un cmdlet, debe registrarlo con Windows PowerShell a través de un complemento de Windows PowerShell.
Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Probar el Cmdlet

Cuando el cmdlet se ha registrado con PowerShell, puede probarla mediante la ejecución de la línea de comandos.
Vamos a probar el cmdlet Get-Proc de ejemplo para ver si notifica un error:

- Inicie PowerShell y use el cmdlet Get-Proc para recuperar los procesos que se denomina "TEST".

    ```powershell
    PS> get-proc -name test
    ```

Aparece el siguiente resultado.

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a>Véase también

[Agregar parámetros de entrada de la canalización de proceso](./adding-parameters-that-process-pipeline-input.md)

[Adición de parámetros que procesa la entrada de línea de comandos](./adding-parameters-that-process-command-line-input.md)

[Creación del primer Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Extensión de tipos de objeto y el formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Referencia de Windows PowerShell](../windows-powershell-reference.md)

[Ejemplos de cmdlet](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
