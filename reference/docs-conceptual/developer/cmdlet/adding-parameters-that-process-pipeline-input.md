---
title: Agregando parámetros que procesan la entrada de canalización | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: 9ecb73a4138a5853fa5fb378874da2d81c5dbdba
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364604"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Adición de parámetros que procesan la entrada de la canalización

Un origen de entrada para un cmdlet es un objeto de la canalización que se origina en un cmdlet de nivel superior. En esta sección se describe cómo agregar un parámetro al cmdlet Get-proc (descrito en [creación del primer cmdlet](./creating-a-cmdlet-without-parameters.md)) para que el cmdlet pueda procesar objetos de canalización.

Este cmdlet Get-proc usa un parámetro `Name` que acepta la entrada de un objeto de canalización, recupera información del proceso del equipo local en función de los nombres proporcionados y, a continuación, muestra información sobre los procesos en la línea de comandos.

## <a name="defining-the-cmdlet-class"></a>Definir la clase de cmdlet

El primer paso en la creación de un cmdlet es siempre nombrar el cmdlet y declarar la clase .NET que implementa el cmdlet. Este cmdlet recupera información de proceso, por lo que el nombre de verbo elegido aquí es "Get". (Casi cualquier tipo de cmdlet que sea capaz de recuperar información puede procesar la entrada de la línea de comandos). Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).

A continuación se ofrece la definición de este cmdlet Get-proc. Los detalles de esta definición se proporcionan [al crear el primer cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>Definir la entrada de la canalización

En esta sección se describe cómo definir la entrada desde la canalización para un cmdlet. Este cmdlet Get-proc define una propiedad que representa el parámetro `Name` tal y como se describe en [agregar parámetros que procesan la entrada de la línea de comandos](./adding-parameters-that-process-command-line-input.md). (Vea ese tema para obtener información general sobre la declaración de parámetros).

Sin embargo, cuando un cmdlet necesita procesar la entrada de canalización, el tiempo de ejecución de Windows PowerShell debe enlazar sus parámetros a los valores de entrada. Para ello, debe agregar la palabra clave `ValueFromPipeline` o agregar la palabra clave `ValueFromPipelineByProperty` a la declaración [del atributo System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) . Especifique la palabra clave `ValueFromPipeline` si el cmdlet tiene acceso al objeto de entrada completo. Especifique el `ValueFromPipelineByProperty` si el cmdlet tiene acceso solo a una propiedad del objeto.

Esta es la declaración de parámetro para el parámetro `Name` de este cmdlet Get-proc que acepta la entrada de canalización.

[!code-csharp[GetProcessSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

La declaración anterior establece la palabra clave `ValueFromPipeline` en `true` para que el tiempo de ejecución de Windows PowerShell enlace el parámetro al objeto entrante si el objeto es del mismo tipo que el parámetro, o si se puede convertir en el mismo tipo. La palabra clave `ValueFromPipelineByPropertyName` también se establece en `true` para que el tiempo de ejecución de Windows PowerShell Compruebe el objeto de entrada de una propiedad `Name`. Si el objeto entrante tiene este tipo de propiedad, el tiempo de ejecución enlazará el parámetro `Name` a la propiedad `Name` del objeto entrante.

> [!NOTE]
> La configuración de la palabra clave del atributo `ValueFromPipeline` para un parámetro tiene prioridad sobre la configuración de la palabra clave `ValueFromPipelineByPropertyName`.

## <a name="overriding-an-input-processing-method"></a>Reemplazar un método de procesamiento de entrada

Si el cmdlet controla la entrada de canalización, debe invalidar los métodos de procesamiento de entrada adecuados. Los métodos de procesamiento de entrada básicos se introducen en [crear el primer cmdlet](./creating-a-cmdlet-without-parameters.md).

Este cmdlet Get-proc invalida el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) para controlar la entrada de parámetro `Name` proporcionada por el usuario o un script. Este método obtendrá los procesos de cada nombre de proceso solicitado o de todos los procesos si no se proporciona ningún nombre. Tenga en cuenta que en [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), la llamada a [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) es el mecanismo de salida para enviar objetos de salida a la canalización. El segundo parámetro de esta llamada, `enumerateCollection`, se establece en `true` para indicar al tiempo de ejecución de Windows PowerShell que Enumere la matriz de objetos de proceso y que escriba un proceso cada vez en la línea de comandos.

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
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Código de ejemplo

Para obtener el C# código de ejemplo completo, vea el [ejemplo de GetProcessSample03](./getprocesssample03-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto y formato

Windows PowerShell pasa información entre cmdlets mediante objetos .net. Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que el cmdlet tenga que extender un tipo existente proporcionado por otro cmdlet. Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Compilación del cmdlet

Después de implementar un cmdlet, debe registrarse con Windows PowerShell a través de un complemento de Windows PowerShell. Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Prueba del cmdlet

Cuando el cmdlet se haya registrado con Windows PowerShell, pruébelo en la línea de comandos. Por ejemplo, pruebe el código para el cmdlet de ejemplo. Para obtener más información sobre el uso de cmdlets desde la línea de comandos, consulte la [Introducción con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- En el símbolo del sistema de Windows PowerShell, escriba los siguientes comandos para recuperar los nombres de los procesos a través de la canalización.

    ```powershell
    PS> type ProcessNames | get-proc
    ```

Aparece el siguiente resultado.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- Escriba las líneas siguientes para obtener los objetos de proceso que tienen una propiedad `Name` de los procesos denominados "IEXPLORE". En este ejemplo se usa el cmdlet `Get-Process` (proporcionado por Windows PowerShell) como un comando de nivel superior para recuperar los procesos "IEXPLORE".

    ```powershell
    PS> get-process iexplore | get-proc
    ```

Aparece el siguiente resultado.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a>Véase también

[Agregar parámetros que procesan la entrada de la línea de comandos](./adding-parameters-that-process-command-line-input.md)

[Creación del primer cmdlet](./creating-a-cmdlet-without-parameters.md)

[Extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85))

[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85))

[Referencia de Windows PowerShell](../windows-powershell-reference.md)

[Ejemplos de cmdlet](./cmdlet-samples.md)
