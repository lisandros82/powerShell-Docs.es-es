---
title: Agregar alias, expansión de caracteres comodín y ayuda para los parámetros de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: d210a852a90d94df2ab360dd86f0b83a396330e3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415660"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Adición de alias, expansión de caracteres comodín y Ayuda a los parámetros del cmdlet

En esta sección se describe cómo agregar alias, expansión de caracteres comodín y mensajes de ayuda a los parámetros del cmdlet Stop-proc (que se describe en [creación de un cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md)).

Este cmdlet Stop-proc intenta detener los procesos que se recuperan con el cmdlet Get-proc (descrito en [creación del primer cmdlet](./creating-a-cmdlet-without-parameters.md)).

## <a name="defining-the-cmdlet"></a>Definición del cmdlet

El primer paso en la creación de un cmdlet es siempre nombrar el cmdlet y declarar la clase .NET que implementa el cmdlet. Dado que está escribiendo un cmdlet para cambiar el sistema, debe denominarse en consecuencia. Dado que este cmdlet detiene los procesos del sistema, utiliza el verbo "STOP", definido por la clase [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , con el nombre "proc" para indicar el proceso. Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).

El código siguiente es la definición de clase para este cmdlet Stop-proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definir parámetros para la modificación del sistema

El cmdlet debe definir parámetros que admitan las modificaciones del sistema y los comentarios de los usuarios. El cmdlet debe definir un parámetro `Name` o un equivalente para que el cmdlet pueda modificar el sistema mediante algún tipo de identificador. Además, el cmdlet debe definir los parámetros `Force` y `PassThru`. Para obtener más información acerca de estos parámetros, consulte [crear un cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>Definir un alias de parámetro

Un alias de parámetro puede ser un nombre alternativo o un nombre corto de 1 letra o 2 Letras bien definido para un parámetro de cmdlet. En ambos casos, el objetivo de usar alias es simplificar la entrada del usuario desde la línea de comandos. Windows PowerShell admite alias de parámetro mediante el atributo [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) , que usa la sintaxis de declaración [alias ()].

En el código siguiente se muestra cómo se agrega un alias al parámetro `Name`.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

Además de usar el atributo [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) , el tiempo de ejecución de Windows PowerShell realiza una coincidencia parcial de nombres, aunque no se especifique ningún alias. Por ejemplo, si el cmdlet tiene un parámetro `FileName` y éste es el único parámetro que comienza con `F`, el usuario podría escribir `Filename`, `Filenam`, `File`, `Fi`o `F` y seguir reconociendo la entrada como el parámetro `FileName`.

## <a name="creating-help-for-parameters"></a>Crear ayuda para parámetros

Windows PowerShell le permite crear ayuda para los parámetros de cmdlet. Haga esto para cualquier parámetro utilizado para la modificación del sistema y los comentarios de los usuarios. Para que cada parámetro admita la ayuda, puede establecer la palabra clave de atributo `HelpMessage` en la declaración de atributo [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) . Esta palabra clave define el texto que se va a mostrar al usuario para obtener ayuda sobre el uso del parámetro. También puede establecer la palabra clave `HelpMessageBaseName` para identificar el nombre base de un recurso que se va a usar para el mensaje. Si establece esta palabra clave, también debe establecer la palabra clave `HelpMessageResourceId` para especificar el identificador de recursos.

El siguiente código de este cmdlet Stop-proc define la palabra clave del atributo `HelpMessage` para el parámetro `Name`.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a>Reemplazar un método de procesamiento de entrada

El cmdlet debe invalidar un método de procesamiento de entrada, lo que suele ser [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Al modificar el sistema, el cmdlet debe llamar a los métodos [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) para permitir que el usuario proporcione comentarios antes de que se realice un cambio. Para obtener más información acerca de estos métodos, consulte [crear un cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Compatibilidad con la expansión de caracteres comodín

Para permitir la selección de varios objetos, el cmdlet puede usar las clases [System. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) y [System. Management. Automation. Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) para proporcionar compatibilidad con la expansión de caracteres comodín para la entrada de parámetros. Algunos ejemplos de patrones de caracteres comodín son LSA *, \*. txt y [a-c]\*. Use el carácter de comilla inversa (') como carácter de escape cuando el patrón contenga un carácter que se deba usar literalmente.

Las expansiones de comodín de los nombres de archivo y de ruta de acceso son ejemplos de escenarios comunes en los que el cmdlet puede querer permitir la compatibilidad con entradas de ruta de acceso cuando se requiere la selección de varios objetos. Un caso común está en el sistema de archivos, en el que un usuario desea ver todos los archivos que residen en la carpeta actual.

Solo necesitará una implementación personalizada de coincidencia de patrones de caracteres comodín. En este caso, el cmdlet debe ser compatible con la especificación de POSIX 1003,2, 3,13 completa para la expansión de caracteres comodín o el siguiente subconjunto simplificado:

- **Signo de interrogación (?).** Coincide con cualquier carácter que se encuentra en la ubicación especificada.

- **Asterisco (\*).** Coincide con cero o más caracteres que comienzan en la ubicación especificada.

- **Corchete de apertura ([).** Introduce una expresión entre corchetes de patrón que puede contener caracteres o un intervalo de caracteres. Si se requiere un intervalo, se usa un guión (-) para indicar el intervalo.

- **Corchete de cierre (]).** Finaliza una expresión de corchete de patrón.

- **Carácter de escape de comilla inversa (').** Indica que el siguiente carácter debe tomarse literalmente. Tenga en cuenta que al especificar el carácter de comilla inversa desde la línea de comandos (en lugar de especificarlo mediante programación), el carácter de escape de comilla inversa debe especificarse dos veces.

> [!NOTE]
> Para obtener más información sobre los patrones de caracteres comodín, consulte [compatibilidad con caracteres comodín en parámetros de cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).

El código siguiente muestra cómo establecer opciones de carácter comodín y definir el patrón de caracteres comodín que se usa para resolver el parámetro `Name` para este cmdlet.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

En el código siguiente se muestra cómo comprobar si el nombre del proceso coincide con el patrón de caracteres comodín definido. Tenga en cuenta que, en este caso, si el nombre del proceso no coincide con el patrón, el cmdlet continúa para obtener el nombre del proceso siguiente.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Ejemplo de código

Para obtener el C# código de ejemplo completo, vea el [ejemplo de StopProcessSample03](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Definir tipos de objeto y formato

Windows PowerShell pasa información entre cmdlets mediante objetos .net. Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que el cmdlet tenga que extender un tipo existente proporcionado por otro cmdlet. Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Compilación del cmdlet

Después de implementar un cmdlet, debe registrarse con Windows PowerShell a través de un complemento de Windows PowerShell. Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Prueba del cmdlet

Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarlo mediante su ejecución en la línea de comandos. Vamos a probar el cmdlet Stop-proc de ejemplo. Para obtener más información sobre el uso de cmdlets desde la línea de comandos, consulte la [Introducción con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Inicie Windows PowerShell y use STOP-proc para detener un proceso con el alias processName para el parámetro `Name`.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

Aparece la salida siguiente.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Realice la siguiente entrada en la línea de comandos. Dado que el parámetro name es obligatorio, se le pedirá que lo indique. Escribiendo "!?" muestra el texto de ayuda asociado al parámetro.

    ```powershell
    PS> stop-proc
    ```

Aparece la salida siguiente.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- Ahora realice la siguiente entrada para detener todos los procesos que coinciden con el patrón de carácter comodín "* note\*". Se le pedirá antes de detener cada proceso que coincida con el patrón.

    ```powershell
    PS> stop-proc -Name *note*
    ```

Aparece la salida siguiente.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

Aparece la salida siguiente.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

Aparece la salida siguiente.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Véase también

[Crear un cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Cómo crear un cmdlet de Windows PowerShell](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85))

[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85))

[Compatibilidad con caracteres comodín en parámetros de cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
