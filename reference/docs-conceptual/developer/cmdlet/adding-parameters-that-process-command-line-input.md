---
title: Agregar parámetros que procesan la entrada de línea de comandos | Microsoft Docs
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
ms.openlocfilehash: 7db93af33717dc4802ed915793f6cd570cfb48f6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364634"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Adición de parámetros que procesan la entrada de la línea de comandos

Un origen de entrada para un cmdlet es la línea de comandos. En este tema se describe cómo agregar un parámetro al cmdlet **Get-proc** (que se describe en [creación del primer cmdlet](./creating-a-cmdlet-without-parameters.md)) para que el cmdlet pueda procesar la entrada del equipo local en función de los objetos explícitos pasados al cmdlet. El cmdlet **Get-proc** que se describe aquí recupera procesos en función de sus nombres y, a continuación, muestra información sobre los procesos en un símbolo del sistema.

## <a name="defining-the-cmdlet-class"></a>Definir la clase de cmdlet

El primer paso en la creación de un cmdlet es la nomenclatura de los cmdlets y la declaración de la clase .NET Framework que implementa el cmdlet. Este cmdlet recupera información de proceso, por lo que el nombre de verbo elegido aquí es "Get". (Casi cualquier tipo de cmdlet que sea capaz de recuperar información puede procesar la entrada de la línea de comandos). Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Esta es la declaración de clase para el cmdlet **Get-proc** . En [creación del primer cmdlet](./creating-a-cmdlet-without-parameters.md)se proporcionan detalles sobre esta definición.

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

Un parámetro de cmdlet permite al usuario proporcionar entradas al cmdlet. En el ejemplo siguiente, **Get-proc** y `Get-Member` son los nombres de los cmdlets canalizados y @no__t 2 es un parámetro para el cmdlet `Get-Member`. El parámetro tiene el argumento "Property".

**PS > Get-proc; `get-member`-propiedad MemberType**

Para declarar los parámetros de un cmdlet, primero debe definir las propiedades que representan los parámetros. En el cmdlet **Get-proc** , el único parámetro es `Name`, que en este caso representa el nombre del objeto de proceso de .NET Framework que se va a recuperar. Por lo tanto, la clase de cmdlet define una propiedad de tipo cadena para aceptar una matriz de nombres.

Esta es la declaración de parámetro para el parámetro `Name` del cmdlet **Get-proc** .

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

Para notificar al tiempo de ejecución de Windows PowerShell que esta propiedad es el parámetro `Name`, se agrega un atributo [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) a la definición de propiedad. La sintaxis básica para declarar este atributo es `[Parameter()]`.

> [!NOTE]
> Un parámetro debe marcarse explícitamente como Public. Los parámetros que no están marcados como públicos de forma predeterminada son internos y no se encuentran en el tiempo de ejecución de Windows PowerShell.

Este cmdlet usa una matriz de cadenas para el parámetro `Name`. Si es posible, el cmdlet también debe definir un parámetro como una matriz, ya que esto permite que el cmdlet acepte más de un elemento.

#### <a name="things-to-remember-about-parameter-definitions"></a>Aspectos que se deben recordar sobre las definiciones de parámetros

- Los nombres de parámetros y tipos de datos predefinidos de Windows PowerShell deben reutilizarse lo máximo posible para asegurarse de que el cmdlet es compatible con los cmdlets de Windows PowerShell. Por ejemplo, si todos los cmdlets usan el nombre de parámetro predefinido `Id` para identificar un recurso, el usuario entenderá fácilmente el significado del parámetro, independientemente del cmdlet que estén usando. Básicamente, los nombres de parámetro siguen las mismas reglas que los que se usan para los nombres de variable en el Common Language Runtime (CLR). Para obtener más información sobre la nomenclatura de parámetros, consulte [nombres de parámetros de cmdlet](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).

- Windows PowerShell reserva algunos nombres de parámetros para proporcionar una experiencia de usuario coherente. No use estos nombres de parámetro: `WhatIf`, `Confirm`, @no__t 2, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable` y `OutBuffer`. Además, se reservan los siguientes alias para los nombres de parámetro: `vb`, `db`, `ea`, `ev`, `ov` y `ob`.

- `Name` es un nombre de parámetro simple y común, que se recomienda para su uso en los cmdlets. Es mejor elegir un nombre de parámetro como este que un nombre complejo que sea único para un cmdlet específico y difícil de recordar.

- Los parámetros no distinguen mayúsculas de minúsculas en Windows PowerShell, aunque de forma predeterminada el shell conserva el uso de mayúsculas y minúsculas. La distinción de mayúsculas y minúsculas de los argumentos depende de la operación del cmdlet. Los argumentos se pasan a un parámetro tal y como se especifica en la línea de comandos.

- Para obtener ejemplos de otras declaraciones de parámetros, vea [parámetros de cmdlet](./cmdlet-parameters.md).

## <a name="declaring-parameters-as-positional-or-named"></a>Declarar parámetros como posicionales o con nombre

Un cmdlet debe establecer cada parámetro como un parámetro posicional o con nombre. Ambos tipos de parámetros aceptan argumentos únicos, varios argumentos separados por comas y valores booleanos. Un parámetro booleano, también denominado *modificador*, solo controla valores booleanos. El modificador se usa para determinar la presencia del parámetro. El valor predeterminado recomendado es `false`.

El cmdlet **Get-proc** de ejemplo define el parámetro `Name` como un parámetro posicional con la posición 0. Esto significa que el primer argumento que el usuario escribe en la línea de comandos se inserta automáticamente para este parámetro. Si desea definir un parámetro con nombre, para el que el usuario debe especificar el nombre del parámetro desde la línea de comandos, deje la palabra clave `Position` fuera de la declaración de atributo.

> [!NOTE]
> A menos que los parámetros se deban nombrar, se recomienda que haga que los parámetros más usados sean posicionales para que los usuarios no tengan que escribir el nombre del parámetro.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Declarar parámetros como obligatorios u opcionales

Un cmdlet debe establecer cada parámetro como parámetro opcional o obligatorio. En el cmdlet **Get-proc** de ejemplo, el parámetro `Name` se define como opcional porque la palabra clave `Mandatory` no está establecida en la declaración de atributo.

## <a name="supporting-parameter-validation"></a>Compatibilidad con la validación de parámetros

El cmdlet **Get-proc** de ejemplo agrega un atributo de validación de entrada, [System. Management. Automation. Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), al parámetro `Name` para habilitar la validación de que la entrada no está `null` ni está vacía. Este atributo es uno de varios atributos de validación proporcionados por Windows PowerShell. Para obtener ejemplos de otros atributos de validación, vea [validar la entrada de parámetros](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Reemplazar un método de procesamiento de entrada

Si el cmdlet controla la entrada de la línea de comandos, debe invalidar los métodos de procesamiento de entrada adecuados. Los métodos de procesamiento de entrada básicos se introducen en [crear el primer cmdlet](./creating-a-cmdlet-without-parameters.md).

El cmdlet **Get-proc** invalida el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) para controlar la entrada de parámetros `Name` proporcionada por el usuario o un script. Este método obtiene los procesos para cada nombre de proceso solicitado, o todos para los procesos si no se proporciona ningún nombre. Observe que en [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), la llamada a [System. Management. Automation. cmdlet. writeObject% 28System. Object% 2CSystem. Boolean %29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) es el mecanismo de salida para enviar objetos de salida a la DUCCION. El segundo parámetro de esta llamada, `enumerateCollection`, se establece en `true` para notificar al tiempo de ejecución de Windows PowerShell que Enumere la matriz de salida de objetos de proceso y que escriba un proceso cada vez en la línea de comandos.

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

## <a name="code-sample"></a>Código de ejemplo

Para obtener el C# código de ejemplo completo, vea el [ejemplo de GetProcessSample02](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto y formato

Windows PowerShell pasa información entre cmdlets mediante el uso de objetos de .NET Framework. Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que un cmdlet necesite extender un tipo existente proporcionado por otro cmdlet. Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Compilación del cmdlet

Después de implementar un cmdlet, debe registrarlo con Windows PowerShell mediante un complemento de Windows PowerShell. Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Prueba del cmdlet

Cuando el cmdlet se registra con Windows PowerShell, puede probarlo mediante su ejecución en la línea de comandos. A continuación se muestran dos maneras de probar el código para el cmdlet de ejemplo. Para obtener más información sobre el uso de cmdlets desde la línea de comandos, vea [Introducción con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- En el símbolo del sistema de Windows PowerShell, use el siguiente comando para mostrar el proceso de Internet Explorer, que se denomina "IEXPLORE".

    ```powershell
    PS> get-proc -name iexplore
    ```

Aparece el siguiente resultado.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- Para enumerar los procesos de Internet Explorer, Outlook y Notepad denominados "IEXPLORE", "OUTLOOK" y "NOTEPAD", use el siguiente comando. Si hay varios procesos, se muestran todos ellos.

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

[Agregar parámetros que procesan la entrada de canalización](./adding-parameters-that-process-pipeline-input.md)

[Creación del primer cmdlet](./creating-a-cmdlet-without-parameters.md)

[Extender tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Referencia de Windows PowerShell](../windows-powershell-reference.md)

[Ejemplos de cmdlet](./cmdlet-samples.md)
