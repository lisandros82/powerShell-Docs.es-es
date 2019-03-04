---
title: Código de ejemplo de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: 264e9f7538e13b48d899e87541239250eb88f14e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863361"
---
# <a name="windows-powershell-sample-code"></a>Código de ejemplo de Windows PowerShell

Ejemplos de Windows PowerShell® están disponibles a través del SDK de Windows. Esta sección contiene el código de ejemplo que se encuentra en los ejemplos del SDK de Windows.

> [!NOTE]
> Cuando se instala el SDK de Windows, un **ejemplos** directorio se crea en el que están disponibles todos los ejemplos de Windows PowerShell. Un directorio de instalación típica es **C:\Program Files\Microsoft SDKs\Windows\v6.0**. Iniciar Windows PowerShell y escriba **"cd Samples\SysMgmt\PowerShell"** para buscar el directorio de ejemplos de Windows PowerShell. En este documento, el directorio de ejemplos de Windows PowerShell se conoce como  **\<ejemplos de PowerShell >**.

## <a name="sample-code-listing"></a>Lista de código de ejemplo

|Código de ejemplo|Descripción|
|-----------------|-----------------|
|[Ejemplo de código AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md)|Éste es el proveedor que se describe en [creación de un proveedor de PowerShell de Windows básico](./creating-a-basic-windows-powershell-provider.md).|
|[Ejemplo de código AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md)|Éste es el proveedor que se describe en [creación de un proveedor de la unidad de Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).|
|[Ejemplo de código AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md)|Éste es el proveedor que se describe en [creación de un proveedor de elementos de Windows PowerShell](./creating-a-windows-powershell-item-provider.md).|
|[Ejemplo de código AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md)|Éste es el proveedor que se describe en [creación de un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).|
|[Ejemplo de código AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md)|Éste es el proveedor que se describe en [creación de un proveedor de navegación de Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).|
|[Ejemplo de código AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md)|Éste es el proveedor que se describe en [creación de un proveedor de contenido de Windows PowerShell](./creating-a-windows-powershell-content-provider.md).|
|[Ejemplos de código GetProc01](./getproc01-code-samples.md)|Se trata de las opciones básicas `Get-Process` ejemplo de cmdlet que se describen en [crear su primer Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md).|
|[Ejemplos de código GetProc02](./getproc02-code-samples.md)|Se trata de la `Get-Process` ejemplo de cmdlet que se describen en [agregar parámetros que procesan datos de línea de comandos](../cmdlet/adding-parameters-that-process-command-line-input.md).|
|[Ejemplos de código GetProc03](./getproc03-code-samples.md)|Se trata de la `Get-Process` ejemplo de cmdlet que se describen en [agregar parámetros de entrada de la canalización de ese proceso](../cmdlet/adding-parameters-that-process-pipeline-input.md).|
|[Ejemplos de código GetProc04](./getproc04-code-samples.md)|Se trata de la `Get-Process` ejemplo de cmdlet que se describen en [adición de no terminación informe de errores para el Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[Ejemplos de código GetProc05](./getproc05-code-samples.md)|Esto `Get-Process` cmdlet es similar al cmdlet que se describe en [adición de no terminación informe de errores para el Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[Ejemplos de código StopProc01](./stopproc01-code-samples.md)|Se trata de la `Stop-Process` ejemplo de cmdlet que se describen en [creación de un Cmdlet que modifica el sistema](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).|
|[Ejemplos de código StopProcessSample04](./stopprocesssample04-code-samples.md)|Se trata de la `Stop-Process` ejemplo de cmdlet que se describen en [agregar conjuntos de parámetros a un Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).|
|[Ejemplos de código Runspace01](./runspace01-code-samples.md)|Estos son los ejemplos de código para el espacio de ejecución descrito en [crear una aplicación de consola que ejecuta un comando especificado](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).|
|[Ejemplos de código Runspace02](./runspace02-code-samples.md)|Este ejemplo se utiliza el [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) clase para ejecutar el `Get-Process` cmdlet sincrónicamente.|
|[Ejemplos de código RunSpace03](./runspace03-code-samples.md)|Estos son los ejemplos de código para el espacio de ejecución descrito en [crear una aplicación de consola que funciona una secuencia de comandos especificado](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).|
|[Ejemplos de código RunSpace04](./runspace04-code-samples.md)|Este es un ejemplo de código para un espacio de ejecución que usa el [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) clase para ejecutar un script que genera un error de terminación.|
|[Ejemplo de código RunSpace05](./runspace05-code-sample.md)|Este es el código fuente para el ejemplo Runspace05 descrito en [configurando un RunspaceConfiguration de uso de espacio de ejecución](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).|
|[Ejemplo de código RunSpace06](./runspace06-code-sample.md)|Este es el código fuente para el ejemplo Runspace06 descrito en [configurar un espacio de ejecución mediante un Windows PowerShell Snap-in](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).|
|[Ejemplo de código RunSpace07](./runspace07-code-sample.md)|Este es el código fuente para el ejemplo Runspace07 descrito en [crear una aplicación que agrega comandos de la consola a una canalización](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).|
|[Ejemplo de código RunSpace08](./runspace08-code-sample.md)|Este es el código fuente para el ejemplo Runspace08 descrito en [creación de una consola que agrega parámetros de la aplicación a un comando](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).|
|[Ejemplo de código RunSpace09](./runspace09-code-sample.md)|Este es el código fuente para el ejemplo Runspace09 descrito en [creación de una consola de aplicación que invoca una canalización de forma asincrónica](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).|
|[Ejemplo de código RunSpace10](./runspace10-code-sample.md)|Este es el código fuente del ejemplo Runspace10, que agrega un cmdlet para [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) y, a continuación, usa la información de configuración modificado para crear el espacio de ejecución.|

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)