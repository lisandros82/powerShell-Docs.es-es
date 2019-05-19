---
title: Creación de un Cmdlet sin parámetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: 7f10acf59dedbb4af17bc5250e8624282ba22656
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854966"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Creación de un cmdlet sin parámetros

En esta sección se describe cómo crear un cmdlet que recupera información desde el equipo local sin el uso de parámetros y, a continuación, escribe la información en la canalización. El cmdlet que se describe aquí es un cmdlet Get-Proc que recupera información acerca de los procesos del equipo local y, a continuación, muestra esa información en la línea de comandos.

> [!NOTE]
> Tenga en cuenta que, al escribir cmdlets, los ensamblados de referencia Windows PowerShell® se descargan en el disco (de forma predeterminada en C:\Program programa\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). No se instalan en la caché de ensamblados Global (GAC).

## <a name="naming-the-cmdlet"></a>El Cmdlet de nomenclatura

Un nombre de cmdlet consta de un verbo que indica que la acción que el cmdlet toma y un sustantivo que indica los elementos que actúa el cmdlet. Dado que este cmdlet Get-Proc de ejemplo recupera los objetos de proceso, utiliza el verbo "Get", definido por el [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeración y el sustantivo "Proc" para indicar que el cmdlet funciona en elementos de proceso.

¿Al asignar nombres a los cmdlets, no utilice ninguno de los siguientes caracteres: #, () {} [] & - / \ $;: "' <> &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Elegir un sustantivo

Debe elegir un sustantivo específico. Es mejor usar un nombre singular precedido de una versión abreviada del nombre del producto. Un nombre de cmdlet de ejemplo de este tipo es "`Get-SQLServer`".

### <a name="choosing-a-verb"></a>Elección de un verbo

Debe usar un verbo del conjunto de los nombres de verbo del cmdlet aprobadas. Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

## <a name="defining-the-cmdlet-class"></a>Definición de la clase de Cmdlet

Una vez haya elegido un nombre de cmdlet, defina una clase .NET para implementar el cmdlet. Esta es la definición de clase para este cmdlet Get-Proc de ejemplo:

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

Tenga en cuenta que anteriores a la definición de clase, el [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo con la sintaxis `[Cmdlet(verb, noun, ...)]`, se usa para identificar esta clase como un cmdlet. Este es el único atributo obligatorio para todos los cmdlets y permite el tiempo de ejecución de Windows PowerShell llamar correctamente a ellos. Puede establecer las palabras clave de atributo para declarar aún más la clase si es necesario. Tenga en cuenta que la declaración de atributos para la clase de ejemplo GetProcCommand declara sólo los nombres de sustantivo y el verbo del cmdlet Get-Proc.

> [!NOTE]
> Para todas las clases de atributo de Windows PowerShell, las palabras clave que se pueden establecer se corresponden con las propiedades de la clase de atributo.

Cuando asigne nombre a la clase del cmdlet, es una buena práctica para reflejar el nombre de cmdlet en el nombre de clase. Para ello, use el formato "VerbNounCommand" y reemplace "Verbo" y "Sustantivo" con el verbo y sustantivo que se usa en el nombre del cmdlet. Como se muestra en la definición de clase anteriores, el cmdlet Get-Proc de ejemplo define una clase denominada GetProcCommand, que se deriva de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase base.

> [!IMPORTANT]
> Si desea definir un cmdlet que tiene acceso directo al tiempo de ejecución de Windows PowerShell, debe derivar la clase de .NET de la [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) clase base. Para obtener más información acerca de esta clase, vea [creación de un Cmdlet que conjuntos de parámetros define](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> La clase para un cmdlet debe marcarse explícitamente como pública. Las clases que no están marcadas como público predeterminado será interno y no se encontrará el tiempo de ejecución de Windows PowerShell.

Windows PowerShell usa el [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) espacio de nombres para sus clases de cmdlet. Se recomienda colocar las clases de cmdlet en un espacio de nombres de comandos de su espacio de nombres de API, por ejemplo, xxx.PS.Commands.

## <a name="overriding-an-input-processing-method"></a>Reemplazar una método de procesamiento de entrada

El [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase proporciona tres métodos de procesamiento de entrada principal, al menos uno de los cuales debe invalidar el cmdlet. Para obtener más información acerca de cómo Windows PowerShell procesa los registros, vea [cómo Windows PowerShell funciona](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

Para todos los tipos de entrada, el tiempo de ejecución de Windows PowerShell llama [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) para habilitar el procesamiento. Si el cmdlet debe realizar algún preprocesamiento o programa de instalación, puede hacerlo mediante la invalidación de este método.

> [!NOTE]
> Windows PowerShell usa el término "registro" para describir el conjunto de valores de parámetro proporcionado cuando se llama a un cmdlet.

Si el cmdlet acepta entrada de la canalización, debe reemplazar el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método y opcionalmente el [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)método. Por ejemplo, un cmdlet podría reemplazar ambos métodos si lo recopila todos los datos de entrada mediante [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) y, a continuación, opera en la entrada como un todo en lugar de un elemento a la vez, como el `Sort-Object` hace el cmdlet.

Si el cmdlet no toma ninguna entrada de la canalización, debe invalidar el [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método. Tenga en cuenta que este método se utiliza con frecuencia en lugar de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) cuando el cmdlet no puede funcionar en un elemento a la vez, como es el caso de un cmdlet de ordenación.

Dado que este cmdlet Get-Proc de ejemplo debe recibir la entrada de la canalización, invalida la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método y utiliza las implementaciones predeterminadas para [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) y [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). El [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) invalidación recupera los procesos y los escribe en la línea de comandos mediante la [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método.

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a>Cosas que recordar sobre el procesamiento de entrada

- El origen predeterminado para la entrada es un objeto explícito (por ejemplo, una cadena) proporcionado por el usuario en la línea de comandos. Para obtener más información, consulte [creación de un Cmdlet para entrada de línea de comandos del proceso](./adding-parameters-that-process-command-line-input.md).

- Una método de procesamiento de entrada también puede recibir entradas desde el objeto de salida de un cmdlet de nivel superior en la canalización. Para obtener más información, consulte [creación de un Cmdlet para entrada de la canalización de proceso](./adding-parameters-that-process-pipeline-input.md). Tenga en cuenta que el cmdlet puede recibir entradas de una combinación de línea de comandos y una canalización de orígenes.

- El cmdlet de nivel inferior no puede devolver durante mucho tiempo o no en absoluto. Por ese motivo, el método en el cmdlet de procesamiento de entrada no debe contener los bloqueos durante las llamadas a [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especialmente los bloqueos para el que el ámbito se extiende más allá de la instancia del cmdlet.

> [!IMPORTANT]
> Nunca debe llamar los cmdlets [System.Console.Writeline*](/dotnet/api/System.Console.WriteLine) o su equivalente.

- El cmdlet podría tener las variables de objeto para limpiar cuando haya finalizado de procesamiento (por ejemplo, si se abre un identificador de archivo en el [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método y conserva el identificador se abra para su uso por [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). Es importante recordar que el tiempo de ejecución de Windows PowerShell no llame siempre a la [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método, que debe realizar la limpieza de objetos.

Por ejemplo, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) no es posible que se llama si el cmdlet se cancela a medio camino o si un carácter de terminación se produce error en cualquier parte del cmdlet. Por lo tanto, un cmdlet que requiere la limpieza de objetos debe implementar toda [System.IDisposable](/dotnet/api/System.IDisposable) patrón, incluidos el finalizador, para que el tiempo de ejecución puede llamar a ambos [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) y [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) al final del procesamiento.

## <a name="code-sample"></a>Ejemplo de código

Para la completa C# código de ejemplo, vea [ejemplo GetProcessSample01](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir los tipos de objeto y el formato

Windows PowerShell pasa información entre cmdlets mediante objetos. NET. Por lo tanto, un cmdlet es posible que deba definir su propio tipo o el cmdlet que tenga que ampliar un tipo existente proporcionado por otro cmdlet. Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Compilar el Cmdlet

Después de implementar un cmdlet, debe registrarlo con Windows PowerShell a través de un complemento de Windows PowerShell. Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Probar el Cmdlet

Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarla mediante la ejecución de la línea de comandos. El código para el cmdlet Get-Proc de ejemplo es pequeño, pero sigue usando el tiempo de ejecución de Windows PowerShell y un objeto .NET existente, que es suficiente para que resulte útil. Vamos a probarlo para entender mejor lo que puede hacer Get-Proc y cómo se puede usar su salida. Para obtener más información sobre el uso de cmdlets de la línea de comandos, consulte el [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Inicie Windows PowerShell, y obtengan los procesos actuales que se ejecutan en el equipo.

    ```powershell
    get-proc
    ```

    Aparece el siguiente resultado.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. Asignar una variable a los resultados del cmdlet para una manipulación más fácil.

    ```powershell
    $p=get-proc
    ```

3. Obtiene el número de procesos.

    ```powershell
    $p.length
    ```

    Aparece el siguiente resultado.

    ```output
    63
    ```

4. Recuperar un proceso específico.

    ```powershell
    $p[6]
    ```

    Aparece el siguiente resultado.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. Obtiene la hora de inicio de este proceso.

    ```powershell
    $p[6].starttime
    ```

    Aparece el siguiente resultado.

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. Obtener los procesos para el que el recuento de identificadores es mayor que 500 y clasificar el resultado.

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    Aparece el siguiente resultado.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. Use el `Get-Member` cmdlet para enumerar las propiedades disponibles para cada proceso.

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    Aparece el siguiente resultado.

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>Véase también

[Creación de un Cmdlet para procesar la entrada de línea de comandos](./adding-parameters-that-process-command-line-input.md)

[Creación de un Cmdlet para procesar la entrada de la canalización](./adding-parameters-that-process-pipeline-input.md)

[Creación de un Cmdlet de Windows PowerShell](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Extensión de tipos de objeto y el formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cómo funciona Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Referencia de Windows PowerShell](../windows-powershell-reference.md)

[Ejemplos de cmdlet](./cmdlet-samples.md)