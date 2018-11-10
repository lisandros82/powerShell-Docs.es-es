---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Introducción a la Galería de PowerShell
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225682"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="de7b5-103">Introducción a la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="de7b5-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="de7b5-104">La manera adecuada para instalar paquetes desde la Galería de PowerShell es usar los cmdlets en el módulo [PowerShellGet](/powershell/module/powershellget).</span><span class="sxs-lookup"><span data-stu-id="de7b5-104">The proper way to install packages from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="de7b5-105">No es necesario iniciar sesión para descargar los elementos de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de7b5-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="de7b5-106">Es posible descargar un paquete desde la Galería de PowerShell directamente, pero este no es un enfoque recomendado.</span><span class="sxs-lookup"><span data-stu-id="de7b5-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span>
> <span data-ttu-id="de7b5-107">Para más información, vea [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download) (Descargar paquete de forma manual).</span><span class="sxs-lookup"><span data-stu-id="de7b5-107">For more details, see [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="de7b5-108">Detectar paquetes de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="de7b5-108">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="de7b5-109">Puede buscar paquetes en la Galería de PowerShell mediante el control de **búsqueda** en este sitio web o la exploración de las páginas Scripts y Módulos.</span><span class="sxs-lookup"><span data-stu-id="de7b5-109">You can find packages in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="de7b5-110">También puede buscar paquetes de la Galería de PowerShell al ejecutar los cmdlets [Find-Module][] y [Find-Script][], en función del tipo de paquete, con `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="de7b5-110">You can also find packages from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="de7b5-111">Puede filtrar los resultados de la Galería mediante los siguientes parámetros:</span><span class="sxs-lookup"><span data-stu-id="de7b5-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="de7b5-112">Nombre</span><span class="sxs-lookup"><span data-stu-id="de7b5-112">Name</span></span>
- <span data-ttu-id="de7b5-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="de7b5-113">AllVersions</span></span>
- <span data-ttu-id="de7b5-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="de7b5-114">MinimumVersion</span></span>
- <span data-ttu-id="de7b5-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="de7b5-115">RequiredVersion</span></span>
- <span data-ttu-id="de7b5-116">Etiqueta</span><span class="sxs-lookup"><span data-stu-id="de7b5-116">Tag</span></span>
- <span data-ttu-id="de7b5-117">Includes</span><span class="sxs-lookup"><span data-stu-id="de7b5-117">Includes</span></span>
- <span data-ttu-id="de7b5-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="de7b5-118">DscResource</span></span>
- <span data-ttu-id="de7b5-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="de7b5-119">RoleCapability</span></span>
- <span data-ttu-id="de7b5-120">Comando</span><span class="sxs-lookup"><span data-stu-id="de7b5-120">Command</span></span>
- <span data-ttu-id="de7b5-121">Filtro</span><span class="sxs-lookup"><span data-stu-id="de7b5-121">Filter</span></span>

<span data-ttu-id="de7b5-122">Si solo le interesa detectar recursos de DSC específicos en la Galería, puede ejecutar el cmdlet [Find-DscResource].</span><span class="sxs-lookup"><span data-stu-id="de7b5-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="de7b5-123">Find-DscResource devuelve datos sobre los recursos de DSC contenidos en la Galería.</span><span class="sxs-lookup"><span data-stu-id="de7b5-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="de7b5-124">Dado que los recursos de DSC siempre se entregan como parte de un módulo, debe ejecutar [Install-Module][] para instalar dichos recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="de7b5-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="de7b5-125">Obtener información sobre los paquetes de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="de7b5-125">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="de7b5-126">Una vez identificado un paquete de su interés, tal vez quiera obtener más información.</span><span class="sxs-lookup"><span data-stu-id="de7b5-126">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="de7b5-127">Puede hacerlo examinando la página específica de ese paquete en la Galería.</span><span class="sxs-lookup"><span data-stu-id="de7b5-127">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="de7b5-128">En la página, podrá ver todos los metadatos cargados con el paquete.</span><span class="sxs-lookup"><span data-stu-id="de7b5-128">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="de7b5-129">El autor del paquete es quien proporciona estos metadatos, que Microsoft no comprueba.</span><span class="sxs-lookup"><span data-stu-id="de7b5-129">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="de7b5-130">El propietario del paquete está estrechamente ligado a la cuenta de la Galería que se usa para publicar el paquete, y es más confiable que el campo Autor.</span><span class="sxs-lookup"><span data-stu-id="de7b5-130">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="de7b5-131">Si cree que un paquete no se ha publicado de buena fe, haga clic en **Notificar abuso** en la página de ese paquete.</span><span class="sxs-lookup"><span data-stu-id="de7b5-131">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="de7b5-132">Si está ejecutando [Find-Module][] o [Find-Script][], puede ver estos datos en el objeto PSGetModuleInfo devuelto.</span><span class="sxs-lookup"><span data-stu-id="de7b5-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="de7b5-133">Por ejemplo, la ejecución de `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="de7b5-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="de7b5-134">devuelve datos en el módulo PSReadLine de la galería.</span><span class="sxs-lookup"><span data-stu-id="de7b5-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="de7b5-135">Descargar paquetes de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="de7b5-135">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="de7b5-136">Se recomienda el proceso siguiente al descargar paquetes de la Galería de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="de7b5-136">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="de7b5-137">Inspeccionar</span><span class="sxs-lookup"><span data-stu-id="de7b5-137">Inspect</span></span>

<span data-ttu-id="de7b5-138">Para descargar un paquete de la Galería para su inspección, ejecute el cmdlet [Save-Module][] o [Save-Script][], en función del tipo de paquete.</span><span class="sxs-lookup"><span data-stu-id="de7b5-138">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="de7b5-139">Esto le permite guardar el paquete localmente sin instalarlo e inspeccionar su contenido.</span><span class="sxs-lookup"><span data-stu-id="de7b5-139">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="de7b5-140">Recuerde eliminar el paquete guardado manualmente.</span><span class="sxs-lookup"><span data-stu-id="de7b5-140">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="de7b5-141">Algunos de estos paquetes los crea Microsoft y otros los crea la comunidad de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de7b5-141">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="de7b5-142">Microsoft recomienda que se revisen el contenido y el código de los paquetes de esta Galería antes de la instalación.</span><span class="sxs-lookup"><span data-stu-id="de7b5-142">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="de7b5-143">Si cree que un paquete no se ha publicado de buena fe, haga clic en **Notificar abuso** en la página de ese paquete.</span><span class="sxs-lookup"><span data-stu-id="de7b5-143">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="de7b5-144">Instalar</span><span class="sxs-lookup"><span data-stu-id="de7b5-144">Install</span></span>

<span data-ttu-id="de7b5-145">Para instalar un paquete desde la Galería para su uso, ejecute el cmdlet [Install-Module][] o [Install-Script][], en función del tipo de paquete.</span><span class="sxs-lookup"><span data-stu-id="de7b5-145">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="de7b5-146">[Install-Module][] instala el módulo en `$env:ProgramFiles\WindowsPowerShell\Modules` de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="de7b5-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="de7b5-147">Para ello es necesaria una cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="de7b5-147">This requires an administrator account.</span></span> <span data-ttu-id="de7b5-148">Si agrega el parámetro `-Scope CurrentUser`, el módulo se instala en `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="de7b5-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="de7b5-149">[Install-Script][] instala el script en `$env:ProgramFiles\WindowsPowerShell\Scripts` de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="de7b5-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="de7b5-150">Para ello es necesaria una cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="de7b5-150">This requires an administrator account.</span></span> <span data-ttu-id="de7b5-151">Si agrega el parámetro `-Scope CurrentUser`, el script se instala en `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.</span><span class="sxs-lookup"><span data-stu-id="de7b5-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="de7b5-152">De forma predeterminada, [Install-Module][] e [Install-Script][] instalan la última versión de un paquete.</span><span class="sxs-lookup"><span data-stu-id="de7b5-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span>
<span data-ttu-id="de7b5-153">Para instalar una versión anterior del paquete, agregue el parámetro `-RequiredVersion`.</span><span class="sxs-lookup"><span data-stu-id="de7b5-153">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="de7b5-154">Implementar</span><span class="sxs-lookup"><span data-stu-id="de7b5-154">Deploy</span></span>

<span data-ttu-id="de7b5-155">Para implementar un paquete desde la Galería de PowerShell en Azure Automation, haga clic en **Deploy to Azure Automation** (Implementar en Azure Automation) en la página de detalles del paquete.</span><span class="sxs-lookup"><span data-stu-id="de7b5-155">To deploy a package from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="de7b5-156">Se le redirigirá al Portal de administración de Azure, donde deberá iniciar sesión con sus credenciales de la cuenta de Azure.</span><span class="sxs-lookup"><span data-stu-id="de7b5-156">You will be redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="de7b5-157">Tenga en cuenta que si se implementan paquetes con dependencias, se implementarán todas las dependencias en Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="de7b5-157">Note that deploying packages with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="de7b5-158">El botón Deploy to Azure Automation (Implementar en Azure Automation) se puede deshabilitar mediante la adición de la etiqueta **AzureAutomationNotSupported** a los metadatos del paquete.</span><span class="sxs-lookup"><span data-stu-id="de7b5-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="de7b5-159">Para obtener más información sobre Azure Automation, consulte la documentación de [Azure Automation](/azure/automation).</span><span class="sxs-lookup"><span data-stu-id="de7b5-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="de7b5-160">Actualizar paquetes desde la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="de7b5-160">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="de7b5-161">Para actualizar paquetes instalados desde la Galería de PowerShell, ejecute los cmdlets [Update-Module][] o [Update-Script][].</span><span class="sxs-lookup"><span data-stu-id="de7b5-161">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="de7b5-162">Cuando se ejecuta sin parámetros adicionales, [Update-Module][] intenta actualizar cada módulo instalado mediante la ejecución de [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="de7b5-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="de7b5-163">Para actualizar módulos de forma selectiva, agregue el parámetro `-Name`.</span><span class="sxs-lookup"><span data-stu-id="de7b5-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="de7b5-164">Del mismo modo, cuando se ejecuta sin parámetros adicionales, [Update-Script][] también intenta actualizar cada script instalado mediante la ejecución de [Install-Script][].</span><span class="sxs-lookup"><span data-stu-id="de7b5-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="de7b5-165">Para actualizar scripts de forma selectiva, agregue el parámetro `-Name`.</span><span class="sxs-lookup"><span data-stu-id="de7b5-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="de7b5-166">Enumerar los paquetes instalados desde la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="de7b5-166">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="de7b5-167">Para averiguar qué módulos ha instalado desde la Galería de PowerShell, ejecute el cmdlet [Get-InstalledModule][].</span><span class="sxs-lookup"><span data-stu-id="de7b5-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="de7b5-168">Este comando enumera todos los módulos del sistema que se instalaron directamente desde la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de7b5-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="de7b5-169">Del mismo modo, para averiguar qué scripts ha instalado desde la Galería de PowerShell, ejecute el cmdlet [Get-InstalledScript][].</span><span class="sxs-lookup"><span data-stu-id="de7b5-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="de7b5-170">Este comando enumera todos los scripts del sistema que se instalaron directamente desde la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de7b5-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
