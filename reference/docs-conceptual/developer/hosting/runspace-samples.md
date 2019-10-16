---
title: Ejemplos de espacio de ejecución | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361004"
---
# <a name="runspace-samples"></a>Ejemplos de espacio de ejecución

En esta sección se incluye código de ejemplo que muestra cómo usar diferentes tipos de espacios de ejecución para ejecutar comandos de forma sincrónica y asincrónica. Puede usar Microsoft Visual Studio para crear una aplicación de consola y, a continuación, copiar el código de los temas de esta sección en la aplicación host.

## <a name="in-this-section"></a>En esta sección

> [!NOTE]
> Para obtener ejemplos de aplicaciones host que crean interfaces de host personalizadas, consulte [ejemplos de hosts personalizados](./custom-host-samples.md).

 [Ejemplo de Runspace01](./runspace01-sample.md) En este ejemplo se muestra cómo usar la clase [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) para ejecutar el cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) sincrónicamente y mostrar el resultado en una ventana de la consola.

 [Ejemplo de Runspace02](./runspace02-sample.md) En este ejemplo se muestra cómo usar la clase [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) para ejecutar los cmdlets [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) y [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) sincrónicamente. Los resultados de estos comandos se muestran mediante un control [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) .

 [Ejemplo de Runspace03](./runspace03-sample.md) En este ejemplo se muestra cómo usar la clase [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) para ejecutar un script de forma sincrónica y cómo controlar los errores de no terminación. El script recibe una lista de nombres de procesos y después los recupera. Los resultados del script, incluidos los errores de no terminación generados al ejecutarlo, se muestran en una ventana de consola.

 [Ejemplo de Runspace04](./runspace04-sample.md) En este ejemplo se muestra cómo usar la clase [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) para ejecutar comandos y cómo detectar los errores de terminación que se producen al ejecutar los comandos. Se ejecutan dos comandos; al último, se le pasa un argumento de parámetro que no es válido. Como resultado, no se devuelve ningún objeto y se produce un error de terminación.

 [Ejemplo de Runspace05](./runspace05-sample.md) En este ejemplo se muestra cómo agregar un complemento a un objeto [System. Management. Automation. runspace. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) para que el cmdlet del complemento esté disponible cuando se abra el espacio de ejecución. El complemento proporciona un cmdlet Get-proc (definido por el [ejemplo GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) que se ejecuta de forma sincrónica mediante un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

 [Ejemplo de Runspace06](./runspace06-sample.md) En este ejemplo se muestra cómo agregar un módulo a un objeto [System. Management. Automation. runspace. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) para que el módulo se cargue cuando se abra el espacio de ejecución. El módulo proporciona un cmdlet Get-proc (definido por el [ejemplo GetProcessSample02](../cmdlet/getprocesssample02-sample.md)) que se ejecuta de forma sincrónica mediante un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

 [Ejemplo de Runspace07](./runspace07-sample.md) En este ejemplo se muestra cómo crear un espacio de ejecución y, a continuación, usar ese espacio de ejecución para ejecutar dos cmdlets de forma sincrónica mediante un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

 [Ejemplo de Runspace08](./runspace08-sample.md) En este ejemplo se muestra cómo agregar comandos y argumentos a la canalización de un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) y cómo ejecutar los comandos sincrónicamente.

 [Ejemplo de Runspace09](./runspace09-sample.md) En este ejemplo se muestra cómo agregar un script a la canalización de un objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) y cómo ejecutar el script de forma asincrónica. Los eventos se usan para controlar la salida del script.

 [Ejemplo de Runspace10](./runspace10-sample.md) En este ejemplo se muestra cómo crear un estado de sesión inicial predeterminado, cómo agregar un cmdlet a [System. Management. Automation. runspace. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), cómo crear un espacio de ejecución que usa el estado de sesión inicial y cómo ejecutar el comando mediante un cmdlet Objeto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

 [Ejemplo de Runspace11](./runspace11-sample.md) Esto muestra cómo usar la clase [System. Management. Automation. ProxyCommand](/dotnet/api/System.Management.Automation.ProxyCommand) para crear un comando de proxy que llama a un cmdlet existente, pero restringe el conjunto de parámetros disponibles. El comando de proxy se agrega entonces a un estado de sesión inicial que se usa para crear un espacio de ejecución restringido. Esto significa que el usuario puede tener acceso a la funcionalidad del cmdlet solo mediante el comando de proxy.

## <a name="see-also"></a>Véase también
