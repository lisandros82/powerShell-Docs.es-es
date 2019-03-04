---
title: Agregar alias, expansión de caracteres comodín y ayudar a los parámetros de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: 0f025213087e6f308adf8e597fc01c1320251f76
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859331"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Adición de alias, expansión de caracteres comodín y Ayuda a los parámetros del cmdlet

En esta sección se describe cómo agregar los alias, expansión de caracteres comodín, y los mensajes de ayuda a los parámetros del cmdlet Stop-Proc (se describe en [creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md)).

Este cmdlet Stop-Proc intenta detener los procesos que se recuperan mediante el cmdlet Get-Proc (se describe en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Temas de esta sección incluyen lo siguiente:

- [Definir el Cmdlet](#Defining-the-Cmdlet)

- [Definir parámetros para la modificación del sistema](#Defining-Parameters-for-System-Modification)

- [Definir un Alias de parámetro](#Defining-a-Parameter-Alias)

- [Ayuda para los parámetros de creación](#Creating-Help-for-Parameters)

- [Reemplazar una método de procesamiento de entrada](#Overriding-an-Input-Processing-Method)

- [Compatibilidad con la expansión de caracteres comodín](#Supporting-Wildcard-Expansion)

- [Ejemplo de código](#Defining-a-Parameter-Alias)

- [Definir los tipos de objeto y el formato](#Define-Object-Types-and-Formatting)

- [Compilar el Cmdlet](#Building-the-Cmdlet)

- [Probar el Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definir el Cmdlet

El primer paso en la creación de cmdlet siempre es el cmdlet de nomenclatura y declarar la clase de .NET que implementa el cmdlet. Dado que está escribiendo un cmdlet para cambiar el sistema, debe llamarse en consecuencia. Dado que este cmdlet detiene los procesos del sistema, utiliza el verbo "Stop", definido por el [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) (clase), con el sustantivo "Proc" para indicar el proceso. Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

El código siguiente es la definición de clase para este cmdlet Stop-Proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definir parámetros para la modificación del sistema

El cmdlet debe definir los parámetros que las modificaciones del sistema de soporte técnico y comentarios del usuario. El cmdlet debe definir un `Name` parámetro o un equivalente para que el cmdlet pueda modificar el sistema por algún tipo de identificador. Además, debe definir el cmdlet la `Force` y `PassThru` parámetros. Para obtener más información acerca de estos parámetros, vea [creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>Definir un Alias de parámetro

Un alias de parámetro puede ser un nombre alternativo o un bien definido letra de 1 o 2 nombre corto para un parámetro de cmdlet. En ambos casos, el objetivo de uso de alias es simplificar la entrada de usuario desde la línea de comandos. Windows PowerShell es compatible con alias de parámetro a través de la [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, que utiliza la sintaxis de declaración [Alias()].

El código siguiente muestra cómo se agrega un alias para el `Name` parámetro.

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

Además de utilizar el [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atributo, el tiempo de ejecución de Windows PowerShell realiza la coincidencia de nombres parciales, incluso si no se especifican ningún alias. Por ejemplo, si su cmdlet tiene un `FileName` parámetro y que es el único parámetro que empieza por `F`, el usuario puede escribir `Filename`, `Filenam`, `File`, `Fi`, o `F` y aún reconoce los entrada de la `FileName` parámetro.

## <a name="creating-help-for-parameters"></a>Ayuda para los parámetros de creación

Windows PowerShell le permite crear ayuda para los parámetros de cmdlet. Hacer esto para cualquier parámetro que se usa para los comentarios de usuario y la modificación del sistema. Para que cada parámetro admitir la Ayuda, puede establecer el `HelpMessage` atributo palabra clave en el [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaración de atributos. Esta palabra clave define el texto para mostrar al usuario para asistencia en el uso del parámetro. También puede establecer el `HelpMessageBaseName` palabra clave para identificar el nombre de base de un recurso que se usará para el mensaje. Si establece esta palabra clave, también debe establecer el `HelpMessageResourceId` palabra clave para especificar el identificador de recurso.

El siguiente código de este cmdlet Stop-Proc define la `HelpMessage` atributo palabra clave para el `Name` parámetro.

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

## <a name="overriding-an-input-processing-method"></a>Reemplazar una método de procesamiento de entrada

El cmdlet debe invalidar una método de procesamiento de entrada, con más frecuencia esto será [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Cuando se modifica el sistema, el cmdlet debe llamar a la [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos para permitir que el usuario para proporcionar comentarios antes de que se realiza un cambio. Para obtener más información acerca de estos métodos, consulte [creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Compatibilidad con la expansión de caracteres comodín

Para permitir la selección de varios objetos, puede usar el cmdlet la [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) y [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) las clases para proporcionar compatibilidad con la expansión de caracteres comodín para el parámetro de entrada. Ejemplos de patrones de caracteres comodín son lsa * \*.txt y [a-c]\*. Use el carácter de comilla invertida (') como carácter de escape cuando el modelo contiene un carácter que se debe usar literalmente.

Las expansiones de comodín de nombres de archivo y ruta de acceso son ejemplos de escenarios comunes en el cmdlet puede que desee permitir la compatibilidad para las entradas de ruta de acceso cuando se requiere la selección de varios objetos. Un caso común es en el sistema de archivos, donde un usuario desea ver todos los archivos que residen en la carpeta actual.

Es necesario una implementación de coincidencia de patrón comodín personalizados solo en raras ocasiones. En este caso, el cmdlet debe admitir la versión 1003.2 POSIX completa, 3,13 especificación para la expansión de caracteres comodín o el siguiente subconjunto simplificado:

- **Signo de interrogación (?).** Coincide con cualquier carácter que ocupa la posición especificada.

- **Asterisk (\*).** Coincide con cero o más caracteres, empezando en la ubicación especificada.

- **Corchete de apertura ([]).** Presenta una expresión entre corchetes de patrón que puede contener caracteres o un intervalo de caracteres. Si se requiere un intervalo, un guión (-) se utiliza para indicar el intervalo.

- **Corchete de cierre (]).** Finaliza una expresión entre corchetes.

- **Carácter de escape (') comilla.** Indica que se debe tomar literalmente el carácter siguiente. Tenga en cuenta que al especificar el carácter de comilla desde la línea de comandos (en lugar de especificar mediante programación), el carácter de comilla escape debe especificarse dos veces.

> [!NOTE]
> Para obtener más información sobre los patrones de caracteres comodín, consulte [que admiten caracteres comodín en los parámetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).

El código siguiente muestra cómo establecer las opciones de comodín y definir el modelo de carácter comodín se utiliza para resolver el `Name` parámetro para este cmdlet.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

El código siguiente se muestra cómo probar si el nombre del proceso coincide con el patrón comodín definido. Tenga en cuenta que, en este caso, si el nombre del proceso no coincide con el patrón, el cmdlet continúa en obtener el nombre del proceso siguiente.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Ejemplo de código

Para la completa C# código de ejemplo, vea [StopProcessSample03 ejemplo](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Definir tipos de objeto y el formato

Windows PowerShell pasa información entre cmdlets mediante objetos. NET. Por lo tanto, un cmdlet que deba definir su propio tipo o el cmdlet puede necesitar extender un tipo existente proporcionado por otro cmdlet. Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Compilar el Cmdlet

Después de implementar un cmdlet, se debe registrar con Windows PowerShell a través de un complemento de Windows PowerShell. Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Probar el Cmdlet

Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarla mediante la ejecución de la línea de comandos. Vamos a probar el cmdlet Stop-Proc de ejemplo. Para obtener más información sobre el uso de cmdlets de la línea de comandos, consulte el [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Inicie Windows PowerShell y use Stop-Proc para detener un proceso mediante el alias de nombre de proceso para el `Name` parámetro.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

Aparece el siguiente resultado.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Escriba lo siguiente en la línea de comandos. Dado que el parámetro de nombre es obligatorio, le para él. Escribir "!?" aparece el texto de ayuda asociado al parámetro.

    ```powershell
    PS> stop-proc
    ```

Aparece el siguiente resultado.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- Ahora escriba lo siguiente para detener todos los procesos que coinciden con el patrón de carácter comodín "* Nota\*". Se le solicite antes de detener todos los procesos que coincide con el modelo.

    ```powershell
    PS> stop-proc -Name *note*
    ```

Aparece el siguiente resultado.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

Aparece el siguiente resultado.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

Aparece el siguiente resultado.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Véase también

[Crear un Cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Creación de un Cmdlet de Windows PowerShell](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Extensión de tipos de objeto y el formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Compatibilidad con caracteres comodín en los parámetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
