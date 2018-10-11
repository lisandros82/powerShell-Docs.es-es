---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Introducción a la Galería de PowerShell
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523066"
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="84679-103">Introducción a la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="84679-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="84679-104">La manera adecuada para instalar elementos desde la Galería de PowerShell es usar los cmdlets en el módulo [PowerShellGet](/powershell/module/powershellget).</span><span class="sxs-lookup"><span data-stu-id="84679-104">The proper way to install items from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="84679-105">No es necesario iniciar sesión para descargar los elementos de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="84679-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="84679-106">Es posible descargar un paquete desde la Galería de PowerShell directamente, pero este no es un enfoque recomendado.</span><span class="sxs-lookup"><span data-stu-id="84679-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span> <span data-ttu-id="84679-107">Para más información, vea [Manual Package Download](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md) (Descargar paquete de forma manual).</span><span class="sxs-lookup"><span data-stu-id="84679-107">For more details, see [Manual Package Download](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).</span></span>  


## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="84679-108">Detectar elementos de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="84679-108">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="84679-109">Puede buscar elementos en la Galería de PowerShell mediante el control de **búsqueda** en este sitio web o la examinación de las páginas Scripts y Módulos.</span><span class="sxs-lookup"><span data-stu-id="84679-109">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="84679-110">También puede buscar elementos de la Galería de PowerShell al ejecutar los cmdlets [Find-Module][] y [Find-Script][], en función del tipo de elemento, con `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="84679-110">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="84679-111">Puede filtrar los resultados de la Galería mediante los siguientes parámetros:</span><span class="sxs-lookup"><span data-stu-id="84679-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="84679-112">Nombre</span><span class="sxs-lookup"><span data-stu-id="84679-112">Name</span></span>
- <span data-ttu-id="84679-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="84679-113">AllVersions</span></span>
- <span data-ttu-id="84679-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="84679-114">MinimumVersion</span></span>
- <span data-ttu-id="84679-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="84679-115">RequiredVersion</span></span>
- <span data-ttu-id="84679-116">Etiqueta</span><span class="sxs-lookup"><span data-stu-id="84679-116">Tag</span></span>
- <span data-ttu-id="84679-117">Includes</span><span class="sxs-lookup"><span data-stu-id="84679-117">Includes</span></span>
- <span data-ttu-id="84679-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="84679-118">DscResource</span></span>
- <span data-ttu-id="84679-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="84679-119">RoleCapability</span></span>
- <span data-ttu-id="84679-120">Comando</span><span class="sxs-lookup"><span data-stu-id="84679-120">Command</span></span>
- <span data-ttu-id="84679-121">Filtro</span><span class="sxs-lookup"><span data-stu-id="84679-121">Filter</span></span>

<span data-ttu-id="84679-122">Si solo le interesa detectar recursos de DSC específicos en la Galería, puede ejecutar el cmdlet [Find-DscResource].</span><span class="sxs-lookup"><span data-stu-id="84679-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="84679-123">Find-DscResource devuelve datos sobre los recursos de DSC contenidos en la Galería.</span><span class="sxs-lookup"><span data-stu-id="84679-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="84679-124">Dado que los recursos de DSC siempre se entregan como parte de un módulo, debe ejecutar [Install-Module][] para instalar dichos recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="84679-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="84679-125">Obtener información sobre los elementos de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="84679-125">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="84679-126">Una vez que haya identificado el elemento que le interesa, tal vez quiera obtener más información.</span><span class="sxs-lookup"><span data-stu-id="84679-126">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="84679-127">Puede hacerlo examinando la página específica de ese elemento en la Galería.</span><span class="sxs-lookup"><span data-stu-id="84679-127">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="84679-128">En la página, podrá ver todos los metadatos cargados con el elemento.</span><span class="sxs-lookup"><span data-stu-id="84679-128">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="84679-129">El autor del elemento es quien proporciona estos metadatos del elemento, que Microsoft no comprueba.</span><span class="sxs-lookup"><span data-stu-id="84679-129">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="84679-130">El propietario del elemento está estrechamente ligado a la cuenta de la Galería que se usa para publicar el elemento, y es más confiable que el campo Autor.</span><span class="sxs-lookup"><span data-stu-id="84679-130">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="84679-131">Si cree que un elemento no se ha publicado de buena fe, haga clic en **Notificar abuso** en la página de ese elemento.</span><span class="sxs-lookup"><span data-stu-id="84679-131">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="84679-132">Si está ejecutando [Find-Module][] o [Find-Script][], puede ver estos datos en el objeto PSGetModuleInfo devuelto.</span><span class="sxs-lookup"><span data-stu-id="84679-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="84679-133">Por ejemplo, la ejecución de `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="84679-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="84679-134">devuelve datos en el módulo PSReadLine de la galería.</span><span class="sxs-lookup"><span data-stu-id="84679-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="84679-135">Descargar elementos de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="84679-135">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="84679-136">Se recomienda el proceso siguiente al descargar elementos de la Galería de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="84679-136">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="84679-137">Inspeccionar</span><span class="sxs-lookup"><span data-stu-id="84679-137">Inspect</span></span>

<span data-ttu-id="84679-138">Para descargar un elemento de la Galería para su inspección, ejecute el cmdlet [Save-Module][] o [Save-Script][], en función del tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="84679-138">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="84679-139">Esto le permite guardar el elemento localmente sin instalarlo e inspeccionar su contenido.</span><span class="sxs-lookup"><span data-stu-id="84679-139">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="84679-140">Recuerde eliminar el elemento guardado manualmente.</span><span class="sxs-lookup"><span data-stu-id="84679-140">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="84679-141">Algunos de estos elementos son creación de Microsoft y otros son creación de la comunidad de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="84679-141">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="84679-142">Microsoft recomienda que se revisen el contenido y el código de los elementos de esta Galería antes de la instalación.</span><span class="sxs-lookup"><span data-stu-id="84679-142">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="84679-143">Si cree que un elemento no se ha publicado de buena fe, haga clic en **Notificar abuso** en la página de ese elemento.</span><span class="sxs-lookup"><span data-stu-id="84679-143">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="84679-144">Instalar</span><span class="sxs-lookup"><span data-stu-id="84679-144">Install</span></span>

<span data-ttu-id="84679-145">Para instalar un elemento desde la Galería para su uso, ejecute el cmdlet [Install-Module][] o [Install-Script][], en función del tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="84679-145">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="84679-146">[Install-Module][] instala el módulo en `$env:ProgramFiles\WindowsPowerShell\Modules` de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="84679-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="84679-147">Para ello es necesaria una cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="84679-147">This requires an administrator account.</span></span> <span data-ttu-id="84679-148">Si agrega el parámetro `-Scope CurrentUser`, el módulo se instala en `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="84679-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="84679-149">[Install-Script][] instala el script en `$env:ProgramFiles\WindowsPowerShell\Scripts` de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="84679-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="84679-150">Para ello es necesaria una cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="84679-150">This requires an administrator account.</span></span> <span data-ttu-id="84679-151">Si agrega el parámetro `-Scope CurrentUser`, el script se instala en `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.</span><span class="sxs-lookup"><span data-stu-id="84679-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="84679-152">De forma predeterminada, [Install-Module][] e [Install-Script][] instalan la versión más reciente de un elemento.</span><span class="sxs-lookup"><span data-stu-id="84679-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="84679-153">Para instalar una versión anterior del elemento, agregue el parámetro `-RequiredVersion`.</span><span class="sxs-lookup"><span data-stu-id="84679-153">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="84679-154">Implementar</span><span class="sxs-lookup"><span data-stu-id="84679-154">Deploy</span></span>

<span data-ttu-id="84679-155">Para implementar un elemento desde la Galería de PowerShell en Automatización de Azure, haga clic en **Deploy to Azure Automation** (Implementar en Automatización de Azure) en la página de detalles del elemento.</span><span class="sxs-lookup"><span data-stu-id="84679-155">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="84679-156">Se le redirigirá al Portal de administración de Azure, donde deberá iniciar sesión con sus credenciales de la cuenta de Azure.</span><span class="sxs-lookup"><span data-stu-id="84679-156">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="84679-157">Tenga en cuenta que si se implementan elementos con dependencias, se implementarán todas las dependencias en Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="84679-157">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="84679-158">El botón Deploy to Azure Automation (Implementar en Automatización de Azure) se puede deshabilitar agregando la etiqueta **AzureAutomationNotSupported** a los metadatos del elemento.</span><span class="sxs-lookup"><span data-stu-id="84679-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="84679-159">Para obtener más información sobre Azure Automation, consulte la documentación de [Azure Automation](/azure/automation).</span><span class="sxs-lookup"><span data-stu-id="84679-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="84679-160">Actualizar elementos de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="84679-160">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="84679-161">Para actualizar elementos instalados desde la Galería de PowerShell, ejecute el cmdlet [Update-Module][] o [Update-Script][].</span><span class="sxs-lookup"><span data-stu-id="84679-161">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="84679-162">Cuando se ejecuta sin parámetros adicionales, [Update-Module][] intenta actualizar cada módulo instalado mediante la ejecución de [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="84679-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="84679-163">Para actualizar módulos de forma selectiva, agregue el parámetro `-Name`.</span><span class="sxs-lookup"><span data-stu-id="84679-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="84679-164">Del mismo modo, cuando se ejecuta sin parámetros adicionales, [Update-Script][] también intenta actualizar cada script instalado mediante la ejecución de [Install-Script][].</span><span class="sxs-lookup"><span data-stu-id="84679-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="84679-165">Para actualizar scripts de forma selectiva, agregue el parámetro `-Name`.</span><span class="sxs-lookup"><span data-stu-id="84679-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="84679-166">Enumerar los elementos instalados desde la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="84679-166">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="84679-167">Para averiguar qué módulos ha instalado desde la Galería de PowerShell, ejecute el cmdlet [Get-InstalledModule][].</span><span class="sxs-lookup"><span data-stu-id="84679-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="84679-168">Este comando enumera todos los módulos del sistema que se instalaron directamente desde la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="84679-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="84679-169">Del mismo modo, para averiguar qué scripts ha instalado desde la Galería de PowerShell, ejecute el cmdlet [Get-InstalledScript][].</span><span class="sxs-lookup"><span data-stu-id="84679-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="84679-170">Este comando enumera todos los scripts del sistema que se instalaron directamente desde la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="84679-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

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