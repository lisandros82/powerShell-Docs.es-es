---
title: Estado de sesión de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369104"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="51c03-102">Estado de sesión de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="51c03-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="51c03-103">El estado de sesión hace referencia a la configuración actual de un módulo o sesión de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51c03-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="51c03-104">Una sesión de Windows PowerShell es el entorno operativo que usa el usuario de línea de comandos de forma interactiva o mediante programación para una aplicación host.</span><span class="sxs-lookup"><span data-stu-id="51c03-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="51c03-105">El estado de sesión de una sesión se conoce como estado de sesión global.</span><span class="sxs-lookup"><span data-stu-id="51c03-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="51c03-106">Desde la perspectiva del desarrollador, una sesión de Windows PowerShell se refiere al tiempo entre el momento en que una aplicación host abre un espacio de ejecución de Windows PowerShell y cuando cierra el espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="51c03-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="51c03-107">En otra forma, la sesión es la duración de una instancia del motor de Windows PowerShell que se invoca mientras existe el espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="51c03-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="51c03-108">Estado de sesión del módulo</span><span class="sxs-lookup"><span data-stu-id="51c03-108">Module Session State</span></span>

<span data-ttu-id="51c03-109">Los Estados de la sesión del módulo se crean cada vez que el módulo o uno de sus módulos anidados se importa en la sesión.</span><span class="sxs-lookup"><span data-stu-id="51c03-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="51c03-110">Cuando un módulo exporta un elemento, como un cmdlet, una función o un script, se agrega una referencia a ese elemento al estado de sesión global de la sesión.</span><span class="sxs-lookup"><span data-stu-id="51c03-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="51c03-111">Sin embargo, cuando se ejecuta el elemento, se ejecuta en el estado de sesión del módulo.</span><span class="sxs-lookup"><span data-stu-id="51c03-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="51c03-112">Datos de estado de sesión</span><span class="sxs-lookup"><span data-stu-id="51c03-112">Session-State Data</span></span>

<span data-ttu-id="51c03-113">Los datos de estado de sesión pueden ser públicos o privados.</span><span class="sxs-lookup"><span data-stu-id="51c03-113">Session state data can be public or private.</span></span> <span data-ttu-id="51c03-114">Los datos públicos están disponibles para las llamadas desde fuera del estado de sesión mientras que los datos privados solo están disponibles para las llamadas desde el estado de sesión.</span><span class="sxs-lookup"><span data-stu-id="51c03-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="51c03-115">Por ejemplo, un módulo puede tener una función privada a la que solo puede llamar el módulo o que solo un elemento público que se ha exportado internamente.</span><span class="sxs-lookup"><span data-stu-id="51c03-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="51c03-116">Esto es similar a los miembros públicos y privados de un tipo de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51c03-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="51c03-117">Los datos de estado de sesión se almacenan en la instancia actual del motor de ejecución en el contexto de la sesión actual de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51c03-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="51c03-118">Los datos de estado de sesión se componen de los siguientes elementos:</span><span class="sxs-lookup"><span data-stu-id="51c03-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="51c03-119">Información de ruta de acceso</span><span class="sxs-lookup"><span data-stu-id="51c03-119">Path information</span></span>

- <span data-ttu-id="51c03-120">Información de la unidad</span><span class="sxs-lookup"><span data-stu-id="51c03-120">Drive information</span></span>

- <span data-ttu-id="51c03-121">Información del proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="51c03-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="51c03-122">Información sobre los módulos importados y las referencias a los elementos de módulo (como cmdlets, funciones y scripts) que exporta el módulo.</span><span class="sxs-lookup"><span data-stu-id="51c03-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="51c03-123">Esta información y estas referencias solo son para el estado de sesión global.</span><span class="sxs-lookup"><span data-stu-id="51c03-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="51c03-124">Información de variable de estado de sesión</span><span class="sxs-lookup"><span data-stu-id="51c03-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="51c03-125">Obtener acceso a los datos de estado de sesión en cmdlets</span><span class="sxs-lookup"><span data-stu-id="51c03-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="51c03-126">Los cmdlets pueden tener acceso indirectamente a los datos de estado de sesión a través de la propiedad [System. Management. Automation. PSCmdlet. SessionState \*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) de la clase de cmdlet o directamente a través de la clase [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) .</span><span class="sxs-lookup"><span data-stu-id="51c03-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="51c03-127">La clase [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) proporciona propiedades que se pueden utilizar para investigar distintos tipos de datos de estado de sesión.</span><span class="sxs-lookup"><span data-stu-id="51c03-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="51c03-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="51c03-128">See Also</span></span>

[<span data-ttu-id="51c03-129">System. Management. Automation. PSCmdlet. SessionState</span><span class="sxs-lookup"><span data-stu-id="51c03-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="51c03-130">System. Management. Automation. SessionState? Displayproperty = FullName</span><span class="sxs-lookup"><span data-stu-id="51c03-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="51c03-131">Cmdlets de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="51c03-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="51c03-132">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="51c03-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="51c03-133">SDK de Windows PowerShell Shell</span><span class="sxs-lookup"><span data-stu-id="51c03-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
