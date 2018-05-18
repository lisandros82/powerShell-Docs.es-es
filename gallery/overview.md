---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Galería de PowerShell
ms.openlocfilehash: cffb2f0182ffe9072f9fbbc7f4cdfcf28de276db
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="96ff9-103">Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="96ff9-103">The PowerShell Gallery</span></span>

<span data-ttu-id="96ff9-104">La Galería de PowerShell es el repositorio central del contenido de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96ff9-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="96ff9-105">En ella, encontrará módulos útiles de PowerShell que contienen comandos de PowerShell y los recursos de configuración de estado deseado (DSC).</span><span class="sxs-lookup"><span data-stu-id="96ff9-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="96ff9-106">También encontrará scripts de PowerShell (algunos de los cuales pueden contener flujos de trabajo de PowerShell), que describen un conjunto de tareas y proporcionan la secuenciación de dichas tareas.</span><span class="sxs-lookup"><span data-stu-id="96ff9-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="96ff9-107">Algunos de estos elementos son creación de Microsoft y otros son creación de la comunidad de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96ff9-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="96ff9-108">Información general de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="96ff9-108">PowerShellGet Overview</span></span>

<span data-ttu-id="96ff9-109">El módulo PowerShellGet contiene cmdlets para detectar, instalar, actualizar y publicar los artefactos de PowerShell como módulos, recursos de DSC, funcionalidades de rol y scripts desde la [Galería de PowerShell](https://www.PowerShellGallery.com) y otros repositorios privados.</span><span class="sxs-lookup"><span data-stu-id="96ff9-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="96ff9-110">Introducción a la Galería</span><span class="sxs-lookup"><span data-stu-id="96ff9-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="96ff9-111">Para instalar elementos de la Galería es necesaria la versión más reciente del módulo PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="96ff9-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="96ff9-112">Vea [Instalación de PowerShellGet](installing-psget.md) para ver las instrucciones completas.</span><span class="sxs-lookup"><span data-stu-id="96ff9-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="96ff9-113">Consulte la página [Introducción](getting-started.md) para obtener más información sobre el uso de comandos PowerShellGet con la Galería.</span><span class="sxs-lookup"><span data-stu-id="96ff9-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="96ff9-114">También puede ejecutar *Update-Help -Module PowerShellGet* para instalar la Ayuda local para estos comandos.</span><span class="sxs-lookup"><span data-stu-id="96ff9-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="96ff9-115">Sistemas operativos compatibles</span><span class="sxs-lookup"><span data-stu-id="96ff9-115">Supported Operating Systems</span></span>

<span data-ttu-id="96ff9-116">El módulo **PowerShellGet** requiere **PowerShell 3.0 o posterior**.</span><span class="sxs-lookup"><span data-stu-id="96ff9-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="96ff9-117">Por lo tanto, **PowerShellGet** requiere uno de los siguientes sistemas operativos:</span><span class="sxs-lookup"><span data-stu-id="96ff9-117">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="96ff9-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="96ff9-118">Windows 10</span></span>
- <span data-ttu-id="96ff9-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="96ff9-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="96ff9-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="96ff9-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="96ff9-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="96ff9-121">Windows 7 SP1</span></span>
- <span data-ttu-id="96ff9-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="96ff9-122">Windows Server 2016</span></span>
- <span data-ttu-id="96ff9-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="96ff9-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="96ff9-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="96ff9-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="96ff9-125">**PowerShellGet** también requiere .NET Framework 4.5 o una versión posterior.</span><span class="sxs-lookup"><span data-stu-id="96ff9-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="96ff9-126">Puede instalar .NET Framework 4.5 o posterior desde [aquí](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="96ff9-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="96ff9-127">¿Tiene alguna pregunta?</span><span class="sxs-lookup"><span data-stu-id="96ff9-127">Got a question?</span></span> <span data-ttu-id="96ff9-128">¿Tiene comentarios?</span><span class="sxs-lookup"><span data-stu-id="96ff9-128">Have feedback?</span></span>

<span data-ttu-id="96ff9-129">Encontrará más información sobre la Galería de PowerShell y PowerShellGet en la página [Introducción](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="96ff9-129">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="96ff9-130">Proporcione comentarios e informe de problemas mediante [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="96ff9-130">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>