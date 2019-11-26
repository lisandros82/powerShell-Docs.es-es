---
title: Crear un cmdlet sin parámetros | Microsoft Docs
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
ms.openlocfilehash: af41c2c9855310d047404114a07b27180a7aa8fc
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74415673"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Creación de un cmdlet sin parámetros

En esta sección se describe cómo crear un cmdlet que recupera información del equipo local sin el uso de parámetros y, a continuación, escribe la información en la canalización. El cmdlet descrito aquí es un cmdlet Get-proc que recupera información sobre los procesos del equipo local y, a continuación, muestra esa información en la línea de comandos.

> [!NOTE]
> Tenga en cuenta que al escribir cmdlets, los ensamblados de referencia de® de Windows PowerShell se descargan en el disco (de forma predeterminada, en C:\Archivos de Programa\reference Assemblies\Microsoft\WindowsPowerShell\v1.0). No se instalan en la caché de ensamblados global (GAC).

## <a name="naming-the-cmdlet"></a>Asignar nombre al cmdlet

Un nombre de cmdlet consta de un verbo que indica la acción que el cmdlet toma y un sustantivo que indica los elementos sobre los que actúa el cmdlet. Dado que este cmdlet Get-proc de ejemplo recupera objetos de proceso, usa el verbo "Get", definido por la enumeración [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) y el nombre "proc" para indicar que el cmdlet funciona en elementos de proceso.

Al asignar nombres a los cmdlets, no use ninguno de los siguientes caracteres: #, () {} [] &-/\ $; : "' < > &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Elección de un Sustantivo

Debe elegir un nombre específico. Es mejor usar un Sustantivo Singular precedido de una versión abreviada del nombre del producto. Un nombre de cmdlet de ejemplo de este tipo es "`Get-SQLServer`".

### <a name="choosing-a-verb"></a>Elección de un verbo

Debe usar un verbo del conjunto de nombres de verbo de cmdlet aprobados. Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).

## <a name="defining-the-cmdlet-class"></a>Definir la clase de cmdlet

Una vez que haya elegido un nombre de cmdlet, defina una clase .NET para implementar el cmdlet. Esta es la definición de clase de este cmdlet Get-proc de ejemplo:

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

Observe que antes de la definición de clase, el atributo [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) , con la sintaxis `[Cmdlet(verb, noun, ...)]`, se usa para identificar esta clase como un cmdlet. Este es el único atributo necesario para todos los cmdlets y permite que el tiempo de ejecución de Windows PowerShell los llame correctamente. Puede establecer palabras clave de atributo para declarar más la clase si es necesario. Tenga en cuenta que la declaración de atributo para la clase GetProcCommand de ejemplo declara solo los nombres de nombre y verbo para el cmdlet Get-proc.

> [!NOTE]
> Para todas las clases de atributos de Windows PowerShell, las palabras clave que se pueden establecer corresponden a las propiedades de la clase de atributo.

Al asignar un nombre a la clase del cmdlet, se recomienda reflejar el nombre del cmdlet en el nombre de clase. Para ello, use el formato "VerbNounCommand" y reemplace "Verb" y "Sustantivo" por el verbo y el sustantivo usados en el nombre del cmdlet. Como se muestra en la definición de clase anterior, el cmdlet Get-proc de ejemplo define una clase denominada GetProcCommand, que deriva de la clase base [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .

> [!IMPORTANT]
> Si desea definir un cmdlet que tenga acceso directamente al tiempo de ejecución de Windows PowerShell, la clase .NET debe derivarse de la clase base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Para obtener más información sobre esta clase, consulte [crear un cmdlet que defina conjuntos de parámetros](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> La clase de un cmdlet debe marcarse explícitamente como Public. Las clases que no están marcadas como públicas tendrán como valor predeterminado Internal y el tiempo de ejecución de Windows PowerShell no las encontrará.

Windows PowerShell usa el espacio de nombres [Microsoft. PowerShell. Commands](/dotnet/api/Microsoft.PowerShell.Commands) para sus clases de cmdlet. Se recomienda colocar las clases de cmdlet en un espacio de nombres de comandos del espacio de nombres de la API, por ejemplo, xxx. PS. Commands.

## <a name="overriding-an-input-processing-method"></a>Reemplazar un método de procesamiento de entrada

La clase [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) proporciona tres métodos de procesamiento de entrada principales, al menos uno de los cuales el cmdlet debe reemplazar. Para obtener más información sobre cómo Windows PowerShell procesa los registros, vea [Cómo funciona Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

En el caso de todos los tipos de entrada, el tiempo de ejecución de Windows PowerShell llama a [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) para habilitar el procesamiento. Si el cmdlet debe realizar algún proceso de preprocesamiento o configuración, puede hacerlo invalidando este método.

> [!NOTE]
> Windows PowerShell usa el término "registro" para describir el conjunto de valores de parámetro proporcionados cuando se llama a un cmdlet.

Si el cmdlet acepta la entrada de canalización, debe invalidar el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) y, opcionalmente, el método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Por ejemplo, un cmdlet podría invalidar ambos métodos si recopila toda la entrada mediante [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) y, a continuación, opera en la entrada como un conjunto en lugar de un elemento a la vez, como hace el cmdlet `Sort-Object`.

Si el cmdlet no toma la entrada de canalización, debe invalidar el método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Tenga en cuenta que este método se usa con frecuencia en lugar de [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) cuando el cmdlet no puede operar en un elemento cada vez, como es el caso de un cmdlet de ordenación.

Dado que este cmdlet Get-proc de ejemplo debe recibir la entrada de canalización, invalida el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) y usa las implementaciones predeterminadas para [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) y [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). La invalidación [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) recupera los procesos y los escribe en la línea de comandos mediante el método [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .

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

#### <a name="things-to-remember-about-input-processing"></a>Aspectos que se deben recordar sobre el procesamiento de entradas

- El origen predeterminado de la entrada es un objeto explícito (por ejemplo, una cadena) proporcionado por el usuario en la línea de comandos. Para obtener más información, vea [crear un cmdlet para procesar la entrada de la línea de comandos](./adding-parameters-that-process-command-line-input.md).

- Un método de procesamiento de entrada también puede recibir la entrada del objeto de salida de un cmdlet de nivel superior en la canalización. Para obtener más información, vea [crear un cmdlet para procesar la entrada de canalización](./adding-parameters-that-process-pipeline-input.md). Tenga en cuenta que el cmdlet puede recibir la entrada de una combinación de orígenes de línea de comandos y de canalización.

- Es posible que el cmdlet de nivel inferior no devuelva mucho tiempo o que no se encuentre en absoluto. Por ese motivo, el método de procesamiento de entrada del cmdlet no debe mantener bloqueos durante las llamadas a [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especialmente los bloqueos para los que el ámbito se extiende más allá de la instancia del cmdlet.

> [!IMPORTANT]
> Los cmdlets nunca deben llamar a [System. Console. WriteLine *](/dotnet/api/System.Console.WriteLine) ni a su equivalente.

- Es posible que el cmdlet tenga variables de objeto para realizar la limpieza cuando termine el procesamiento (por ejemplo, si abre un identificador de archivo en el método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) y mantiene el identificador abierto para su uso por [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). Es importante recordar que el tiempo de ejecución de Windows PowerShell no siempre llama al método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) , que debe realizar la limpieza de objetos.

Por ejemplo, no se puede llamar a [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) si el cmdlet se cancela a la mitad o si se produce un error de terminación en cualquier parte del cmdlet. Por lo tanto, un cmdlet que requiera la limpieza de objetos debe implementar el patrón [System. IDisposable](/dotnet/api/System.IDisposable) completo, incluido el finalizador, de modo que el tiempo de ejecución pueda llamar a [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) y [System. IDisposable. Dispose *](/dotnet/api/System.IDisposable.Dispose) al final del procesamiento.

## <a name="code-sample"></a>Código de ejemplo

Para obtener el C# código de ejemplo completo, vea el [ejemplo de GetProcessSample01](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto y formato

Windows PowerShell pasa información entre cmdlets mediante objetos .NET. Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que el cmdlet tenga que extender un tipo existente proporcionado por otro cmdlet. Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Compilación del cmdlet

Después de implementar un cmdlet, debe registrarlo con Windows PowerShell a través de un complemento de Windows PowerShell. Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Prueba del cmdlet

Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarlo mediante su ejecución en la línea de comandos. El código de nuestro cmdlet Get-proc de ejemplo es pequeño, pero todavía usa el tiempo de ejecución de Windows PowerShell y un objeto .NET existente, que es suficiente para que resulte útil. Vamos a probarlo para comprender mejor lo que puede hacer Get-proc y cómo puede usarse su salida. Para obtener más información sobre el uso de cmdlets desde la línea de comandos, consulte la [Introducción con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Inicie Windows PowerShell y obtenga los procesos actuales que se ejecutan en el equipo.

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

2. Asigne una variable a los resultados del cmdlet para facilitar la manipulación.

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

6. Obtiene los procesos para los que el número de identificadores es mayor que 500 y ordena el resultado.

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

7. Use el cmdlet `Get-Member` para mostrar las propiedades disponibles para cada proceso.

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

## <a name="see-also"></a>Vea también

[Crear un cmdlet para procesar la entrada de la línea de comandos](./adding-parameters-that-process-command-line-input.md)

[Crear un cmdlet para procesar la entrada de canalización](./adding-parameters-that-process-pipeline-input.md)

[Cómo crear un cmdlet de Windows PowerShell](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85))

[Cómo funciona Windows PowerShell](/previous-versions//ms714658(v=vs.85))

[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85))

[Referencia de Windows PowerShell](../windows-powershell-reference.md)

[Ejemplos de cmdlet](./cmdlet-samples.md)
