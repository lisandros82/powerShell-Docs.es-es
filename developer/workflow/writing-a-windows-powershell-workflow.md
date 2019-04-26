---
title: Escribir un flujo de trabajo de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080329"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="cb4f4-102">Escribir un flujo de trabajo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb4f4-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="cb4f4-103">Puede crear un flujo de trabajo XAML mediante la adición de actividades expuestas por los ensamblados de Windows PowerShell para el Diseñador de flujo de trabajo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cb4f4-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="cb4f4-104">Los siguientes ensamblados de Windows PowerShell exponen las actividades de flujo de trabajo habilitado.</span><span class="sxs-lookup"><span data-stu-id="cb4f4-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb4f4-105">Un flujo de trabajo XAML se debe empaquetar como un módulo si desea proporcionar ayuda para el flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="cb4f4-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="cb4f4-106">Para obtener información acerca de los módulos, consulte [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="cb4f4-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="cb4f4-107">Microsoft.Powershell.Activities</span><span class="sxs-lookup"><span data-stu-id="cb4f4-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="cb4f4-108">Microsoft.Powershell.Core.Activities</span><span class="sxs-lookup"><span data-stu-id="cb4f4-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="cb4f4-109">Microsoft.Powershell.Diagnostics.Activities</span><span class="sxs-lookup"><span data-stu-id="cb4f4-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="cb4f4-110">Microsoft.Powershell.Management.Activities</span><span class="sxs-lookup"><span data-stu-id="cb4f4-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="cb4f4-111">Microsoft.Powershell.Security.Activities</span><span class="sxs-lookup"><span data-stu-id="cb4f4-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="cb4f4-112">Microsoft.Powershell.Utility.Activities</span><span class="sxs-lookup"><span data-stu-id="cb4f4-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="cb4f4-113">Los temas siguientes describen cómo crear un flujo de trabajo mediante actividades de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb4f4-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="cb4f4-114">Adición de actividades de Windows PowerShell en el cuadro de herramientas de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cb4f4-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="cb4f4-115">Creación de un flujo de trabajo con actividades de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb4f4-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="cb4f4-116">Creación de un flujo de trabajo mediante una secuencia de comandos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb4f4-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="cb4f4-117">Importación e invocar un flujo de trabajo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb4f4-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="cb4f4-118">Creación de una actividad de flujo de trabajo desde un Cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb4f4-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)