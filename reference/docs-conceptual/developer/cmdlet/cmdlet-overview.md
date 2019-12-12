---
title: Información general sobre los cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: 14200aed2fb94c37c8b8af29650f602945e7ac1c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365894"
---
# <a name="cmdlet-overview"></a>Información general del cmdlet

Un cmdlet es un comando ligero que se usa en el entorno de Windows PowerShell. El tiempo de ejecución de Windows PowerShell invoca estos cmdlets en el contexto de los scripts de automatización que se proporcionan en la línea de comandos. El tiempo de ejecución de Windows PowerShell también los invoca mediante programación a través de las API de Windows PowerShell.

## <a name="cmdlets"></a>Cmdlets

Los cmdlets realizan una acción y normalmente devuelven un objeto de Microsoft .NET Framework al siguiente comando de la canalización. Para escribir un cmdlet, debe implementar una clase de cmdlet que derive de una de las dos clases base de cmdlets especializadas. La clase derivada debe:

- Declare un atributo que identifique la clase derivada como un cmdlet.

- Defina las propiedades públicas que se decoran con atributos que identifican las propiedades públicas como parámetros de cmdlet.

- Invalide uno o varios métodos de procesamiento de entrada para procesar los registros.

Puede cargar el ensamblado que contiene la clase directamente mediante el cmdlet [Import-Module](/powershell/module/microsoft.powershell.core/import-module) , o puede crear una aplicación host que cargue el ensamblado mediante la API [System. Management. Automation. espacios de Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) . Ambos métodos proporcionan acceso de línea de comandos y mediante programación a la funcionalidad del cmdlet.

## <a name="cmdlet-terms"></a>Términos del cmdlet

Los siguientes términos se usan con frecuencia en la documentación del cmdlet de Windows PowerShell:

### <a name="cmdlet-attribute"></a>Atributo de cmdlet

.NET Framework atributo que se usa para declarar una clase de cmdlet como un cmdlet.
Aunque PowerShell usa otros atributos que son opcionales, el atributo de cmdlet es obligatorio.
Para obtener más información sobre este atributo, vea [declaración de atributos de cmdlet](cmdlet-attribute-declaration.md).

### <a name="cmdlet-parameter"></a>Parámetro del cmdlet

Propiedades públicas que definen los parámetros que están disponibles para el usuario o la aplicación que ejecuta el cmdlet.
Los cmdlets pueden tener parámetros obligatorios, con nombre, posicionales y *Modificadores* .
Los parámetros switch permiten definir parámetros que solo se evalúan si los parámetros se especifican en la llamada.
Para obtener más información sobre los diferentes tipos de parámetros, vea [parámetros de cmdlet](cmdlet-parameters.md).

### <a name="parameter-set"></a>Conjunto de parámetros

Grupo de parámetros que pueden usarse en el mismo comando para realizar una acción específica.
Un cmdlet puede tener varios conjuntos de parámetros, pero cada conjunto de parámetros debe tener al menos un parámetro que sea único.
Un buen diseño de los cmdlets sugiere que el parámetro único también sea un parámetro necesario.
Para obtener más información sobre los conjuntos de parámetros, vea [conjuntos de parámetros de cmdlet](cmdlet-parameter-sets.md).

### <a name="dynamic-parameter"></a>Parámetro dinámico

Parámetro que se agrega al cmdlet en tiempo de ejecución.
Normalmente, los parámetros dinámicos se agregan al cmdlet cuando otro parámetro se establece en un valor específico.
Para obtener más información sobre los parámetros dinámicos, consulte [parámetros dinámicos de cmdlet](cmdlet-dynamic-parameters.md).

### <a name="input-processing-method"></a>Método de procesamiento de entrada

Método que un cmdlet puede usar para procesar los registros que recibe como entrada.
Los métodos de procesamiento de entrada incluyen el método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) , el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , el método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) y el método [System. Management. Automation. cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) . Al implementar un cmdlet, debe invalidar al menos uno de los métodos [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)y [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .
Normalmente, el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) es el método que se invalida porque se llama para cada registro que el cmdlet procesa.
En cambio, se llama una vez al método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) y al método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) para realizar el procesamiento previo o el procesamiento posterior de los registros.
Para obtener más información sobre estos métodos, vea [métodos de procesamiento de entrada](cmdlet-input-processing-methods.md).

### <a name="shouldprocess-feature"></a>ShouldProcess (característica)

PowerShell le permite crear cmdlets que solicitan información al usuario antes de que el cmdlet realice un cambio en el sistema.
Para usar esta característica, el cmdlet debe declarar que admite la característica ShouldProcess al declarar el atributo de cmdlet y el cmdlet debe llamar a los métodos [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) desde dentro de un método de procesamiento de entrada.
Para obtener más información sobre cómo admitir la funcionalidad de ShouldProcess, consulte [solicitar confirmación](requesting-confirmation-from-cmdlets.md).

### <a name="transaction"></a>Transacción

Grupo lógico de comandos que se tratan como una sola tarea.
La tarea genera un error automáticamente si se produce un error en algún comando del grupo y el usuario tiene la opción de aceptar o rechazar las acciones realizadas dentro de la transacción.
Para participar en una transacción, el cmdlet debe declarar que admite transacciones cuando se declara el atributo de cmdlet.
La compatibilidad con transacciones se presentó en Windows PowerShell 2,0.
Para obtener más información acerca de las transacciones, consulte [How to Support Transactions](how-to-support-transactions.md).

## <a name="how-cmdlets-differ-from-commands"></a>Diferencias entre los cmdlets y los comandos

Los cmdlets se diferencian de los comandos en otros entornos de Shell de comandos de las siguientes maneras:

- Los cmdlets son instancias de clases .NET Frameworks; no son ejecutables independientes.

- Los cmdlets se pueden crear desde tan solo una docena de líneas de código.

- Los cmdlets no realizan normalmente su propio análisis, presentación de errores o formato de salida. El tiempo de ejecución de Windows PowerShell controla el análisis, la presentación de los errores y el formato de salida.

- Los cmdlets procesan los objetos de entrada de la canalización en lugar de los flujos de texto, y los cmdlets suelen ofrecer objetos como salida a la canalización.

- Los cmdlets están orientados a registros porque procesan un solo objeto cada vez.

## <a name="cmdlet-base-classes"></a>Clases base de cmdlet

Windows PowerShell admite cmdlets que se derivan de las dos clases base siguientes.

- La mayoría de los cmdlets se basan en .NET Framework clases que derivan de la clase base [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . La derivación de esta clase permite a un cmdlet usar el conjunto mínimo de dependencias en el tiempo de ejecución de Windows PowerShell. lo que ofrece dos ventajas. La primera ventaja es que los objetos de cmdlet son más pequeños y es menos probable que se vea afectado por los cambios en el tiempo de ejecución de Windows PowerShell. La segunda ventaja es que, si es necesario, puede crear directamente una instancia del objeto de cmdlet y, a continuación, invocarla directamente en lugar de invocarla a través del tiempo de ejecución de Windows PowerShell.

- Los cmdlets más complejos se basan en .NET Framework clases que derivan de la clase base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . La derivación de esta clase proporciona mucho más acceso al tiempo de ejecución de Windows PowerShell. Este acceso permite que el cmdlet llame a scripts, para obtener acceso a los proveedores y para obtener acceso al estado de sesión actual. (Para tener acceso al estado de sesión actual, se obtienen y establecen las preferencias y las variables de la sesión). Sin embargo, la derivación de esta clase aumenta el tamaño del objeto de cmdlet y significa que el cmdlet se acopla más estrechamente a la versión actual del tiempo de ejecución de Windows PowerShell.

En general, a menos que necesite el acceso extendido al tiempo de ejecución de Windows PowerShell, debe derivar de la clase [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . Sin embargo, el tiempo de ejecución de Windows PowerShell tiene amplias capacidades de registro para la ejecución de cmdlets. Si el modelo de auditoría depende de este registro, puede impedir la ejecución de su cmdlet desde otro cmdlet mediante la derivación de la clase [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

## <a name="input-processing-methods"></a>Métodos de procesamiento de entrada

La clase [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) proporciona los siguientes métodos virtuales que se usan para procesar registros. Todas las clases de cmdlet derivadas deben invalidar uno o varios de los tres primeros métodos:

- [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): se usa para proporcionar una funcionalidad de procesamiento previo opcional única para el cmdlet.

- [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): se usa para proporcionar la funcionalidad de procesamiento de registro por registro para el cmdlet. Se puede llamar al método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cualquier número de veces, o no, en función de la entrada del cmdlet.

- [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): se usa para proporcionar una funcionalidad de procesamiento posterior opcional única para el cmdlet.

- [System. Management. Automation. cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): se usa para detener el procesamiento cuando el usuario detiene el cmdlet de forma asincrónica (por ejemplo, presionando Ctrl + C).

Para obtener más información sobre estos métodos, vea [métodos de procesamiento de entrada de cmdlet](./cmdlet-input-processing-methods.md).

## <a name="cmdlet-attributes"></a>Atributos del cmdlet

Windows PowerShell define varios .NET Framework atributos que se usan para administrar los cmdlets y para especificar la funcionalidad común proporcionada por Windows PowerShell y que el cmdlet puede necesitar. Por ejemplo, los atributos se usan para designar una clase como un cmdlet, especificar los parámetros del cmdlet y solicitar la validación de la entrada para que los desarrolladores de cmdlets no tengan que implementar esa funcionalidad en su código de cmdlet. Para obtener más información sobre los atributos, vea [atributos de Windows PowerShell](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Nombres de cmdlets

Windows PowerShell usa un par de nombres de verbo y sustantivo para asignar nombres a los cmdlets. Por ejemplo, el cmdlet `Get-Command` incluido en Windows PowerShell se usa para obtener todos los cmdlets que están registrados en el shell de comandos. El verbo identifica la acción que realiza el cmdlet y el nombre identifica el recurso en el que el cmdlet realiza su acción.

Estos nombres se especifican cuando la clase .NET Framework se declara como un cmdlet. Para obtener más información sobre cómo declarar una clase .NET Framework como un cmdlet, consulte [declaración de atributo de cmdlet](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Escribir código de cmdlet

En este documento se proporcionan dos maneras de detectar cómo se escribe el código de cmdlet. Si prefiere ver el código sin mucha explicación, consulte [ejemplos de código de cmdlet](./examples-of-cmdlet-code.md). Si prefiere obtener una explicación más detallada sobre el código, vea los temas tutorial de [GetProc](./getproc-tutorial.md), tutorial de [StopProc](./stopproc-tutorial.md)o [tutorial de SelectStr](./selectstr-tutorial.md) .

Para obtener más información sobre las instrucciones para escribir cmdlets, vea instrucciones para el [desarrollo de cmdlets](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Véase también

[Conceptos de cmdlets de Windows PowerShell](./windows-powershell-cmdlet-concepts.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
