---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Instalación y uso de Windows PowerShell Web Access"
ms.openlocfilehash: a860f7c22829da46f0458ea729fa0afd1fe4fb6f
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
#  <a name="install-and-use-windows-powershell-web-access"></a><span data-ttu-id="ef11c-103">Instalación y uso de Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="ef11c-103">Install and Use Windows PowerShell Web Access</span></span>

<span data-ttu-id="ef11c-104">Actualizado: 5 de noviembre de 2013</span><span class="sxs-lookup"><span data-stu-id="ef11c-104">Updated: November 5, 2013</span></span>

<span data-ttu-id="ef11c-105">Se aplica a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="ef11c-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="ef11c-106">Windows PowerShell® Web Access, que se incluyó por primera vez en Windows Server® 2012, actúa como puerta de enlace de Windows PowerShell, ofreciendo una consola de Windows PowerShell basada en web dirigida a un equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="ef11c-106">Windows PowerShell® Web Access, first introduced in Windows Server® 2012, acts as a Windows PowerShell gateway, providing a web-based Windows PowerShell console that is targeted at a remote computer.</span></span> <span data-ttu-id="ef11c-107">Permite a los profesionales de TI ejecutar comandos y scripts de Windows PowerShell desde una consola de Windows PowerShell en un explorador web, sin que sea necesario contar con Windows PowerShell, software de administración remota o la instalación de un complemento de explorador en el dispositivo cliente.</span><span class="sxs-lookup"><span data-stu-id="ef11c-107">It enables IT Pros to run Windows PowerShell commands and scripts from a Windows PowerShell console in a web browser, with no Windows PowerShell, remote management software, or browser plug-in installation necessary on the client device.</span></span> <span data-ttu-id="ef11c-108">Lo único que se necesita para ejecutar la consola de Windows PowerShell basada en web es una puerta de enlace de Windows PowerShell Web Access correctamente configurada y un explorador en el dispositivo cliente que admita JavaScript® y acepte cookies.</span><span class="sxs-lookup"><span data-stu-id="ef11c-108">All that is required to run the web-based Windows PowerShell console is a properly-configured Windows PowerShell Web Access gateway, and a client device browser that supports JavaScript® and accepts cookies.</span></span>

<span data-ttu-id="ef11c-109">Entre los dispositivos cliente se incluyen equipos portátiles, equipos que no son de trabajo, equipos prestados, Tablet PC, quioscos multimedia web, equipos que no ejecutan un sistema operativo Windows y exploradores de teléfono móvil.</span><span class="sxs-lookup"><span data-stu-id="ef11c-109">Examples of client devices include laptops, non-work personal computers, borrowed computers, tablet computers, web kiosks, computers that are not running a Windows-based operating system, and cell phone browsers.</span></span> <span data-ttu-id="ef11c-110">Los profesionales de TI pueden llevar a cabo tareas críticas de administración en servidores remotos basados en Windows desde dispositivos que cuenten con acceso a una conexión de Internet y un explorador web.</span><span class="sxs-lookup"><span data-stu-id="ef11c-110">IT Pros can perform critical management tasks on remote Windows-based servers from devices that have access to an Internet connection and a web browser.</span></span>

<span data-ttu-id="ef11c-111">Después de instalar y configurar la puerta de enlace correctamente, los usuarios pueden obtener acceso a una consola de Windows PowerShell mediante un explorador web.</span><span class="sxs-lookup"><span data-stu-id="ef11c-111">After successful gateway setup and configuration, users can access a Windows PowerShell console by using a web browser.</span></span> <span data-ttu-id="ef11c-112">Al abrir el sitio web protegido de Windows PowerShell Web Access y, una vez que se hayan autenticado correctamente, los usuarios podrán ejecutar una consola de Windows PowerShell basada en web.</span><span class="sxs-lookup"><span data-stu-id="ef11c-112">When users open the secured Windows PowerShell Web Access website, they can run a web-based Windows PowerShell console after successful authentication.</span></span>

<span data-ttu-id="ef11c-113">El proceso de instalación y configuración de Windows PowerShell Web Access consta de tres pasos:</span><span class="sxs-lookup"><span data-stu-id="ef11c-113">Windows PowerShell Web Access setup and configuration is a three-step process:</span></span>

1.  <span data-ttu-id="ef11c-114">Instalación de Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="ef11c-114">Installing Windows PowerShell Web Access</span></span>

2.  <span data-ttu-id="ef11c-115">Configuración de la puerta de enlace</span><span class="sxs-lookup"><span data-stu-id="ef11c-115">Configuring the gateway</span></span>

3.  <span data-ttu-id="ef11c-116">Configuración de las reglas de autorización que permiten a los usuarios tener acceso a la consola de Windows PowerShell basada en web</span><span class="sxs-lookup"><span data-stu-id="ef11c-116">Configuring authorization rules that allow users access to the web-based Windows PowerShell console</span></span>

<span data-ttu-id="ef11c-117">Antes de instalar y configurar Windows PowerShell Web Access, se recomienda leer toda la guía, que incluye instrucciones sobre cómo instalar, proteger y desinstalar Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-117">Before you install and configure Windows PowerShell Web Access, we recommend that you read this entire guide, which includes instructions about how to install, secure, and uninstall Windows PowerShell Web Access.</span></span> <span data-ttu-id="ef11c-118">En el tema [Uso de la consola de Windows PowerShell basada en web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) se describe cómo los usuarios inician sesión en la consola basada en web y se explican las limitaciones y diferencias entre la consola de Windows PowerShell basada en web y la consola de **powershell.exe**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-118">The [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) topic describes how users sign in to the web-based console, and covers limitations and differences between the web-based Windows PowerShell console and the **powershell.exe** console.</span></span> <span data-ttu-id="ef11c-119">Los usuarios finales de la consola basada en web deben leer [Uso de la consola de Windows PowerShell basada en web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx), pero no es necesario que lean el resto de esta guía.</span><span class="sxs-lookup"><span data-stu-id="ef11c-119">End users of the web-based console should read [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx), but do not need to read the rest of this guide.</span></span>

<span data-ttu-id="ef11c-120">En este tema, no se proporciona una guía de operaciones de Servidor web (IIS) exhaustiva, sino solo los pasos necesarios para configurar la puerta de enlace de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-120">This topic does not provide in-depth Web Server (IIS) operations guidance; only those steps required to configure the Windows PowerShell Web Access gateway are described in this topic.</span></span> <span data-ttu-id="ef11c-121">Para obtener más información sobre la configuración y protección de sitios web en IIS, vea los recursos de documentación de IIS en la sección Vea también.</span><span class="sxs-lookup"><span data-stu-id="ef11c-121">For more information about configuring and securing websites in IIS, see the IIS documentation resources in the See Also section.</span></span>

<span data-ttu-id="ef11c-122">En el siguiente diagrama se muestra cómo funciona Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-122">The following diagram shows how Windows PowerShell Web Access works.</span></span>

<span><img src="https://i-technet.sec.s-msft.com/dynimg/IC564303.jpeg" title="Windows PowerShell Web Access diagram" alt="Windows PowerShell Web Access diagram" id="ee15fa8f-ce13-49e5-933d-514f6d60a2b1" /></span>

<span data-ttu-id="ef11c-123">En este tema:</span><span class="sxs-lookup"><span data-stu-id="ef11c-123">In this topic:</span></span>

-   [<span data-ttu-id="ef11c-124">Requisitos para ejecutar Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="ef11c-124">Requirements for running Windows PowerShell Web Access</span></span>](#BKMK_reqs)

-   [<span data-ttu-id="ef11c-125">Compatibilidad con exploradores y dispositivos cliente</span><span class="sxs-lookup"><span data-stu-id="ef11c-125">Browser and client device support</span></span>](#BKMK_browser)

-   [<span data-ttu-id="ef11c-126">Implementación recomendada (rápida)</span><span class="sxs-lookup"><span data-stu-id="ef11c-126">Recommended (quick) deployment</span></span>](#BKMK_recm)

-   [<span data-ttu-id="ef11c-127">Implementación personalizada</span><span class="sxs-lookup"><span data-stu-id="ef11c-127">Custom deployment</span></span>](#BKMK_custom)

-   [<span data-ttu-id="ef11c-128">Configurar un certificado original</span><span class="sxs-lookup"><span data-stu-id="ef11c-128">Configure a genuine certificate</span></span>](#BKMK_configcert)

<a href="" id="BKMK_reqs"></a>

<span data-ttu-id="ef11c-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requisitos para ejecutar Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requirements for running Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ef11c-130">Windows PowerShell Web Access requiere que Servidor web (IIS), .NET Framework 4.5 y Windows PowerShell 3.0 o Windows PowerShell 4.0 se ejecuten en el servidor donde desea ejecutar la puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="ef11c-130">Windows PowerShell Web Access requires Web Server (IIS), .NET Framework 4.5, and Windows PowerShell 3.0 or Windows PowerShell 4.0 to be running on the server on which you want to run the gateway.</span></span> <span data-ttu-id="ef11c-131">Puede instalar Windows PowerShell Web Access en un servidor que ejecuta Windows Server 2012 R2 o Windows Server 2012 mediante el uso del Asistente para agregar roles y características en el Administrador del servidor o de los cmdlets de implementación de Windows PowerShell para el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="ef11c-131">You can install Windows PowerShell Web Access on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either the Add Roles and Features Wizard in Server Manager, or Windows PowerShell deployment cmdlets for Server Manager.</span></span> <span data-ttu-id="ef11c-132">Al instalar Windows PowerShell Web Access mediante el Administrador del servidor o sus cmdlets de implementación, automáticamente se agregan los roles y las características necesarios como parte del proceso de instalación.</span><span class="sxs-lookup"><span data-stu-id="ef11c-132">When you install Windows PowerShell Web Access by using Server Manager or its deployment cmdlets, required roles and features are automatically added as part of the installation process.</span></span>

<span data-ttu-id="ef11c-133">Windows PowerShell Web Access permite a los usuarios remotos obtener acceso a los equipos de la organización mediante Windows PowerShell en un explorador web.</span><span class="sxs-lookup"><span data-stu-id="ef11c-133">Windows PowerShell Web Access allows remote users to access computers in your organization by using Windows PowerShell in a web browser.</span></span> <span data-ttu-id="ef11c-134">Si bien Windows PowerShell Web Access es una herramienta de administración eficaz y conveniente, el acceso web conlleva riesgos de seguridad, por lo que debe configurarse de la manera más segura posible.</span><span class="sxs-lookup"><span data-stu-id="ef11c-134">Although Windows PowerShell Web Access is a convenient and powerful management tool, the web-based access poses security risks, and should be configured as securely as possible.</span></span> <span data-ttu-id="ef11c-135">Se recomienda que los administradores que configuran la puerta de enlace de Windows PowerShell Web Access usen los niveles de seguridad disponibles, tanto las reglas de autorización basadas en cmdlets incluidas con Windows PowerShell Web Access como los niveles de seguridad disponibles en Servidor web (IIS) y en aplicaciones de terceros.</span><span class="sxs-lookup"><span data-stu-id="ef11c-135">We recommend that administrators who configure the Windows PowerShell Web Access gateway use available security layers, both the cmdlet-based authorization rules included with Windows PowerShell Web Access, and security layers that are available in Web Server (IIS) and third-party applications.</span></span> <span data-ttu-id="ef11c-136">En esta documentación se incluyen ejemplos que no son seguros, recomendados únicamente para entornos de prueba, así como ejemplos recomendados para implementaciones seguras.</span><span class="sxs-lookup"><span data-stu-id="ef11c-136">This documentation includes both unsecure examples that are only recommended for test environments, as well as examples that are recommended for secure deployments.</span></span>

<a href="" id="BKMK_browser"></a>

<span data-ttu-id="ef11c-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Compatibilidad con exploradores y dispositivos cliente</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser and client device support</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ef11c-138">Windows PowerShell Web Access admite los siguientes exploradores de Internet.</span><span class="sxs-lookup"><span data-stu-id="ef11c-138">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="ef11c-139">Aunque los exploradores móviles no se admiten oficialmente, muchos de ellos pueden ejecutar la consola de Windows PowerShell basada en web.</span><span class="sxs-lookup"><span data-stu-id="ef11c-139">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="ef11c-140">También se espera que funcionen otros exploradores que aceptan cookies y ejecutan JavaScript y sitios web HTTPS, pero no se han probado de manera oficial.</span><span class="sxs-lookup"><span data-stu-id="ef11c-140">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="ef11c-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Exploradores de equipos de escritorio admitidos</span></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="ef11c-142">Windows® Internet Explorer® para Microsoft Windows® 8.0, 9.0, 10.0 y 11.0</span><span class="sxs-lookup"><span data-stu-id="ef11c-142">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="ef11c-143">Mozilla Firefox® 10.0.2</span><span class="sxs-lookup"><span data-stu-id="ef11c-143">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="ef11c-144">Google Chrome™ 17.0.963.56m para Windows</span><span class="sxs-lookup"><span data-stu-id="ef11c-144">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="ef11c-145">Apple Safari® 5.1.2 para Windows</span><span class="sxs-lookup"><span data-stu-id="ef11c-145">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="ef11c-146">Apple Safari 5.1.2 para Mac OS®</span><span class="sxs-lookup"><span data-stu-id="ef11c-146">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="ef11c-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Exploradores o dispositivos móviles mínimamente probados</span></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="ef11c-148">Windows Phone 7 y 7.5</span><span class="sxs-lookup"><span data-stu-id="ef11c-148">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="ef11c-149">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span><span class="sxs-lookup"><span data-stu-id="ef11c-149">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="ef11c-150">Apple Safari para sistema operativo iPhone 5.0.1</span><span class="sxs-lookup"><span data-stu-id="ef11c-150">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="ef11c-151">Apple Safari para sistema operativo iPad 2 5.0.1</span><span class="sxs-lookup"><span data-stu-id="ef11c-151">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="ef11c-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requisitos de explorador</span></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ef11c-153">Para usar la consola de Windows PowerShell Web Access basada en web, los exploradores deben poder hacer lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="ef11c-153">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="ef11c-154">Permitir cookies del sitio web de la puerta de enlace de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-154">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="ef11c-155">Abrir y leer páginas HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ef11c-155">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="ef11c-156">Abrir y ejecutar sitios web que usen JavaScript.</span><span class="sxs-lookup"><span data-stu-id="ef11c-156">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_recm"></a>

<span data-ttu-id="ef11c-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Implementación recomendada (rápida)</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ef11c-158">Puede instalar la puerta de enlace de Windows PowerShell Web Access en un servidor que ejecuta Windows Server 2012 R2 o Windows Server 2012 mediante el uso de los cmdlets de Windows PowerShell o del Asistente para agregar roles y características que se abre desde el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="ef11c-158">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either Windows PowerShell cmdlets, or by using the Add Roles and Features Wizard that is opened from within Server Manager.</span></span> <span data-ttu-id="ef11c-159">Para la instalación y la configuración rápida, use cmdlets de Windows PowerShell, como se describe en esta sección.</span><span class="sxs-lookup"><span data-stu-id="ef11c-159">For quick installation and configuration, use Windows PowerShell cmdlets, as described in this section.</span></span>

-   [<span data-ttu-id="ef11c-160">Paso 1: Instalar Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="ef11c-160">Step 1: Install Windows PowerShell Web Access</span></span>](#BKMK_step1)

-   [<span data-ttu-id="ef11c-161">Paso 2: Configurar la puerta de enlace</span><span class="sxs-lookup"><span data-stu-id="ef11c-161">Step 2: Configure the gateway</span></span>](#BKMK_step2)

-   [<span data-ttu-id="ef11c-162">Paso 3: Configurar una regla de autorización restrictiva</span><span class="sxs-lookup"><span data-stu-id="ef11c-162">Step 3: Configure a restrictive authorization rule</span></span>](#BKMK_step3)

<a href="" id="BKMK_step1"></a>
###

<span data-ttu-id="ef11c-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Paso 1: Instalar Windows PowerShell Web Access</span></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="ef11c-164">Para instalar Windows PowerShell Web Access mediante cmdlets de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef11c-164">To install Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="ef11c-165">Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell con derechos de usuario elevados.</span><span class="sxs-lookup"><span data-stu-id="ef11c-165">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="ef11c-166">En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell**, en la barra de tareas y, luego,en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-166">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="ef11c-167">En la pantalla **Inicio** de Windows, haga clic con el botón derecho en **Windows PowerShell** y, luego, en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-167">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="ef11c-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="ef11c-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="ef11c-169">En Windows PowerShell 3.0 y 4.0, no es necesario importar el módulo de cmdlets del Administrador del servidor en la sesión de Windows PowerShell antes de ejecutar los cmdlets que forman parte del módulo.</span><span class="sxs-lookup"><span data-stu-id="ef11c-169">In Windows PowerShell 3.0 and 4.0, there is no need to import the Server Manager cmdlet module into the Windows PowerShell session before running cmdlets that are part of the module.</span></span> <span data-ttu-id="ef11c-170">El módulo se importa automáticamente la primera vez que se ejecuta un cmdlet que es parte del módulo.</span><span class="sxs-lookup"><span data-stu-id="ef11c-170">A module is automatically imported the first time you run a cmdlet that is part of the module.</span></span> <span data-ttu-id="ef11c-171">Asimismo, los cmdlets de Windows PowerShell no distinguen mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ef11c-171">Also, Windows PowerShell cmdlets are not case-sensitive.</span></span></p></td>
    </tr>
    </tbody>
    </table>

2.  <span data-ttu-id="ef11c-172">Escriba lo siguiente y después presione **Entrar**, donde *computer_name* representa un equipo remoto en el cual desea instalar Windows PowerShell Web Access, si procede.</span><span class="sxs-lookup"><span data-stu-id="ef11c-172">Type the following, and then press **Enter**, where *computer_name* represents a remote computer on which you want to install Windows PowerShell Web Access, if applicable.</span></span> <span data-ttu-id="ef11c-173">El parámetro <span class="code">Restart</span> reinicia automáticamente los servidores de destino si es necesario.</span><span class="sxs-lookup"><span data-stu-id="ef11c-173">The <span class="code">Restart</span> parameter automatically restarts destination servers if required.</span></span>

    [<span data-ttu-id="ef11c-174">Copy</span><span class="sxs-lookup"><span data-stu-id="ef11c-174">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_374a9c21-4f6e-471e-b957-bb190a594533'); "Copy to clipboard.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="ef11c-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="ef11c-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="ef11c-176">Al instalarse Windows PowerShell Web Access mediante el uso de los cmdlets de Windows PowerShell, no se agregan herramientas de administración de Servidor web (IIS) de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="ef11c-176">Installing Windows PowerShell Web Access by using Windows PowerShell cmdlets does not add Web Server (IIS) management tools by default.</span></span> <span data-ttu-id="ef11c-177">Si desea instalar las herramientas de administración en el mismo servidor que el de la puerta de enlace de Windows PowerShell Web Access, agregue el parámetro <span class="code">IncludeManagementTools</span> al comando de instalación (como se indica en este paso).</span><span class="sxs-lookup"><span data-stu-id="ef11c-177">If you want to install the management tools on the same server as the Windows PowerShell Web Access gateway, add the <span class="code">IncludeManagementTools</span> parameter to the installation command (as provided in this step).</span></span> <span data-ttu-id="ef11c-178">Si administra el sitio web de Windows PowerShell Web Access desde un equipo remoto, instale el complemento Administrador de IIS mediante la instalación de las <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Herramientas de administración remota del servidor para Windows 8.1</a> o <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Herramientas de administración remota del servidor para Windows 8</a> en el equipo desde el cual desea administrar la puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="ef11c-178">If you are managing the Windows PowerShell Web Access website from a remote computer, install the IIS Manager snap-in by installing <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Remote Server Administration Tools for Windows 8.1</a> or <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Remote Server Administration Tools for Windows 8</a> on the computer from which you want to manage the gateway.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="ef11c-179">Para instalar roles y características en un VHD sin conexión, debe agregar los parámetros <span class="code">ComputerName</span> y <span class="code">VHD</span>.</span><span class="sxs-lookup"><span data-stu-id="ef11c-179">To install roles and features on an offline VHD, you must add both the <span class="code">ComputerName</span> parameter and the <span class="code">VHD</span> parameter.</span></span> <span data-ttu-id="ef11c-180">El parámetro <span class="code">ComputerName</span> contiene el nombre del servidor en el que se montará el VHD y el parámetro <span class="code">VHD</span> contiene la ruta de acceso al archivo VHD en el servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="ef11c-180">The <span class="code">ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="ef11c-181">Copy</span><span class="sxs-lookup"><span data-stu-id="ef11c-181">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_d841d509-347e-49d0-bf54-8d1f306bece6'); "Copy to clipboard.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart

3.  <span data-ttu-id="ef11c-182">Una vez completada la instalación, compruebe que Windows PowerShell Web Access se haya instalado en los servidores de destino mediante la ejecución del cmdlet **Get-WindowsFeature** en un servidor de destino, en una consola de Windows PowerShell abierta con derechos de usuario elevados.</span><span class="sxs-lookup"><span data-stu-id="ef11c-182">When installation is complete, verify that Windows PowerShell Web Access was installed on destination servers by running the **Get-WindowsFeature** cmdlet on a destination server, in a Windows PowerShell console that has been opened with elevated user rights.</span></span> <span data-ttu-id="ef11c-183">Otro modo de comprobar que se haya instalado Windows PowerShell Web Access en la consola del Administrador del servidor consiste en seleccionar un servidor de destino en la página **Todos los servidores** y, a continuación, visualizar el icono **Roles y características** del servidor seleccionado.</span><span class="sxs-lookup"><span data-stu-id="ef11c-183">You can also verify that Windows PowerShell Web Access was installed in the Server Manager console, by selecting a destination server on the **All Servers** page, and then viewing the **Roles and Features** tile for the selected server.</span></span> <span data-ttu-id="ef11c-184">También puede ver el archivo Léame para Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-184">You can also view the readme file for Windows PowerShell Web Access.</span></span>

4.  <span data-ttu-id="ef11c-185">Una vez instalado Windows PowerShell Web Access, se le pedirá que revise el archivo Léame, que contiene las instrucciones de configuración necesarias básicas para la puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="ef11c-185">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="ef11c-186">Estas instrucciones de configuración también se encuentran en la sección siguiente, [Paso 2: Configurar la puerta de enlace](#BKMK_step2).</span><span class="sxs-lookup"><span data-stu-id="ef11c-186">These setup instructions are also in the following section, [Step 2: Configure the gateway](#BKMK_step2).</span></span> <span data-ttu-id="ef11c-187">La ruta de acceso al archivo Léame es <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span><span class="sxs-lookup"><span data-stu-id="ef11c-187">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

<a href="" id="BKMK_step2"></a>
###

<span data-ttu-id="ef11c-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Paso 2: Configurar la puerta de enlace</span></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ef11c-189">El cmdlet **Install-PswaWebApplication** es un método rápido para configurar Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-189">The **Install-PswaWebApplication** cmdlet is a quick way to get Windows PowerShell Web Access configured.</span></span> <span data-ttu-id="ef11c-190">Si bien puede agregar el parámetro <span class="code">UseTestCertificate</span> al cmdlet <span class="code">Install-PswaWebApplication</span> para instalar un certificado SSL autofirmado con fines de prueba, esto no es seguro. En un entorno de producción seguro, siempre use un certificado SSL válido firmado por una entidad de certificación (CA).</span><span class="sxs-lookup"><span data-stu-id="ef11c-190">Although you can add the <span class="code">UseTestCertificate</span> parameter to the <span class="code">Install-PswaWebApplication</span> cmdlet to install a self-signed SSL certificate for test purposes, this is not secure; for a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="ef11c-191">Los administradores pueden reemplazar el certificado de prueba por un certificado firmado de su elección mediante la consola del Administrador de IIS.</span><span class="sxs-lookup"><span data-stu-id="ef11c-191">Administrators can replace the test certificate with a signed certificate of their choice by using the IIS Manager console.</span></span>

<span data-ttu-id="ef11c-192">Puede completar la configuración de la aplicación web Windows PowerShell Web Access mediante la ejecución del cmdlet <span class="code">Install-PswaWebApplication</span> o mediante los pasos de configuración basados en GUI del Administrador de IIS.</span><span class="sxs-lookup"><span data-stu-id="ef11c-192">You can complete Windows PowerShell Web Access web application configuration either by running the <span class="code">Install-PswaWebApplication</span> cmdlet or by performing GUI-based configuration steps in IIS Manager.</span></span> <span data-ttu-id="ef11c-193">De manera predeterminada, el cmdlet instala la aplicación web, **pswa** (y un grupo de aplicaciones, **pswa\_pool**), en el contenedor **Sitio web predeterminado**, como se muestra en el Administrador de IIS. Si lo desea, puede indicar al cmdlet que cambie el contenedor de sitio predeterminado de la aplicación web.</span><span class="sxs-lookup"><span data-stu-id="ef11c-193">By default, the cmdlet installs the web application, **pswa** (and an application pool for it, **pswa_pool**), in the **Default Web Site** container, as shown in IIS Manager; if desired, you can instruct the cmdlet to change the default site container of the web application.</span></span> <span data-ttu-id="ef11c-194">El Administrador de IIS proporciona opciones de configuración que se encuentran disponibles para las aplicaciones web, como cambiar el número de puerto o el certificado de Capa de sockets seguros (SSL).</span><span class="sxs-lookup"><span data-stu-id="ef11c-194">IIS Manager offers configuration options that are available for web applications, such as changing the port number or the Secure Sockets Layer (SSL) certificate.</span></span>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="ef11c-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle">Nota de seguridad</span></span><span class="sxs-lookup"><span data-stu-id="ef11c-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="ef11c-196">Se recomienda encarecidamente que los administradores configuren la puerta de enlace para que use un certificado válido firmado por una CA.</span><span class="sxs-lookup"><span data-stu-id="ef11c-196">We strongly recommend that administrators configure the gateway to use a valid certificate that has been signed by a CA.</span></span></p></td>
</tr>
</tbody>
</table>

-   [<span data-ttu-id="ef11c-197">Para configurar la puerta de enlace de Windows PowerShell Web Access con un certificado de prueba mediante Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="ef11c-197">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>](#BKMK_testcert)

-   [<span data-ttu-id="ef11c-198">Para configurar la puerta de enlace de Windows PowerShell Web Access con un certificado original mediante Install-PswaWebApplication y el Administrador de IIS</span><span class="sxs-lookup"><span data-stu-id="ef11c-198">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>](#BKMK_gencert)

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a><span data-ttu-id="ef11c-199">Para configurar la puerta de enlace de Windows PowerShell Web Access con un certificado de prueba mediante Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="ef11c-199">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>

1.  <span data-ttu-id="ef11c-200">Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef11c-200">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="ef11c-201">En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell** en la barra de tareas.</span><span class="sxs-lookup"><span data-stu-id="ef11c-201">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="ef11c-202">En la pantalla **Inicio** de Windows, haga clic en **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-202">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="ef11c-203">Escriba lo siguiente y, después, presione **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-203">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="ef11c-204">**Install-PswaWebApplication -UseTestCertificate**</span><span class="sxs-lookup"><span data-stu-id="ef11c-204">**Install-PswaWebApplication -UseTestCertificate**</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="ef11c-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle">Nota de seguridad</span></span><span class="sxs-lookup"><span data-stu-id="ef11c-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="ef11c-206">El parámetro <span class="code">UseTestCertificate</span> solo debe usarse en un entorno de prueba privado.</span><span class="sxs-lookup"><span data-stu-id="ef11c-206">The <span class="code">UseTestCertificate</span> parameter should only be used in a private test environment.</span></span> <span data-ttu-id="ef11c-207">Para un entorno de producción seguro, se recomienda usar un certificado válido firmado por una CA.</span><span class="sxs-lookup"><span data-stu-id="ef11c-207">For a secure production environment, we recommend using a valid certificate that has been signed by a CA.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="ef11c-208">La ejecución del cmdlet instala la aplicación web Windows PowerShell Web Access dentro del contenedor Sitio web predeterminado de IIS.</span><span class="sxs-lookup"><span data-stu-id="ef11c-208">Running the cmdlet installs the Windows PowerShell Web Access web application within the IIS Default Web Site container.</span></span> <span data-ttu-id="ef11c-209">El cmdlet crea la infraestructura necesaria para ejecutar Windows PowerShell Web Access en el sitio web predeterminado, https://&lt;server_name&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="ef11c-209">The cmdlet creates the infrastructure required to run Windows PowerShell Web Access on the default website, https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="ef11c-210">Para instalar la aplicación web en otro sitio web, proporcione el nombre del sitio web mediante la adición del parámetro <span class="code">WebSiteName</span>.</span><span class="sxs-lookup"><span data-stu-id="ef11c-210">To install the web application in a different website, provide the website name by adding the <span class="code">WebSiteName</span> parameter.</span></span> <span data-ttu-id="ef11c-211">Para cambiar el nombre de la aplicación web (el nombre predeterminado es <span class="code">pswa</span>), agregue el parámetro <span class="code">WebApplicationName</span>.</span><span class="sxs-lookup"><span data-stu-id="ef11c-211">To change the name of the web application (the default is <span class="code">pswa</span>), add the <span class="code">WebApplicationName</span> parameter.</span></span>

    <span data-ttu-id="ef11c-212">La siguiente configuración se establece mediante la ejecución del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ef11c-212">The following settings are configured by running the cmdlet.</span></span> <span data-ttu-id="ef11c-213">Puede cambiarla de forma manual en la consola del Administrador de IIS, si lo desea.</span><span class="sxs-lookup"><span data-stu-id="ef11c-213">You can change these manually in the IIS Manager console, if desired.</span></span>

    -   <span data-ttu-id="ef11c-214">Path: /pswa</span><span class="sxs-lookup"><span data-stu-id="ef11c-214">Path: /pswa</span></span>

    -   <span data-ttu-id="ef11c-215">ApplicationPool: pswa_pool</span><span class="sxs-lookup"><span data-stu-id="ef11c-215">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="ef11c-216">EnabledProtocols: http</span><span class="sxs-lookup"><span data-stu-id="ef11c-216">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="ef11c-217">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="ef11c-217">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

    <span data-ttu-id="ef11c-218"><span class="label">Ejemplo:</span> <span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span><span class="sxs-lookup"><span data-stu-id="ef11c-218"><span class="label">Example:</span> <span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span></span>

    <span data-ttu-id="ef11c-219">En este ejemplo, el sitio web resultante para Windows PowerShell Web Access es https://&lt; *server_name*&gt;/myWebApp.</span><span class="sxs-lookup"><span data-stu-id="ef11c-219">In this example, the resulting website for Windows PowerShell Web Access is https://&lt; *server_name*&gt;/myWebApp.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="ef11c-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="ef11c-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="ef11c-221">No podrá iniciar sesión hasta que se haya concedido a los usuarios acceso al sitio web mediante la adición de reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="ef11c-221">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="ef11c-222">Para obtener más información, consulte <a href="#BKMK_step3">Paso 3: Configurar una regla de autorización restrictiva</a> y <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Reglas de autorización y características de seguridad de Windows PowerShell Web Access</a>.</span><span class="sxs-lookup"><span data-stu-id="ef11c-222">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table>

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a><span data-ttu-id="ef11c-223">Para configurar la puerta de enlace de Windows PowerShell Web Access con un certificado original mediante Install-PswaWebApplication y el Administrador de IIS</span><span class="sxs-lookup"><span data-stu-id="ef11c-223">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>

1.  <span data-ttu-id="ef11c-224">Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef11c-224">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="ef11c-225">En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell** en la barra de tareas.</span><span class="sxs-lookup"><span data-stu-id="ef11c-225">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="ef11c-226">En la pantalla **Inicio** de Windows, haga clic en **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-226">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="ef11c-227">Escriba lo siguiente y, después, presione **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-227">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="ef11c-228">**Install-PswaWebApplication**</span><span class="sxs-lookup"><span data-stu-id="ef11c-228">**Install-PswaWebApplication**</span></span>

    <span data-ttu-id="ef11c-229">La siguiente configuración de puerta de enlace se establece mediante la ejecución del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ef11c-229">The following gateway settings are configured by running the cmdlet.</span></span> <span data-ttu-id="ef11c-230">Puede cambiarla de forma manual en la consola del Administrador de IIS, si lo desea.</span><span class="sxs-lookup"><span data-stu-id="ef11c-230">You can change these manually in the IIS Manager console, if desired.</span></span> <span data-ttu-id="ef11c-231">También puede especificar valores para los parámetros <span class="code">WebsiteName</span> y <span class="code">WebApplicationName</span> del cmdlet <span class="code">Install-PswaWebApplication</span>.</span><span class="sxs-lookup"><span data-stu-id="ef11c-231">You can also specify values for the <span class="code">WebsiteName</span> and <span class="code">WebApplicationName</span> parameters of the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span>

    -   <span data-ttu-id="ef11c-232">Path: /pswa</span><span class="sxs-lookup"><span data-stu-id="ef11c-232">Path: /pswa</span></span>

    -   <span data-ttu-id="ef11c-233">ApplicationPool: pswa_pool</span><span class="sxs-lookup"><span data-stu-id="ef11c-233">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="ef11c-234">EnabledProtocols: http</span><span class="sxs-lookup"><span data-stu-id="ef11c-234">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="ef11c-235">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="ef11c-235">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

3.  <span data-ttu-id="ef11c-236">Abra la consola del Administrador de IIS mediante uno de los siguientes procedimientos.</span><span class="sxs-lookup"><span data-stu-id="ef11c-236">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="ef11c-237">En el escritorio de Windows, haga clic en **Administrador del servidor** en la barra de tareas de Windows para iniciar el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="ef11c-237">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="ef11c-238">En el menú **Herramientas** del Administrador del servidor, haga clic en **Administrador de Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-238">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="ef11c-239">En la pantalla **Inicio** de Windows, haga clic en **Administrador del servidor**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-239">On the Windows **Start** screen, click **Server Manager**.</span></span>

4.  <span data-ttu-id="ef11c-240">En el panel del árbol del Administrador de IIS, expanda el nodo del servidor en el que está instalado Windows PowerShell Web Access hasta que aparezca la carpeta **Sitios**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-240">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="ef11c-241">Expanda la carpeta **Sitios**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-241">Expand the **Sites** folder.</span></span>

5.  <span data-ttu-id="ef11c-242">Seleccione el sitio web en el que ha instalado la aplicación web Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-242">Select the website in which you have installed the Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="ef11c-243">En el panel **Acciones**, haga clic en **Enlaces**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-243">In the **Actions** pane, click **Bindings**.</span></span>

6.  <span data-ttu-id="ef11c-244">En el cuadro de diálogo **Enlaces de sitios**, haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-244">In the **Site Binding** dialog box, click **Add**.</span></span>

7.  <span data-ttu-id="ef11c-245">En el cuadro de diálogo **Agregar enlace de sitio**, en el campo **Tipo**, seleccione **https**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-245">In the **Add Site Binding** dialog box, in the **Type** field, select **https**.</span></span>

8.  <span data-ttu-id="ef11c-246">En el campo **Certificado SSL**, seleccione su certificado firmado en el menú desplegable.</span><span class="sxs-lookup"><span data-stu-id="ef11c-246">In the **SSL certificate** field, select your signed certificate from the drop-down menu.</span></span> <span data-ttu-id="ef11c-247">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-247">Click **OK**.</span></span> <span data-ttu-id="ef11c-248">Consulte [Para configurar un certificado SSL en el Administrador de IIS](#BKMK_cert) en este tema para obtener más información sobre cómo obtener un certificado.</span><span class="sxs-lookup"><span data-stu-id="ef11c-248">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

    <span data-ttu-id="ef11c-249">La aplicación web Windows PowerShell Web Access ya está configurada para usar su certificado SSL firmado.</span><span class="sxs-lookup"><span data-stu-id="ef11c-249">The Windows PowerShell Web Access web application is now configured to use your signed SSL certificate.</span></span> <span data-ttu-id="ef11c-250">Para obtener acceso a Windows PowerShell Web Access, abra https://&lt;server_name&gt;/pswa en una ventana del explorador.</span><span class="sxs-lookup"><span data-stu-id="ef11c-250">You can access Windows PowerShell Web Access by opening https://&lt;server_name&gt;/pswa in a browser window.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="ef11c-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="ef11c-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="ef11c-252">No podrá iniciar sesión hasta que se haya concedido a los usuarios acceso al sitio web mediante la adición de reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="ef11c-252">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="ef11c-253">Para obtener más información, consulte <a href="#BKMK_step3">Paso 3: Configurar una regla de autorización restrictiva</a> y <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Reglas de autorización y características de seguridad de Windows PowerShell Web Access</a>.</span><span class="sxs-lookup"><span data-stu-id="ef11c-253">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table><span data-ttu-id="ef11c-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Paso 3: Configurar una regla de autorización restrictiva</span></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ef11c-255">Una vez instalado Windows PowerShell Web Access y configurada la puerta de enlace, los usuarios podrán abrir la página de inicio de sesión en un explorador, pero no podrán iniciar sesión hasta que el administrador de Windows PowerShell Web Access les conceda acceso de manera explícita.</span><span class="sxs-lookup"><span data-stu-id="ef11c-255">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="ef11c-256">El control de acceso de Windows PowerShell Web Access se administra mediante el conjunto de cmdlets de Windows PowerShell descrito en la siguiente tabla.</span><span class="sxs-lookup"><span data-stu-id="ef11c-256">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="ef11c-257">No existe una GUI comparable para agregar o administrar reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="ef11c-257">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="ef11c-258">Para obtener más información sobre los cmdlets de Windows PowerShell Web Access, consulte los temas de referencia de cmdlet, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx) (Cmdlets de Windows PowerShell Web Access).</span><span class="sxs-lookup"><span data-stu-id="ef11c-258">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="ef11c-259">Para obtener más información sobre la seguridad y las reglas de autorización de Windows PowerShell Web Access, consulte [Reglas de autorización y características de seguridad de Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="ef11c-259">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="ef11c-260">Para agregar una regla de autorización restrictiva</span><span class="sxs-lookup"><span data-stu-id="ef11c-260">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="ef11c-261">Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell con derechos de usuario elevados.</span><span class="sxs-lookup"><span data-stu-id="ef11c-261">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="ef11c-262">En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell**, en la barra de tareas y, luego,en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-262">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="ef11c-263">En la pantalla **Inicio** de Windows, haga clic con el botón derecho en **Windows PowerShell** y, luego, en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-263">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="ef11c-264"><span class="label">Paso opcional para restringir el acceso del usuario mediante configuraciones de sesión:</span> Compruebe que las configuraciones de sesión que quiere usar en las reglas ya existen.</span><span class="sxs-lookup"><span data-stu-id="ef11c-264"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="ef11c-265">Si aún no se han creado, use las instrucciones para crear configuraciones de sesión proporcionadas en [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) (Acerca de los archivos de configuración de sesión) en MSDN.</span><span class="sxs-lookup"><span data-stu-id="ef11c-265">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="ef11c-266">Escriba lo siguiente y, después, presione **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-266">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="ef11c-267">Copy</span><span class="sxs-lookup"><span data-stu-id="ef11c-267">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_f9e7959b-75d0-4d63-8f8e-02334a8dd09d'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="ef11c-268">Esta regla de autorización concede a un usuario específico acceso a un equipo de la red al que tiene acceso normalmente, con acceso a una configuración de sesión determinada en el ámbito de las necesidades de cmdlet y scripting típicas del usuario.</span><span class="sxs-lookup"><span data-stu-id="ef11c-268">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="ef11c-269">En el siguiente ejemplo, se concede acceso a un usuario llamado <span class="code">JSmith</span> en el dominio <span class="code">Contoso</span> para administrar el equipo <span class="code">Contoso_214</span> y usar una configuración de sesión llamada <span class="code">NewAdminsOnly</span>.</span><span class="sxs-lookup"><span data-stu-id="ef11c-269">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="ef11c-270">Copy</span><span class="sxs-lookup"><span data-stu-id="ef11c-270">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ebd5bc5e-ec5d-4955-a86a-63843e480e37'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="ef11c-271">Compruebe que se ha creado la regla ejecutando el cmdlet **Get-PswaAuthorizationRule** o **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span><span class="sxs-lookup"><span data-stu-id="ef11c-271">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="ef11c-272">Por ejemplo, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-272">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="ef11c-273">Después de configurar una regla de autorización, está listo para que los usuarios autorizados inicien sesión en la consola basada en web y empiecen a usar Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-273">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_custom"></a>

<span data-ttu-id="ef11c-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Implementación personalizada</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ef11c-275">Puede instalar la puerta de enlace de Windows PowerShell Web Access en un servidor que ejecuta Windows Server 2012 R2 o Windows Server 2012 mediante el uso del Asistente para agregar roles y características en el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="ef11c-275">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using the Add Roles and Features Wizard in Server Manager.</span></span> <span data-ttu-id="ef11c-276">Después de instalar Windows PowerShell Web Access, puede personalizar la configuración de la puerta de enlace en el Administrador de IIS.</span><span class="sxs-lookup"><span data-stu-id="ef11c-276">After Windows PowerShell Web Access is installed, you can customize the configuration of the gateway in IIS Manager.</span></span>

<a href="" id="BKMK_custom1"></a>
###

<span data-ttu-id="ef11c-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Paso 1: Instalar Windows PowerShell Web Access</span></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a><span data-ttu-id="ef11c-278">Para instalar Windows PowerShell Web Access mediante el Asistente para agregar roles y características</span><span class="sxs-lookup"><span data-stu-id="ef11c-278">To install Windows PowerShell Web Access by using the Add Roles and Features Wizard</span></span>

1.  <span data-ttu-id="ef11c-279">Si ya se ha abierto el Administrador del servidor, vaya al siguiente paso.</span><span class="sxs-lookup"><span data-stu-id="ef11c-279">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="ef11c-280">Si todavía no se ha abierto el Administrador del servidor, ábralo mediante una de las siguientes acciones.</span><span class="sxs-lookup"><span data-stu-id="ef11c-280">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="ef11c-281">En el escritorio de Windows, haga clic en **Administrador del servidor** en la barra de tareas de Windows para iniciar el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="ef11c-281">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="ef11c-282">En la pantalla **Inicio** de Windows, haga clic en **Administrador del servidor**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-282">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="ef11c-283">En el menú **Administrar**, haga clic en **Agregar roles y características**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-283">On the **Manage** menu, click **Add Roles and Features**.</span></span>

3.  <span data-ttu-id="ef11c-284">En la página **Seleccionar tipo de instalación**, seleccione **Instalación basada en características o en roles**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-284">On the **Select installation type** page, select **Role-based or feature-based installation**.</span></span> <span data-ttu-id="ef11c-285">Haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-285">Click **Next**.</span></span>

4.  <span data-ttu-id="ef11c-286">En la página **Seleccionar servidor de destino**, seleccione un servidor del grupo de servidores o un VHD sin conexión.</span><span class="sxs-lookup"><span data-stu-id="ef11c-286">On the **Select destination server** page, select a server from the server pool, or select an offline VHD.</span></span> <span data-ttu-id="ef11c-287">Para seleccionar un VHD sin conexión como servidor de destino, primero seleccione el servidor en el que montará el VHD y, a continuación, seleccione el archivo VHD.</span><span class="sxs-lookup"><span data-stu-id="ef11c-287">To select an offline VHD as your destination server, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="ef11c-288">Para obtener información sobre cómo agregar servidores al grupo de servidores, consulte la Ayuda del Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="ef11c-288">For information about how to add servers to your server pool, see the Server Manager Help.</span></span> <span data-ttu-id="ef11c-289">Una vez seleccionado el servidor de destino, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-289">After you have selected the destination server, click **Next**.</span></span>

5.  <span data-ttu-id="ef11c-290">En la página **Seleccionar características** del asistente, expanda **Windows PowerShell** y seleccione **Windows PowerShell Web Access**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-290">On the **Select features** page of the wizard, expand **Windows PowerShell**, and then select **Windows PowerShell Web Access**.</span></span>

6.  <span data-ttu-id="ef11c-291">Se le pedirá que agregue las características necesarias, como .NET Framework 4.5 y los servicios de rol de Servidor web (IIS).</span><span class="sxs-lookup"><span data-stu-id="ef11c-291">Note that you are prompted to add required features, such as .NET Framework 4.5, and role services of Web Server (IIS).</span></span> <span data-ttu-id="ef11c-292">Agregue las características necesarias y continúe.</span><span class="sxs-lookup"><span data-stu-id="ef11c-292">Add required features and continue.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="ef11c-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="ef11c-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="ef11c-294">Al instalar Windows PowerShell Web Access mediante el uso del Asistente para agregar roles y características también se instala Servidor web (IIS), incluido el complemento Administrador de IIS.</span><span class="sxs-lookup"><span data-stu-id="ef11c-294">Installing Windows PowerShell Web Access by using the Add Roles and Features Wizard also installs Web Server (IIS), including the IIS Manager snap-in.</span></span> <span data-ttu-id="ef11c-295">El complemento y otras herramientas de administración de IIS se instalan de manera predeterminada si usa el Asistente para agregar roles y características.</span><span class="sxs-lookup"><span data-stu-id="ef11c-295">The snap-in and other IIS management tools are installed by default if you use Add Roles and Features Wizard.</span></span> <span data-ttu-id="ef11c-296">Si instala Windows PowerShell Web Access mediante cmdlets de Windows PowerShell, como se describe en el siguiente procedimiento, las herramientas de administración no se agregan de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="ef11c-296">If you install Windows PowerShell Web Access by using Windows PowerShell cmdlets as described in the following procedure, management tools are not added by default.</span></span></p></td>
    </tr>
    </tbody>
    </table>

7.  <span data-ttu-id="ef11c-297">En la página **Confirmar selecciones de instalación**, si los archivos de características para Windows PowerShell Web Access no están almacenados en el servidor de destino seleccionado en el paso 4, haga clic en **Especifique una ruta de acceso de origen alternativa** y proporcione la ruta de acceso a los archivos de características.</span><span class="sxs-lookup"><span data-stu-id="ef11c-297">On the **Confirm installation selections** page, if the feature files for Windows PowerShell Web Access are not stored on the destination server that you selected in step 4, click **Specify an alternate source path**, and provide the path to the feature files.</span></span> <span data-ttu-id="ef11c-298">De lo contrario, haga clic en **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-298">Otherwise, click **Install**.</span></span>

8.  <span data-ttu-id="ef11c-299">Después de hacer clic en **Instalar**, la página **Progreso de la instalación** mostrará el progreso de la instalación, los resultados y diferentes mensajes, como advertencias, errores o los pasos de configuración posteriores a la instalación necesarios para Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-299">After you click **Install**, the **Installation progress** page displays installation progress, results, and messages such as warnings, failures, or post-installation configuration steps that are required for Windows PowerShell Web Access.</span></span> <span data-ttu-id="ef11c-300">Una vez instalado Windows PowerShell Web Access, se le pedirá que revise el archivo Léame, que contiene las instrucciones de configuración necesarias básicas para la puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="ef11c-300">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="ef11c-301">Estas instrucciones también se incluyen en este tema.</span><span class="sxs-lookup"><span data-stu-id="ef11c-301">These instructions are also included in this topic.</span></span> <span data-ttu-id="ef11c-302">La ruta de acceso al archivo Léame es <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span><span class="sxs-lookup"><span data-stu-id="ef11c-302">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

###

<span data-ttu-id="ef11c-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Paso 2: Configurar la puerta de enlace</span></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ef11c-304">Las instrucciones de esta sección explican cómo instalar la aplicación web Windows PowerShell Web Access en un subdirectorio del sitio web, no en el directorio raíz.</span><span class="sxs-lookup"><span data-stu-id="ef11c-304">Instructions in this section are for installing the Windows PowerShell Web Access web application in a subdirectory—and not in the root directory—of your website.</span></span> <span data-ttu-id="ef11c-305">Este procedimiento es el equivalente basado en GUI de las acciones realizadas por el cmdlet <span class="code">Install-PswaWebApplication</span>.</span><span class="sxs-lookup"><span data-stu-id="ef11c-305">This procedure is the GUI-based equivalent of the actions performed by the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span> <span data-ttu-id="ef11c-306">En esta sección, también se incluyen instrucciones sobre cómo usar el Administrador de IIS para configurar la puerta de enlace de Windows PowerShell Web Access como un sitio web raíz.</span><span class="sxs-lookup"><span data-stu-id="ef11c-306">This section also includes instructions for how to use IIS Manager to configure the Windows PowerShell Web Access gateway as a root website.</span></span>

-   [<span data-ttu-id="ef11c-307">Para usar el Administrador de IIS para configurar la puerta de enlace en un sitio web existente</span><span class="sxs-lookup"><span data-stu-id="ef11c-307">To use IIS Manager to configure the gateway in an existing website</span></span>](#BKMK_configman)

-   [<span data-ttu-id="ef11c-308">Para usar el Administrador de IIS para configurar la puerta de enlace como sitio web raíz con un certificado de prueba</span><span class="sxs-lookup"><span data-stu-id="ef11c-308">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>](#BKMK_configroot)

-   

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a><span data-ttu-id="ef11c-309">Para usar el Administrador de IIS para configurar la puerta de enlace en un sitio web existente</span><span class="sxs-lookup"><span data-stu-id="ef11c-309">To use IIS Manager to configure the gateway in an existing website</span></span>

1.  <span data-ttu-id="ef11c-310">Abra la consola del Administrador de IIS mediante uno de los siguientes procedimientos.</span><span class="sxs-lookup"><span data-stu-id="ef11c-310">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="ef11c-311">En el escritorio de Windows, haga clic en **Administrador del servidor** en la barra de tareas de Windows para iniciar el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="ef11c-311">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="ef11c-312">En el menú **Herramientas** del Administrador del servidor, haga clic en **Administrador de Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-312">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="ef11c-313">En la pantalla **Inicio** de Windows, escriba cualquier parte del nombre **Administrador de Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-313">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="ef11c-314">Haga clic en el acceso directo cuando se muestre en los resultados de **Aplicaciones**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-314">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="ef11c-315">Cree un nuevo grupo de aplicaciones para Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-315">Create a new application pool for Windows PowerShell Web Access.</span></span> <span data-ttu-id="ef11c-316">Expanda el nodo del servidor de puerta de enlace en el panel del árbol del Administrador de IIS, seleccione **Grupos de aplicaciones** y haga clic en **Agregar grupo de aplicaciones** en el panel **Acciones**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-316">Expand the node of the gateway server in the IIS Manager tree pane, select **Application Pools**, and click **Add Application Pool** in the **Actions** pane.</span></span>

3.  <span data-ttu-id="ef11c-317">Agregue un nuevo grupo de aplicaciones con el nombre **pswa_pool** o proporcione otro nombre.</span><span class="sxs-lookup"><span data-stu-id="ef11c-317">Add a new application pool with the name **pswa_pool**, or provide another name.</span></span> <span data-ttu-id="ef11c-318">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-318">Click **OK**.</span></span>

4.  <span data-ttu-id="ef11c-319">En el panel del árbol del Administrador de IIS, expanda el nodo del servidor en el que está instalado Windows PowerShell Web Access hasta que aparezca la carpeta **Sitios**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-319">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="ef11c-320">Seleccione la carpeta **Sitios**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-320">Select the **Sites** folder.</span></span>

5.  <span data-ttu-id="ef11c-321">Haga clic con el botón derecho en el sitio web (por ejemplo, **Sitio web predeterminado**) en el que quiere agregar el sitio web de Windows PowerShell Web Access y, después, haga clic en **Agregar aplicación**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-321">Right-click the website (for example, **Default Web Site**) to which you would like to add the Windows PowerShell Web Access website, and then click **Add Application**.</span></span>

6.  <span data-ttu-id="ef11c-322">En el campo **Alias**, escriba pswa o proporcione un alias diferente.</span><span class="sxs-lookup"><span data-stu-id="ef11c-322">In the **Alias** field, type pswa, or provide another alias.</span></span> <span data-ttu-id="ef11c-323">El alias se convierte en el nombre de directorio virtual.</span><span class="sxs-lookup"><span data-stu-id="ef11c-323">The alias becomes the virtual directory name.</span></span> <span data-ttu-id="ef11c-324">Por ejemplo, **pswa** en la siguiente dirección URL representa el alias especificado en este paso: https://&lt;server_name&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="ef11c-324">For example, **pswa** in the following URL represents the alias specified in this step: https://&lt;server_name&gt;/pswa.</span></span>

7.  <span data-ttu-id="ef11c-325">En el campo **Grupo de aplicaciones**, seleccione el grupo de aplicaciones creado en el paso 3.</span><span class="sxs-lookup"><span data-stu-id="ef11c-325">In the **Application pool** field, select the application pool that you created in step 3.</span></span>

8.  <span data-ttu-id="ef11c-326">En el campo **Ruta de acceso física**, busque la ubicación de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ef11c-326">In the **Physical path** field, browse for the location of the application.</span></span> <span data-ttu-id="ef11c-327">Puede usar la ubicación predeterminada %windir%/Web/PowerShellWebAccess/wwwroot.</span><span class="sxs-lookup"><span data-stu-id="ef11c-327">You can use the default location, %windir%/Web/PowerShellWebAccess/wwwroot.</span></span> <span data-ttu-id="ef11c-328">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-328">Click **OK**.</span></span>

9.  <span data-ttu-id="ef11c-329">Siga los pasos del procedimiento [Para configurar un certificado SSL en el Administrador de IIS](#BKMK_cert) en este tema.</span><span class="sxs-lookup"><span data-stu-id="ef11c-329">Follow the steps in the procedure [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic.</span></span>

10. <span data-ttu-id="ef11c-330"><span class="label">Paso de seguridad opcional:</span> con el sitio web seleccionado en el panel del árbol, haga doble clic en **Configuración de SSL** en el panel de contenido.</span><span class="sxs-lookup"><span data-stu-id="ef11c-330"><span class="label">Optional security step:</span> With the website selected in the tree pane, double-click **SSL Settings** in the content pane.</span></span> <span data-ttu-id="ef11c-331">Seleccione **Requerir SSL** y, a continuación, en el panel **Acciones**, haga clic en **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-331">Select **Require SSL**, and then in the **Actions** pane, click **Apply**.</span></span> <span data-ttu-id="ef11c-332">De forma opcional, en el panel **Configuración de SSL**, puede requerir que los usuarios que se conecten al sitio web de Windows PowerShell Web Access tengan certificados de cliente.</span><span class="sxs-lookup"><span data-stu-id="ef11c-332">Optionally, in the **SSL Settings** pane, you can require that users connecting to the Windows PowerShell Web Access website have client certificates.</span></span> <span data-ttu-id="ef11c-333">Los certificados de cliente ayudan a comprobar la identidad de un usuario del dispositivo cliente.</span><span class="sxs-lookup"><span data-stu-id="ef11c-333">Client certificates help to verify the identity of a client device user.</span></span> <span data-ttu-id="ef11c-334">Para más información sobre el modo en que se puede incrementar la seguridad de Windows PowerShell Web Access al requerir certificados de cliente, consulte [Reglas de autorización y características de seguridad de Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) en esta guía.</span><span class="sxs-lookup"><span data-stu-id="ef11c-334">For more information about how requiring client certificates can increase the security of Windows PowerShell Web Access, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) in this guide.</span></span>

11. <span data-ttu-id="ef11c-335">Abra una sesión del explorador en un dispositivo cliente.</span><span class="sxs-lookup"><span data-stu-id="ef11c-335">Open a browser session on a client device.</span></span> <span data-ttu-id="ef11c-336">Para más información sobre los dispositivos y exploradores admitidos, consulte [Compatibilidad con exploradores y dispositivos cliente](#BKMK_browser) en este tema.</span><span class="sxs-lookup"><span data-stu-id="ef11c-336">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this topic.</span></span>

12. <span data-ttu-id="ef11c-337">Abra el nuevo sitio web de Windows PowerShell Web Access, https://&lt; *gateway_server_name*&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="ef11c-337">Open the new Windows PowerShell Web Access website, https://&lt; *gateway_server_name*&gt;/pswa.</span></span>

    <span data-ttu-id="ef11c-338">El explorador debe mostrar la página de inicio de sesión de la consola de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-338">The browser should display the Windows PowerShell Web Access console sign-in page.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="ef11c-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="ef11c-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="ef11c-340">No podrá iniciar sesión hasta que se haya concedido a los usuarios acceso al sitio web mediante la adición de reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="ef11c-340">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

13. <span data-ttu-id="ef11c-341">En una sesión de Windows PowerShell abierta con derechos de usuario elevados (Ejecutar como administrador), ejecute el siguiente script, en el que *application_pool_name* representa el nombre del grupo de aplicaciones creado en el paso 3, para conceder al grupo de aplicaciones derechos de acceso en el archivo de autorización.</span><span class="sxs-lookup"><span data-stu-id="ef11c-341">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 3, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="ef11c-342">Copy</span><span class="sxs-lookup"><span data-stu-id="ef11c-342">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c1a80a93-8fcf-4beb-a025-5f81bfb8bdae'); "Copy to clipboard.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="ef11c-343">Para ver los derechos de acceso existentes en el archivo de autorización, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="ef11c-343">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="ef11c-344">Copy</span><span class="sxs-lookup"><span data-stu-id="ef11c-344">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ac2179c2-9548-4a17-8663-267fdd105380'); "Copy to clipboard.")

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a><span data-ttu-id="ef11c-345">Para usar el Administrador de IIS para configurar la puerta de enlace como sitio web raíz con un certificado de prueba</span><span class="sxs-lookup"><span data-stu-id="ef11c-345">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>

1.  <span data-ttu-id="ef11c-346">Abra la consola del Administrador de IIS mediante uno de los siguientes procedimientos.</span><span class="sxs-lookup"><span data-stu-id="ef11c-346">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="ef11c-347">En el escritorio de Windows, haga clic en **Administrador del servidor** en la barra de tareas de Windows para iniciar el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="ef11c-347">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="ef11c-348">En el menú **Herramientas** del Administrador del servidor, haga clic en **Administrador de Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-348">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="ef11c-349">En la pantalla **Inicio** de Windows, escriba cualquier parte del nombre **Administrador de Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-349">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="ef11c-350">Haga clic en el acceso directo cuando se muestre en los resultados de **Aplicaciones**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-350">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="ef11c-351">En el panel del árbol del Administrador de IIS, expanda el nodo del servidor en el que está instalado Windows PowerShell Web Access hasta que aparezca la carpeta **Sitios**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-351">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="ef11c-352">Seleccione la carpeta **Sitios**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-352">Select the **Sites** folder.</span></span>

3.  <span data-ttu-id="ef11c-353">En el panel **Acciones**, haga clic en **Agregar sitio web**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-353">In the **Actions** pane, click **Add Website**.</span></span>

4.  <span data-ttu-id="ef11c-354">Escriba un nombre para el sitio web, como **Windows PowerShell Web Access**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-354">Type a name for the website, such as **Windows PowerShell Web Access**.</span></span>

5.  <span data-ttu-id="ef11c-355">Se creará automáticamente un grupo de aplicaciones para el nuevo sitio web.</span><span class="sxs-lookup"><span data-stu-id="ef11c-355">An application pool is automatically created for the new website.</span></span> <span data-ttu-id="ef11c-356">Para usar un grupo de aplicaciones diferente, haga clic en **Seleccionar** para seleccionar un grupo de aplicaciones a fin de asociarlo con el nuevo sitio web.</span><span class="sxs-lookup"><span data-stu-id="ef11c-356">To use a different application pool, click **Select** to select an application pool to associate with the new website.</span></span> <span data-ttu-id="ef11c-357">Seleccione el grupo de aplicaciones alternativo en el cuadro de diálogo **Seleccionar grupo de aplicaciones** y, después, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-357">Select the alternate application pool in the **Select Application Pool** dialog box, and then click **OK**.</span></span>

6.  <span data-ttu-id="ef11c-358">En el cuadro de texto **Ruta de acceso física**, vaya a %*windir*%/Web/PowerShellWebAccess/wwwroot.</span><span class="sxs-lookup"><span data-stu-id="ef11c-358">In the **Physical path** text box, navigate to %*windir*%/Web/PowerShellWebAccess/wwwroot.</span></span>

7.  <span data-ttu-id="ef11c-359">En el campo **Tipo** del área **Enlace**, seleccione **https**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-359">In the **Type** field of the **Binding** area, select **https**.</span></span>

8.  <span data-ttu-id="ef11c-360">Asigne al sitio web un número de puerto que no esté en uso por otro sitio o aplicación.</span><span class="sxs-lookup"><span data-stu-id="ef11c-360">Assign a port number to the website that is not already in use by another site or application.</span></span> <span data-ttu-id="ef11c-361">Para encontrar puertos abiertos, puede ejecutar el comando **netstat** en una ventana del símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="ef11c-361">To locate open ports, you can run the **netstat** command in a Command Prompt window.</span></span> <span data-ttu-id="ef11c-362">El número de puerto predeterminado es 443.</span><span class="sxs-lookup"><span data-stu-id="ef11c-362">The default port number is 443.</span></span>

    <span data-ttu-id="ef11c-363">Cambie el puerto predeterminado si otro sitio web ya está usando el 443 o por algún otro motivo de seguridad.</span><span class="sxs-lookup"><span data-stu-id="ef11c-363">Change the default port if another website is already using 443, or if you have other security reasons for changing the port number.</span></span> <span data-ttu-id="ef11c-364">Si otro sitio web que se ejecuta en el servidor de puerta de enlace está usando el puerto seleccionado, se mostrará una advertencia cuando haga clic en **Aceptar** en el cuadro de diálogo **Agregar sitio web**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-364">If another website that is running on your gateway server is using your selected port, a warning is displayed when you click **OK** in the **Add Website** dialog box.</span></span> <span data-ttu-id="ef11c-365">Debe usar un puerto que no esté en uso para ejecutar Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-365">You must use an unused port to run Windows PowerShell Web Access.</span></span>

9.  <span data-ttu-id="ef11c-366">De forma opcional, si es necesario en su organización, especifique un nombre de host que tenga sentido para la organización y los usuarios, como **www.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-366">Optionally, if needed for your organization, specify a host name that makes sense to your organization and users, such as **www.contoso.com**.</span></span> <span data-ttu-id="ef11c-367">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-367">Click **OK**.</span></span>

10. <span data-ttu-id="ef11c-368">En un entorno de producción más seguro, se recomienda encarecidamente proporcionar un certificado válido firmado por una CA.</span><span class="sxs-lookup"><span data-stu-id="ef11c-368">For a more secure production environment, we strongly recommend providing a valid certificate that has been signed by a CA.</span></span> <span data-ttu-id="ef11c-369">Debe proporcionar un certificado SSL, porque los usuarios solo se pueden conectar a Windows PowerShell Web Access a través de un sitio web HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ef11c-369">You must provide an SSL certificate, because users can only connect to Windows PowerShell Web Access through an HTTPS website.</span></span> <span data-ttu-id="ef11c-370">Consulte [Para configurar un certificado SSL en el Administrador de IIS](#BKMK_cert) en este tema para obtener más información sobre cómo obtener un certificado.</span><span class="sxs-lookup"><span data-stu-id="ef11c-370">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

11. <span data-ttu-id="ef11c-371">Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Agregar sitio web**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-371">Click **OK** to close the **Add Website** dialog box.</span></span>

12. <span data-ttu-id="ef11c-372">En una sesión de Windows PowerShell abierta con derechos de usuario elevados (Ejecutar como administrador), ejecute el siguiente script, en el que *application_pool_name* representa el nombre del grupo de aplicaciones creado en el paso 4, para conceder al grupo de aplicaciones derechos de acceso en el archivo de autorización.</span><span class="sxs-lookup"><span data-stu-id="ef11c-372">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 4, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="ef11c-373">Copy</span><span class="sxs-lookup"><span data-stu-id="ef11c-373">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_35ae9944-ca44-4af7-9c96-616083b3e3db'); "Copy to clipboard.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="ef11c-374">Para ver los derechos de acceso existentes en el archivo de autorización, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="ef11c-374">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="ef11c-375">Copy</span><span class="sxs-lookup"><span data-stu-id="ef11c-375">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0eb6d70a-2807-498b-b088-fa5233ed68d5'); "Copy to clipboard.")

        c:\windows\system32\icacls.exe $authorizationFile

13. <span data-ttu-id="ef11c-376">Con el nuevo sitio web seleccionado en el panel del árbol del Administrador de IIS, haga clic en **Inicio** en el panel **Acciones** para iniciar el sitio web.</span><span class="sxs-lookup"><span data-stu-id="ef11c-376">With the new website selected in the IIS Manager tree pane, click **Start** in the **Actions** pane to start the website.</span></span>

14. <span data-ttu-id="ef11c-377">Abra una sesión del explorador en un dispositivo cliente.</span><span class="sxs-lookup"><span data-stu-id="ef11c-377">Open a browser session on a client device.</span></span> <span data-ttu-id="ef11c-378">Para más información sobre los dispositivos y exploradores admitidos, consulte [Compatibilidad con exploradores y dispositivos cliente](#BKMK_browser) en este documento.</span><span class="sxs-lookup"><span data-stu-id="ef11c-378">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this document.</span></span>

15. <span data-ttu-id="ef11c-379">Abra el nuevo sitio web de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-379">Open the new Windows PowerShell Web Access website.</span></span>

    <span data-ttu-id="ef11c-380">Como el sitio web raíz apunta a la carpeta Windows PowerShell Web Access, el explorador debería mostrar la página de inicio de sesión de Windows PowerShell Web Access cuando abra https://&lt; *gateway_server_name*&gt;.</span><span class="sxs-lookup"><span data-stu-id="ef11c-380">Because the root website points to the Windows PowerShell Web Access folder, the browser should display the Windows PowerShell Web Access sign-in page when you open https://&lt; *gateway_server_name*&gt;.</span></span> <span data-ttu-id="ef11c-381">No será necesario que agregue **/pswa** a la dirección URL.</span><span class="sxs-lookup"><span data-stu-id="ef11c-381">You should not need to add **/pswa** to the URL.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="ef11c-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="ef11c-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="ef11c-383">No podrá iniciar sesión hasta que se haya concedido a los usuarios acceso al sitio web mediante la adición de reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="ef11c-383">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="ef11c-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Paso 3: Configurar una regla de autorización restrictiva</span></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ef11c-385">Una vez instalado Windows PowerShell Web Access y configurada la puerta de enlace, los usuarios podrán abrir la página de inicio de sesión en un explorador, pero no podrán iniciar sesión hasta que el administrador de Windows PowerShell Web Access les conceda acceso de manera explícita.</span><span class="sxs-lookup"><span data-stu-id="ef11c-385">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="ef11c-386">El control de acceso de Windows PowerShell Web Access se administra mediante el conjunto de cmdlets de Windows PowerShell descrito en la siguiente tabla.</span><span class="sxs-lookup"><span data-stu-id="ef11c-386">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="ef11c-387">No existe una GUI comparable para agregar o administrar reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="ef11c-387">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="ef11c-388">Para obtener más información sobre los cmdlets de Windows PowerShell Web Access, consulte los temas de referencia de cmdlet, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx) (Cmdlets de Windows PowerShell Web Access).</span><span class="sxs-lookup"><span data-stu-id="ef11c-388">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="ef11c-389">Para obtener más información sobre la seguridad y las reglas de autorización de Windows PowerShell Web Access, consulte [Reglas de autorización y características de seguridad de Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="ef11c-389">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="ef11c-390">Para agregar una regla de autorización restrictiva</span><span class="sxs-lookup"><span data-stu-id="ef11c-390">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="ef11c-391">Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell con derechos de usuario elevados.</span><span class="sxs-lookup"><span data-stu-id="ef11c-391">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="ef11c-392">En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell**, en la barra de tareas y, luego,en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-392">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="ef11c-393">En la pantalla **Inicio** de Windows, haga clic con el botón derecho en **Windows PowerShell** y, luego, en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-393">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="ef11c-394"><span class="label">Paso opcional para restringir el acceso del usuario mediante configuraciones de sesión:</span> Compruebe que las configuraciones de sesión que quiere usar en las reglas ya existen.</span><span class="sxs-lookup"><span data-stu-id="ef11c-394"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="ef11c-395">Si aún no se han creado, use las instrucciones para crear configuraciones de sesión proporcionadas en [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) (Acerca de los archivos de configuración de sesión) en MSDN.</span><span class="sxs-lookup"><span data-stu-id="ef11c-395">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="ef11c-396">Escriba lo siguiente y, después, presione **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-396">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="ef11c-397">Copy</span><span class="sxs-lookup"><span data-stu-id="ef11c-397">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4df22c91-f56f-4bb5-91e7-99f9b365ed5d'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="ef11c-398">Esta regla de autorización concede a un usuario específico acceso a un equipo de la red al que tiene acceso normalmente, con acceso a una configuración de sesión determinada en el ámbito de las necesidades de cmdlet y scripting típicas del usuario.</span><span class="sxs-lookup"><span data-stu-id="ef11c-398">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="ef11c-399">En el siguiente ejemplo, se concede acceso a un usuario llamado <span class="code">JSmith</span> en el dominio <span class="code">Contoso</span> para administrar el equipo <span class="code">Contoso_214</span> y usar una configuración de sesión llamada <span class="code">NewAdminsOnly</span>.</span><span class="sxs-lookup"><span data-stu-id="ef11c-399">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="ef11c-400">Copy</span><span class="sxs-lookup"><span data-stu-id="ef11c-400">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_efc3999a-2905-453f-86cd-014b41658ffc'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="ef11c-401">Compruebe que se ha creado la regla ejecutando el cmdlet **Get-PswaAuthorizationRule** o **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span><span class="sxs-lookup"><span data-stu-id="ef11c-401">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="ef11c-402">Por ejemplo, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-402">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="ef11c-403">Después de configurar una regla de autorización, está listo para que los usuarios autorizados inicien sesión en la consola basada en web y empiecen a usar Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-403">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_configcert"></a>

<span data-ttu-id="ef11c-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configurar un certificado original</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configure a genuine certificate</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ef11c-405">Para un entorno de producción seguro, se recomienda usar un certificado SSL válido firmado por una entidad de certificación (CA).</span><span class="sxs-lookup"><span data-stu-id="ef11c-405">For a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="ef11c-406">En el procedimiento descrito en esta sección se explica cómo obtener y aplicar un certificado SSL válido de una CA.</span><span class="sxs-lookup"><span data-stu-id="ef11c-406">The procedure in this section describes how to obtain and apply a valid SSL certificate from a CA.</span></span>

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a><span data-ttu-id="ef11c-407">Para configurar un certificado SSL en el Administrador de IIS</span><span class="sxs-lookup"><span data-stu-id="ef11c-407">To configure an SSL certificate in IIS Manager</span></span>

1.  <span data-ttu-id="ef11c-408">En el panel del árbol del Administrador de IIS, seleccione el servidor en el que está instalado Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef11c-408">In the IIS Manager tree pane, select the server on which Windows PowerShell Web Access is installed.</span></span>

2.  <span data-ttu-id="ef11c-409">En el panel de contenido, haga doble clic en **Certificados de servidor**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-409">In the content pane, double click **Server Certificates**.</span></span>

3.  <span data-ttu-id="ef11c-410">En el panel **Acciones**, realice una de las acciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="ef11c-410">In the **Actions** pane, do one of the following.</span></span> <span data-ttu-id="ef11c-411">Para obtener más información sobre la configuración de certificados de servidor en IIS, consulte [Configurar certificados de servidor en IIS 7](https://technet.microsoft.com/library/cc732230.aspx).</span><span class="sxs-lookup"><span data-stu-id="ef11c-411">For more information about configuring server certificates in IIS, see [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230.aspx).</span></span>

    -   <span data-ttu-id="ef11c-412">Haga clic en **Importar** para importar un certificado válido existente desde una ubicación de la red.</span><span class="sxs-lookup"><span data-stu-id="ef11c-412">Click **Import** to import an existing, valid certificate from a location on your network.</span></span>

    -   <span data-ttu-id="ef11c-413">Haga clic en **Crear una solicitud de certificado** para solicitar un certificado de una CA como VeriSign™, Thawte o GeoTrust®.</span><span class="sxs-lookup"><span data-stu-id="ef11c-413">Click **Create Certificate Request** to request a certificate from a CA such as VeriSign™, Thawte, or GeoTrust®.</span></span> <span data-ttu-id="ef11c-414">El nombre común del certificado debe coincidir con el encabezado host de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="ef11c-414">The certificate's common name must match the host header in the request.</span></span> <span data-ttu-id="ef11c-415">Por ejemplo, si el explorador del cliente solicita http://www.contoso.com/, el nombre común también deberá ser http://www.contoso.com/.</span><span class="sxs-lookup"><span data-stu-id="ef11c-415">For example, if the client browser requests http://www.contoso.com/, then the common name must also be http://www.contoso.com/.</span></span> <span data-ttu-id="ef11c-416">Esta es la opción más segura y recomendada para proporcionar la puerta de enlace de Windows PowerShell Web Access con un certificado.</span><span class="sxs-lookup"><span data-stu-id="ef11c-416">This is the most secure and recommended option for providing the Windows PowerShell Web Access gateway with a certificate.</span></span>

    -   <span data-ttu-id="ef11c-417">Haga clic en **Crear un certificado autofirmado** para crear un certificado para usarlo inmediatamente y, más tarde, hágalo firmar por una CA, si lo desea.</span><span class="sxs-lookup"><span data-stu-id="ef11c-417">Click **Create a Self-Signed Certificate** to create a certificate that you can use immediately, and have signed later by a CA if desired.</span></span> <span data-ttu-id="ef11c-418">Especifique un nombre descriptivo para el certificado autofirmado, como **Windows PowerShell Web Access**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-418">Specify a friendly name for the self-signed certificate, such as **Windows PowerShell Web Access**.</span></span> <span data-ttu-id="ef11c-419">Esta opción no se considera segura y solo se recomienda para un entorno de prueba privado.</span><span class="sxs-lookup"><span data-stu-id="ef11c-419">This option is not considered secure, and is recommended only for a private test environment.</span></span>

4.  <span data-ttu-id="ef11c-420">Una vez creado u obtenido el certificado, seleccione el sitio web al que se aplicará (por ejemplo, **Sitio web predeterminado**) en el panel del árbol del Administrador de IIS y, a continuación, haga clic en **Enlaces** en el panel **Acciones**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-420">After creating or obtaining a certificate, select the website to which the certificate is applied (for example, **Default Web Site**) in the IIS Manager tree pane, and then click **Bindings** in the **Actions** pane.</span></span>

5.  <span data-ttu-id="ef11c-421">En el cuadro de diálogo **Agregar enlace de sitio**, agregue un enlace **https** para el sitio, si aún no se muestra ninguno.</span><span class="sxs-lookup"><span data-stu-id="ef11c-421">In the **Add Site Binding** dialog box, add an **https** binding for the site, if one is not already displayed.</span></span> <span data-ttu-id="ef11c-422">Si no usa un certificado autofirmado, especifique el nombre de host del paso 3 de este procedimiento.</span><span class="sxs-lookup"><span data-stu-id="ef11c-422">If you are not using a self-signed certificate, specify the host name from step 3 of this procedure.</span></span> <span data-ttu-id="ef11c-423">Si usa un certificado autofirmado, este paso no es necesario.</span><span class="sxs-lookup"><span data-stu-id="ef11c-423">If you are using a self-signed certificate, this step is not required.</span></span>

6.  <span data-ttu-id="ef11c-424">Seleccione el certificado obtenido o creado en el paso 3 de este procedimiento y, después, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="ef11c-424">Select the certificate that you obtained or created in step 3 of this procedure, and then click **OK**.</span></span>

<a href="" id="BKMK_using"></a>

<span data-ttu-id="ef11c-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Uso de la consola de Windows PowerShell basada en web</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Using the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ef11c-426">Una vez instalado Windows PowerShell Web Access y configurada la puerta de enlace como se describe en este tema, la consola de Windows PowerShell basada en web estará lista para usarse.</span><span class="sxs-lookup"><span data-stu-id="ef11c-426">After Windows PowerShell Web Access is installed and the gateway configuration is finished as described in this topic, the Windows PowerShell web-based console is ready to use.</span></span> <span data-ttu-id="ef11c-427">Para obtener más información sobre la introducción a la consola basada en web, consulte [Uso de la consola de Windows PowerShell basada en web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="ef11c-427">For more information about getting started in the web-based console, see [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).</span></span>

<span data-ttu-id="ef11c-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Consulte también</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="ef11c-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ef11c-429">[Documentación de Internet Information Services (IIS) 7.0](https://technet.microsoft.com/library/cc753433.aspx)
[Ayuda del Administrador de IIS 7.0](https://technet.microsoft.com/library/cc732664.aspx)
[Configurar la seguridad de los servidores web (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[Recursos de implementación de IPsec](https://technet.microsoft.com/network/bb531150)</span><span class="sxs-lookup"><span data-stu-id="ef11c-429">[Internet Information Services (IIS) 7.0 Documentation](https://technet.microsoft.com/library/cc753433.aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)
[Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec Deployment Resources](https://technet.microsoft.com/network/bb531150)</span></span>

<span data-ttu-id="ef11c-430"><span>Mostrar:</span> heredado protegido</span><span class="sxs-lookup"><span data-stu-id="ef11c-430"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="ef11c-431"><span class="stdr-votetitle">¿Le resultó útil esta página?</span></span><span class="sxs-lookup"><span data-stu-id="ef11c-431"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="ef11c-432">Sí No</span><span class="sxs-lookup"><span data-stu-id="ef11c-432">Yes No</span></span>

<span data-ttu-id="ef11c-433">¿Algún otro comentario?</span><span class="sxs-lookup"><span data-stu-id="ef11c-433">Additional feedback?</span></span>

<span data-ttu-id="ef11c-434"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caracteres restantes</span> Enviar Omitir esto</span><span class="sxs-lookup"><span data-stu-id="ef11c-434"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="ef11c-435"><span class="stdr-thankyou">Gracias.</span></span><span class="sxs-lookup"><span data-stu-id="ef11c-435"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="ef11c-436"><span class="stdr-appreciate">Apreciamos sus comentarios.</span></span><span class="sxs-lookup"><span data-stu-id="ef11c-436"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="ef11c-437">Administre su perfil</span><span class="sxs-lookup"><span data-stu-id="ef11c-437">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="ef11c-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span>Comentarios del sitio</a> Comentarios del sitio</span><span class="sxs-lookup"><span data-stu-id="ef11c-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="ef11c-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="ef11c-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="ef11c-440">Cuéntenos su experiencia...</span><span class="sxs-lookup"><span data-stu-id="ef11c-440">Tell us about your experience...</span></span>

<span data-ttu-id="ef11c-441">¿Se ha cargado rápido la página?</span><span class="sxs-lookup"><span data-stu-id="ef11c-441">Did the page load quickly?</span></span>

<span data-ttu-id="ef11c-442"><span> Sí<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="ef11c-442"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="ef11c-443">¿Le gusta el diseño de página?</span><span class="sxs-lookup"><span data-stu-id="ef11c-443">Do you like the page design?</span></span>

<span data-ttu-id="ef11c-444"><span> Sí<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="ef11c-444"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="ef11c-445">Más información</span><span class="sxs-lookup"><span data-stu-id="ef11c-445">Tell us more</span></span>

-   [<span data-ttu-id="ef11c-446">Boletín de Flash</span><span class="sxs-lookup"><span data-stu-id="ef11c-446">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="ef11c-447">Póngase en contacto con nosotros</span><span class="sxs-lookup"><span data-stu-id="ef11c-447">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="ef11c-448">Declaración de privacidad</span><span class="sxs-lookup"><span data-stu-id="ef11c-448">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="ef11c-449">Términos de uso</span><span class="sxs-lookup"><span data-stu-id="ef11c-449">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="ef11c-450">Marcas comerciales</span><span class="sxs-lookup"><span data-stu-id="ef11c-450">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="ef11c-451">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="ef11c-451">© 2016 Microsoft</span></span>

<span data-ttu-id="ef11c-452">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="ef11c-452">© 2016 Microsoft</span></span>

<span data-ttu-id="ef11c-453">Los scripts y el código de terceros vinculados a este sitio web o a los que este hace referencia se le ofrecen a usted bajo licencia de las partes propietarias de dicho código, no de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ef11c-453">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="ef11c-454">Consulte los términos de uso de Ajax CDN para ASP.NET en http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="ef11c-454">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

