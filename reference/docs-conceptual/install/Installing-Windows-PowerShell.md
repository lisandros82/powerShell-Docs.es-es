---
ms.date: 08/09/2017
keywords: powershell,cmdlet,descargar,instalar,configurar,windows 10,windows 8.1,windows 8.0,windows 7
title: Instalación de Windows PowerShell
ms.openlocfilehash: 345cde8012bece730e7217ed16be6175ad26bb28
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "62086483"
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="eae78-103">Instalación de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eae78-103">Installing Windows PowerShell</span></span>

<span data-ttu-id="eae78-104">A partir de las ediciones Windows 7 SP1 y Windows Server 2008 R2 SP1, Windows PowerShell viene instalado en Windows de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="eae78-104">Windows PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="eae78-105">Si está interesado en PowerShell 6 y versiones posteriores, debe instalar PowerShell Core en lugar de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eae78-105">If you are interested in PowerShell 6 and later, you need to install PowerShell Core instead of Windows PowerShell.</span></span> <span data-ttu-id="eae78-106">Para ello, consulte [Instalación de PowerShell Core en Windows](Installing-PowerShell-Core-on-Windows.md).</span><span class="sxs-lookup"><span data-stu-id="eae78-106">For that, see [Installing PowerShell Core on Windows](Installing-PowerShell-Core-on-Windows.md).</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="eae78-107">Búsqueda de PowerShell en Windows 10, 8.1, 8.0 y 7</span><span class="sxs-lookup"><span data-stu-id="eae78-107">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="eae78-108">Encontrar la consola o el ISE (entorno de scripting integrado) de PowerShell en Windows puede ser difícil, ya que su ubicación cambia en función de la versión del sistema.</span><span class="sxs-lookup"><span data-stu-id="eae78-108">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as its location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="eae78-109">En las tablas siguientes se proporciona información para poder encontrar PowerShell según la versión de Windows que se esté usando.</span><span class="sxs-lookup"><span data-stu-id="eae78-109">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="eae78-110">Todas las versiones que se muestran aquí son las originales, tal y como se publican y sin actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="eae78-110">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="eae78-111">Consola</span><span class="sxs-lookup"><span data-stu-id="eae78-111">For Console</span></span>

<span data-ttu-id="eae78-112">Version</span><span class="sxs-lookup"><span data-stu-id="eae78-112">Version</span></span> | <span data-ttu-id="eae78-113">Ubicación</span><span class="sxs-lookup"><span data-stu-id="eae78-113">Location</span></span>
-- | --
<span data-ttu-id="eae78-114">Windows 10</span><span class="sxs-lookup"><span data-stu-id="eae78-114">Windows 10</span></span> | <span data-ttu-id="eae78-115">Haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eae78-115">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="eae78-116">Windows 8.1 u 8.0</span><span class="sxs-lookup"><span data-stu-id="eae78-116">Windows 8.1, 8.0</span></span> | <span data-ttu-id="eae78-117">En la pantalla Inicio, empiece a escribir PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eae78-117">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="eae78-118">Si está en el escritorio, haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eae78-118">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="eae78-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="eae78-119">Windows 7 SP1</span></span> | <span data-ttu-id="eae78-120">Haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir PowerShell en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="eae78-120">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="eae78-121">ISE</span><span class="sxs-lookup"><span data-stu-id="eae78-121">For ISE</span></span>

<span data-ttu-id="eae78-122">Version</span><span class="sxs-lookup"><span data-stu-id="eae78-122">Version</span></span> | <span data-ttu-id="eae78-123">Ubicación</span><span class="sxs-lookup"><span data-stu-id="eae78-123">Location</span></span>
-- | --
<span data-ttu-id="eae78-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="eae78-124">Windows 10</span></span> | <span data-ttu-id="eae78-125">Haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir ISE.</span><span class="sxs-lookup"><span data-stu-id="eae78-125">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="eae78-126">Windows 8.1 u 8.0</span><span class="sxs-lookup"><span data-stu-id="eae78-126">Windows 8.1, 8.0</span></span> | <span data-ttu-id="eae78-127">En la pantalla Inicio, escriba **PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="eae78-127">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="eae78-128">Si está en el escritorio, haga clic en el icono de Windows de la esquina inferior izquierda y escriba **PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="eae78-128">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="eae78-129">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="eae78-129">Windows 7 SP1</span></span> | <span data-ttu-id="eae78-130">Haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir PowerShell en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="eae78-130">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="eae78-131">Búsqueda de PowerShell en versiones de Windows Server</span><span class="sxs-lookup"><span data-stu-id="eae78-131">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="eae78-132">A partir de Windows Server 2008 R2, el sistema operativo Windows puede instalarse sin la interfaz gráfica de usuario (GUI).</span><span class="sxs-lookup"><span data-stu-id="eae78-132">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="eae78-133">Las ediciones de Windows Server sin GUI se conocen como ediciones **básicas**, mientras que las que sí que tienen GUI se conocen como **de escritorio**.</span><span class="sxs-lookup"><span data-stu-id="eae78-133">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="eae78-134">Ediciones básicas de Windows Server</span><span class="sxs-lookup"><span data-stu-id="eae78-134">Windows Server Core editions</span></span>

<span data-ttu-id="eae78-135">En todas las ediciones básicas, se mostrará una ventana del símbolo del sistema de Windows al iniciar sesión en el servidor.</span><span class="sxs-lookup"><span data-stu-id="eae78-135">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="eae78-136">Escriba `powershell` y pulse **ENTRAR** para iniciar PowerShell en la sesión del símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="eae78-136">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span>
<span data-ttu-id="eae78-137">Escriba `exit` para finalizar la sesión de PowerShell y volver al símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="eae78-137">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="eae78-138">Ediciones de escritorio de Windows Server</span><span class="sxs-lookup"><span data-stu-id="eae78-138">Windows Server Desktop editions</span></span>

<span data-ttu-id="eae78-139">En todas las ediciones de escritorio, deberá hacer clic en el icono de Windows de la esquina inferior izquierda y empezar a escribir PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eae78-139">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="eae78-140">Se mostrarán las opciones de la consola y el ISE.</span><span class="sxs-lookup"><span data-stu-id="eae78-140">You get both console and ISE options.</span></span>

<span data-ttu-id="eae78-141">La única excepción a la regla anterior se produce en el caso del ISE en Windows Server 2008 R2 SP1. En ese caso, haga clic en el icono de Windows de la esquina inferior izquierda y escriba PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="eae78-141">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="eae78-142">Comprobación de la versión de PowerShell</span><span class="sxs-lookup"><span data-stu-id="eae78-142">How to check the version of PowerShell</span></span>

<span data-ttu-id="eae78-143">Para consultar qué versión de PowerShell ha instalado, inicie una consola de PowerShell (o el ISE), escriba `$PSVersionTable` y pulse **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="eae78-143">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span> <span data-ttu-id="eae78-144">Busque el valor `PSVersion`.</span><span class="sxs-lookup"><span data-stu-id="eae78-144">Look for the `PSVersion` value.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="eae78-145">Actualización de Windows PowerShell existente</span><span class="sxs-lookup"><span data-stu-id="eae78-145">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="eae78-146">El paquete de instalación de PowerShell está incluido en un instalador WMF.</span><span class="sxs-lookup"><span data-stu-id="eae78-146">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="eae78-147">La versión del instalador WMF coincide con la versión de PowerShell; no hay ningún instalador independiente de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eae78-147">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="eae78-148">Si debe actualizar la versión existente de PowerShell en Windows, use la tabla siguiente para encontrar el instalador correspondiente a la versión de PowerShell que quiera aplicar.</span><span class="sxs-lookup"><span data-stu-id="eae78-148">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="eae78-149">Windows</span><span class="sxs-lookup"><span data-stu-id="eae78-149">Windows</span></span> | <span data-ttu-id="eae78-150">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="eae78-150">PS 3.0</span></span> | <span data-ttu-id="eae78-151">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="eae78-151">PS 4.0</span></span> | <span data-ttu-id="eae78-152">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="eae78-152">PS 5.0</span></span> | <span data-ttu-id="eae78-153">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="eae78-153">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="eae78-154">Windows 10 (consulte Nota 1)</span><span class="sxs-lookup"><span data-stu-id="eae78-154">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="eae78-155">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="eae78-155">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="eae78-156">Instalado</span><span class="sxs-lookup"><span data-stu-id="eae78-156">installed</span></span>
<span data-ttu-id="eae78-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="eae78-157">Windows 8.1</span></span><br/><span data-ttu-id="eae78-158">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="eae78-158">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="eae78-159">Instalado</span><span class="sxs-lookup"><span data-stu-id="eae78-159">installed</span></span> | [<span data-ttu-id="eae78-160">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="eae78-160">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="eae78-161">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="eae78-161">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="eae78-162">Windows 8</span><span class="sxs-lookup"><span data-stu-id="eae78-162">Windows 8</span></span><br/><span data-ttu-id="eae78-163">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="eae78-163">Windows Server 2012</span></span> | <span data-ttu-id="eae78-164">Instalado</span><span class="sxs-lookup"><span data-stu-id="eae78-164">installed</span></span> | [<span data-ttu-id="eae78-165">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="eae78-165">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="eae78-166">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="eae78-166">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="eae78-167">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="eae78-167">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="eae78-168">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="eae78-168">Windows 7 SP1</span></span><br/><span data-ttu-id="eae78-169">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="eae78-169">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="eae78-170">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="eae78-170">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="eae78-171">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="eae78-171">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="eae78-172">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="eae78-172">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="eae78-173">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="eae78-173">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> [!NOTE]
>
> <span data-ttu-id="eae78-174">En la versión inicial de Windows 10, con las actualizaciones automáticas habilitadas, PowerShell se actualiza de la versión 5.0 a la 5.1.</span><span class="sxs-lookup"><span data-stu-id="eae78-174">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
>
> <span data-ttu-id="eae78-175">Si no se actualiza la versión original de Windows 10 mediante las actualizaciones de Windows, la versión de PowerShell será la 5.0.</span><span class="sxs-lookup"><span data-stu-id="eae78-175">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="eae78-176">Obtención de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="eae78-176">Need Azure PowerShell</span></span>

<span data-ttu-id="eae78-177">Si está buscando **Azure PowerShell**, puede empezar por el artículo [Overview of Azure PowerShell](/powershell/azure/overview) (Información general sobre Azure PowerShell).</span><span class="sxs-lookup"><span data-stu-id="eae78-177">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](/powershell/azure/overview).</span></span>

<span data-ttu-id="eae78-178">De lo contrario, consulte [Install and configure Azure PowerShell](/powershell/azure/install-az-ps) (Instalación y configuración de Azure PowerShell).</span><span class="sxs-lookup"><span data-stu-id="eae78-178">Otherwise, what you might need is [Install and configure Azure PowerShell](/powershell/azure/install-az-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="eae78-179">Véase también</span><span class="sxs-lookup"><span data-stu-id="eae78-179">See Also</span></span>

[<span data-ttu-id="eae78-180">Requisitos del sistema de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eae78-180">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)

[<span data-ttu-id="eae78-181">Inicio de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eae78-181">Starting Windows PowerShell</span></span>](../getting-started/Starting-Windows-PowerShell.md)
