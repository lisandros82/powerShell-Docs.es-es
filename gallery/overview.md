---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Galería de PowerShell
ms.openlocfilehash: dc7e8dd7e4d96d8424a62cb3256c3164b63a3684
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482937"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="df496-103">Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="df496-103">The PowerShell Gallery</span></span>

<span data-ttu-id="df496-104">La Galería de PowerShell es el repositorio central del contenido de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df496-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="df496-105">En ella, encontrará módulos útiles de PowerShell que contienen comandos de PowerShell y los recursos de configuración de estado deseado (DSC).</span><span class="sxs-lookup"><span data-stu-id="df496-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="df496-106">También encontrará scripts de PowerShell (algunos de los cuales pueden contener flujos de trabajo de PowerShell), que describen un conjunto de tareas y proporcionan la secuenciación de dichas tareas.</span><span class="sxs-lookup"><span data-stu-id="df496-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="df496-107">Algunos de estos elementos son creación de Microsoft y otros son creación de la comunidad de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df496-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="df496-108">Información general de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="df496-108">PowerShellGet Overview</span></span>

<span data-ttu-id="df496-109">El módulo PowerShellGet contiene cmdlets para detectar, instalar, actualizar y publicar los artefactos de PowerShell como módulos, recursos de DSC, funcionalidades de rol y scripts desde la [Galería de PowerShell](https://www.PowerShellGallery.com) y otros repositorios privados.</span><span class="sxs-lookup"><span data-stu-id="df496-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="df496-110">Introducción a la Galería</span><span class="sxs-lookup"><span data-stu-id="df496-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="df496-111">Para instalar elementos de la Galería es necesaria la versión más reciente del módulo PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="df496-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="df496-112">Vea [Instalación de PowerShellGet](installing-psget.md) para ver las instrucciones completas.</span><span class="sxs-lookup"><span data-stu-id="df496-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="df496-113">Consulte la página [Introducción](getting-started.md) para obtener más información sobre el uso de comandos PowerShellGet con la Galería.</span><span class="sxs-lookup"><span data-stu-id="df496-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="df496-114">También puede ejecutar *Update-Help -Module PowerShellGet* para instalar la Ayuda local para estos comandos.</span><span class="sxs-lookup"><span data-stu-id="df496-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="df496-115">Sistemas operativos compatibles</span><span class="sxs-lookup"><span data-stu-id="df496-115">Supported Operating Systems</span></span>

<span data-ttu-id="df496-116">El módulo **PowerShellGet** requiere **Windows PowerShell 3.0 o posterior**, o bien **PowerShell Core 6.0 o posterior**.</span><span class="sxs-lookup"><span data-stu-id="df496-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="df496-117">Una versión adecuada de **Windows PowerShell** está disponible para estos sistemas operativos:</span><span class="sxs-lookup"><span data-stu-id="df496-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="df496-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="df496-118">Windows 10</span></span>
- <span data-ttu-id="df496-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="df496-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="df496-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="df496-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="df496-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="df496-121">Windows 7 SP1</span></span>
- <span data-ttu-id="df496-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="df496-122">Windows Server 2016</span></span>
- <span data-ttu-id="df496-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="df496-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="df496-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="df496-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="df496-125">**PowerShellGet** también requiere .NET Framework 4.5 o una versión posterior.</span><span class="sxs-lookup"><span data-stu-id="df496-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="df496-126">Puede instalar .NET Framework 4.5 o posterior desde [aquí](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="df496-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="df496-127">**PowerShell Core** admite muchos sistemas operativos.</span><span class="sxs-lookup"><span data-stu-id="df496-127">**PowerShell Core** supports many operating systems.</span></span> <span data-ttu-id="df496-128">Consulte [este artículo](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) para ver una lista completa.</span><span class="sxs-lookup"><span data-stu-id="df496-128">See [this article](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) for a full list.</span></span>

<span data-ttu-id="df496-129">Muchos módulos hospedados en la galería admitirán diferentes sistemas operativos y tendrán requisitos adicionales.</span><span class="sxs-lookup"><span data-stu-id="df496-129">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="df496-130">Consulte la documentación de los módulos para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="df496-130">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="df496-131">¿Tiene alguna pregunta?</span><span class="sxs-lookup"><span data-stu-id="df496-131">Got a question?</span></span> <span data-ttu-id="df496-132">¿Tiene comentarios?</span><span class="sxs-lookup"><span data-stu-id="df496-132">Have feedback?</span></span>

<span data-ttu-id="df496-133">Encontrará más información sobre la Galería de PowerShell y PowerShellGet en la página [Introducción](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="df496-133">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="df496-134">Proporcione comentarios e informe de problemas mediante [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="df496-134">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
