---
title: Agregar actividades de Windows PowerShell al cuadro de herramientas de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359654"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="72959-102">Adición de actividades de Windows PowerShell al cuadro de herramientas de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="72959-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="72959-103">Antes de crear un flujo de trabajo de PowerShell mediante Diseñador de flujo de trabajo, primero debe agregar las actividades de PowerShell al cuadro de herramientas en un proyecto de aplicación de consola de flujos de trabajo de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="72959-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="72959-104">En el procedimiento siguiente se muestra cómo agregar las actividades del ensamblado Microsoft. PowerShell. Core. Activities al cuadro de herramientas de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="72959-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="72959-105">Agregar actividades de Windows PowerShell al cuadro de herramientas</span><span class="sxs-lookup"><span data-stu-id="72959-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="72959-106">Cree un nuevo proyecto de aplicación de consola de flujos de trabajo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="72959-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="72959-107">En el menú **Ver** , haga clic en **cuadro de herramientas**.</span><span class="sxs-lookup"><span data-stu-id="72959-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="72959-108">Agregue una nueva pestaña en el cuadro de herramientas; para ello, haga clic con el botón derecho en el cuadro de herramientas y haga clic en **Agregar pestaña**y asigne un nombre a la nueva pestaña, como "actividades de PowerShell".</span><span class="sxs-lookup"><span data-stu-id="72959-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="72959-109">Agregar una pestaña permite agrupar las actividades de PowerShell independientes de otras herramientas del cuadro de herramientas.</span><span class="sxs-lookup"><span data-stu-id="72959-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="72959-110">En la pestaña nuevo cuadro de herramientas, haga clic en **elegir elementos.** ... Aparece el cuadro de diálogo **elegir elementos del cuadro de herramientas** .</span><span class="sxs-lookup"><span data-stu-id="72959-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="72959-111">En el cuadro de diálogo **elegir elementos del cuadro de herramientas** , haga clic en la pestaña **System. Activities** .</span><span class="sxs-lookup"><span data-stu-id="72959-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="72959-112">Haga clic en **examinar**.</span><span class="sxs-lookup"><span data-stu-id="72959-112">Click **Browse**.</span></span>

7. <span data-ttu-id="72959-113">Vaya a la carpeta%WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e y haga doble clic en Microsoft. PowerShell. Core. Activities. dll.</span><span class="sxs-lookup"><span data-stu-id="72959-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="72959-114">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="72959-114">Click **OK**.</span></span> <span data-ttu-id="72959-115">Las actividades definidas por el ensamblado Microsoft. PowerShell. Core. Activities ahora están disponibles en el cuadro de herramientas.</span><span class="sxs-lookup"><span data-stu-id="72959-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="72959-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="72959-116">See Also</span></span>

[<span data-ttu-id="72959-117">Escribir un flujo de trabajo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="72959-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="72959-118">Crear un flujo de trabajo con actividades de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="72959-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)