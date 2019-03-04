---
title: Instrucciones de desarrollo necesarias | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: a4b228be91bba27670b26fe21e765ae942afe968
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860721"
---
# <a name="required-development-guidelines"></a>Directrices de desarrollo necesarias

Las siguientes directrices se deben seguir al escribir sus cmdlets. Se dividen en las directrices para diseñar los cmdlets y las instrucciones para escribir el código del cmdlet. Si no sigue estas instrucciones, podría producirse un error en los cmdlets y los usuarios podrían tener una experiencia deficiente al usar los cmdlets.

## <a name="in-this-topic"></a>En este tema

### <a name="design-guidelines"></a>Instrucciones de diseño

- [Use solamente los verbos (RD01) aprobados](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Nombres de cmdlet: Caracteres que no se puede usar (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Los nombres de parámetros que no se puede usar (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Compatibilidad con las solicitudes de confirmación (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Admite el parámetro Force para sesiones interactivas (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Objetos de documento de salida (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Instrucciones de código

- [Derivar de las clases de PSCmdlet (RC01) o el Cmdlet](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Especificar el atributo de Cmdlet (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Invalidar una método (RC03) de procesamiento de entrada](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Especificar el atributo OutputType (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [No conservan los identificadores de objetos de salida (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Administrar con eficacia los errores (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Usar un módulo de Windows PowerShell para implementar sus Cmdlets (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Instrucciones de diseño

Las siguientes directrices se deben seguir al diseñar los cmdlets para garantizar una experiencia de usuario coherente entre el uso de los cmdlets y otros cmdlets. Cuando encuentre una guía de diseño que se aplica a su situación, asegúrese de consultar las instrucciones de código para obtener instrucciones similares.

### <a name="use-only-approved-verbs-rd01"></a>Use solamente los verbos (RD01) aprobados

El verbo especificado en el atributo de Cmdlet debe proceder de la reconocida conjunto de verbos proporcionados por Windows PowerShell. No debe ser uno de los sinónimos prohibidos. Utilice las cadenas constantes que se definen mediante las siguientes enumeraciones para especificar los verbos de cmdlet:

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Para obtener más información acerca de los nombres de verbo aprobado, consulte [verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Los usuarios necesitan un conjunto de nombres de cmdlet detectables y esperado. Use el verbo adecuado para que el usuario puede realizar una evaluación rápida de lo que hace un cmdlet y detectar fácilmente las capacidades del sistema. Por ejemplo, el siguiente comando de línea de comandos obtiene una lista de todos los comandos en el sistema cuyos nombres comienzan con "start": `get-command start-*`. Use los nombres de los cmdlets para diferenciar los cmdlets de otros cmdlets. El nombre indica el recurso en el que se realizará la operación. La operación en sí se representa mediante el verbo.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Nombres de cmdlet: Caracteres que no se puede usar (RD02)

Cuando asigne nombre a los cmdlets, no utilice ninguno de los siguientes caracteres especiales.

|Carácter|Nombre|
|---------------|----------|
|#|signo de número|
|,|comma|
|()|Paréntesis|
|{}|ortodoncia|
|[]|corchetes|
|&|"y" comercial|
|-|guión **Nota:**  Se puede usar el guión para separar el verbo desde el sustantivo, pero no puede utilizarse dentro de la palabra o el verbo.|
|/|marca de barra diagonal|
|\|backslash|
|$|Signo de dólar|
|^|Símbolo de intercalación|
|;|semicolon|
|:|Dos puntos|
|"|comillas dobles|
|'|comilla simple|
|<>|corchetes angulares|
|&#124;|barra vertical|
|?|signo de interrogación|
|@|arroba|
|' | hacer una copia de graduación (acento grave)|
|*|asterisk|
|%|Signo de porcentaje|
|+|Signo más|
|=|Signo igual|
|~|tilda|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Los nombres de parámetros que no se puede usar (RD03)

Windows PowerShell ofrece un conjunto común de parámetros para todos los cmdlets más parámetros adicionales que se agregan en situaciones específicas. Al diseñar sus propios cmdlets no puede usar los siguientes nombres: Confirmar, Debug, ErrorAction, ErrorVariable, OutVariable OutBuffer, WarningAction, WarningVariable, WhatIf, UseTransaction y detallado. Para obtener más información acerca de estos parámetros, vea [comunes de los nombres de parámetro](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Compatibilidad con las solicitudes de confirmación (RD04)

Para los cmdlets que realizan una operación que modifique el sistema, debe llamar a la [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para solicitar confirmación y, en casos especiales, llame a la [ System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método. (El [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método se debe llamar solo después de la [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) se llama al método.)

Para realizar estas llamadas debe especificar el cmdlet que admite solicitudes de confirmación estableciendo el `SupportsShouldProcess` palabra clave del atributo de Cmdlet. Para obtener más información acerca de cómo establecer este atributo, vea [declaración de atributo de Cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Si el atributo de Cmdlet de la clase de cmdlet indica que el cmdlet admite llamadas a la [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) no se puede realizar la llamada al método y el cmdlet la [ System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método, el usuario podría modificar el sistema de forma inesperada.

Use la [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para cualquier modificación del sistema. Una preferencia de usuario y la `Whatif` control parámetro el [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. En cambio, el [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) llamada lleva a cabo una comprobación adicional para realizar modificaciones potencialmente peligrosas. Este método no se controla mediante las preferencias de usuario o el `Whatif` parámetro. Si llama al cmdlet la [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método, debe tener un `Force` parámetro que pasa por alto las llamadas a estos dos métodos y que continúa con la operación. Esto es importante porque permite que el cmdlet para usarse en hosts y las secuencias de comandos no interactivo.

Si los cmdlets de admiten estas llamadas, el usuario puede determinar si realmente se debe realizar la acción. Por ejemplo, el [Stop-Process](/powershell/module/microsoft.powershell.management/stop-process) cmdlet llamadas la [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método antes de detenerse un conjunto de procesos vitales, incluido el sistema, Winlogon, y Spoolsrv procesos.

Para obtener más información sobre la compatibilidad con estos métodos, consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Admite el parámetro Force para sesiones interactivas (RD05)

Si el cmdlet se usa de forma interactiva, siempre proporcione un parámetro Force para invalidar las acciones interactivas, como mensajes o la lectura de líneas de entrada). Esto es importante porque permite que el cmdlet para usarse en hosts y las secuencias de comandos no interactivo. Los métodos siguientes pueden implementarse mediante un host interactivo.

- [System.Management.Automation.Host.PSHostUserInterface.Prompt*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection.PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForCredential*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLine*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLineAsSecureString*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Objetos de documento de salida (RD06)

Windows PowerShell usa los objetos que se escriben en la canalización. En orden para que los usuarios aprovechar las ventajas de los objetos devueltos por cada cmdlet, debe documentar los objetos que se devuelven y debe documentar para qué se utilizan los miembros de los objetos devueltos.

## <a name="code-guidelines"></a>Instrucciones de código

Las siguientes directrices se deben seguir al escribir el código del cmdlet. Cuando encuentre una directriz de código que se aplica a su situación, asegúrese de consultar las instrucciones de diseño para obtener instrucciones similares.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Derivar de las clases de PSCmdlet (RC01) o el Cmdlet

Un cmdlet debe derivarse de o el [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) o [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) clase base. Los cmdlets que se derivan de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase no dependen del tiempo de ejecución de Windows PowerShell. Se puede llamar directamente desde cualquier lenguaje de Microsoft .NET Framework. Los cmdlets que se derivan de la [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) clase dependen del tiempo de ejecución de Windows PowerShell. Por lo tanto, se ejecutan dentro de un espacio de ejecución.

Todas las clases de cmdlet que implemente deben ser clases públicas. Para obtener más información sobre estas clases de cmdlet, consulte [información general cmdlets](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Especificar el atributo de Cmdlet (RC02)

Para que un cmdlet de Windows PowerShell reconozca, su clase de .NET Framework debe decorarse con el atributo de Cmdlet. Este atributo especifica las características siguientes del cmdlet.

- El par de verbo y sustantivo que identifica el cmdlet.

- El conjunto de parámetros predeterminados que se usa cuando se especifican varios conjuntos de parámetros. El conjunto de parámetros de forma predeterminada se usa cuando Windows PowerShell no tiene suficiente información para determinar qué conjunto de parámetros para usar.

- Indica si el cmdlet admite llamadas a la [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. Este método muestra un mensaje de confirmación al usuario antes de que el cmdlet realiza un cambio en el sistema. Para obtener más información acerca de cómo se realizan las solicitudes de confirmación, vea [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).

- Indicar el nivel de impacto (o gravedad) de la acción asociada con el mensaje de confirmación. En la mayoría de los casos, debe usarse el valor predeterminado de medio. Para obtener más información sobre cómo el nivel de impacto afecta a las solicitudes de confirmación que se muestran al usuario, consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).

Para obtener más información acerca de cómo declarar el atributo de cmdlet, consulte [declaración CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Invalidar una método (RC03) de procesamiento de entrada

Para que el cmdlet para participar en el entorno de Windows PowerShell, debe reemplazar al menos uno de los siguientes *métodos de procesamiento de entrada*.

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) este método se llama una vez y se utiliza para proporcionar funcionalidad de procesamiento previo.

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) este método se llama varias veces y se utiliza para proporcionar funcionalidad de registro por registro.

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) este método se llama una vez y se utiliza para proporcionar funcionalidad de procesamiento posterior.

### <a name="specify-the-outputtype-attribute-rc04"></a>Especificar el atributo OutputType (RC04)

El atributo OutputType (introducido en Windows PowerShell 2.0) especifica el tipo de .NET Framework que el cmdlet devuelve a la canalización. Al especificar el tipo de salida de los cmdlets de realizar los objetos devueltos por el cmdlet más reconocibles por otros cmdlets. Para obtener más información acerca de la decoración de la clase del cmdlet con este atributo, vea [declaración de atributo OutputType](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>No conservan los identificadores de objetos de salida (RC05)

El cmdlet no debe conservar los identificadores a los objetos que se pasan a la [System.Management.Automation.Cmdlet.WriteObject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. Estos objetos se pasan al siguiente cmdlet en la canalización o son usados por una secuencia de comandos. Si mantiene los identificadores de los objetos, dos entidades pertenecerán a cada objeto, lo que produce errores.

### <a name="handle-errors-robustly-rc06"></a>Administrar con eficacia los errores (RC06)

Intrínsecamente un entorno de administración detecta y realiza cambios importantes en el sistema que está administrando. Por lo tanto, es fundamental que los cmdlets de controlar correctamente los errores. Para obtener más información acerca de los registros de error, consulte [informes de errores de Windows PowerShell](./error-reporting-concepts.md).

- Cuando un error impide que un cmdlet continúe procesar más registros, es un error de terminación. El cmdlet debe llamar a la [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método que hace referencia a un [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto. Si no se detecta una excepción mediante el cmdlet, el propio tiempo de ejecución de Windows PowerShell produce un error de terminación que contiene menos información.

- Para un error de no terminación que no se detiene en la siguiente operación de registro que procede de la canalización (por ejemplo, un registro generado por un proceso diferente), el cmdlet debe llamar el [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método que hace referencia a un [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto. Un ejemplo de un error de no terminación es el error que se produce si no se puede detener un proceso determinado. Una llamada a la [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método permite al usuario que constantemente realizan las acciones solicitadas y para conservar la información de acciones concretas que producirá un error. El cmdlet debe controlar cada registro que de manera independiente como sea posible.

- El [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto al que hace referencia el [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) y [ System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) métodos requiere una excepción en su núcleo. Siga las instrucciones de diseño de .NET Framework al determinar la excepción a usar. Si el error es semánticamente igual que una excepción existente, use esa excepción o se derivan de esa excepción. En caso contrario, derivar una nueva excepción o la jerarquía de excepciones directamente desde el [System.Exception](/dotnet/api/System.Exception) tipo.

Un [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto también requiere una categoría de error que agrupa los errores para el usuario. El usuario puede ver los errores según la categoría estableciendo el valor de la `$ErrorView` variable del shell a CategoryView. Las categorías posibles se definen mediante la [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeración.

- Si un cmdlet crea un nuevo subproceso, y el código que se está ejecutando en ese subproceso produce una excepción no controlada, Windows PowerShell no detectará el error y finalizará el proceso.

- Si un objeto tiene código en su destructor que produce una excepción no controlada, Windows PowerShell no detectará el error y finalizará el proceso. Esto también ocurre si un objeto llama a los métodos Dispose que provocan una excepción no controlada.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Usar un módulo de Windows PowerShell para implementar sus Cmdlets (RC07)

Crear un módulo de Windows PowerShell para empaquetar e implementar sus cmdlets. Compatibilidad con los módulos se introdujo en Windows PowerShell 2.0. Puede usar los ensamblados que contienen las clases de su cmdlet directamente como archivos de módulo binario (Esto es muy útil al probar los cmdlets), o puede crear un manifiesto de módulo que hace referencia a los ensamblados de cmdlet. (También puede agregar los ensamblados de complementos existentes al utilizar los módulos.) Para obtener más información acerca de los módulos, consulte [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Véase también

[Directrices de recomienda encarecidamente autorizados durante el desarrollo](./strongly-encouraged-development-guidelines.md)

[Instrucciones de desarrollo de asesoría](./advisory-development-guidelines.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
