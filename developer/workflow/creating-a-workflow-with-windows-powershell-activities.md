---
title: Creación de un flujo de trabajo con actividades de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080439"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="0e846-102">Creación de un flujo de trabajo con actividades de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e846-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="0e846-103">Puede crear un flujo de trabajo de Windows PowerShell seleccionando las actividades desde el cuadro de herramientas de Visual Studio y arrastrarlos a la ventana del Diseñador de flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="0e846-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="0e846-104">Para obtener información acerca de cómo agregar actividades de Windows PowerShell en el cuadro de herramientas de Visual Studio, consulte [agregar actividades de Windows PowerShell para Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="0e846-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="0e846-105">Los procedimientos siguientes describen cómo crear un flujo de trabajo que comprueba el estado de dominio de un grupo de equipos especificado por el usuario, se une a un dominio si ya no están combinadas y, a continuación, comprueba el estado de nuevo.</span><span class="sxs-lookup"><span data-stu-id="0e846-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="0e846-106">Configurar el proyecto</span><span class="sxs-lookup"><span data-stu-id="0e846-106">Setting up the Project</span></span>

1. <span data-ttu-id="0e846-107">Siga el procedimiento de [agregar actividades de Windows PowerShell para Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) para crear un proyecto de flujo de trabajo y agregar las actividades desde el [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) y [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) ensamblados en el cuadro de herramientas.</span><span class="sxs-lookup"><span data-stu-id="0e846-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="0e846-108">Agregar System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities y Microsoft.PowerShell.Commands.Management como para el proyecto como ensamblados de referencia.</span><span class="sxs-lookup"><span data-stu-id="0e846-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="0e846-109">Agregar actividades al flujo de trabajo</span><span class="sxs-lookup"><span data-stu-id="0e846-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="0e846-110">Agregar un **secuencia** actividad al flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="0e846-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="0e846-111">Creación de un argumento con nombre `ComputerName` con un tipo de argumento `String[]`.</span><span class="sxs-lookup"><span data-stu-id="0e846-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="0e846-112">Este argumento representa los nombres de los equipos para comprobar y join.</span><span class="sxs-lookup"><span data-stu-id="0e846-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="0e846-113">Creación de un argumento con nombre `DomainCred` typu [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="0e846-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="0e846-114">Este argumento representa las credenciales de dominio de una cuenta de dominio que está autorizado para unir un equipo al dominio.</span><span class="sxs-lookup"><span data-stu-id="0e846-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="0e846-115">Creación de un argumento con nombre `MachineCred` typu [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="0e846-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="0e846-116">Este argumento representa las credenciales de administrador en los equipos para comprobar y join.</span><span class="sxs-lookup"><span data-stu-id="0e846-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="0e846-117">Agregar un **ParallelForEach** actividad dentro de la **secuencia** actividad.</span><span class="sxs-lookup"><span data-stu-id="0e846-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="0e846-118">Escriba `comp` y `ComputerName` en los cuadros de texto para que el bucle recorre en iteración los elementos de la `ComputerName` matriz.</span><span class="sxs-lookup"><span data-stu-id="0e846-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="0e846-119">Agregar un **secuencia** actividad en el cuerpo de la **ParallelForEach** actividad.</span><span class="sxs-lookup"><span data-stu-id="0e846-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="0e846-120">Establecer el **DisplayName** propiedad de la secuencia de `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="0e846-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="0e846-121">Agregar un **GetWmiObject** actividad a la **JoinDomain** secuencia.</span><span class="sxs-lookup"><span data-stu-id="0e846-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="0e846-122">Editar las propiedades de la **GetWmiObject** actividad como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="0e846-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="0e846-123">Propiedad</span><span class="sxs-lookup"><span data-stu-id="0e846-123">Property</span></span>|<span data-ttu-id="0e846-124">Value</span><span class="sxs-lookup"><span data-stu-id="0e846-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="0e846-125">**Clase**</span><span class="sxs-lookup"><span data-stu-id="0e846-125">**Class**</span></span>|<span data-ttu-id="0e846-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="0e846-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="0e846-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="0e846-127">**PSComputerName**</span></span>|<span data-ttu-id="0e846-128">{comp}</span><span class="sxs-lookup"><span data-stu-id="0e846-128">{comp}</span></span>|
   |<span data-ttu-id="0e846-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="0e846-129">**PSCredential**</span></span>|<span data-ttu-id="0e846-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="0e846-130">MachineCred</span></span>|

9. <span data-ttu-id="0e846-131">Agregar un **AddComputer** actividad a la **JoinDomain** secuencia después de la **GetWmiObject** actividad.</span><span class="sxs-lookup"><span data-stu-id="0e846-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="0e846-132">Editar las propiedades de la **AddComputer** actividad como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="0e846-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="0e846-133">Propiedad</span><span class="sxs-lookup"><span data-stu-id="0e846-133">Property</span></span>|<span data-ttu-id="0e846-134">Value</span><span class="sxs-lookup"><span data-stu-id="0e846-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="0e846-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="0e846-135">**ComputerName**</span></span>|<span data-ttu-id="0e846-136">{comp}</span><span class="sxs-lookup"><span data-stu-id="0e846-136">{comp}</span></span>|
    |<span data-ttu-id="0e846-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="0e846-137">**DomainCredential**</span></span>|<span data-ttu-id="0e846-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="0e846-138">DomainCred</span></span>|

11. <span data-ttu-id="0e846-139">Agregar un **RestartComputer** actividad a la **JoinDomain** secuencia después de la **AddComputer** actividad.</span><span class="sxs-lookup"><span data-stu-id="0e846-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="0e846-140">Editar las propiedades de la **RestartComputer** actividad como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="0e846-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="0e846-141">Propiedad</span><span class="sxs-lookup"><span data-stu-id="0e846-141">Property</span></span>|<span data-ttu-id="0e846-142">Value</span><span class="sxs-lookup"><span data-stu-id="0e846-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="0e846-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="0e846-143">**ComputerName**</span></span>|<span data-ttu-id="0e846-144">{comp}</span><span class="sxs-lookup"><span data-stu-id="0e846-144">{comp}</span></span>|
    |<span data-ttu-id="0e846-145">**Credencial**</span><span class="sxs-lookup"><span data-stu-id="0e846-145">**Credential**</span></span>|<span data-ttu-id="0e846-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="0e846-146">MachineCred</span></span>|
    |<span data-ttu-id="0e846-147">**para**</span><span class="sxs-lookup"><span data-stu-id="0e846-147">**For**</span></span>|<span data-ttu-id="0e846-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e846-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="0e846-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="0e846-149">**Force**</span></span>|<span data-ttu-id="0e846-150">True</span><span class="sxs-lookup"><span data-stu-id="0e846-150">True</span></span>|
    |<span data-ttu-id="0e846-151">Wait</span><span class="sxs-lookup"><span data-stu-id="0e846-151">Wait</span></span>|<span data-ttu-id="0e846-152">True</span><span class="sxs-lookup"><span data-stu-id="0e846-152">True</span></span>|
    |<span data-ttu-id="0e846-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="0e846-153">PSComputerName</span></span>|<span data-ttu-id="0e846-154">{""}</span><span class="sxs-lookup"><span data-stu-id="0e846-154">{""}</span></span>|

13. <span data-ttu-id="0e846-155">Agregar un **GetWmiObject** actividad a la **JoinDomain** secuencia después de la **RestartComputer** actividad.</span><span class="sxs-lookup"><span data-stu-id="0e846-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="0e846-156">Editar sus propiedades para que sea el mismo que el anterior **GetWmiObject** actividad.</span><span class="sxs-lookup"><span data-stu-id="0e846-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="0e846-157">Cuando haya terminado los procedimientos, la ventana de diseño de flujo de trabajo debe tener este aspecto.</span><span class="sxs-lookup"><span data-stu-id="0e846-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="0e846-158">![JoinDomain XAML en el Diseñador de flujo de trabajo](../media/joindomainworkflow.png)
    ![JoinDomain XAML en el Diseñador de flujo de trabajo](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="0e846-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>