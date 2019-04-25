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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082743"
---
# <a name="runspace-samples"></a>Ejemplos de espacio de ejecución

En esta sección se incluye código de ejemplo que muestra cómo usar diferentes tipos de espacios de ejecución para ejecutar comandos de forma sincrónica y asincrónica. Puede utilizar Microsoft Visual Studio para crear una aplicación de consola y, a continuación, copie el código de los temas de esta sección en la aplicación host.

## <a name="in-this-section"></a>En esta sección

> [!NOTE]
> Para obtener ejemplos de aplicaciones de host que crear interfaces de host personalizado, vea [ejemplos de Host personalizados](./custom-host-samples.md).

 [Ejemplo Runspace01](./runspace01-sample.md) en este ejemplo se muestra cómo usar el [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) clase para ejecutar el [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet sincrónicamente y mostrar el resultado en una consola de ventana.

 [Ejemplo Runspace02](./runspace02-sample.md) en este ejemplo se muestra cómo usar el [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) clase para ejecutar el [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) y [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets de forma sincrónica. Los resultados de estos comandos se muestran mediante un [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.

 [Ejemplo de Runspace03](./runspace03-sample.md) en este ejemplo se muestra cómo usar el [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) clase para ejecutar un script de forma sincrónica y cómo controlar errores de no terminación. El script recibe una lista de nombres de procesos y después los recupera. Los resultados del script, incluidos los errores de no terminación generados al ejecutarlo, se muestran en una ventana de consola.

 [Ejemplo de Runspace04](./runspace04-sample.md) en este ejemplo se muestra cómo usar el [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) clase para ejecutar comandos y cómo capturar los errores de terminación que se producen al ejecutar los comandos. Se ejecutan dos comandos; al último, se le pasa un argumento de parámetro que no es válido. Como resultado se devuelve ningún objeto y se produce un error de terminación.

 [Ejemplo Runspace05](./runspace05-sample.md) en este ejemplo se muestra cómo agregar un complemento a un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto para que el cmdlet del complemento está disponible cuando se abre el espacio de ejecución. El complemento proporciona un cmdlet Get-Proc (definido por el [ejemplo GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) que se ejecuta de forma sincrónica mediante un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

 [Ejemplo Runspace06](./runspace06-sample.md) en este ejemplo se muestra cómo agregar un módulo a un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto para que el módulo se carga cuando se abre el espacio de ejecución. El módulo proporciona un cmdlet Get-Proc (definido por el [ejemplo GetProcessSample02](../cmdlet/getprocesssample02-sample.md)) que se ejecuta de forma sincrónica mediante un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

 [Ejemplo de Runspace07](./runspace07-sample.md) este ejemplo muestra cómo crear un espacio de ejecución y, a continuación, usar ese espacio de ejecución para ejecutar dos cmdlets de forma sincrónica mediante un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

 [Ejemplo de Runspace08](./runspace08-sample.md) en este ejemplo se muestra cómo agregar comandos y argumentos a la canalización de un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto y cómo ejecutar los comandos de forma sincrónica.

 [Ejemplo de Runspace09](./runspace09-sample.md) en este ejemplo se muestra cómo agregar una secuencia de comandos a la canalización de un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto y cómo ejecutar el script de forma asincrónica. Los eventos se usan para controlar la salida del script.

 [Ejemplo Runspace10](./runspace10-sample.md) en este ejemplo se muestra cómo crear un estado de sesión inicial predeterminado, cómo agregar un cmdlet para el [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), cómo crear un espacio de ejecución que usa el estado de sesión inicial y cómo ejecutar el comando mediante el uso de un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

 [Ejemplo de Runspace11](./runspace11-sample.md) Esto muestra cómo usar el [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) clase para crear un comando de proxy que llama a un cmdlet existente, pero restringe el conjunto de parámetros disponibles. El comando de proxy se agrega entonces a un estado de sesión inicial que se usa para crear un espacio de ejecución restringido. Esto significa que el usuario puede tener acceso a la funcionalidad del cmdlet solo mediante el comando de proxy.

## <a name="see-also"></a>Véase también
