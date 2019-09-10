---
title: Código de ejemplo de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: e9df44b17453e9f73f6eb388d9cbc8a69fce4ba2
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848001"
---
# <a name="windows-powershell-sample-code"></a>Código de ejemplo de Windows PowerShell

Los ejemplos de® de Windows PowerShell están disponibles a través de la Windows SDK. Esta sección contiene el código de ejemplo que se encuentra en los ejemplos de Windows SDK.

> [!NOTE]
> Cuando se instala el Windows SDK, se crea un directorio de **ejemplos** en el que se ponen a disposición todos los ejemplos de Windows PowerShell. Un directorio de instalación típico es **c:\Archivos de Programa\microsoft SDKs\Windows\v6.0**.
> Inicie Windows PowerShell y escriba **"CD Samples\SysMgmt\PowerShell"** para buscar el directorio de ejemplos de Windows PowerShell. En este documento, el directorio de ejemplos de Windows PowerShell se conoce como  **\<ejemplos de PowerShell >** .

## <a name="sample-code-listing"></a>Lista de códigos de ejemplo

|Código de ejemplo|DESCRIPCIÓN|
|-----------------|-----------------|
|[Código de ejemplo de AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md)|Este es el proveedor que se describe en [crear un proveedor básico de Windows PowerShell](./creating-a-basic-windows-powershell-provider.md).|
|[Código de ejemplo de AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md)|Este es el proveedor que se describe en [crear un proveedor de unidades de Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).|
|[Código de ejemplo de AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md)|Este es el proveedor que se describe en [crear un proveedor de elementos de Windows PowerShell](./creating-a-windows-powershell-item-provider.md).|
|[Código de ejemplo de AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md)|Este es el proveedor que se describe en [crear un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).|
|[Código de ejemplo de AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md)|Este es el proveedor que se describe en [crear un proveedor de navegación de Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).|
|[Código de ejemplo de AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md)|Este es el proveedor que se describe en [crear un proveedor de contenido de Windows PowerShell](./creating-a-windows-powershell-content-provider.md).|
|[Ejemplos de código de GetProc01](./getproc01-code-samples.md)|Este es el ejemplo `Get-Process` de cmdlet básico que se describe en [creación del primer cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md).|
|[Ejemplos de código de GetProc02](./getproc02-code-samples.md)|Este es el `Get-Process` ejemplo de cmdlet descrito en [agregar parámetros que procesan la entrada de la línea de comandos](../cmdlet/adding-parameters-that-process-command-line-input.md).|
|[Ejemplos de código de GetProc03](./getproc03-code-samples.md)|Este es el `Get-Process` ejemplo de cmdlet descrito en [agregar parámetros que procesan la entrada de canalización](../cmdlet/adding-parameters-that-process-pipeline-input.md).|
|[Ejemplos de código de GetProc04](./getproc04-code-samples.md)|Este es el `Get-Process` ejemplo de cmdlet que se describe en [Agregar informes de errores de no terminación al cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[Ejemplos de código de GetProc05](./getproc05-code-samples.md)|Este `Get-Process` cmdlet es similar al cmdlet descrito en [Agregar informes de errores de no terminación al cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[Ejemplos de código de StopProc01](./stopproc01-code-samples.md)|Este es el `Stop-Process` ejemplo de cmdlet que se describe en [creación de un cmdlet que modifica el sistema](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).|
|[Ejemplos de código de StopProcessSample04](./stopprocesssample04-code-samples.md)|Este es el `Stop-Process` ejemplo de cmdlet descrito en [Agregar conjuntos de parámetros a un cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).|
|[Ejemplos de código de Runspace01](./runspace01-code-samples.md)|Estos son los ejemplos de código para el espacio de ejecución que se describe en [crear una aplicación de consola que ejecuta un comando especificado](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).|
|[Ejemplos de código de Runspace02](./runspace02-code-samples.md)|En este ejemplo se usa la clase [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) para `Get-Process` ejecutar el cmdlet sincrónicamente.|
|[Ejemplos de código de RunSpace03](./runspace03-code-samples.md)|Estos son los ejemplos de código para el espacio de ejecución que se describe en "crear una aplicación de consola que ejecuta un script especificado".|
|[Ejemplos de código de RunSpace04](./runspace04-code-samples.md)|Este es un ejemplo de código para un espacio de ejecución que usa la clase [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) para ejecutar un script que genera un error de terminación.|
|[Código de ejemplo de RunSpace05](./runspace05-code-sample.md)|Este es el código fuente del ejemplo Runspace05 que se describe en [configuración de un espacio de ejecución con RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).|
|[Código de ejemplo de RunSpace06](./runspace06-code-sample.md)|Este es el código fuente del ejemplo Runspace06 que se describe en [configuración de un espacio de ejecución mediante un complemento de Windows PowerShell](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).|
|[Código de ejemplo de RunSpace07](./runspace07-code-sample.md)|Este es el código fuente del ejemplo Runspace07 que se describe en [crear una aplicación de consola que agrega comandos a una canalización](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).|
|[Código de ejemplo de RunSpace08](./runspace08-code-sample.md)|Este es el código fuente del ejemplo Runspace08 que se describe en [crear una aplicación de consola que agrega parámetros a un comando](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).|
|[Código de ejemplo de RunSpace09](./runspace09-code-sample.md)|Este es el código fuente del ejemplo Runspace09 que se describe en [crear una aplicación de consola que invoca una canalización de forma asincrónica](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).|
|[Código de ejemplo de RunSpace10](./runspace10-code-sample.md)|Este es el código fuente del ejemplo Runspace10, que agrega un cmdlet a [System. Management. Automation. runspace. Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) y, a continuación, usa la información de configuración modificada para crear el espacio de ejecución.|

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)