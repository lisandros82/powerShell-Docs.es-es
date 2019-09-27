---
title: Agregando informes de errores de no terminación al cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: a4426abec96cd922360aeef8c157b4e9f41a15b9
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322873"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Adición de informes de errores de no terminación al cmdlet

Los cmdlets pueden notificar errores de no terminación llamando al método [System. Management. Automation. cmdlet. WriteError][] y continúan funcionando en el objeto de entrada actual o en objetos de canalización de entrada adicionales.
En esta sección se explica cómo crear un cmdlet que informe de errores de no terminación de sus métodos de procesamiento de entrada.

En el caso de los errores de no terminación (así como de los errores de terminación), el cmdlet debe pasar un objeto [System. Management. Automation. ErrorRecord][] que identifique el error.
Cada registro de error se identifica mediante una cadena única denominada "identificador de error".
Además del identificador, la categoría de cada error se especifica mediante constantes definidas por una enumeración [System. Management. Automation. ErrorCategory][] .
El usuario puede ver los errores en función de su categoría estableciendo `$ErrorView` la variable en "CategoryView".

Para obtener más información sobre los registros de errores, consulte [registros de errores de Windows PowerShell](./windows-powershell-error-records.md).

## <a name="defining-the-cmdlet"></a>Definición del cmdlet

El primer paso en la creación de un cmdlet es siempre nombrar el cmdlet y declarar la clase .NET que implementa el cmdlet.
Este cmdlet recupera información de proceso, por lo que el nombre de verbo elegido aquí es "Get".
(Casi cualquier tipo de cmdlet que sea capaz de recuperar información puede procesar la entrada de la línea de comandos). Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](approved-verbs-for-windows-powershell-commands.md).

A continuación se ofrece la definición de este cmdlet Get-proc.
Los detalles de esta definición se proporcionan [al crear el primer cmdlet](creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>Definir parámetros

Si es necesario, el cmdlet debe definir parámetros para procesar la entrada.
Este cmdlet Get-proc define un parámetro de **nombre** tal y como se describe en [agregar parámetros que procesan la entrada de la línea de comandos](adding-parameters-that-process-command-line-input.md).

Esta es la declaración de parámetro para el parámetro **Name** de este cmdlet Get-proc.

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

## <a name="overriding-input-processing-methods"></a>Reemplazar métodos de procesamiento de entrada

Todos los cmdlets deben invalidar al menos uno de los métodos de procesamiento de entrada proporcionados por la clase [System. Management. Automation. cmdlet][] .
Estos métodos se describen en [creación del primer cmdlet](creating-a-cmdlet-without-parameters.md).

> [!NOTE]
> El cmdlet debe administrar cada registro de la forma más independiente posible.

Este cmdlet Get-proc invalida el método [System. Management. Automation. cmdlet. ProcessRecord][] para controlar el parámetro **Name** para la entrada proporcionada por el usuario o un script.
Este método obtendrá los procesos de cada nombre de proceso solicitado o de todos los procesos si no se proporciona ningún nombre.
Los detalles de esta invalidación se proporcionan [al crear el primer cmdlet](creating-a-cmdlet-without-parameters.md).

### <a name="things-to-remember-when-reporting-errors"></a>Aspectos que se deben recordar al informar de errores

El objeto [System. Management. Automation. ErrorRecord][] que el cmdlet pasa cuando se escribe un error requiere una excepción en su núcleo.
Siga las instrucciones de .NET para determinar la excepción que se va a usar.
Básicamente, si el error es semánticamente igual que una excepción existente, el cmdlet debe usar o derivar de esa excepción.
De lo contrario, debe derivar una nueva jerarquía de excepción o excepción directamente de la clase [System. Exception][] .

Al crear identificadores de error (a los que se tiene acceso a través de la propiedad FullyQualifiedErrorId de la clase ErrorRecord) tenga en cuenta lo siguiente.

- Use cadenas destinadas a fines de diagnóstico para que, al inspeccionar el identificador completo, pueda determinar cuál es el error y dónde procede el error.

- Un identificador de error completo bien formado puede ser como se indica A continuación.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

Observe que en el ejemplo anterior, el identificador de error (el primer token) designa cuál es el error y la parte restante indica dónde procede el error.

- En escenarios más complejos, el identificador de error puede ser un token separado por puntos que se puede analizar en la inspección.
  Esto le permite crear una bifurcación en las partes del identificador de error, así como el identificador de error y la categoría de error.

El cmdlet debe asignar identificadores de error específicos a rutas de acceso de código diferentes.
Tenga en cuenta la siguiente información para la asignación de identificadores de error:

- Un identificador de error debe permanecer constante en todo el ciclo de vida del cmdlet.
  No cambie la semántica de un identificador de error entre las versiones de los cmdlets.

- Use texto para un identificador de error que tersely corresponda con el error que se va a informar.
  No utilice espacios en blanco ni signos de puntuación.

- Haga que el cmdlet genere solo identificadores de error que se pueden reproducir.
  Por ejemplo, no debe generar un identificador que incluya un identificador de proceso.
  Los identificadores de error son útiles para un usuario solo cuando se corresponden con los identificadores que ven otros usuarios que experimentan el mismo problema.

PowerShell no detecta las excepciones no controladas en las siguientes condiciones:

- Si un cmdlet crea un nuevo subproceso y el código que se ejecuta en ese subproceso produce una excepción no controlada, PowerShell no detectará el error y finalizará el proceso.

- Si un objeto tiene código en su destructor o métodos Dispose que causan una excepción no controlada, PowerShell no detectará el error y finalizará el proceso.

## <a name="reporting-nonterminating-errors"></a>Informes de errores de no terminación

Cualquiera de los métodos de procesamiento de entrada puede notificar un error de no terminación en el flujo de salida mediante el método [System. Management. Automation. cmdlet. WriteError][] .

Este es un ejemplo de código de este cmdlet Get-proc que ilustra la llamada a [System. Management. Automation. cmdlet. WriteError][] desde dentro de la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord][] .
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

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Aspectos que se deben recordar sobre la escritura de errores de no terminación

En el caso de un error de no terminación, el cmdlet debe generar un identificador de error específico para cada objeto de entrada concreto.

Con frecuencia, un cmdlet necesita modificar la acción de PowerShell generada por un error de no terminación.
Para ello, puede definir los `ErrorAction` parámetros y. `ErrorVariable`
Si define el `ErrorAction` parámetro, el cmdlet presenta las opciones de usuario [System. Management. Automation. ActionPreference][], también puede influir directamente en la acción estableciendo `$ErrorActionPreference` la variable.

El cmdlet puede guardar errores de no terminación en una variable mediante `ErrorVariable` el parámetro, que no se ve afectado por la `ErrorAction`configuración de.
Los errores se pueden anexar a una variable de error existente agregando un signo más (+) al principio del nombre de la variable.

## <a name="code-sample"></a>Código de ejemplo

Para obtener el C# código de ejemplo completo, vea el [ejemplo de GetProcessSample04](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Definir tipos de objeto y formato

PowerShell pasa información entre cmdlets mediante objetos .NET.
Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que el cmdlet tenga que extender un tipo existente proporcionado por otro cmdlet.
Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Compilación del cmdlet

Después de implementar un cmdlet, debe registrarlo con Windows PowerShell a través de un complemento de Windows PowerShell.
Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Prueba del cmdlet

Cuando el cmdlet se ha registrado con PowerShell, puede probarlo mediante su ejecución en la línea de comandos.
Vamos a probar el cmdlet Get-proc de ejemplo para ver si informa de un error:

- Inicie PowerShell y use el cmdlet Get-proc para recuperar los procesos denominados "TEST".

    ```powershell
    PS> get-proc -name test
    ```

Aparece el siguiente resultado.

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a>Vea también

[Agregar parámetros que procesan la entrada de canalización](./adding-parameters-that-process-pipeline-input.md)

[Agregar parámetros que procesan la entrada de la línea de comandos](./adding-parameters-that-process-command-line-input.md)

[Creación del primer cmdlet](./creating-a-cmdlet-without-parameters.md)

[Extender tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Referencia de Windows PowerShell](../windows-powershell-reference.md)

[Ejemplos de cmdlet](./cmdlet-samples.md)

[System. Exception]: /dotnet/api/System.Exception
[System. Management. Automation. ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System. Management. Automation. cmdlet. ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System. Management. Automation. cmdlet. WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System. Management. Automation. cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System. Management. Automation. ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System. Management. Automation. ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
