---
title: Adición de parámetros que procesan la entrada de línea de comandos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: c9ad84c5bcb6826fcf51db9a1f1a578a65a1f275
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854942"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Adición de parámetros que procesan la entrada de la línea de comandos

Un origen de entrada para un cmdlet es la línea de comandos. En este tema se describe cómo agregar un parámetro a la **Get-Proc** cmdlet (que se describe en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md)) para que el cmdlet puede procesar la entrada desde el equipo local basado en explícito los objetos pasan al cmdlet. El **Get-Proc** cmdlet descrito aquí recupera los procesos basados en sus nombres y, a continuación, muestra información acerca de los procesos en un símbolo del sistema.

## <a name="defining-the-cmdlet-class"></a>Definición de la clase de Cmdlet

El primer paso en la creación de cmdlet es la declaración de la clase de .NET Framework que implementa el cmdlet y nombres de cmdlet. Este cmdlet recupera información de proceso, por lo que el nombre del verbo seleccionado aquí es "Get". (Casi cualquier tipo de cmdlet que es capaz de recuperar la información puede procesar la entrada de línea de comandos). Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Esta es la declaración de clase para el **Get-Proc** cmdlet. Se proporcionan detalles sobre esta definición en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>Declarar parámetros

Un parámetro de cmdlet permite al usuario proporcionar la entrada al cmdlet. En el ejemplo siguiente, **Get-Proc** y `Get-Member` son los nombres de los cmdlets de canalizadas y `MemberType` es un parámetro para el `Get-Member` cmdlet. El parámetro tiene el argumento "property".

**PS > get-proc; `get-member` propiedad membertype:**

Para declarar parámetros para un cmdlet, primero debe definir las propiedades que representan los parámetros. En el **Get-Proc** es el único parámetro de cmdlet, `Name`, en este caso, que representa el nombre del objeto de proceso de .NET Framework para recuperar. Por lo tanto, la clase del cmdlet define una propiedad de tipo string para aceptar una matriz de nombres.

Esta es la declaración de parámetros para el `Name` parámetro de la **Get-Proc** cmdlet.

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

Informar al runtime de Windows PowerShell que esta propiedad es el `Name` parámetro, un [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo se agrega a la definición de propiedad. La sintaxis básica para declarar este atributo es `[Parameter()]`.

> [!NOTE]
> Un parámetro debe marcarse explícitamente como público. Parámetros que no están marcados como público predeterminado para interno y no se encuentran el tiempo de ejecución de Windows PowerShell.

Este cmdlet usa una matriz de cadenas para el `Name` parámetro. Si es posible, el cmdlet también debe definir un parámetro como una matriz, ya que esto permite al cmdlet que acepte más de un elemento.

#### <a name="things-to-remember-about-parameter-definitions"></a>Cosas que recordar acerca de las definiciones de parámetro

- Se deben utilizar predefinidos Windows PowerShell parámetro nombres y tipos de datos tanto como sea posible para asegurarse de que el cmdlet es compatible con los cmdlets de Windows PowerShell. Por ejemplo, si todos los cmdlets usan predefinido `Id` nombre de parámetro para identificar un recurso, el usuario tendrá fácilmente entender el significado del parámetro, independientemente de qué cmdlet usan. Básicamente, los nombres de parámetro siguen las mismas reglas que los usados para los nombres de variable en common language runtime (CLR). Para obtener más información sobre la nomenclatura de parámetros, vea [los nombres de parámetro de Cmdlet](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).

- Windows PowerShell se reserva algunos nombres de parámetro para proporcionar una experiencia de usuario coherente. No use estos nombres de parámetro: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, y `OutBuffer`. Además, se reservan los siguientes alias para estos nombres de parámetro: `vb`, `db`, `ea`, `ev`, `ov`, y `ob`.

- `Name` es un nombre de parámetro simples y común, recomendado para su uso en sus cmdlets. Es mejor elegir un nombre de parámetro, así que un nombre complejo que es difícil de recordar y único para un cmdlet específico.

- Los parámetros distinguen mayúsculas de minúsculas en Windows PowerShell, aunque de forma predeterminada el shell mantiene las mayúsculas. Diferenciación de los argumentos depende de la operación del cmdlet. Argumentos se pasan a un parámetro, tal como se especifica en la línea de comandos.

- Para obtener ejemplos de otras declaraciones de parámetros, vea [parámetros de Cmdlet](./cmdlet-parameters.md).

## <a name="declaring-parameters-as-positional-or-named"></a>Declarar parámetros como posicional o con nombre

Un cmdlet debe establecer cada parámetro como un parámetro posicional o con nombre. Ambos tipos de parámetros aceptan argumentos únicos, varios argumentos separados por comas y valores booleanos. Un parámetro booleano, también se denomina un *cambiar*, controla sólo la configuración del tipo Boolean. El modificador se usa para determinar la presencia del parámetro. El valor predeterminado recomendado es `false`.

El ejemplo **Get-Proc** cmdlet define el `Name` parámetro como un parámetro de posición por la posición 0. Esto significa que el primer argumento que el usuario escribe en la línea de comandos se inserta automáticamente para este parámetro. Si desea definir un parámetro con nombre, para que el usuario debe especificar el nombre del parámetro de la línea de comandos, deje el `Position` palabra clave fuera de la declaración de atributo.

> [!NOTE]
> A menos que los parámetros deben tener un nombre, se recomienda que use los parámetros usados más posicionales para que los usuarios no tendrán que escribir el nombre del parámetro.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Declarar parámetros como obligatorio u opcional

Un cmdlet debe establecer cada parámetro como opcional o un parámetro obligatorio. En el ejemplo **Get-Proc** cmdlet, el `Name` parámetro se define como opcional, porque el `Mandatory` palabra clave no está establecida en la declaración de atributo.

## <a name="supporting-parameter-validation"></a>Compatibilidad con la validación de parámetros

El ejemplo **Get-Proc** cmdlet agrega un atributo de validación de entrada, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), a la `Name` parámetro para habilitar la validación que el entrada no es ni `null` ni está vacío. Este atributo es uno de varios atributos de validación proporcionados por Windows PowerShell. Para obtener ejemplos de otros atributos de validación, consulte [validar entrada de parámetros](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Reemplazar una método de procesamiento de entrada

Si es su cmdlet controlar la entrada de línea de comandos, debe invalidar los métodos de procesamiento de entrada adecuada. Los métodos de procesamiento de entrada básico se introducen en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md).

El **Get-Proc** cmdlet reemplaza el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para controlar el `Name` proporcionado por el usuario o un script de entrada de parámetros. Este método obtiene los procesos para cada nombre de proceso solicitado, o todos los procesos si no se proporciona ningún nombre. Tenga en cuenta que en [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), la llamada a [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) es el resultado mecanismo para enviar el resultado de los objetos a la canalización. El segundo parámetro de esta llamada, `enumerateCollection`, se establece en `true` informar al runtime de Windows PowerShell para enumerar la matriz de salida de objetos de proceso y escribir un proceso a la vez en la línea de comandos.

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
    // Write the processes to the pipeline making them available
    // to the next cmdlet. The second argument of this call tells
    // PowerShell to enumerate the array, and send one process at a
    // time to the pipeline.
    WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Ejemplo de código

Para la completa C# código de ejemplo, vea [ejemplo GetProcessSample02](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir los tipos de objeto y el formato

Windows PowerShell pasa información entre los cmdlets de mediante el uso de objetos de .NET Framework. Por lo tanto, podría necesitar un cmdlet definir su propio tipo, o un cmdlet que tenga que ampliar un tipo existente proporcionado por otro cmdlet. Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Compilar el Cmdlet

Después de implementar un cmdlet, debe registrarlo con Windows PowerShell mediante el uso de un complemento de Windows PowerShell. Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Probar el Cmdlet

Cuando el cmdlet se registra con Windows PowerShell, puede probarla mediante la ejecución de la línea de comandos. Hay dos formas para probar el código para el cmdlet de ejemplo. Para obtener más información sobre el uso de cmdlets de la línea de comandos, consulte [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- En el símbolo del sistema de Windows PowerShell, use el siguiente comando para enumerar el proceso de Internet Explorer, que se denomina "IEXPLORE."

    ```powershell
    PS> get-proc -name iexplore
    ```

Aparece el siguiente resultado.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- Para enumerar los procesos de Internet Explorer, Outlook y el Bloc de notas denominados "IEXPLORE", "OUTLOOK" y "NOTEPAD", usan el siguiente comando. Si hay varios procesos, todos ellos se muestran.

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

Aparece el siguiente resultado.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a>Véase también

[Agregar parámetros de entrada de la canalización de proceso](./adding-parameters-that-process-pipeline-input.md)

[Creación del primer Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Extensión de tipos de objeto y el formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Referencia de Windows PowerShell](../windows-powershell-reference.md)

[Ejemplos de cmdlet](./cmdlet-samples.md)
