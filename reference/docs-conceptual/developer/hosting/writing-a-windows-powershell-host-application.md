---
title: Escritura de una aplicación host de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: fe0393634a1e5bb1a3d4a98ccf245e199beb0f16
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75869918"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="f373c-102">Escritura de una aplicación de Host de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f373c-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="f373c-103">Puede hospedar Windows PowerShell en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f373c-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="f373c-104">La aplicación host puede definir el espacio de ejecución donde se ejecutan los comandos, abrir sesiones en un equipo local o remoto e invocar los comandos de forma sincrónica o asincrónica según las necesidades de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f373c-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="f373c-105">En los temas siguientes se explica cómo crear una aplicación que hospede Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f373c-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f373c-106">En esta sección</span><span class="sxs-lookup"><span data-stu-id="f373c-106">In This Section</span></span>

<span data-ttu-id="f373c-107">[Inicio rápido de host de Windows PowerShell](./windows-powershell-host-quickstart.md) Proporciona instrucciones y ejemplos de código para empezar a crear aplicaciones host.</span><span class="sxs-lookup"><span data-stu-id="f373c-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="f373c-108">[Crear espacios de espacios](./creating-runspaces.md) Un conjunto de temas que explican cómo crear espacios de ejecución para ejecutar el comando de Windows PowerShell en una aplicación host.</span><span class="sxs-lookup"><span data-stu-id="f373c-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="f373c-109">[Agregar e invocar comandos](./adding-and-invoking-commands.md) Explica cómo crear y ejecutar una canalización de comandos en la aplicación host.</span><span class="sxs-lookup"><span data-stu-id="f373c-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="f373c-110">[Crear espacios de control remotos](./creating-remote-runspaces.md) Explica cómo conectar un espacio de ejecución a un equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="f373c-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="f373c-111">[Crear una interfaz de usuario personalizada](./creating-a-custom-user-interface.md) Presenta interfaces de usuario personalizadas y proporciona vínculos a ejemplos.</span><span class="sxs-lookup"><span data-stu-id="f373c-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="f373c-112">[Ejemplos de aplicaciones host](./host-application-samples.md) En esta sección se incluyen ejemplos de aplicaciones host completas.</span><span class="sxs-lookup"><span data-stu-id="f373c-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>
