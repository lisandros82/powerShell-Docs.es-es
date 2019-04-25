---
title: Creación de espacios de ejecución | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082947"
---
# <a name="creating-runspaces"></a><span data-ttu-id="a938c-102">Creación de espacios de ejecución</span><span class="sxs-lookup"><span data-stu-id="a938c-102">Creating Runspaces</span></span>

<span data-ttu-id="a938c-103">Un espacio de ejecución es el entorno operativo para los comandos que se invocan mediante una aplicación host.</span><span class="sxs-lookup"><span data-stu-id="a938c-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="a938c-104">Este entorno incluye los comandos y los datos que se encuentran actualmente y las restricciones de lenguaje que se aplican actualmente.</span><span class="sxs-lookup"><span data-stu-id="a938c-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="a938c-105">Las aplicaciones host pueden utilizar el espacio de ejecución predeterminada proporcionada por Windows PowerShell, que incluye todos los comandos de núcleo disponible, o crear un espacio de ejecución personalizado que incluya solo un subconjunto de los comandos disponibles.</span><span class="sxs-lookup"><span data-stu-id="a938c-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="a938c-106">Para crear un espacio de ejecución personalizado, cree un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) de objetos y asignarla a su espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="a938c-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="a938c-107">Tareas del espacio de ejecución</span><span class="sxs-lookup"><span data-stu-id="a938c-107">Runspace tasks</span></span>

1. [<span data-ttu-id="a938c-108">Creación de un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="a938c-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="a938c-109">Creación de un espacio de ejecución restringida</span><span class="sxs-lookup"><span data-stu-id="a938c-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="a938c-110">Crear varios espacios de ejecución</span><span class="sxs-lookup"><span data-stu-id="a938c-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="a938c-111">Véase también</span><span class="sxs-lookup"><span data-stu-id="a938c-111">See Also</span></span>
