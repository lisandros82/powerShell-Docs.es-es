---
title: Adición de actividades de Windows PowerShell en el cuadro de herramientas de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080482"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="03178-102">Adición de actividades de Windows PowerShell al cuadro de herramientas de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="03178-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="03178-103">Antes de crear un flujo de trabajo de PowerShell mediante el Diseñador de flujo de trabajo, primero debe agregar las actividades de PowerShell en el cuadro de herramientas en un proyecto de aplicación de consola de flujo de trabajo de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03178-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="03178-104">El siguiente procedimiento muestra cómo agregar las actividades desde el ensamblado Microsoft.PowerShell.Core.Activities al cuadro de herramientas de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03178-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="03178-105">Adición de actividades de Windows PowerShell en el cuadro de herramientas</span><span class="sxs-lookup"><span data-stu-id="03178-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="03178-106">Crear un nuevo proyecto de aplicación de consola de flujo de trabajo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03178-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="03178-107">En el **vista** menú, haga clic en **cuadro de herramientas**.</span><span class="sxs-lookup"><span data-stu-id="03178-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="03178-108">Agregar una nueva pestaña del cuadro de herramientas con el botón secundario en el cuadro de herramientas y haciendo clic en **Agregar pestaña**y asigne un nombre como "Actividades de PowerShell" a la nueva pestaña.</span><span class="sxs-lookup"><span data-stu-id="03178-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="03178-109">Agregando una pestaña permite agrupar las actividades de PowerShell independiente de otras herramientas en el cuadro de herramientas.</span><span class="sxs-lookup"><span data-stu-id="03178-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="03178-110">En la nueva pestaña del cuadro de herramientas, haga clic en **elegir elementos...** . El **elegir elementos del cuadro de herramientas** aparece el cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="03178-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="03178-111">En el **elegir elementos del cuadro de herramientas** cuadro de diálogo, haga clic en el **System.Activities** ficha.</span><span class="sxs-lookup"><span data-stu-id="03178-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="03178-112">Haga clic en **examinar**.</span><span class="sxs-lookup"><span data-stu-id="03178-112">Click **Browse**.</span></span>

7. <span data-ttu-id="03178-113">Navegue hasta la carpeta %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e y haga doble clic en Microsoft.PowerShell.Core.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="03178-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="03178-114">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="03178-114">Click **OK**.</span></span> <span data-ttu-id="03178-115">Las actividades definidas por el ensamblado Microsoft.PowerShell.Core.Activities ahora están disponibles en el cuadro de herramientas.</span><span class="sxs-lookup"><span data-stu-id="03178-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="03178-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="03178-116">See Also</span></span>

[<span data-ttu-id="03178-117">Escribir un flujo de trabajo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="03178-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="03178-118">Creación de un flujo de trabajo con actividades de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="03178-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)