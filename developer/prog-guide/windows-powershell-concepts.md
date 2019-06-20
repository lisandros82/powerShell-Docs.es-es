---
title: Windows PowerShell conceptos | Microsoft Docs
ms.custom: ''
ms.date: 6/12/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: 4410b1f9c80afefd5479fa68154f9947b805edcf
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263848"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="13ec5-102">Conceptos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="13ec5-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="13ec5-103">Esta sección contiene información conceptual que le ayudará a comprender de PowerShell desde el punto de vista del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="13ec5-103">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="13ec5-104">Nombre del tema</span><span class="sxs-lookup"><span data-stu-id="13ec5-104">Topic Name</span></span>|<span data-ttu-id="13ec5-105">Descripción</span><span class="sxs-lookup"><span data-stu-id="13ec5-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="13ec5-106">about_Objects</span><span class="sxs-lookup"><span data-stu-id="13ec5-106">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="13ec5-107">Descripción de los objetos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13ec5-107">Description of PowerShell objects.</span></span> <span data-ttu-id="13ec5-108">Para obtener más información, consulte [sobre la creación de objetos](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span><span class="sxs-lookup"><span data-stu-id="13ec5-108">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="13ec5-109">Creación de espacios de ejecución</span><span class="sxs-lookup"><span data-stu-id="13ec5-109">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="13ec5-110">Los entornos operativos que se procesan los comandos.</span><span class="sxs-lookup"><span data-stu-id="13ec5-110">The operating environments where commands are processed.</span></span> <span data-ttu-id="13ec5-111">Para obtener más información, consulte [clases del espacio de ejecución](/dotnet/api/system.management.automation.runspaces.runspace).</span><span class="sxs-lookup"><span data-stu-id="13ec5-111">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="13ec5-112">Extender los objetos de salida</span><span class="sxs-lookup"><span data-stu-id="13ec5-112">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="13ec5-113">Cómo extender los objetos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13ec5-113">How to extend PowerShell objects.</span></span> <span data-ttu-id="13ec5-114">Para obtener más información, consulte [Types.ps1xml acerca de](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="13ec5-114">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="13ec5-115">Registrar los Cmdlets</span><span class="sxs-lookup"><span data-stu-id="13ec5-115">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="13ec5-116">Cómo hacer que los módulos y complementos disponibles en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13ec5-116">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="13ec5-117">Para obtener más información, consulte [módulos y complementos](../cmdlet/modules-and-snap-ins.md).</span><span class="sxs-lookup"><span data-stu-id="13ec5-117">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="13ec5-118">Solicitar confirmación de los Cmdlets</span><span class="sxs-lookup"><span data-stu-id="13ec5-118">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="13ec5-119">Cómo los cmdlets y proveedores de solicitan comentarios del usuario antes de que se realiza una acción.</span><span class="sxs-lookup"><span data-stu-id="13ec5-119">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="13ec5-120">Clase RuntimeDefinedParameter</span><span class="sxs-lookup"><span data-stu-id="13ec5-120">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="13ec5-121">Declaraciones de parámetro en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="13ec5-121">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="13ec5-122">System.Management.Automation Namespace</span><span class="sxs-lookup"><span data-stu-id="13ec5-122">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="13ec5-123">Información general de los espacios de nombres de la API de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13ec5-123">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="13ec5-124">Información general sobre el proveedor de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="13ec5-124">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="13ec5-125">Almacena la información general sobre los proveedores de PowerShell que se usan para tener acceso a datos.</span><span class="sxs-lookup"><span data-stu-id="13ec5-125">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="13ec5-126">Escribir ayuda para Cmdlets de PowerShell</span><span class="sxs-lookup"><span data-stu-id="13ec5-126">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="13ec5-127">Cómo escribir ayuda de cmdlet de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13ec5-127">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="13ec5-128">Vea también</span><span class="sxs-lookup"><span data-stu-id="13ec5-128">See also</span></span>

[<span data-ttu-id="13ec5-129">Clase de PowerShell</span><span class="sxs-lookup"><span data-stu-id="13ec5-129">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="13ec5-130">Referencia de API de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="13ec5-130">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0)

[<span data-ttu-id="13ec5-131">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="13ec5-131">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="13ec5-132">Escribir la Ayuda de módulos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="13ec5-132">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="13ec5-133">Escribir un proveedor de Windows Powershell</span><span class="sxs-lookup"><span data-stu-id="13ec5-133">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="13ec5-134">Referencia de API de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="13ec5-134">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0)

[<span data-ttu-id="13ec5-135">Referencia de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="13ec5-135">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)