---
title: Escribir una aplicación de Host de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: 2039e181becd1b39fc3d6cf0cdbcf0c20e9fc206
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863181"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="8129c-102">Escritura de una aplicación de Host de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8129c-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="8129c-103">Windows PowerShell se puede hospedar en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8129c-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="8129c-104">La aplicación host puede definir el espacio de ejecución donde los comandos son ejecutar, abra las sesiones en un equipo local o remoto e invocar los comandos de forma sincrónica o asincrónica se basa en las necesidades de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8129c-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="8129c-105">Los siguientes temas explican cómo crear una aplicación que hospeda</span><span class="sxs-lookup"><span data-stu-id="8129c-105">The following topics explain how to create an application that hosts</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8129c-106">En esta sección</span><span class="sxs-lookup"><span data-stu-id="8129c-106">In This Section</span></span>

<span data-ttu-id="8129c-107">[Inicio rápido de Host de Windows PowerShell](./windows-powershell-host-quickstart.md) proporciona instrucciones y ejemplos de código para ayudarle a crear aplicaciones de host.</span><span class="sxs-lookup"><span data-stu-id="8129c-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="8129c-108">[Creación de espacios de ejecución](./creating-runspaces.md) un conjunto de temas que explican cómo crear espacios de ejecución para ejecutar el comando de Windows PowerShell en una aplicación host.</span><span class="sxs-lookup"><span data-stu-id="8129c-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="8129c-109">[Agregar e invocar comandos](./adding-and-invoking-commands.md) se explica cómo crear y ejecutar una canalización de comandos en la aplicación host...</span><span class="sxs-lookup"><span data-stu-id="8129c-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="8129c-110">[Creación de espacios de ejecución remoto](./creating-remote-runspaces.md) Expains cómo conectarse a un espacio de ejecución a un equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="8129c-110">[Creating remote runspaces](./creating-remote-runspaces.md) Expains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="8129c-111">[Creación de una interfaz de usuario personalizada](./creating-a-custom-user-interface.md) proporciona vínculos a ejemplos e interfaces de usuario personalizado presenta.</span><span class="sxs-lookup"><span data-stu-id="8129c-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="8129c-112">[Ejemplos de aplicación de host](./host-application-samples.md) esta sección incluyen ejemplos de aplicaciones de host completo.</span><span class="sxs-lookup"><span data-stu-id="8129c-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="8129c-113">Véase también</span><span class="sxs-lookup"><span data-stu-id="8129c-113">See Also</span></span>

[<span data-ttu-id="8129c-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8129c-114">Windows PowerShell</span></span>](http://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)