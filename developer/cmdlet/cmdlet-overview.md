---
title: Información general cmdlets | Microsoft Docs
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
ms.openlocfilehash: f8a8c9300d1ac811c7fbbf7050dd24f78306db8f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056675"
---
# <a name="cmdlet-overview"></a>Información general del cmdlet

Un cmdlet es un comando ligero que se usa en el entorno de Windows PowerShell. El tiempo de ejecución de Windows PowerShell invoca estos cmdlets en el contexto de scripts de automatización que se proporcionan en la línea de comandos. El tiempo de ejecución de Windows PowerShell también invoca mediante programación por medio de Windows PowerShell APIs.

## <a name="cmdlets"></a>Cmdlets

Los cmdlets realizan una acción y normalmente devuelven un objeto de Microsoft .NET Framework para el comando siguiente en la canalización. Para escribir un cmdlet, debe implementar una clase de cmdlet que se deriva de una de dos clases base cmdlet especializado. La clase derivada debe:

- Declarar un atributo que identifica la clase derivada como un cmdlet.

- Definir las propiedades públicas que se decoran con atributos que identifican las propiedades públicas como parámetros de cmdlet.

- Invalide uno o varios de los métodos para procesar los registros de procesamiento de entrada.

Puede cargar el ensamblado que contiene la clase directamente mediante el [Import-Module](/powershell/module/microsoft.powershell.core/import-module) cmdlet, o bien puede crear una aplicación host que carga el ensamblado mediante el uso de la [ System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API. Ambos métodos proporcionan acceso mediante programación y de línea de comandos a la funcionalidad del cmdlet.

## <a name="cmdlet-terms"></a>Términos de cmdlet

Los siguientes términos se usan con frecuencia en la documentación del cmdlet de Windows PowerShell:

- **Atributo de cmdlet**: Un atributo de .NET Framework que se utiliza para declarar una clase de cmdlet como un cmdlet. Aunque Windows PowerShell usa varios otros atributos que son opcionales, se requiere el atributo de Cmdlet. Para obtener más información acerca de este atributo, vea [declaración de atributo de Cmdlet](./cmdlet-attribute-declaration.md).

- **Parámetro de cmdlet**: Las propiedades públicas que definen los parámetros que están disponibles para los usuarios o a la aplicación que se está ejecutando el cmdlet. Cmdlets puede necesarias, con nombre, posición, y *cambiar* parámetros. Los parámetros de modificador permiten definir los parámetros que se evalúan solo si se especifican los parámetros en la llamada. Para obtener más información sobre los diferentes tipos de parámetros, vea [parámetros de Cmdlet](./cmdlet-parameters.md).

- **Conjunto de parámetros**: Grupo de parámetros que pueden usarse en el mismo comando para realizar una acción específica. Un cmdlet puede tener varios conjuntos de parámetros, pero cada conjunto de parámetros debe tener al menos un parámetro que sea único. Cmdlet de buen diseño sugiere que el parámetro unique también ser un parámetro necesario. Para obtener más información acerca de conjuntos de parámetros, vea [conjuntos de parámetros de Cmdlet](./cmdlet-parameter-sets.md).

- **Parámetro dinámico**: Un parámetro que se agrega al cmdlet en tiempo de ejecución. Normalmente, los parámetros dinámicos se agregan al cmdlet cuando otro parámetro se establece en un valor específico. Para obtener más información sobre los parámetros dinámicos, consulte [parámetros dinámicos de Cmdlet](./cmdlet-dynamic-parameters.md).

- **Método de procesamiento de entrada**: Método que un cmdlet puede usar para procesar los registros que recibe como entrada. Los métodos de procesamiento de entrada incluyen el [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método, el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método, el [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método y el [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) método. Al implementar un cmdlet, debe reemplazar al menos uno de los [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)y [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) métodos. Normalmente, el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) es el método que invalide porque se llama para cada registro que el cmdlet procesa. En cambio, el [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método y el [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) se llama al método una vez para realizar procesamiento previo o posterior al procesamiento de los registros. Para obtener más información acerca de estos métodos, consulte [métodos de procesamiento de entrada](./cmdlet-input-processing-methods.md).

- **Característica ShouldProcess**: Windows PowerShell le permite crear cmdlets que pedir al usuario comentarios antes de que el cmdlet realiza un cambio en el sistema. Para usar esta característica, debe declarar el cmdlet que admite la característica ShouldProcess al declarar el atributo de Cmdlet y el cmdlet debe llamar a la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos desde dentro de un método de procesamiento de entrada. Para obtener más información sobre cómo admitir la funcionalidad de ShouldProcess, consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).

- **Transacción**: Un grupo lógico de los comandos que se tratan como una sola tarea. La tarea error automáticamente si se produce un error en cualquier comando en el grupo y el usuario tiene la opción de Aceptar o rechazar las acciones realizadas dentro de la transacción. Para participar en una transacción, el cmdlet debe declarar que admite transacciones cuando se declara el atributo de Cmdlet. Compatibilidad con las transacciones se introdujo en Windows PowerShell 2.0. Para obtener más información acerca de las transacciones, vea [transacciones de Windows PowerShell](http://msdn.microsoft.com/en-us/74d7bac7-bc53-49f1-a47a-272e8da84710).

## <a name="how-cmdlets-differ-from-commands"></a>Cómo los Cmdlets difieren de comandos

Los cmdlets difieren de comandos en otros entornos de shell de comandos de las maneras siguientes:

- Los cmdlets son instancias de clases de .NET Framework; no son archivos ejecutables independientes.

- Los cmdlets pueden crearse desde tan solo una docena de líneas de código.

- Cmdlets de hacer sus propios análisis, presentación de error o el formato de salida con carácter general. Análisis, presentación del error y el formato de salida se controlan mediante el tiempo de ejecución de Windows PowerShell.

- Objetos de la canalización en lugar de secuencias de texto de entrada de proceso de los cmdlets y cmdlets normalmente entregar objetos como salida en la canalización.

- Los cmdlets son orientado a registro puesto que procesan un solo objeto a la vez.

## <a name="cmdlet-base-classes"></a>Clases Base del cmdlet

Windows PowerShell admite cmdlets que se derivan de las siguientes dos clases base.

- Mayoría de los cmdlets se basa en las clases de .NET Framework que se derivan de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase base. Derivar de esta clase permite que un cmdlet para utilizar el conjunto mínimo de dependencias en el tiempo de ejecución de Windows PowerShell. Esto tiene dos ventajas. La primera ventaja es que los objetos de cmdlet son más pequeños y es menos probable que se vea afectado por los cambios realizados en el tiempo de ejecución de Windows PowerShell. La segunda ventaja es que, si es necesario, puede crear directamente una instancia del objeto de cmdlet y, a continuación, invocarlo directamente en lugar de invocarlo a través del tiempo de ejecución de Windows PowerShell.

- Los cmdlets más complejos se basan en las clases de .NET Framework que se derivan de la [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) clase base. Derivar de esta clase ofrece mucho más acceso al tiempo de ejecución de Windows PowerShell. Este acceso permite que el cmdlet llamar a las secuencias de comandos, para tener acceso a los proveedores y para acceder al estado de la sesión actual. (Para obtener acceso al estado de la sesión actual, obtener y establece variables de sesión y las preferencias.) Sin embargo, derivar de esta clase aumenta el tamaño del objeto de cmdlet y significa que el cmdlet está más estrechamente a la versión actual del tiempo de ejecución de Windows PowerShell.

En general, a menos que necesite el acceso total al tiempo de ejecución de Windows PowerShell, debe derivar de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase. Sin embargo, el tiempo de ejecución de Windows PowerShell tiene amplias funciones de registro para la ejecución de cmdlets. Si el modelo de auditoría depende de este registro, puede evitar la ejecución de su cmdlet desde dentro de otro cmdlet derivando de la [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) clase.

## <a name="input-processing-methods"></a>Métodos de procesamiento de entrada

El [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase proporciona los siguientes métodos virtuales que se utilizan para procesar registros. Todas las clases de cmdlet derivadas deben invalidar uno o varios de los tres métodos:

- [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): Se utiliza para proporcionar funcionalidad opcional de procesamiento previo único para el cmdlet.

- [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Se utiliza para proporcionar funcionalidad de procesamiento registro por registro para el cmdlet. El [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método podría llamarse cualquier número de veces o no en absoluto, dependiendo de la entrada del cmdlet.

- [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): Se utiliza para proporcionar funcionalidad opcional de procesamiento posterior único para el cmdlet.

- [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): Se utiliza para detener el procesamiento cuando el usuario detiene el cmdlet de forma asincrónica (por ejemplo, presionando CTRL + C).

Para obtener más información acerca de estos métodos, consulte [métodos de procesamiento de entrada de Cmdlet](./cmdlet-input-processing-methods.md).

## <a name="cmdlet-attributes"></a>Atributos del cmdlet

Windows PowerShell define varios atributos de .NET Framework que se usan para administrar los cmdlets y para especificar la funcionalidad común proporcionada por Windows PowerShell y que podría ser necesario por el cmdlet. Por ejemplo, los atributos se utilizan para designar una clase como un cmdlet, para especificar los parámetros del cmdlet y para solicitar la validación de entrada para que los desarrolladores de cmdlets no es necesario que implementar esa funcionalidad en su código del cmdlet. Para obtener más información acerca de los atributos, vea [Windows PowerShell atributos](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Nombres de cmdlets

Windows PowerShell usa un par de nombre del verbo y sustantivo para cmdlets de nombre. Por ejemplo, el `Get-Command` cmdlet incluida en Windows PowerShell se usa para obtener todos los cmdlets que están registrados en el shell de comandos. El verbo identifica la acción que realiza el cmdlet y el sustantivo identifica el recurso en el que el cmdlet realiza su acción.

Estos nombres se especifican cuando se declara la clase de .NET Framework como un cmdlet. Para obtener más información acerca de cómo declarar una clase de .NET Framework como un cmdlet, consulte [declaración de atributo de Cmdlet](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Cmdlet de escritura de código

Este documento proporciona dos maneras de descubrir cómo se escribe el código del cmdlet. Si prefiere ver el código sin muchas explicaciones, consulte [ejemplos de código del Cmdlet](./examples-of-cmdlet-code.md). Si prefiere más explicaciones sobre el código, vea el [GetProc Tutorial](./getproc-tutorial.md), [StopProc Tutorial](./stopproc-tutorial.md), o [SelectStr Tutorial](./selectstr-tutorial.md) temas.

Para obtener más información sobre las directrices para la escritura de cmdlets, consulte [las instrucciones de desarrollo de Cmdlet](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Véase también

[Conceptos de Cmdlet de PowerShell de Windows](./windows-powershell-cmdlet-concepts.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
