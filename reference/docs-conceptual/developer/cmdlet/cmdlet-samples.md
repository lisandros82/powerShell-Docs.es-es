---
title: Ejemplos de cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365884"
---
# <a name="cmdlet-samples"></a>Ejemplos de cmdlet

En esta sección se describe el código de ejemplo que se proporciona en el SDK de Windows PowerShell 2,0. Puede copiar el código de los temas de esta sección o abrir los archivos de origen instalados con el SDK. El [Kit de desarrollo de software (SDK) de Windows PowerShell 2,0](https://www.microsoft.com/en-us/download/details.aspx?id=2560) proporciona archivos Léame, archivos de código fuente y archivos de proyecto de Visual Studio para cada ejemplo. Con el SDK de instalado, puede encontrar los ejemplos en la carpeta `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

## <a name="in-this-section"></a>En esta sección

[Ejemplo de GetProcessSample01](./getprocesssample01-sample.md) Este ejemplo muestra cómo escribir un cmdlet que recupere los procesos en el equipo local.

[Ejemplo de GetProcessSample02](./getprocesssample02-sample.md) Este ejemplo muestra cómo escribir un cmdlet que recupere los procesos en el equipo local. Proporciona un parámetro de nombre que se puede utilizar para especificar los procesos que se van a recuperar.

[Ejemplo de GetProcessSample03](./getprocesssample03-sample.md) Este ejemplo muestra cómo escribir un cmdlet que recupere los procesos en el equipo local. Proporciona un parámetro de nombre que puede aceptar un objeto de la canalización o un valor de una propiedad de un objeto cuyo nombre de propiedad es el mismo que el nombre del parámetro.

[Ejemplo de GetProcessSample04](./getprocesssample04-sample.md) Este ejemplo muestra cómo escribir un cmdlet que recupere los procesos en el equipo local. Genera un error de no terminación si se produce un error al recuperar un proceso.

[Ejemplo de GetProcessSample05](./getprocesssample05-sample.md) En este ejemplo se muestra una versión completa del cmdlet Get-proc.

[Ejemplo de StopProcessSample01](./stopprocesssample01-sample.md) En este ejemplo se muestra cómo escribir un cmdlet que solicita información al usuario antes de intentar detener un proceso y cómo implementar un parámetro `PassThru` que indica que el usuario desea que el cmdlet devuelva un objeto.

[Ejemplo de StopProcessSample02](./stopprocesssample02-sample.md) Este ejemplo muestra cómo escribir un cmdlet que escriba mensajes de depuración, detallado y de advertencia mientras detiene los procesos en el equipo local.

[Ejemplo de StopProcessSample03](./stopprocesssample03-sample.md) En este ejemplo se muestra cómo escribir un cmdlet cuyos parámetros tienen alias y que admiten caracteres comodín.

[Ejemplo de StopProcessSample04](./stopprocesssample04-sample.md) En este ejemplo se muestra cómo escribir un cmdlet que declara conjuntos de parámetros, especifica el conjunto de parámetros predeterminado y puede aceptar un objeto de entrada.

[Ejemplo de Events01](./events01-sample.md) En este ejemplo se muestra cómo crear un cmdlet que permite al usuario registrarse para eventos generados por [System. IO. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher). Con este cmdlet, los usuarios pueden, por ejemplo, registrar una acción para que se ejecute cuando se cree un archivo en un directorio específico. Este ejemplo se deriva de la clase base [Microsoft. PowerShell. Commands. Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
