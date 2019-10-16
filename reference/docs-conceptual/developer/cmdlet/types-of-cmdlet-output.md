---
title: Tipos de salida de cmdlet | Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369294"
---
# <a name="types-of-cmdlet-output"></a>Tipos de salida de cmdlet

PowerShell proporciona varios métodos a los que pueden llamar los cmdlets para generar la salida. Estos métodos usan una operación específica para escribir su salida en un flujo de datos concreto, como el flujo de datos correcto o el flujo de datos de error. En este artículo se describen los tipos de resultados y los métodos que se usan para generarlos.

## <a name="types-of-output"></a>Tipos de salida

### <a name="success-output"></a>Salida correcta

Los cmdlets pueden notificar el éxito devolviendo un objeto que puede ser procesado por el siguiente comando en la canalización. Después de que el cmdlet haya realizado correctamente su acción, el cmdlet llama al método [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Se recomienda llamar a este método en lugar de a los métodos [System. Console. WriteLine](/dotnet/api/System.Console.WriteLine) o [System. Management. Automation. host. PSHostUserInterface. WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) .

Puede proporcionar un parámetro de modificador **Passthru** para cmdlets que normalmente no devuelven objetos.
Cuando se especifica el parámetro de modificador **Passthru** en la línea de comandos, se pide al cmdlet que devuelva un objeto. Para ver un ejemplo de un cmdlet que tiene un parámetro **Passthru** , consulte [Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Salida de error

Los cmdlets pueden informar de errores. Cuando se produce un error de terminación, el cmdlet produce una excepción. Cuando se produce un error de no terminación, el cmdlet llama al método [System. Management. Automation. Provider. CmdletProvider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) para enviar un registro de error al flujo de datos de error. Para obtener más información sobre los informes de errores, vea [conceptos de informes de errores](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Resultados detallados

Los cmdlets pueden proporcionar información útil mientras el cmdlet procesa correctamente los registros llamando al método [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) . El método genera mensajes detallados que indican cómo se va a continuar la acción.

De forma predeterminada, los mensajes detallados no se muestran. Puede especificar el parámetro **verbose** cuando se ejecuta el cmdlet para mostrar estos mensajes. **Verbose** es un parámetro común que está disponible para todos los cmdlets.

### <a name="progress-output"></a>Salida de progreso

Los cmdlets pueden proporcionar información de progreso cuando el cmdlet realiza tareas que tardan mucho tiempo en completarse, como copiar un directorio de forma recursiva. Para mostrar la información de progreso, el cmdlet llama al método [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .

### <a name="debug-output"></a>Salida de depuración

Los cmdlets pueden proporcionar mensajes de depuración que son útiles para solucionar problemas del código de cmdlet. Para mostrar la información de depuración, el cmdlet llama al método [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) .

De forma predeterminada, no se muestran los mensajes de depuración. Puede especificar el parámetro **Debug** cuando se ejecuta el cmdlet para mostrar estos mensajes. **Debug** es un parámetro común que está disponible para todos los cmdlets.

### <a name="warning-output"></a>Salida de advertencia

Los cmdlets pueden mostrar mensajes de advertencia llamando al método [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) .

De forma predeterminada, se muestran los mensajes de advertencia. Sin embargo, puede configurar mensajes de advertencia mediante la variable `$WarningPreference` o mediante los parámetros **verbose** y **Debug** cuando se llama al cmdlet.

## <a name="displaying-output"></a>Mostrar resultados

Para todas las llamadas de método de escritura, la presentación del contenido viene determinada por variables en tiempo de ejecución específicas. La excepción es el método [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Mediante el uso de estas variables, puede realizar la llamada de escritura adecuada en el lugar correcto del código y no preocuparse por si se debe mostrar la salida.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Obtener acceso a la funcionalidad de salida de una aplicación host

También puede diseñar un cmdlet para acceder directamente a la funcionalidad de salida de una aplicación host a través del tiempo de ejecución de PowerShell. El uso de las API de host que proporciona PowerShell en lugar de [System. Console](/dotnet/api/System.Console) o [System. Windows. Forms](/dotnet/api/System.Windows.Forms) garantiza que el cmdlet funcionará con varios hosts. Por ejemplo: el host de consola de **PowerShell. exe** , el host gráfico **powershell_ise. exe** , el host de comunicación remota de PowerShell y los hosts de terceros.

## <a name="see-also"></a>Consulta también

[Conceptos de informes de errores](./error-reporting-concepts.md)

[Introducción a los cmdlets](./cmdlet-overview.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)