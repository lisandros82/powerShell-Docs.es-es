---
title: Tipos de salida del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853931"
---
# <a name="types-of-cmdlet-output"></a>Tipos de salida del cmdlet

PowerShell proporciona varios métodos que pueden llamarse mediante los cmdlets para generar la salida. Estos métodos usan una operación específica para escribir sus resultados a una secuencia de datos específicos, como el flujo de datos de éxito o el flujo de datos de error. En este artículo se describe los tipos de salida y los métodos utilizados para generarlos.

## <a name="types-of-output"></a>Tipos de salida

### <a name="success-output"></a>Resultado correcto

Cmdlets puede notificar éxito devolviendo un objeto que puede procesarse mediante el comando siguiente en la canalización. Después de que el cmdlet ha realizado correctamente su acción, el cmdlet se llama a la [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. Se recomienda que llame a este método en lugar de la [System.Console.WriteLine](/dotnet/api/System.Console.WriteLine) o [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) métodos.

Puede proporcionar un **PassThru** modificador de parámetro para los cmdlets que no devuelven objetos normalmente.
Cuando el **PassThru** parámetro de modificador se especifica en la línea de comandos, se solicita el cmdlet para devolver un objeto. Para obtener un ejemplo de un cmdlet que tiene un **PassThru** parámetro, vea [Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Salida de error

Cmdlets puede informar sobre errores. Cuando se produce un error de terminación, el cmdlet produce una excepción. Cuando se produce un error de no terminación, el cmdlet se llama a la [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método para enviar un registro de errores en el flujo de datos de error. Para obtener más información acerca de los informes de error, consulte [Error Reporting conceptos](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Resultados detallados

Los cmdlets pueden proporcionar información útil para usted mientras el cmdlet está procesando correctamente los registros mediante una llamada a la [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método. El método genera mensajes detallados que indican cómo se está realizando la acción.

De forma predeterminada, no se muestran los mensajes detallados. Puede especificar el **detallado** parámetro cuando se ejecuta el cmdlet para mostrar estos mensajes. **Detallado** es un parámetro común que está disponible para todos los cmdlets.

### <a name="progress-output"></a>Salida de progreso

Los cmdlets pueden proporcionar información de progreso le cuando el cmdlet realiza tareas que toman mucho tiempo en completarse, como copiar un directorio de forma recursiva. Para mostrar información sobre el progreso del cmdlet llama a la [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) método.

### <a name="debug-output"></a>Salida de depuración

Los cmdlets pueden proporcionar mensajes de depuración que resultan útiles al solucionar problemas del código del cmdlet. Para mostrar información de depuración del cmdlet llama a la [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método.

De forma predeterminada, no se muestran los mensajes de depuración. Puede especificar el **depurar** parámetro cuando se ejecuta el cmdlet para mostrar estos mensajes. **Depurar** es un parámetro común que está disponible para todos los cmdlets.

### <a name="warning-output"></a>Salida de advertencia

Los cmdlets pueden mostrar mensajes de advertencia mediante una llamada a la [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método.

De forma predeterminada, se muestran los mensajes de advertencia. Sin embargo, puede configurar los mensajes de advertencia con el `$WarningPreference` variable o mediante el **detallado** y **depurar** parámetros cuando se llama el cmdlet.

## <a name="displaying-output"></a>Mostrar la salida

Para todas las llamadas de método de escritura, el contenido que se muestra viene determinada por las variables en tiempo de ejecución específica. La excepción es el [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. Mediante estas variables, puede hacer adecuado escribir la llamada en el lugar correcto en el código y no preocuparse cuando o si se debe mostrar la salida.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Obtener acceso a la funcionalidad de salida de una aplicación host

También puede diseñar un cmdlet para tener acceso directamente a la funcionalidad de salida de una aplicación host mediante el tiempo de ejecución de PowerShell. Mediante el host de las API proporcionadas por PowerShell en lugar de [System.Console](/dotnet/api/System.Console) o [System.Windows.Forms](/dotnet/api/System.Windows.Forms) garantiza que el cmdlet funcionará con una variedad de hosts. Por ejemplo: el **powershell.exe** host de consola, el **powershell_ise.exe** host gráfica, el host de comunicación remota de PowerShell y hosts de terceros.

## <a name="see-also"></a>Vea también

[Conceptos de informes de error](./error-reporting-concepts.md)

[Información general del cmdlet](./cmdlet-overview.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)