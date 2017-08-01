---
title: Windows Management Framework (WMF)
ms.date: 2016-05-16
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: eacd33d2a0a92977a3990132e23eef9871a7f0dc
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
# <a name="windows-management-framework"></a><span data-ttu-id="3bdb9-103">Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="3bdb9-103">Windows Management Framework</span></span>

<span data-ttu-id="3bdb9-104">Windows Management Framework (WMF) es el mecanismo de entrega que proporciona una interfaz de administración coherente entre las distintas versiones de Windows y Windows Server.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-104">Windows Management Framework (WMF) is the delivery mechanism that provides a consistent management interface across the various flavors of Windows and Windows Server.</span></span>
<span data-ttu-id="3bdb9-105">Con la instalación de WMF, los clientes consiguen una manera de poder operar en diferentes sistemas operativos del entorno sin problemas.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-105">With the installation of WMF, customers get a seamless way to interoperate between mixes of OSes in their environment.</span></span>
<span data-ttu-id="3bdb9-106">WMF hace que las actualizaciones de la funcionalidad de administración, de una versión determinada de Windows y Windows Server, estén disponibles para su instalación en las versiones inferiores (normalmente, en 2 versiones inferiores) de Windows y Windows Server.</span><span class="sxs-lookup"><span data-stu-id="3bdb9-106">WMF makes the updates to management functionality, in a given release of Windows and Windows Server, available for installation on lower versions (typically, 2 lower versions) of Windows and Windows Server.</span></span>

<span data-ttu-id="3bdb9-107">La instalación de WMF permite agregar o actualizar las características siguientes:</span><span class="sxs-lookup"><span data-stu-id="3bdb9-107">WMF installation adds and/or updates the following features:</span></span>

- <span data-ttu-id="3bdb9-108">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3bdb9-108">Windows PowerShell</span></span>
- <span data-ttu-id="3bdb9-109">Configuración de estado deseado (DSC) de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3bdb9-109">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="3bdb9-110">Windows PowerShell Integrated Script Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="3bdb9-110">Windows PowerShell Integrated Script Environment (ISE)</span></span>
- <span data-ttu-id="3bdb9-111">Administración remota de Windows (WinRM)</span><span class="sxs-lookup"><span data-stu-id="3bdb9-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="3bdb9-112">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="3bdb9-112">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="3bdb9-113">Windows PowerShell Web Services (Extensión IIS Management OData)</span><span class="sxs-lookup"><span data-stu-id="3bdb9-113">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="3bdb9-114">Registro de inventario de software (SIL)</span><span class="sxs-lookup"><span data-stu-id="3bdb9-114">Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="3bdb9-115">Proveedor de CIM del administrador del servidor</span><span class="sxs-lookup"><span data-stu-id="3bdb9-115">Server Manager CIM Provider</span></span>

## <a name="wmf-release-notes"></a><span data-ttu-id="3bdb9-116">Notas de la versión WMF</span><span class="sxs-lookup"><span data-stu-id="3bdb9-116">WMF Release Notes</span></span>
<span data-ttu-id="3bdb9-117">Para más información acerca de las diversas mejoras en PowerShell y en otros componentes de un determinado WMF, consulte los vínculos siguientes para revisar las notas de la versión:</span><span class="sxs-lookup"><span data-stu-id="3bdb9-117">To learn about various enhancements in PowerShell and other components of a given WMF, please refer to the links below to review the release notes:</span></span>


- [<span data-ttu-id="3bdb9-118">WMF 5.1 (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="3bdb9-118">WMF 5.1 (Preview)</span></span>](5.1/release-notes.md)
- [<span data-ttu-id="3bdb9-119">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="3bdb9-119">WMF 5.0</span></span>](5.0/releasenotes.md)


## <a name="wmf-availability-across-windows-operating-systems"></a><span data-ttu-id="3bdb9-120">Disponibilidad WMF entre sistemas operativos Windows</span><span class="sxs-lookup"><span data-stu-id="3bdb9-120">WMF Availability Across Windows Operating Systems</span></span>

><span data-ttu-id="3bdb9-121">TODO: Agregar vínculos a un DLC de WMF específico en el encabezado de columna</span><span class="sxs-lookup"><span data-stu-id="3bdb9-121">TODO: Add links to specific WMF DLC on the column header</span></span>

| <span data-ttu-id="3bdb9-122">Versión de sistema operativo</span><span class="sxs-lookup"><span data-stu-id="3bdb9-122">Operating System Version</span></span> | [<span data-ttu-id="3bdb9-123">Versión preliminar de WMF 5.1*</span><span class="sxs-lookup"><span data-stu-id="3bdb9-123">WMF 5.1 Preview*</span></span>]() | [<span data-ttu-id="3bdb9-124">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="3bdb9-124">WMF 5.0</span></span>]() | [<span data-ttu-id="3bdb9-125">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="3bdb9-125">WMF 4.0</span></span>]() |  [<span data-ttu-id="3bdb9-126">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="3bdb9-126">WMF 3.0</span></span>]() | [<span data-ttu-id="3bdb9-127">WMF (2.0)</span><span class="sxs-lookup"><span data-stu-id="3bdb9-127">WMF (2.0)</span></span>]() |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| <span data-ttu-id="3bdb9-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="3bdb9-128">Windows Server 2016</span></span> | <span data-ttu-id="3bdb9-129">Se envía en la caja*</span><span class="sxs-lookup"><span data-stu-id="3bdb9-129">Ships in-box*</span></span> | <span data-ttu-id="3bdb9-130">Se envía en la caja*</span><span class="sxs-lookup"><span data-stu-id="3bdb9-130">Ships in-box*</span></span> |  |  |  |
| <span data-ttu-id="3bdb9-131">Windows 10</span><span class="sxs-lookup"><span data-stu-id="3bdb9-131">Windows 10</span></span> | <span data-ttu-id="3bdb9-132">Se envía en la caja*</span><span class="sxs-lookup"><span data-stu-id="3bdb9-132">Ships in-box*</span></span> | <span data-ttu-id="3bdb9-133">Se envía en la caja*</span><span class="sxs-lookup"><span data-stu-id="3bdb9-133">Ships in-box*</span></span>  | | | |  
| <span data-ttu-id="3bdb9-134">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="3bdb9-134">Windows Server 2012 R2</span></span>| <span data-ttu-id="3bdb9-135">??</span><span class="sxs-lookup"><span data-stu-id="3bdb9-135">??</span></span> | <span data-ttu-id="3bdb9-136">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-136">Yes</span></span> | <span data-ttu-id="3bdb9-137">Se envía en la caja</span><span class="sxs-lookup"><span data-stu-id="3bdb9-137">Ships in-box</span></span> |  |  |
| <span data-ttu-id="3bdb9-138">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="3bdb9-138">Windows 8.1</span></span> | <span data-ttu-id="3bdb9-139">??</span><span class="sxs-lookup"><span data-stu-id="3bdb9-139">??</span></span> | <span data-ttu-id="3bdb9-140">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-140">Yes</span></span> |  <span data-ttu-id="3bdb9-141">Se envía en la caja</span><span class="sxs-lookup"><span data-stu-id="3bdb9-141">Ships in-box</span></span> |  |  |
| <span data-ttu-id="3bdb9-142">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3bdb9-142">Windows Server 2012</span></span> | <span data-ttu-id="3bdb9-143">??</span><span class="sxs-lookup"><span data-stu-id="3bdb9-143">??</span></span> | <span data-ttu-id="3bdb9-144">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-144">Yes</span></span> | <span data-ttu-id="3bdb9-145">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-145">Yes</span></span> |  <span data-ttu-id="3bdb9-146">Se envía en la caja</span><span class="sxs-lookup"><span data-stu-id="3bdb9-146">Ships in-box</span></span> | |
| <span data-ttu-id="3bdb9-147">Windows 8</span><span class="sxs-lookup"><span data-stu-id="3bdb9-147">Windows 8</span></span> |  |  |  | <span data-ttu-id="3bdb9-148">Se envía en la caja</span><span class="sxs-lookup"><span data-stu-id="3bdb9-148">Ships in-box</span></span> | |
| <span data-ttu-id="3bdb9-149">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="3bdb9-149">Windows Server 2008 R2 SP1</span></span> | <span data-ttu-id="3bdb9-150">??</span><span class="sxs-lookup"><span data-stu-id="3bdb9-150">??</span></span> | <span data-ttu-id="3bdb9-151">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-151">Yes</span></span> | <span data-ttu-id="3bdb9-152">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-152">Yes</span></span> |  <span data-ttu-id="3bdb9-153">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-153">Yes</span></span>| <span data-ttu-id="3bdb9-154">Se envía en la caja</span><span class="sxs-lookup"><span data-stu-id="3bdb9-154">Ships in-box</span></span> |
| <span data-ttu-id="3bdb9-155">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="3bdb9-155">Windows 7 SP1</span></span>  | <span data-ttu-id="3bdb9-156">??</span><span class="sxs-lookup"><span data-stu-id="3bdb9-156">??</span></span> | <span data-ttu-id="3bdb9-157">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-157">Yes</span></span> | <span data-ttu-id="3bdb9-158">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-158">Yes</span></span> | <span data-ttu-id="3bdb9-159">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-159">Yes</span></span> | <span data-ttu-id="3bdb9-160">Se envía en la caja</span><span class="sxs-lookup"><span data-stu-id="3bdb9-160">Ships in-box</span></span> |
| <span data-ttu-id="3bdb9-161">Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="3bdb9-161">Windows Server 2008 SP2</span></span> | | | | <span data-ttu-id="3bdb9-162">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-162">Yes</span></span> | <span data-ttu-id="3bdb9-163">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-163">Yes</span></span> |
| <span data-ttu-id="3bdb9-164">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="3bdb9-164">Windows Vista</span></span> | | | | | <span data-ttu-id="3bdb9-165">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-165">Yes</span></span> |
| <span data-ttu-id="3bdb9-166">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="3bdb9-166">Windows Server 2003</span></span>| | | |  | <span data-ttu-id="3bdb9-167">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-167">Yes</span></span> |
| <span data-ttu-id="3bdb9-168">Windows XP</span><span class="sxs-lookup"><span data-stu-id="3bdb9-168">Windows XP</span></span> | | | |  | <span data-ttu-id="3bdb9-169">Sí</span><span class="sxs-lookup"><span data-stu-id="3bdb9-169">Yes</span></span> |

><span data-ttu-id="3bdb9-170">TODO: Explicar * en la tabla anterior</span><span class="sxs-lookup"><span data-stu-id="3bdb9-170">TODO: Explain * in the above table</span></span>
