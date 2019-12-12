---
title: Conceptos de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 6/12/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: 4410b1f9c80afefd5479fa68154f9947b805edcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366684"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="af5ce-102">Conceptos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="af5ce-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="af5ce-103">Esta sección contiene información conceptual que le ayudará a comprender PowerShell desde el punto de vista de un desarrollador.</span><span class="sxs-lookup"><span data-stu-id="af5ce-103">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="af5ce-104">Nombre del tema</span><span class="sxs-lookup"><span data-stu-id="af5ce-104">Topic Name</span></span>|<span data-ttu-id="af5ce-105">Descripción</span><span class="sxs-lookup"><span data-stu-id="af5ce-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="af5ce-106">about_Objects</span><span class="sxs-lookup"><span data-stu-id="af5ce-106">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="af5ce-107">Descripción de los objetos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="af5ce-107">Description of PowerShell objects.</span></span> <span data-ttu-id="af5ce-108">Para obtener más información, vea [acerca de la creación de objetos](/powershell/module/microsoft.powershell.core/about/about_object_creation) .</span><span class="sxs-lookup"><span data-stu-id="af5ce-108">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="af5ce-109">Crear espacios de espacios</span><span class="sxs-lookup"><span data-stu-id="af5ce-109">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="af5ce-110">Los entornos operativos en los que se procesan los comandos.</span><span class="sxs-lookup"><span data-stu-id="af5ce-110">The operating environments where commands are processed.</span></span> <span data-ttu-id="af5ce-111">Para obtener más información, vea [Runspace (clase](/dotnet/api/system.management.automation.runspaces.runspace)).</span><span class="sxs-lookup"><span data-stu-id="af5ce-111">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="af5ce-112">Extender objetos de salida</span><span class="sxs-lookup"><span data-stu-id="af5ce-112">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="af5ce-113">Cómo extender objetos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="af5ce-113">How to extend PowerShell objects.</span></span> <span data-ttu-id="af5ce-114">Para obtener más información, vea [About Types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="af5ce-114">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="af5ce-115">Registrar cmdlets</span><span class="sxs-lookup"><span data-stu-id="af5ce-115">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="af5ce-116">Cómo hacer que los módulos y complementos estén disponibles en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="af5ce-116">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="af5ce-117">Para obtener más información, consulte [módulos y complementos](../cmdlet/modules-and-snap-ins.md).</span><span class="sxs-lookup"><span data-stu-id="af5ce-117">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="af5ce-118">Solicitar confirmación de cmdlets</span><span class="sxs-lookup"><span data-stu-id="af5ce-118">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="af5ce-119">Cómo los cmdlets y los proveedores solicitan comentarios al usuario antes de que se realice una acción.</span><span class="sxs-lookup"><span data-stu-id="af5ce-119">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="af5ce-120">Clase RuntimeDefinedParameter</span><span class="sxs-lookup"><span data-stu-id="af5ce-120">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="af5ce-121">Declaraciones de parámetros en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="af5ce-121">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="af5ce-122">Espacio de nombres System. Management. Automation</span><span class="sxs-lookup"><span data-stu-id="af5ce-122">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="af5ce-123">Información general sobre los espacios de nombres de la API de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="af5ce-123">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="af5ce-124">Información general del proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="af5ce-124">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="af5ce-125">Información general sobre los proveedores de PowerShell que se usan para tener acceso a los almacenes de datos.</span><span class="sxs-lookup"><span data-stu-id="af5ce-125">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="af5ce-126">Escribir ayuda para cmdlets de PowerShell</span><span class="sxs-lookup"><span data-stu-id="af5ce-126">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="af5ce-127">Cómo escribir la ayuda de los cmdlets de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="af5ce-127">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="af5ce-128">Consulta también</span><span class="sxs-lookup"><span data-stu-id="af5ce-128">See also</span></span>

[<span data-ttu-id="af5ce-129">Clase de PowerShell</span><span class="sxs-lookup"><span data-stu-id="af5ce-129">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="af5ce-130">Referencia de la API principal de PowerShell</span><span class="sxs-lookup"><span data-stu-id="af5ce-130">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0)

[<span data-ttu-id="af5ce-131">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="af5ce-131">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="af5ce-132">Escribir ayuda para módulos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="af5ce-132">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="af5ce-133">Escribir un proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="af5ce-133">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="af5ce-134">Referencia de la API de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="af5ce-134">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0)

[<span data-ttu-id="af5ce-135">Referencia de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="af5ce-135">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)