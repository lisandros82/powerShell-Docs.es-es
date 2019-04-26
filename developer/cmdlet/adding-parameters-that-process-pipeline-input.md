---
title: Adición de parámetros que procesan la entrada de la canalización | Microsoft Docs
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
ms.openlocfilehash: bd52dc8aee7975d0899083a5c2f595b17690dc33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068766"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Adición de parámetros que procesan la entrada de la canalización

Un origen de entrada para un cmdlet es un objeto en la canalización que se origina en un cmdlet de nivel superior. En esta sección se describe cómo agregar un parámetro al cmdlet Get-Proc (se describe en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md)) para que el cmdlet puede procesar objetos de la canalización.

Este cmdlet Get-Proc usa un `Name` parámetro que acepta la entrada desde un objeto de canalización, recupera información de proceso del equipo local en función de los nombres proporcionados y, a continuación, muestra información acerca de los procesos en la línea de comandos.

Temas de esta sección incluyen lo siguiente:

- [Definición de la clase de Cmdlet](#Defining-the-Cmdlet-Class)

- [Definir la entrada de la canalización](#Defining-Input-from-the-Pipeline)

- [Reemplazar una método de procesamiento de entrada](#Overriding-an-Input-Processing-Method)

- [Ejemplo de código](#Code-Sample)

- [Definir los tipos de objeto y el formato](#Defining-Object-Types-and-Formatting)

- [Compilar el Cmdlet](#Building-the-Cmdlet)

- [Probar el Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Definición de la clase de Cmdlet

El primer paso en la creación de cmdlet siempre es el cmdlet de nomenclatura y declarar la clase de .NET que implementa el cmdlet. Este cmdlet recupera información de proceso, por lo que el nombre del verbo seleccionado aquí es "Get". (Casi cualquier tipo de cmdlet que es capaz de recuperar la información puede procesar la entrada de línea de comandos). Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

La siguiente es la definición de este cmdlet Get-Proc. Se proporcionan detalles de esta definición [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md).

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

En esta sección se describe cómo definir la entrada de la canalización para un cmdlet. Este cmdlet Get-Proc define una propiedad que representa el `Name` parámetro tal y como se describe en [agregar parámetros que procesan datos de línea de comandos](./adding-parameters-that-process-command-line-input.md). (Consulte ese tema para obtener información general sobre la declaración de parámetros).

Sin embargo, cuando un cmdlet debe procesar la entrada de la canalización, debe tener sus parámetros enlazados a los valores de entrada por el tiempo de ejecución de Windows PowerShell. Para ello, debe agregar el `ValueFromPipeline` palabra clave o agregar el `ValueFromPipelineByProperty` palabra clave para el [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaración de atributos. Especifique el `ValueFromPipeline` palabra clave si el cmdlet obtiene acceso al objeto de entrada completando. Especifique el `ValueFromPipelineByProperty` si el cmdlet obtiene acceso a una propiedad del objeto.

Esta es la declaración de parámetros para el `Name` parámetro de este cmdlet Get-Proc que acepta la entrada de la canalización.

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

Los conjuntos de la declaración anterior el `ValueFromPipeline` palabra clave para `true` para que el tiempo de ejecución de Windows PowerShell enlazará el parámetro para el objeto entrante, si el objeto es el mismo tipo que el parámetro, o si se puede convertirse en el mismo tipo. El `ValueFromPipelineByPropertyName` palabra clave también se establece en `true` para que el tiempo de ejecución de Windows PowerShell comprobará el objeto entrante para un `Name` propiedad. Si el objeto entrante tiene dicha propiedad, el tiempo de ejecución se enlazará el `Name` parámetro para el `Name` propiedad del objeto entrante.

> [!NOTE]
> La configuración de la `ValueFromPipeline` palabra clave de atributo de un parámetro tiene prioridad sobre la configuración de la `ValueFromPipelineByPropertyName` palabra clave.

## <a name="overriding-an-input-processing-method"></a>Reemplazar una método de procesamiento de entrada

Si es su cmdlet controlar la entrada de canalización, debe invalidar los métodos de procesamiento de entrada adecuada. Los métodos de procesamiento de entrada básico se introducen en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md).

Este cmdlet Get-Proc invalida la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para controlar el `Name` proporcionado por el usuario o un script de entrada de parámetros. Este método obtiene los procesos para cada nombre de proceso solicitado o todos los procesos si se proporciona ningún nombre. Tenga en cuenta que dentro de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), la llamada a [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) es el resultado mecanismo para enviar el resultado de los objetos a la canalización. El segundo parámetro de esta llamada, `enumerateCollection`, se establece en `true` para indicar al runtime de Windows PowerShell para enumerar la matriz de objetos de proceso y escribir un proceso a la vez en la línea de comandos.

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

## <a name="code-sample"></a>Ejemplo de código

Para la completa C# código de ejemplo, vea [GetProcessSample03 ejemplo](./getprocesssample03-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir los tipos de objeto y el formato

Windows PowerShell pasa información entre cmdlets mediante objetos. NET. Por lo tanto, un cmdlet que deba definir su propio tipo o el cmdlet puede necesitar extender un tipo existente proporcionado por otro cmdlet. Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Compilar el Cmdlet

Después de implementar un cmdlet se debe registrar con Windows PowerShell a través de un complemento de Windows PowerShell. Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Probar el Cmdlet

Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarla mediante la ejecución de la línea de comandos. Por ejemplo, pruebe el código para el cmdlet de ejemplo. Para obtener más información sobre el uso de cmdlets de la línea de comandos, consulte el [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- En el símbolo del sistema de Windows PowerShell, escriba los comandos siguientes para recuperar los nombres de proceso a través de la canalización.

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

- Escriba las líneas siguientes para obtener los objetos de proceso que tienen un `Name` propiedad de los procesos denominados "IEXPLORE". Este ejemplo se usa el `Get-Process` cmdlet (proporcionado por Windows PowerShell) como un comando para recuperar los procesos "IEXPLORE" ascendente.

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

[Adición de parámetros que procesa la entrada de línea de comandos](./adding-parameters-that-process-command-line-input.md)

[Creación del primer Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Extensión de tipos de objeto y el formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Referencia de Windows PowerShell](../windows-powershell-reference.md)

[Ejemplos de cmdlet](./cmdlet-samples.md)
