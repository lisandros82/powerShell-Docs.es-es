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
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="686d1-102">Ejemplos de API de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="686d1-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="686d1-103">En esta sección se incluye código de ejemplo que muestra cómo crear espacios de ejecución que restringen la funcionalidad y cómo ejecutar de forma asincrónica comandos mediante el uso de un grupo de espacio de ejecución para proporcionar los espacios de ejecución.</span><span class="sxs-lookup"><span data-stu-id="686d1-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="686d1-104">Puede utilizar Microsoft Visual Studio para crear una aplicación de consola y, a continuación, copie el código de los temas de esta sección en la aplicación host.</span><span class="sxs-lookup"><span data-stu-id="686d1-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="686d1-105">En esta sección</span><span class="sxs-lookup"><span data-stu-id="686d1-105">In This Section</span></span>

<span data-ttu-id="686d1-106">[Ejemplo de PowerShell01](./windows-powershell01-sample.md) en este ejemplo se muestra cómo usar un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto para limitar la funcionalidad de un espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="686d1-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="686d1-107">La salida de este ejemplo muestra cómo restringir el modo de lenguaje el espacio de ejecución, cómo marcar un cmdlet como privado, cómo agregar y quitar cmdlets y proveedores, cómo agregar un comando de proxy y mucho más.</span><span class="sxs-lookup"><span data-stu-id="686d1-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="686d1-108">[Ejemplo de PowerShell02](./windows-powershell02-sample.md) este ejemplo muestra cómo ejecutar comandos de forma asincrónica mediante el uso de los espacios de ejecución de un grupo de espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="686d1-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="686d1-109">El ejemplo genera una lista de comandos y, a continuación, ejecuta esos comandos mientras el motor de Windows PowerShell abre un espacio de ejecución de la agrupación cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="686d1-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>