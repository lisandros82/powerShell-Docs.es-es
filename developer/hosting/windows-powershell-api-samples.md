---
title: Ejemplos de Windows PowerShell API | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082590"
---
# <a name="windows-powershell-api-samples"></a>Ejemplos de API de Windows PowerShell

En esta sección se incluye código de ejemplo que muestra cómo crear espacios de ejecución que restringen la funcionalidad y cómo ejecutar de forma asincrónica comandos mediante el uso de un grupo de espacio de ejecución para proporcionar los espacios de ejecución. Puede utilizar Microsoft Visual Studio para crear una aplicación de consola y, a continuación, copie el código de los temas de esta sección en la aplicación host.

## <a name="in-this-section"></a>En esta sección

[Ejemplo de PowerShell01](./windows-powershell01-sample.md) en este ejemplo se muestra cómo usar un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto para limitar la funcionalidad de un espacio de ejecución. La salida de este ejemplo muestra cómo restringir el modo de lenguaje el espacio de ejecución, cómo marcar un cmdlet como privado, cómo agregar y quitar cmdlets y proveedores, cómo agregar un comando de proxy y mucho más.

[Ejemplo de PowerShell02](./windows-powershell02-sample.md) este ejemplo muestra cómo ejecutar comandos de forma asincrónica mediante el uso de los espacios de ejecución de un grupo de espacio de ejecución. El ejemplo genera una lista de comandos y, a continuación, ejecuta esos comandos mientras el motor de Windows PowerShell abre un espacio de ejecución de la agrupación cuando sea necesario.