---
ms.date: 2017-08-09
keywords: powershell,cmdlet,descargar,instalar,configurar,windows 10,windows 8.1,windows 8.0,windows 7
title: "Instalación de Windows PowerShell"
ms.openlocfilehash: ec8f09087a5c5f2e7ea6237faa01ea3f447ad1f3
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="5bd6c-103">Instalación de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5bd6c-103">Installing Windows PowerShell</span></span>

<span data-ttu-id="5bd6c-104">A partir de las ediciones Windows 7 SP1 y Windows Server 2008 R2 SP1, PowerShell viene instalado en Windows de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-104">PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="5bd6c-105">Los usuarios de Linux, macOS y Windows que quieran instalar **PowerShell 6** (beta) en su máquina deberán hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="5bd6c-105">Linux, macOS, and Windows users that would like to install **PowerShell 6** (beta), in their machines, need to:</span></span>

1. <span data-ttu-id="5bd6c-106">Obtener PowerShell para el sistema operativo adecuado y su versión específica en [GitHub](https://github.com/powershell/powershell#get-powershell)</span><span class="sxs-lookup"><span data-stu-id="5bd6c-106">Get PowerShell for the specific OS and version, from [GitHub](https://github.com/powershell/powershell#get-powershell)</span></span>
1. <span data-ttu-id="5bd6c-107">Instrucciones de instalación</span><span class="sxs-lookup"><span data-stu-id="5bd6c-107">Follow the installation instructions</span></span>
  - [<span data-ttu-id="5bd6c-108">Linux</span><span class="sxs-lookup"><span data-stu-id="5bd6c-108">Linux</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
  - [<span data-ttu-id="5bd6c-109">macOS</span><span class="sxs-lookup"><span data-stu-id="5bd6c-109">macOS</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md)
  - [<span data-ttu-id="5bd6c-110">Windows</span><span class="sxs-lookup"><span data-stu-id="5bd6c-110">Windows</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi)

<span data-ttu-id="5bd6c-111">PowerShell 6 también está disponible para Docker; consulte las instrucciones de [instalación de Docker](https://github.com/PowerShell/PowerShell/tree/master/docker).</span><span class="sxs-lookup"><span data-stu-id="5bd6c-111">PowerShell 6 is also available for Docker; see [Docker installation](https://github.com/PowerShell/PowerShell/tree/master/docker) instructions.</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="5bd6c-112">Búsqueda de PowerShell en Windows 10, 8.1, 8.0 y 7</span><span class="sxs-lookup"><span data-stu-id="5bd6c-112">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="5bd6c-113">Encontrar la consola o el ISE (Entorno de scripting integrado por sus siglas en inglés) de PowerShell en Windows puede ser difícil, ya que su ubicación cambia en función de la versión del sistema.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-113">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as it's location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="5bd6c-114">En las tablas siguientes se proporciona información para poder encontrar PowerShell según la versión de Windows que se esté usando.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-114">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="5bd6c-115">Todas las versiones que se muestran aquí son las originales, tal y como se publican y sin actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-115">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="5bd6c-116">Consola</span><span class="sxs-lookup"><span data-stu-id="5bd6c-116">For Console</span></span>

<span data-ttu-id="5bd6c-117">Version</span><span class="sxs-lookup"><span data-stu-id="5bd6c-117">Version</span></span> | <span data-ttu-id="5bd6c-118">Ubicación</span><span class="sxs-lookup"><span data-stu-id="5bd6c-118">Location</span></span>
-- | --
<span data-ttu-id="5bd6c-119">Windows 10</span><span class="sxs-lookup"><span data-stu-id="5bd6c-119">Windows 10</span></span> | <span data-ttu-id="5bd6c-120">Haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-120">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="5bd6c-121">Windows 8.1 u 8.0</span><span class="sxs-lookup"><span data-stu-id="5bd6c-121">Windows 8.1, 8.0</span></span> | <span data-ttu-id="5bd6c-122">En la pantalla Inicio, empiece a escribir PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-122">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="5bd6c-123">Si está en el escritorio, haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-123">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="5bd6c-124">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="5bd6c-124">Windows 7 SP1</span></span> | <span data-ttu-id="5bd6c-125">Haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir PowerShell en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-125">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="5bd6c-126">ISE</span><span class="sxs-lookup"><span data-stu-id="5bd6c-126">For ISE</span></span>

<span data-ttu-id="5bd6c-127">Version</span><span class="sxs-lookup"><span data-stu-id="5bd6c-127">Version</span></span> | <span data-ttu-id="5bd6c-128">Ubicación</span><span class="sxs-lookup"><span data-stu-id="5bd6c-128">Location</span></span>
-- | --
<span data-ttu-id="5bd6c-129">Windows 10</span><span class="sxs-lookup"><span data-stu-id="5bd6c-129">Windows 10</span></span> | <span data-ttu-id="5bd6c-130">Haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir ISE.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-130">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="5bd6c-131">Windows 8.1 u 8.0</span><span class="sxs-lookup"><span data-stu-id="5bd6c-131">Windows 8.1, 8.0</span></span> | <span data-ttu-id="5bd6c-132">En la pantalla Inicio, escriba **PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-132">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="5bd6c-133">Si está en el escritorio, haga clic en el icono de Windows de la esquina inferior izquierda y escriba **PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-133">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="5bd6c-134">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="5bd6c-134">Windows 7 SP1</span></span> | <span data-ttu-id="5bd6c-135">Haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir PowerShell en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-135">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="5bd6c-136">Búsqueda de PowerShell en versiones de Windows Server</span><span class="sxs-lookup"><span data-stu-id="5bd6c-136">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="5bd6c-137">A partir de Windows Server 2008 R2, el sistema operativo Windows puede instalarse sin la interfaz gráfica de usuario (GUI).</span><span class="sxs-lookup"><span data-stu-id="5bd6c-137">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="5bd6c-138">Las ediciones de Windows Server sin GUI se conocen como ediciones **básicas**, mientras que las que sí que tienen GUI se conocen como **de escritorio**.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-138">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="5bd6c-139">Ediciones básicas de Windows Server</span><span class="sxs-lookup"><span data-stu-id="5bd6c-139">Windows Server Core editions</span></span>

<span data-ttu-id="5bd6c-140">En todas las ediciones básicas, se mostrará una ventana del símbolo del sistema de Windows al iniciar sesión en el servidor.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-140">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="5bd6c-141">Escriba `powershell` y pulse **ENTRAR** para iniciar PowerShell en la sesión del símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-141">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span> <span data-ttu-id="5bd6c-142">Escriba `exit` para finalizar la sesión de PowerShell y volver al símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-142">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="5bd6c-143">Ediciones de escritorio de Windows Server</span><span class="sxs-lookup"><span data-stu-id="5bd6c-143">Windows Server Desktop editions</span></span>

<span data-ttu-id="5bd6c-144">En todas las ediciones de escritorio, deberá hacer clic en el icono de Windows de la esquina inferior izquierda y empezar a escribir PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-144">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="5bd6c-145">Se mostrarán las opciones de la consola y el ISE.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-145">You get both console and ISE options.</span></span>

<span data-ttu-id="5bd6c-146">La única excepción a la regla anterior se produce en el caso del ISE en Windows Server 2008 R2 SP1. En ese caso, haga clic en el icono de Windows de la esquina inferior izquierda y escriba PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-146">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="5bd6c-147">Comprobación de la versión de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5bd6c-147">How to check the version of PowerShell</span></span>

<span data-ttu-id="5bd6c-148">Para consultar qué versión de PowerShell ha instalado, inicie una consola de PowerShell (o el ISE), escriba `$PSVersionTable` y pulse **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-148">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="5bd6c-149">Actualización de Windows PowerShell existente</span><span class="sxs-lookup"><span data-stu-id="5bd6c-149">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="5bd6c-150">El paquete de instalación de PowerShell está incluido en un instalador WMF.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-150">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="5bd6c-151">La versión del instalador WMF coincide con la versión de PowerShell; no hay ningún instalador independiente de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-151">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="5bd6c-152">Si debe actualizar la versión existente de PowerShell en Windows, use la tabla siguiente para encontrar el instalador correspondiente a la versión de PowerShell que quiera aplicar.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-152">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="5bd6c-153">Windows</span><span class="sxs-lookup"><span data-stu-id="5bd6c-153">Windows</span></span> | <span data-ttu-id="5bd6c-154">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="5bd6c-154">PS 3.0</span></span> | <span data-ttu-id="5bd6c-155">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="5bd6c-155">PS 4.0</span></span> | <span data-ttu-id="5bd6c-156">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="5bd6c-156">PS 5.0</span></span> | <span data-ttu-id="5bd6c-157">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="5bd6c-157">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="5bd6c-158">Windows 10 (consulte Nota 1)</span><span class="sxs-lookup"><span data-stu-id="5bd6c-158">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="5bd6c-159">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="5bd6c-159">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="5bd6c-160">Instalado</span><span class="sxs-lookup"><span data-stu-id="5bd6c-160">installed</span></span>
<span data-ttu-id="5bd6c-161">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="5bd6c-161">Windows 8.1</span></span><br/><span data-ttu-id="5bd6c-162">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="5bd6c-162">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="5bd6c-163">Instalado</span><span class="sxs-lookup"><span data-stu-id="5bd6c-163">installed</span></span> | [<span data-ttu-id="5bd6c-164">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="5bd6c-164">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="5bd6c-165">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="5bd6c-165">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="5bd6c-166">Windows 8</span><span class="sxs-lookup"><span data-stu-id="5bd6c-166">Windows 8</span></span><br/><span data-ttu-id="5bd6c-167">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="5bd6c-167">Windows Server 2012</span></span> | <span data-ttu-id="5bd6c-168">Instalado</span><span class="sxs-lookup"><span data-stu-id="5bd6c-168">installed</span></span> | [<span data-ttu-id="5bd6c-169">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="5bd6c-169">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="5bd6c-170">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="5bd6c-170">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="5bd6c-171">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="5bd6c-171">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="5bd6c-172">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="5bd6c-172">Windows 7 SP1</span></span><br/><span data-ttu-id="5bd6c-173">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="5bd6c-173">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="5bd6c-174">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="5bd6c-174">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="5bd6c-175">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="5bd6c-175">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="5bd6c-176">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="5bd6c-176">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="5bd6c-177">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="5bd6c-177">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> <span data-ttu-id="5bd6c-178">**Nota 1**:</span><span class="sxs-lookup"><span data-stu-id="5bd6c-178">**Note 1**:</span></span>
  >>
  >> <span data-ttu-id="5bd6c-179">En la versión inicial de Windows 10, con las actualizaciones automáticas habilitadas, PowerShell se actualiza de la versión 5.0 a la 5.1.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-179">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
  >>
  >> <span data-ttu-id="5bd6c-180">Si no se actualiza la versión original de Windows 10 mediante las actualizaciones de Windows, la versión de PowerShell será la 5.0.</span><span class="sxs-lookup"><span data-stu-id="5bd6c-180">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="5bd6c-181">Obtención de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="5bd6c-181">Need Azure PowerShell</span></span>

<span data-ttu-id="5bd6c-182">Si está buscando **Azure PowerShell**, puede empezar por el artículo [Overview of Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure) (Información general sobre Azure PowerShell).</span><span class="sxs-lookup"><span data-stu-id="5bd6c-182">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).</span></span>

<span data-ttu-id="5bd6c-183">De lo contrario, consulte [Install and configure Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps) (Instalación y configuración de Azure PowerShell).</span><span class="sxs-lookup"><span data-stu-id="5bd6c-183">Otherwise, what you might need is [Install and configure Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="5bd6c-184">Véase también</span><span class="sxs-lookup"><span data-stu-id="5bd6c-184">See Also</span></span>

- [<span data-ttu-id="5bd6c-185">Requisitos del sistema de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5bd6c-185">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="5bd6c-186">Inicio de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5bd6c-186">Starting Windows PowerShell</span></span>](Starting-Windows-PowerShell.md)
