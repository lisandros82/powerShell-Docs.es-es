---
title: Instrucciones de desarrollo requeridas | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: e68e43a91f9139e8d3dc636b5740121515aab2e6
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986680"
---
# <a name="required-development-guidelines"></a>Directrices de desarrollo necesarias

Al escribir los cmdlets, deben seguirse las siguientes directrices. Se dividen en directrices para diseñar cmdlets e instrucciones para escribir el código de cmdlet. Si no sigue estas instrucciones, se podría producir un error en los cmdlets y los usuarios podrían tener una experiencia deficiente al usar los cmdlets.

## <a name="in-this-topic"></a>En este tema

### <a name="design-guidelines"></a>Directrices de diseño

- [Usar solo verbos aprobados (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Nombres de cmdlet: Caracteres que no se pueden usar (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Nombres de parámetros que no se pueden usar (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Solicitudes de confirmación de soporte técnico (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Compatibilidad con el parámetro Force para sesiones interactivas (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Objetos de salida de documento (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Instrucciones de código

- [Derivar de las clases cmdlet o PSCmdlet (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Especificar el atributo de cmdlet (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Invalidar un método de procesamiento de entrada (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Especificar el atributo OutputType (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [No conservar los identificadores de los objetos de salida (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Control de errores de un solo punto (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Usar un módulo de Windows PowerShell para implementar los cmdlets (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Directrices de diseño

Se deben seguir las siguientes directrices al diseñar cmdlets para garantizar una experiencia de usuario coherente entre el uso de los cmdlets y otros cmdlets. Cuando encuentre una directriz de diseño que se aplique a su situación, asegúrese de consultar las instrucciones de código para obtener instrucciones similares.

### <a name="use-only-approved-verbs-rd01"></a>Usar solo verbos aprobados (RD01)

El verbo especificado en el atributo de cmdlet debe proviene del conjunto de verbos reconocidos proporcionado por Windows PowerShell. No debe ser uno de los sinónimos prohibidos. Use las cadenas de constantes definidas por las enumeraciones siguientes para especificar los verbos de cmdlet:

- [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Para obtener más información sobre los nombres de verbo aprobados, vea [verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Los usuarios necesitan un conjunto de nombres de cmdlet reconocible y esperado. Utilice el verbo adecuado para que el usuario pueda realizar una evaluación rápida de lo que hace un cmdlet y detectar fácilmente las capacidades del sistema. Por ejemplo, el siguiente comando de línea de comandos obtiene una lista de todos los comandos del sistema cuyos nombres comienzan por "Start": `get-command start-*`. Use los nombres de los cmdlets para diferenciar los cmdlets de otros cmdlets. El nombre indica el recurso en el que se realizará la operación. La propia operación se representa mediante el verbo.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Nombres de cmdlet: Caracteres que no se pueden usar (RD02)

Cuando asigne nombre a los cmdlets, no use ninguno de los siguientes caracteres especiales.

|Óptico|NOMBRE|
|---------------|----------|
|#|signo de número|
|,|unas|
|()|paréntesis|
|{}|llaves|
|[]|corchetes|
|&|operador|
|-|Nota de guiones **:**  El guion se puede usar para separar el verbo del nombre, pero no se puede usar dentro del sustantivo o dentro del verbo.|
|/|barra diagonal|
|\\| barra diagonal inversa|
|$|signo de dólar|
|^|intercalación|
|;|punto y coma|
|:|y|
|"|comillas dobles|
|'|comilla simple|
|<>|corchetes angulares|
|&#124;|barra vertical|
|?|signo de interrogación|
|@|arroba|
|`|marca de retroceso (acento grave)|
|*|aparezca|
|%|signo de porcentaje|
|+|signo más|
|=|signo igual|
|~|supresor|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Nombres de parámetros que no se pueden usar (RD03)

Windows PowerShell proporciona un conjunto común de parámetros a todos los cmdlets y parámetros adicionales que se agregan en situaciones específicas. Al diseñar sus propios cmdlets, no puede usar los siguientes nombres: CONFIRM, Debug, ErrorAction, ErrorVariable, outbuffer, outvariable, WarningAction, WarningVariable, WhatIf, UseTransaction y verbose. Para obtener más información sobre estos parámetros, consulte [nombres de parámetros comunes](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Solicitudes de confirmación de soporte técnico (RD04)

En el caso de los cmdlets que realizan una operación que modifica el sistema, deben llamar al método [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) para solicitar la confirmación y, en casos especiales, llamar a la [ Método System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . (El método [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) solo debe llamarse después de que se llame al método [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ).

Para realizar estas llamadas, el cmdlet debe especificar que admite solicitudes de confirmación estableciendo la `SupportsShouldProcess` palabra clave del atributo de cmdlet. Para obtener más información sobre la configuración de este atributo, vea [declaración de atributos de cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Si el atributo cmdlet de la clase de cmdlet indica que el cmdlet admite llamadas al método [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y el cmdlet no realiza la llamada a [ System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , el usuario podría modificar el sistema de forma inesperada.

Use el método [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) para cualquier modificación del sistema. Una preferencia de usuario y `WhatIf` el parámetro controlan el método [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . En cambio, la llamada a [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) realiza una comprobación adicional de las modificaciones potencialmente peligrosas. Este método no está controlado por ninguna preferencia de usuario ni `WhatIf` por el parámetro. Si el cmdlet llama al método [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , debe tener un `Force` parámetro que omita las llamadas a estos dos métodos y que continúe con la operación. Esto es importante porque permite que el cmdlet se use en scripts y hosts no interactivos.

Si los cmdlets admiten estas llamadas, el usuario puede determinar si la acción se debe realizar realmente. Por ejemplo, el cmdlet [Stop-Process](/powershell/module/microsoft.powershell.management/stop-process) llama al método [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) antes de detener un conjunto de procesos críticos, incluidos los procesos System, Winlogon y Spoolsv.

Para obtener más información acerca de la compatibilidad con estos métodos, consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Compatibilidad con el parámetro Force para sesiones interactivas (RD05)

Si el cmdlet se usa de forma interactiva, proporcione siempre un parámetro Force para invalidar las acciones interactivas, como mensajes o líneas de entrada de lectura. Esto es importante porque permite que el cmdlet se use en scripts y hosts no interactivos. Un host interactivo puede implementar los métodos siguientes.

- [System. Management. Automation. host. PSHostUserInterface. prompt *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System. Management. Automation. host. Pshostuserinterface. PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System. Management. Automation. host. Ihostuisupportsmultiplechoiceselection. PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System. Management. Automation. host. Pshostuserinterface. PromptForCredential *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System. Management. Automation. host. Pshostuserinterface. ReadLine *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System. Management. Automation. host. Pshostuserinterface. ReadLineAsSecureString *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Objetos de salida de documento (RD06)

Windows PowerShell usa los objetos que se escriben en la canalización. Para que los usuarios puedan aprovechar los objetos devueltos por cada cmdlet, debe documentar los objetos que se devuelven y debe documentar para qué se usan los miembros de esos objetos devueltos.

## <a name="code-guidelines"></a>Instrucciones de código

Las siguientes directrices se deben seguir al escribir código de cmdlet. Cuando encuentre una instrucción de código que se aplique a su situación, asegúrese de consultar las instrucciones de diseño para obtener instrucciones similares.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Derivar de las clases cmdlet o PSCmdlet (RC01)

Un cmdlet debe derivar de la clase base [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) o [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Los cmdlets que se derivan de la clase [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) no dependen del tiempo de ejecución de Windows PowerShell. Se pueden llamar directamente desde cualquier lenguaje de Microsoft .NET Framework. Los cmdlets que derivan de la clase [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) dependen del tiempo de ejecución de Windows PowerShell. Por lo tanto, se ejecutan dentro de un espacio de ejecución.

Todas las clases de cmdlet que implemente deben ser clases públicas. Para obtener más información sobre estas clases de cmdlets, vea [información general](./cmdlet-overview.md)sobre los cmdlets.

### <a name="specify-the-cmdlet-attribute-rc02"></a>Especificar el atributo de cmdlet (RC02)

Para que Windows PowerShell reconozca un cmdlet, su clase .NET Framework debe estar decorada con el atributo del cmdlet. Este atributo especifica las siguientes características del cmdlet.

- El par de verbo y sustantivo que identifica el cmdlet.

- Conjunto de parámetros predeterminado que se utiliza cuando se especifican varios conjuntos de parámetros. El conjunto de parámetros predeterminado se usa cuando Windows PowerShell no tiene información suficiente para determinar el conjunto de parámetros que se va a usar.

- Indica si el cmdlet admite llamadas al método [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Este método muestra un mensaje de confirmación al usuario antes de que el cmdlet realice un cambio en el sistema. Para obtener más información acerca de cómo se realizan las solicitudes de confirmación, consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).

- Indicar el nivel de impacto (o gravedad) de la acción asociada al mensaje de confirmación. En la mayoría de los casos, se debe usar el valor predeterminado de Medium. Para obtener más información sobre cómo afecta el nivel de impacto a las solicitudes de confirmación que se muestran al usuario, consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).

Para obtener más información sobre cómo declarar el atributo cmdlet, consulte [declaración de CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Invalidar un método de procesamiento de entrada (RC03)

Para que el cmdlet participe en el entorno de Windows PowerShell, debe reemplazar al menos uno de los siguientes *métodos de procesamiento de entrada*.

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) se llama a este método una vez y se usa para proporcionar la funcionalidad de procesamiento previo.

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) este método se llama varias veces y se usa para proporcionar la funcionalidad de registro por registro.

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) se llama a este método una vez y se usa para proporcionar la funcionalidad posterior al procesamiento.

### <a name="specify-the-outputtype-attribute-rc04"></a>Especificar el atributo OutputType (RC04)

El atributo OutputType (introducido en Windows PowerShell 2,0) especifica el tipo de .NET Framework que el cmdlet devuelve a la canalización. Al especificar el tipo de salida de los cmdlets, otros cmdlets pueden detectar los objetos devueltos por el cmdlet. Para obtener más información sobre cómo decorar la clase de cmdlet con este atributo, vea la [declaración de atributo OutputType](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>No conservar los identificadores de los objetos de salida (RC05)

El cmdlet no debe conservar ningún controlador para los objetos que se pasan al método [System. Management. Automation. cmdlet. writeObject *](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Estos objetos se pasan al siguiente cmdlet de la canalización o se usan en un script. Si conserva los identificadores de los objetos, dos entidades serán propietarias de cada objeto, lo que provocará errores.

### <a name="handle-errors-robustly-rc06"></a>Control de errores de un solo punto (RC06)

Un entorno de administración detecta de forma inherente y realiza cambios importantes en el sistema que se está administrando. Por lo tanto, es fundamental que los cmdlets controlen correctamente los errores. Para obtener más información sobre los registros de errores, vea [Informe de errores de Windows PowerShell](./error-reporting-concepts.md).

- Cuando un error impide que un cmdlet continúe procesando más registros, se trata de un error de terminación. El cmdlet debe llamar al método [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) que hace referencia a un objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Si el cmdlet no detecta una excepción, el propio tiempo de ejecución de Windows PowerShell genera un error de terminación que contiene menos información.

- En el caso de un error de no terminación que no detenga la operación en el siguiente registro procedente de la canalización (por ejemplo, un registro generado por un proceso diferente), el cmdlet debe llamar al método [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) que hace referencia a un objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Un ejemplo de error de no terminación es el error que se produce si un proceso determinado no se detiene. Llamar al método [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) permite al usuario realizar de forma coherente las acciones solicitadas y conservar la información de acciones concretas que producen un error. El cmdlet debe administrar cada registro de la forma más independiente posible.

- El objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) al que hacen referencia los métodos [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) y [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) requiere un cmdlet excepción en su núcleo. Siga las instrucciones de diseño de .NET Framework cuando determine la excepción que se va a usar. Si el error es semánticamente igual que una excepción existente, use esa excepción o derive de esa excepción. De lo contrario, derive una nueva jerarquía de excepción o excepción directamente del tipo [System. Exception](/dotnet/api/System.Exception) .

Un objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) también requiere una categoría de error que agrupa los errores del usuario. El usuario puede ver los errores en función de la categoría estableciendo el valor de `$ErrorView` la variable de Shell en CategoryView. Las categorías posibles se definen mediante la enumeración [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) .

- Si un cmdlet crea un nuevo subproceso, y si el código que se está ejecutando en ese subproceso produce una excepción no controlada, Windows PowerShell no detectará el error y finalizará el proceso.

- Si un objeto tiene código en su destructor que produce una excepción no controlada, Windows PowerShell no detectará el error y finalizará el proceso. Esto también se produce si un objeto llama a los métodos Dispose que causan una excepción no controlada.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Usar un módulo de Windows PowerShell para implementar los cmdlets (RC07)

Cree un módulo de Windows PowerShell para empaquetar e implementar los cmdlets. La compatibilidad con módulos se incluye en Windows PowerShell 2,0. Puede usar los ensamblados que contienen las clases de cmdlet directamente como archivos de módulo binario (esto es muy útil cuando se prueban los cmdlets) o se puede crear un manifiesto de módulo que haga referencia a los ensamblados de cmdlet. (También puede Agregar ensamblados de complementos existentes al usar módulos). Para obtener más información sobre los módulos, consulte [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Vea también

[Instrucciones de desarrollo muy recomendables](./strongly-encouraged-development-guidelines.md)

[Instrucciones para el desarrollo de asesoría](./advisory-development-guidelines.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
