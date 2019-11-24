---
title: Crear un flujo de trabajo con actividades de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359634"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="52d92-102">Creación de un flujo de trabajo con actividades de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="52d92-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="52d92-103">Puede crear un flujo de trabajo de Windows PowerShell seleccionando actividades en el cuadro de herramientas de Visual Studio y arrastrándolos a la ventana Diseñador de flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="52d92-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="52d92-104">Para obtener información sobre cómo agregar actividades de Windows PowerShell al cuadro de herramientas de Visual Studio, vea [Agregar actividades de Windows PowerShell al cuadro de herramientas de Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="52d92-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="52d92-105">En los procedimientos siguientes se describe cómo crear un flujo de trabajo que comprueba el estado de dominio de un grupo de equipos especificados por el usuario, los une a un dominio si aún no están Unidos y, a continuación, vuelve a comprobar el estado.</span><span class="sxs-lookup"><span data-stu-id="52d92-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="52d92-106">Configurar el proyecto</span><span class="sxs-lookup"><span data-stu-id="52d92-106">Setting up the Project</span></span>

1. <span data-ttu-id="52d92-107">Siga el procedimiento descrito en [Agregar actividades de Windows PowerShell al cuadro de herramientas de Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) para crear un proyecto de flujo de trabajo y agregar las actividades de los ensamblados [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities) y [Microsoft. PowerShell. Management. Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) al cuadro de herramientas.</span><span class="sxs-lookup"><span data-stu-id="52d92-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="52d92-108">Agregue System. Management. Automation, Microsoft. PowerShell. Activities, System. Management, Microsoft. PowerShell. Management. Activities y Microsoft. PowerShell. Commands. Management al proyecto como ensamblados de referencia.</span><span class="sxs-lookup"><span data-stu-id="52d92-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="52d92-109">Agregar actividades al flujo de trabajo</span><span class="sxs-lookup"><span data-stu-id="52d92-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="52d92-110">Agregue una actividad **Sequence** al flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="52d92-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="52d92-111">Cree un argumento denominado `ComputerName` con un tipo de argumento de `String[]`.</span><span class="sxs-lookup"><span data-stu-id="52d92-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="52d92-112">Este argumento representa los nombres de los equipos que se van a comprobar y a los que se va a combinar.</span><span class="sxs-lookup"><span data-stu-id="52d92-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="52d92-113">Cree un argumento denominado `DomainCred` del tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="52d92-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="52d92-114">Este argumento representa las credenciales de dominio de una cuenta de dominio que está autorizada para unir un equipo al dominio.</span><span class="sxs-lookup"><span data-stu-id="52d92-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="52d92-115">Cree un argumento denominado `MachineCred` del tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="52d92-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="52d92-116">Este argumento representa las credenciales de un administrador en los equipos para comprobar y unirse.</span><span class="sxs-lookup"><span data-stu-id="52d92-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="52d92-117">Agregue una actividad **ParallelForEach** dentro de la actividad **Sequence** .</span><span class="sxs-lookup"><span data-stu-id="52d92-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="52d92-118">Escriba `comp` y `ComputerName` en los cuadros de texto para que el bucle recorra en iteración los elementos de la matriz de `ComputerName`.</span><span class="sxs-lookup"><span data-stu-id="52d92-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="52d92-119">Agregue una actividad **Sequence** al cuerpo de la actividad **ParallelForEach** .</span><span class="sxs-lookup"><span data-stu-id="52d92-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="52d92-120">Establezca la propiedad **displayName** de la secuencia en `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="52d92-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="52d92-121">Agregue una actividad **GetWmiObject** a la secuencia **JoinDomain** .</span><span class="sxs-lookup"><span data-stu-id="52d92-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="52d92-122">Edite las propiedades de la actividad **GetWmiObject** como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="52d92-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="52d92-123">Property</span><span class="sxs-lookup"><span data-stu-id="52d92-123">Property</span></span>|<span data-ttu-id="52d92-124">Valor</span><span class="sxs-lookup"><span data-stu-id="52d92-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="52d92-125">**Las**</span><span class="sxs-lookup"><span data-stu-id="52d92-125">**Class**</span></span>|<span data-ttu-id="52d92-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="52d92-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="52d92-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="52d92-127">**PSComputerName**</span></span>|<span data-ttu-id="52d92-128">COMP</span><span class="sxs-lookup"><span data-stu-id="52d92-128">{comp}</span></span>|
   |<span data-ttu-id="52d92-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="52d92-129">**PSCredential**</span></span>|<span data-ttu-id="52d92-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="52d92-130">MachineCred</span></span>|

9. <span data-ttu-id="52d92-131">Agregue una actividad **AddComputer** a la secuencia **JoinDomain** después de la actividad **GetWmiObject** .</span><span class="sxs-lookup"><span data-stu-id="52d92-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="52d92-132">Edite las propiedades de la actividad **AddComputer** como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="52d92-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="52d92-133">Property</span><span class="sxs-lookup"><span data-stu-id="52d92-133">Property</span></span>|<span data-ttu-id="52d92-134">Valor</span><span class="sxs-lookup"><span data-stu-id="52d92-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="52d92-135">**NombreDeEquipo**</span><span class="sxs-lookup"><span data-stu-id="52d92-135">**ComputerName**</span></span>|<span data-ttu-id="52d92-136">COMP</span><span class="sxs-lookup"><span data-stu-id="52d92-136">{comp}</span></span>|
    |<span data-ttu-id="52d92-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="52d92-137">**DomainCredential**</span></span>|<span data-ttu-id="52d92-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="52d92-138">DomainCred</span></span>|

11. <span data-ttu-id="52d92-139">Agregue una actividad **RestartComputer** a la secuencia **JoinDomain** después de la actividad **AddComputer** .</span><span class="sxs-lookup"><span data-stu-id="52d92-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="52d92-140">Edite las propiedades de la actividad **RestartComputer** como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="52d92-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="52d92-141">Property</span><span class="sxs-lookup"><span data-stu-id="52d92-141">Property</span></span>|<span data-ttu-id="52d92-142">Valor</span><span class="sxs-lookup"><span data-stu-id="52d92-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="52d92-143">**NombreDeEquipo**</span><span class="sxs-lookup"><span data-stu-id="52d92-143">**ComputerName**</span></span>|<span data-ttu-id="52d92-144">COMP</span><span class="sxs-lookup"><span data-stu-id="52d92-144">{comp}</span></span>|
    |<span data-ttu-id="52d92-145">**Caja**</span><span class="sxs-lookup"><span data-stu-id="52d92-145">**Credential**</span></span>|<span data-ttu-id="52d92-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="52d92-146">MachineCred</span></span>|
    |<span data-ttu-id="52d92-147">**Para**</span><span class="sxs-lookup"><span data-stu-id="52d92-147">**For**</span></span>|<span data-ttu-id="52d92-148">Microsoft. PowerShell. Commands. WaitForServiceTypes. PowerShell</span><span class="sxs-lookup"><span data-stu-id="52d92-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="52d92-149">**Aplica**</span><span class="sxs-lookup"><span data-stu-id="52d92-149">**Force**</span></span>|<span data-ttu-id="52d92-150">True</span><span class="sxs-lookup"><span data-stu-id="52d92-150">True</span></span>|
    |<span data-ttu-id="52d92-151">Wait</span><span class="sxs-lookup"><span data-stu-id="52d92-151">Wait</span></span>|<span data-ttu-id="52d92-152">True</span><span class="sxs-lookup"><span data-stu-id="52d92-152">True</span></span>|
    |<span data-ttu-id="52d92-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="52d92-153">PSComputerName</span></span>|<span data-ttu-id="52d92-154">{""}</span><span class="sxs-lookup"><span data-stu-id="52d92-154">{""}</span></span>|

13. <span data-ttu-id="52d92-155">Agregue una actividad **GetWmiObject** a la secuencia **JoinDomain** después de la actividad **RestartComputer** .</span><span class="sxs-lookup"><span data-stu-id="52d92-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="52d92-156">Edite sus propiedades para que coincidan con la actividad **GetWmiObject** anterior.</span><span class="sxs-lookup"><span data-stu-id="52d92-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="52d92-157">Cuando haya terminado los procedimientos, la ventana de diseño de flujo de trabajo debería tener este aspecto.</span><span class="sxs-lookup"><span data-stu-id="52d92-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="52d92-158">![el XAML de JoinDomain en el diseñador de flujo de trabajo](../media/joindomainworkflow.png)
    ![JOINDOMAIN XAML en el diseñador de flujo de trabajo](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="52d92-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>