---
title: Crear espacios de espacios | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367584"
---
# <a name="creating-runspaces"></a><span data-ttu-id="3b8de-102">Creación de espacios de ejecución</span><span class="sxs-lookup"><span data-stu-id="3b8de-102">Creating Runspaces</span></span>

<span data-ttu-id="3b8de-103">Un espacio de ejecución es el entorno operativo para los comandos invocados por una aplicación host.</span><span class="sxs-lookup"><span data-stu-id="3b8de-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="3b8de-104">Este entorno incluye los comandos y datos actualmente presentes y cualquier restricción de lenguaje que se aplique actualmente.</span><span class="sxs-lookup"><span data-stu-id="3b8de-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="3b8de-105">Las aplicaciones host pueden usar el espacio de ejecución predeterminado proporcionado por Windows PowerShell, que incluye todos los comandos principales disponibles, o crear un espacio de ejecución personalizado que incluye solo un subconjunto de los comandos disponibles.</span><span class="sxs-lookup"><span data-stu-id="3b8de-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="3b8de-106">Para crear un espacio de ejecución personalizado, cree un objeto [System. Management. Automation. runspace. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) y asígnelo al espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="3b8de-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="3b8de-107">Tareas del espacio de ejecución</span><span class="sxs-lookup"><span data-stu-id="3b8de-107">Runspace tasks</span></span>

1. [<span data-ttu-id="3b8de-108">Creación de un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="3b8de-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="3b8de-109">Crear un espacio de ejecución restringido</span><span class="sxs-lookup"><span data-stu-id="3b8de-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="3b8de-110">Crear varios espacios de espacios</span><span class="sxs-lookup"><span data-stu-id="3b8de-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="3b8de-111">Véase también</span><span class="sxs-lookup"><span data-stu-id="3b8de-111">See Also</span></span>
