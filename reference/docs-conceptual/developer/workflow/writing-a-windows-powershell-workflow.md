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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366014"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="c75bc-102">Escribir un flujo de trabajo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c75bc-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="c75bc-103">Puede crear un flujo de trabajo XAML agregando las actividades expuestas por los ensamblados de Windows PowerShell al diseñador de flujo de trabajo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c75bc-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="c75bc-104">Los siguientes ensamblados de Windows PowerShell exponen actividades habilitadas para el flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="c75bc-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c75bc-105">Un flujo de trabajo de XAML se debe empaquetar como un módulo si desea proporcionar ayuda para el flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="c75bc-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="c75bc-106">Para obtener información acerca de los módulos, consulte [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="c75bc-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="c75bc-107">Microsoft. PowerShell. Activities</span><span class="sxs-lookup"><span data-stu-id="c75bc-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="c75bc-108">Microsoft. PowerShell. Core. Activities</span><span class="sxs-lookup"><span data-stu-id="c75bc-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="c75bc-109">Microsoft. PowerShell. Diagnostics. Activities</span><span class="sxs-lookup"><span data-stu-id="c75bc-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="c75bc-110">Microsoft. PowerShell. Management. Activities</span><span class="sxs-lookup"><span data-stu-id="c75bc-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="c75bc-111">Microsoft. PowerShell. Security. Activities</span><span class="sxs-lookup"><span data-stu-id="c75bc-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="c75bc-112">Microsoft. PowerShell. Utility. Activities</span><span class="sxs-lookup"><span data-stu-id="c75bc-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="c75bc-113">En los temas siguientes se describe cómo crear un flujo de trabajo mediante actividades de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c75bc-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="c75bc-114">Agregar actividades de Windows PowerShell al cuadro de herramientas de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c75bc-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="c75bc-115">Crear un flujo de trabajo con actividades de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c75bc-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="c75bc-116">Crear un flujo de trabajo mediante un script de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c75bc-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="c75bc-117">Importar e invocar un flujo de trabajo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c75bc-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="c75bc-118">Crear una actividad de flujo de trabajo desde un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c75bc-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)