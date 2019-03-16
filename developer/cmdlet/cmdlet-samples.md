---
title: Ejemplos de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058052"
---
# <a name="cmdlet-samples"></a>Ejemplos de cmdlet

Esta sección describe el código de ejemplo que se proporciona en el SDK de Windows PowerShell 2.0. Puede copiar el código de los temas de esta sección, o abrir los archivos de origen que se instala con el SDK. El [Kit de desarrollo de Software (SDK) de Windows PowerShell 2.0](https://www.microsoft.com/en-us/download/details.aspx?id=2560) proporciona los archivos Léame, archivos de código fuente y archivos de proyecto de Visual Studio para cada ejemplo. Con el SDK instalado, puede encontrar los ejemplos en el `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` carpeta.

## <a name="in-this-section"></a>En esta sección

[Ejemplo GetProcessSample01](./getprocesssample01-sample.md) en este ejemplo se muestra cómo escribir un cmdlet que recupera los procesos en el equipo local.

[Ejemplo GetProcessSample02](./getprocesssample02-sample.md) en este ejemplo se muestra cómo escribir un cmdlet que recupera los procesos en el equipo local. Proporciona un parámetro de nombre que puede utilizarse para especificar los procesos que se van a recuperar.

[Ejemplo de GetProcessSample03](./getprocesssample03-sample.md) en este ejemplo se muestra cómo escribir un cmdlet que recupera los procesos en el equipo local. Proporciona un parámetro de nombre que puede aceptar un objeto de la canalización o un valor de una propiedad de un objeto cuyo nombre de propiedad es el mismo que el nombre del parámetro.

[Ejemplo de GetProcessSample04](./getprocesssample04-sample.md) en este ejemplo se muestra cómo escribir un cmdlet que recupera los procesos en el equipo local. Si se produce un error al recuperar un proceso genera un error de no terminación.

[Ejemplo de GetProcessSample05](./getprocesssample05-sample.md) en este ejemplo se muestra una versión completa del cmdlet Get-Proc.

[Ejemplo de StopProcessSample01](./stopprocesssample01-sample.md) este ejemplo muestra cómo escribir un cmdlet que solicita comentarios del usuario antes de intentar detener un proceso y cómo implementar un `PassThru` parámetro que indica que el usuario desea que el cmdlet para devolver una objeto.

[Ejemplo de StopProcessSample02](./stopprocesssample02-sample.md) en este ejemplo se muestra cómo escribir un cmdlet que escribe los mensajes de advertencia y de debug, verbose, al detener los procesos en el equipo local.

[Ejemplo de StopProcessSample03](./stopprocesssample03-sample.md) en este ejemplo se muestra cómo escribir un cmdlet cuyos parámetros tienen alias y que admiten caracteres comodín.

[Ejemplo de StopProcessSample04](./stopprocesssample04-sample.md) en este ejemplo se muestra cómo escribir un cmdlet que declara los conjuntos de parámetros, que especifica el parámetro predeterminado establecido y puede aceptar un objeto de entrada.

[Ejemplo de Events01](./events01-sample.md) en este ejemplo se muestra cómo crear un cmdlet que permite al usuario registrar los eventos generados por [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher). Con este cmdlet a los usuarios, por ejemplo, pueden registrar una acción que se ejecutará cuando se crea un archivo en un directorio específico. En este ejemplo se deriva de la [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) clase base.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
