---
title: Ejemplos de la API de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360844"
---
# <a name="windows-powershell-api-samples"></a>Ejemplos de API de Windows PowerShell

En esta sección se incluye código de ejemplo que muestra cómo crear espacios de ejecución que restringen la funcionalidad y cómo ejecutar comandos de forma asincrónica mediante un grupo de espacio de ejecución para proporcionar los espacios de ejecución. Puede usar Microsoft Visual Studio para crear una aplicación de consola y, a continuación, copiar el código de los temas de esta sección en la aplicación host.

## <a name="in-this-section"></a>En esta sección

[Ejemplo de PowerShell01](./windows-powershell01-sample.md) En este ejemplo se muestra cómo usar un objeto [System. Management. Automation. runspace. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) para limitar la funcionalidad de un espacio de ejecución. La salida de este ejemplo muestra cómo restringir el modo de lenguaje del espacio de ejecución, cómo marcar un cmdlet como privado, cómo agregar y quitar cmdlets y proveedores, cómo agregar un comando de proxy, etc.

[Ejemplo de PowerShell02](./windows-powershell02-sample.md) En este ejemplo se muestra cómo ejecutar comandos de forma asincrónica mediante los espacios de ejecución de un grupo de espacio de ejecución. En el ejemplo se genera una lista de comandos y, a continuación, se ejecutan esos comandos mientras el motor de Windows PowerShell abre un espacio de ejecución desde el grupo cuando es necesario.