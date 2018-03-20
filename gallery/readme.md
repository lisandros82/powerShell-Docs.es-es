---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery,psget
title: "Galería de PowerShell"
ms.openlocfilehash: 7389ce8286c515b0bfc25f32634a482b060cb74c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="a02b8-103">Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a02b8-103">The PowerShell Gallery</span></span>

<span data-ttu-id="a02b8-104">La Galería de PowerShell es el repositorio central del contenido de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a02b8-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="a02b8-105">En la Galería encontrará nuevos comandos de PowerShell o recursos de configuración de estado deseado (DSC).</span><span class="sxs-lookup"><span data-stu-id="a02b8-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="a02b8-106">Información general de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a02b8-106">PowerShellGet Overview</span></span>

<span data-ttu-id="a02b8-107">El módulo PowerShellGet contiene cmdlets para detectar, instalar, actualizar y publicar los artefactos de PowerShell como módulos, recursos de DSC, funcionalidades de rol y scripts desde la [Galería de PowerShell](https://www.PowerShellGallery.com) y otros repositorios privados.</span><span class="sxs-lookup"><span data-stu-id="a02b8-107">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="a02b8-108">Introducción a la Galería</span><span class="sxs-lookup"><span data-stu-id="a02b8-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="a02b8-109">Para instalar elementos desde la Galería se requiere la versión más reciente del módulo PowerShellGet, que está disponible en Windows 10, en Windows Management Framework (WMF) 5.0 o en el programa de instalación basado en MSI (para PowerShell 3 y 4).</span><span class="sxs-lookup"><span data-stu-id="a02b8-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="a02b8-110">[**Obtener Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span><span class="sxs-lookup"><span data-stu-id="a02b8-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="a02b8-111">[**Obtener WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175) u</span><span class="sxs-lookup"><span data-stu-id="a02b8-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="a02b8-112">**Obtener el instalador MSI**</span><span class="sxs-lookup"><span data-stu-id="a02b8-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="a02b8-113">Con la última versión del módulo [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), puede:</span><span class="sxs-lookup"><span data-stu-id="a02b8-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="a02b8-114">Buscar elementos en la Galería con [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) y [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span><span class="sxs-lookup"><span data-stu-id="a02b8-114">Search through items in the Gallery with [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span></span>
-   <span data-ttu-id="a02b8-115">Guardar los elementos en el sistema desde la Galería con [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) y [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span><span class="sxs-lookup"><span data-stu-id="a02b8-115">Save items to your system from the Gallery with [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) and [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span></span>
-   <span data-ttu-id="a02b8-116">Instalar elementos desde la Galería con [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) e [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span><span class="sxs-lookup"><span data-stu-id="a02b8-116">Install items from the Gallery with [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) and [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span></span>
-   <span data-ttu-id="a02b8-117">Cargar elementos en la Galería con [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) y [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span><span class="sxs-lookup"><span data-stu-id="a02b8-117">Upload items to the Gallery with [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) and [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span></span>
-   <span data-ttu-id="a02b8-118">Agregue su propio repositorio personalizado con [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span><span class="sxs-lookup"><span data-stu-id="a02b8-118">Add your own custom repository with [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span></span>

<span data-ttu-id="a02b8-119">Consulte la página [Introducción](psgallery/psgallery_gettingstarted.md) para obtener más información sobre el uso de comandos PowerShellGet con la Galería.</span><span class="sxs-lookup"><span data-stu-id="a02b8-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="a02b8-120">También puede ejecutar *Update-Help -Module PowerShellGet* para instalar la Ayuda local para estos comandos.</span><span class="sxs-lookup"><span data-stu-id="a02b8-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="a02b8-121">Sistemas operativos compatibles</span><span class="sxs-lookup"><span data-stu-id="a02b8-121">Supported Operating Systems</span></span>

<span data-ttu-id="a02b8-122">El módulo **PowerShellGet** requiere **PowerShell 3.0 o posterior**.</span><span class="sxs-lookup"><span data-stu-id="a02b8-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="a02b8-123">Por lo tanto, **PowerShellGet** requiere uno de los siguientes sistemas operativos:</span><span class="sxs-lookup"><span data-stu-id="a02b8-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="a02b8-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="a02b8-124">Windows 10</span></span>
- <span data-ttu-id="a02b8-125">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="a02b8-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="a02b8-126">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="a02b8-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="a02b8-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="a02b8-127">Windows 7 SP1</span></span>
- <span data-ttu-id="a02b8-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="a02b8-128">Windows Server 2016</span></span>
- <span data-ttu-id="a02b8-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a02b8-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="a02b8-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="a02b8-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="a02b8-131">**PowerShellGet** también requiere .NET Framework 4.5 o posterior.</span><span class="sxs-lookup"><span data-stu-id="a02b8-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="a02b8-132">Puede instalar .NET Framework 4.5 o posterior desde [aquí](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="a02b8-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="a02b8-133">¿Tiene alguna pregunta?</span><span class="sxs-lookup"><span data-stu-id="a02b8-133">Got a question?</span></span> <span data-ttu-id="a02b8-134">¿Tiene comentarios?</span><span class="sxs-lookup"><span data-stu-id="a02b8-134">Have feedback?</span></span>

<span data-ttu-id="a02b8-135">Encontrará más información sobre la Galería de PowerShell y PowerShellGet en la página [Introducción](psgallery/psgallery_gettingstarted.md).</span><span class="sxs-lookup"><span data-stu-id="a02b8-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="a02b8-136">Proporcione comentarios e informe de problemas mediante [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="a02b8-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>

