---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Uso de la consola de Windows PowerShell basada en web
ms.openlocfilehash: 48ed1646c00f909c4e950f197f51a30205060ef0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
#  <a name="use-the-web-based-windows-powershell-console"></a><span data-ttu-id="44d34-103">Uso de la consola de Windows PowerShell basada en web</span><span class="sxs-lookup"><span data-stu-id="44d34-103">Use the Web-based Windows PowerShell Console</span></span>

<span data-ttu-id="44d34-104">Actualizado: 24 de junio de 2013</span><span class="sxs-lookup"><span data-stu-id="44d34-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="44d34-105">Se aplica a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="44d34-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="44d34-106">Windows PowerShell® Web Access permite a los usuarios de Windows PowerShell® iniciar sesión en un sitio web protegido mediante la Capa de sockets seguros (SSL) con el fin de usar sesiones, scripts y cmdlets de Windows PowerShell para administrar un equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="44d34-106">Windows PowerShell® Web Access lets Windows PowerShell® users sign in to a Secure Sockets Layer (SSL)-secured website to use Windows PowerShell sessions, cmdlets, and scripts to manage a remote computer.</span></span> <span data-ttu-id="44d34-107">Como la consola de Windows PowerShell se ejecuta en un explorador web, puede abrirse desde una gran variedad de dispositivos cliente, incluidos teléfonos móviles, Tablet PC, quioscos multimedia informáticos públicos, equipos portátiles o equipos compartidos o prestados.</span><span class="sxs-lookup"><span data-stu-id="44d34-107">Because the Windows PowerShell console runs in a web browser, it can be opened from a variety of client devices, including cell phones, tablet computers, public computing kiosks, laptop computers, or shared or borrowed computers.</span></span> <span data-ttu-id="44d34-108">La consola de Windows PowerShell basada en web está destinada a un equipo remoto que especifican los usuarios como parte del proceso de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="44d34-108">The web-based Windows PowerShell console is targeted at a remote computer that is specified by users as part of the sign-in process.</span></span> <span data-ttu-id="44d34-109">En este tema, se describe cómo iniciar sesión en la consola de Windows PowerShell Web Access basada en web y cómo comenzar a usarla.</span><span class="sxs-lookup"><span data-stu-id="44d34-109">This topic describes how to sign in to and start using the Windows PowerShell Web Access web-based console.</span></span>

<span data-ttu-id="44d34-110">No se describe cómo usar Windows PowerShell ni cómo ejecutar cmdlets o scripts.</span><span class="sxs-lookup"><span data-stu-id="44d34-110">This topic does not describe how to use Windows PowerShell or run cmdlets or scripts.</span></span> <span data-ttu-id="44d34-111">Para más información sobre de recursos de scripting y cómo usar Windows PowerShell, consulte la sección Consulte también al final de este tema.</span><span class="sxs-lookup"><span data-stu-id="44d34-111">For information about how to use Windows PowerShell, and scripting resources, see the See Also section at the end of this topic.</span></span>

<span data-ttu-id="44d34-112">En este tema:</span><span class="sxs-lookup"><span data-stu-id="44d34-112">In this topic:</span></span>

-   [<span data-ttu-id="44d34-113">Dispositivos cliente y exploradores admitidos</span><span class="sxs-lookup"><span data-stu-id="44d34-113">Supported browsers and client devices</span></span>](#BKMK_browser)

-   [<span data-ttu-id="44d34-114">Inicio de sesión en Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="44d34-114">Signing in to Windows PowerShell Web Access</span></span>](#BKMK_sign)

-   [<span data-ttu-id="44d34-115">Cierre de sesión y tiempo de espera agotado</span><span class="sxs-lookup"><span data-stu-id="44d34-115">Signing out and timing out</span></span>](#BKMK_timeout)

-   [<span data-ttu-id="44d34-116">Diferencias de la consola de Windows PowerShell basada en web</span><span class="sxs-lookup"><span data-stu-id="44d34-116">Differences in the web-based Windows PowerShell console</span></span>](#BKMK_web)

<a href="" id="BKMK_browser"></a>
------------------------------------------------------------------------

<span data-ttu-id="44d34-117">Windows PowerShell Web Access admite los siguientes exploradores de Internet.</span><span class="sxs-lookup"><span data-stu-id="44d34-117">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="44d34-118">Aunque los exploradores móviles no se admiten oficialmente, muchos de ellos pueden ejecutar la consola de Windows PowerShell basada en web.</span><span class="sxs-lookup"><span data-stu-id="44d34-118">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="44d34-119">También se espera que funcionen otros exploradores que aceptan cookies y ejecutan JavaScript y sitios web HTTPS, pero no se han probado de manera oficial.</span><span class="sxs-lookup"><span data-stu-id="44d34-119">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="44d34-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Exploradores de equipos de escritorio admitidos</span></a></span><span class="sxs-lookup"><span data-stu-id="44d34-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="44d34-121">Windows® Internet Explorer® para Microsoft Windows® 8.0, 9.0, 10.0 y 11.0</span><span class="sxs-lookup"><span data-stu-id="44d34-121">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="44d34-122">Mozilla Firefox® 10.0.2</span><span class="sxs-lookup"><span data-stu-id="44d34-122">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="44d34-123">Google Chrome™ 17.0.963.56m para Windows</span><span class="sxs-lookup"><span data-stu-id="44d34-123">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="44d34-124">Apple Safari® 5.1.2 para Windows</span><span class="sxs-lookup"><span data-stu-id="44d34-124">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="44d34-125">Apple Safari 5.1.2 para Mac OS®</span><span class="sxs-lookup"><span data-stu-id="44d34-125">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="44d34-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Exploradores o dispositivos móviles mínimamente probados</span></a></span><span class="sxs-lookup"><span data-stu-id="44d34-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="44d34-127">Windows Phone 7 y 7.5</span><span class="sxs-lookup"><span data-stu-id="44d34-127">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="44d34-128">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span><span class="sxs-lookup"><span data-stu-id="44d34-128">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="44d34-129">Apple Safari para sistema operativo iPhone 5.0.1</span><span class="sxs-lookup"><span data-stu-id="44d34-129">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="44d34-130">Apple Safari para sistema operativo iPad 2 5.0.1</span><span class="sxs-lookup"><span data-stu-id="44d34-130">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="44d34-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requisitos de explorador</span></a></span><span class="sxs-lookup"><span data-stu-id="44d34-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="44d34-132">Para usar la consola de Windows PowerShell Web Access basada en web, los exploradores deben poder hacer lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="44d34-132">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="44d34-133">Permitir cookies del sitio web de la puerta de enlace de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="44d34-133">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="44d34-134">Abrir y leer páginas HTTPS.</span><span class="sxs-lookup"><span data-stu-id="44d34-134">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="44d34-135">Abrir y ejecutar sitios web que usen JavaScript.</span><span class="sxs-lookup"><span data-stu-id="44d34-135">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_sign"></a>

<span data-ttu-id="44d34-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Inicio de sesión en Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="44d34-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing in to Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="44d34-137">El administrador de Windows PowerShell Web Access debe proporcionar una dirección URL que es la dirección del sitio web de la puerta de enlace de Windows PowerShell Web Access de la organización.</span><span class="sxs-lookup"><span data-stu-id="44d34-137">Your Windows PowerShell Web Access administrator should provide you with a URL that is the address of your organization’s Windows PowerShell Web Access gateway website.</span></span> <span data-ttu-id="44d34-138">De manera predeterminada, la dirección de este sitio web es https://&lt;nombre_servidor&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="44d34-138">By default, this website address is https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="44d34-139">Antes de iniciar sesión en Windows PowerShell Web Access, asegúrese de contar con el nombre o la dirección IP del equipo remoto que desea administrar.</span><span class="sxs-lookup"><span data-stu-id="44d34-139">Before you sign in to Windows PowerShell Web Access, be sure that you have the name or IP address of the remote computer that you want to manage.</span></span> <span data-ttu-id="44d34-140">Debe ser un usuario autorizado en el equipo remoto, y el equipo debe estar configurado para admitir la administración remota.</span><span class="sxs-lookup"><span data-stu-id="44d34-140">You must be an authorized user on the remote computer, and it must be configured to allow remote management.</span></span> <span data-ttu-id="44d34-141">Para más información sobre de la configuración del equipo para que admita la administración remota, consulte el tema sobre cómo [Enable and Use Remote Commands in Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx) (Habilitación y uso de comandos remotos en Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="44d34-141">For more information about configuring your computer to allow remote management, see [Enable and Use Remote Commands in Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx).</span></span> <span data-ttu-id="44d34-142">El método más sencillo de configurar el equipo para que admita la administración remota consiste en ejecutar el cmdlet **Enable-PSRemoting -force** en el equipo, en una sesión de Windows PowerShell abierta con permisos del usuario elevados (**Ejecutar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="44d34-142">The simplest method of configuring your computer to allow remote management is to run the **Enable-PSRemoting -force** cmdlet on the computer, in a Windows PowerShell session that has been opened with elevated user rights (**Run as Administrator**).</span></span>

### <a name="to-sign-in-to-windows-powershell-web-access"></a><span data-ttu-id="44d34-143">Para iniciar sesión en Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="44d34-143">To sign in to Windows PowerShell Web Access</span></span>

1.  <span data-ttu-id="44d34-144">Abra el sitio web de Windows PowerShell Web Access en una pestaña o ventana del explorador de Internet.</span><span class="sxs-lookup"><span data-stu-id="44d34-144">Open the Windows PowerShell Web Access website in an Internet browser window or tab.</span></span>

2.  <span data-ttu-id="44d34-145">En la página de inicio de sesión de Windows PowerShell Web Access, proporcione su nombre de usuario de red, su contraseña y el nombre del equipo que desea administrar (y en el que es un usuario autorizado).</span><span class="sxs-lookup"><span data-stu-id="44d34-145">On the Windows PowerShell Web Access sign-in page, provide your network user name, password, and the name of the computer that you want to manage (and on which you are an authorized user).</span></span> <span data-ttu-id="44d34-146">Si el administrador de Windows PowerShell Web Access le ha indicado que use un URI a un servidor proxy o sitio personalizado en lugar de un nombre de equipo, seleccione **URI de conexión** en el campo **Tipo de conexión** y luego proporcione el URI.</span><span class="sxs-lookup"><span data-stu-id="44d34-146">If the Windows PowerShell Web Access administrator has instructed you to use a URI to a custom site or proxy server instead of a computer name, select **Connection URI** in the **Connection type** field, and then provide the URI.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="44d34-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="44d34-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><ul>
    <li><p><span data-ttu-id="44d34-148">Si el equipo de destino se encuentra en un grupo de trabajo, usa la siguiente sintaxis para proporcionar el nombre de usuario e iniciar sesión en el equipo:&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;.</span><span class="sxs-lookup"><span data-stu-id="44d34-148">If the destination computer is in a workgroup, use the following syntax to provide your user name and sign in to the computer:&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    <li><p><span data-ttu-id="44d34-149">Si el equipo de destino es el servidor de puerta de enlace, puede especificar <strong>localhost</strong> en el campo <strong>Nombre de equipo</strong>.</span><span class="sxs-lookup"><span data-stu-id="44d34-149">If the destination computer is the gateway server, you can specify <strong>localhost</strong> in the <strong>Computer name</strong> field.</span></span></p></li>
    <li><p><span data-ttu-id="44d34-150">Si el equipo de destino es el servidor de puerta de enlace, y el servidor de puerta de enlace se encuentra en un grupo de trabajo, puede usar <strong>localhost</strong> en el campo <strong>Nombre de equipo</strong>, pero no use localhost\&lt;<em>user_name</em>&gt; en el campo <strong>Nombre de usuario</strong>.</span><span class="sxs-lookup"><span data-stu-id="44d34-150">If the destination computer is the gateway server, and the gateway server is in a workgroup, you can use <strong>localhost</strong> in the <strong>Computer name</strong> field, but do not use localhost\&lt;<em>user_name</em>&gt; in the <strong>User name</strong> field.</span></span> <span data-ttu-id="44d34-151">Tiene que usar &lt;<em>workgroup name</em>&gt;\&lt;<em>user_name</em>&gt;.</span><span class="sxs-lookup"><span data-stu-id="44d34-151">You must use &lt;<em>workgroup name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

3.  <span data-ttu-id="44d34-152">La sección **Configuración de conexión opcional** está relacionada con los requisitos de autorización del equipo remoto que desea administrar.</span><span class="sxs-lookup"><span data-stu-id="44d34-152">The **Optional Connection Settings** section relates to the authorization requirements of the remote computer that you want to manage.</span></span> <span data-ttu-id="44d34-153">Para más información sobre los parámetros equivalentes a la configuración de conexión opcional, vea la [ayuda del cmdlet Enter-PSSession](https://technet.microsoft.com/library/dd315384.aspx).</span><span class="sxs-lookup"><span data-stu-id="44d34-153">For more information about the parameters that are equivalent to optional connection settings, see the [Enter-PSSession cmdlet Help](https://technet.microsoft.com/library/dd315384.aspx).</span></span>

    <span data-ttu-id="44d34-154">Por lo general, las credenciales que use para pasar a través de la puerta de enlace de Windows PowerShell Web Access serán las mismas que reconoce el equipo remoto que desea administrar.</span><span class="sxs-lookup"><span data-stu-id="44d34-154">Typically, the credentials you use to pass through the Windows PowerShell Web Access gateway are the same that are recognized by the remote computer that you want to manage.</span></span> <span data-ttu-id="44d34-155">No obstante, si desea usar credenciales diferentes de las especificadas en el paso 2 para administrar el equipo remoto, expanda la sección **Configuración de conexión opcional** y proporcione las credenciales alternativas.</span><span class="sxs-lookup"><span data-stu-id="44d34-155">However, if you want to use different credentials to manage the remote computer that you specified in step 2, expand the **Optional Connection Settings** section, and provide the alternate credentials.</span></span> <span data-ttu-id="44d34-156">De lo contrario, vaya al paso 6.</span><span class="sxs-lookup"><span data-stu-id="44d34-156">Otherwise, skip to step 6.</span></span>

4.  <span data-ttu-id="44d34-157">Si el administrador de Windows PowerShell Web Access ha creado una configuración de sesión personalizada para los usuarios de Windows PowerShell Web Access, escriba el nombre de la configuración de sesión en el campo **Nombre de la configuración**.</span><span class="sxs-lookup"><span data-stu-id="44d34-157">If the Windows PowerShell Web Access administrator has created a custom session configuration for Windows PowerShell Web Access users, type the name of the session configuration name in the **Configuration name** field.</span></span> <span data-ttu-id="44d34-158">Para más información sobre las configuraciones de sesión, vea el tema [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) (Acerca de las configuraciones de sesión) en el sitio web de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="44d34-158">For more information about session configurations, see [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) on the Microsoft website.</span></span>

5.  <span data-ttu-id="44d34-159">Deje el **Tipo de autenticación** establecido en **Predeterminado**, a menos que el administrador de Windows PowerShell Web Access le haya dado otras indicaciones.</span><span class="sxs-lookup"><span data-stu-id="44d34-159">Keep the **Authentication type** set to **Default** unless you have been instructed to do otherwise by the Windows PowerShell Web Access administrator.</span></span>

6.  <span data-ttu-id="44d34-160">Haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="44d34-160">Click **Sign in**.</span></span>

<a href="" id="BKMK_timeout"></a>

<span data-ttu-id="44d34-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Cierre de sesión y tiempo de espera agotado</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="44d34-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing out and timing out</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="44d34-162">Una sesión de Windows PowerShell basada en web se cerrará si el usuario:</span><span class="sxs-lookup"><span data-stu-id="44d34-162">Any of the following signs you out of a web-based Windows PowerShell session.</span></span>

-   <span data-ttu-id="44d34-163">Hace clic en **Cerrar sesión** en la esquina inferior derecha de la consola.</span><span class="sxs-lookup"><span data-stu-id="44d34-163">Clicking **Sign out** in the lower right corner of the console.</span></span> <span data-ttu-id="44d34-164">(Solo Windows Server 2012)</span><span class="sxs-lookup"><span data-stu-id="44d34-164">(Windows Server 2012 only)</span></span>

-   <span data-ttu-id="44d34-165">Hace clic en **Guardar** o **Salir** en la esquina inferior derecha de la consola (solo Windows Server 2012 R2).</span><span class="sxs-lookup"><span data-stu-id="44d34-165">Clicking **Save** or **Exit** in the lower right corner of the console (Windows Server 2012 R2 only).</span></span> <span data-ttu-id="44d34-166">Si hace clic en **Guardar** se guarda y se cierra la sesión de Windows PowerShell Web Access y puede volver a conectarse a la sesión más tarde.</span><span class="sxs-lookup"><span data-stu-id="44d34-166">Clicking **Save** saves and closes your Windows PowerShell Web Access session; you can reconnect to the session later.</span></span> <span data-ttu-id="44d34-167">Al iniciar sesión en Windows PowerShell Web Access de nuevo, Windows PowerShell Web Access muestra una lista de las sesiones guardadas y puede optar por seleccionar una sesión guardada y conectarse a ella, o iniciar una sesión nueva.</span><span class="sxs-lookup"><span data-stu-id="44d34-167">When you sign in to Windows PowerShell Web Access again, Windows PowerShell Web Access displays a list of your saved sessions; you can either select and reconnect to a saved session, or start a new session.</span></span> <span data-ttu-id="44d34-168">El administrador de puerta de enlace configura el número máximo de sesiones abiertas que se permite tener a los usuarios, tanto guardadas como activas.</span><span class="sxs-lookup"><span data-stu-id="44d34-168">The maximum number of open sessions that users are allowed, both saved and active, is configured by the gateway administrator.</span></span>

    <span data-ttu-id="44d34-169">Si hace clic en **Salir** se cierra la sesión de Windows PowerShell Web Access sin guardarla.</span><span class="sxs-lookup"><span data-stu-id="44d34-169">Clicking **Exit** signs you out of the Windows PowerShell Web Access session without saving it.</span></span>

-   <span data-ttu-id="44d34-170">Intenta iniciar sesión para administrar otro equipo remoto en la misma sesión del explorador o en una nueva pestaña de la misma sesión del explorador.</span><span class="sxs-lookup"><span data-stu-id="44d34-170">Attempting to sign in to manage a different remote computer in the same browser session, or in a new tab of the same browser session.</span></span> <span data-ttu-id="44d34-171">(Esto no se aplica si el servidor de puerta de enlace está ejecutando Windows Server 2012 R2; si Windows PowerShell Web Access se ejecuta en Windows Server 2012 R2 se permiten las sesiones de varios usuarios en pestañas nuevas de la misma sesión del explorador.) Para más información sobre cómo usar más de una sesión activa en el mismo equipo, consulte el tema sobre cómo conectarse a varios equipos de destino simultáneamente en la sección [Limitaciones de la consola basada en web](#BKMK_limits) en este tema.</span><span class="sxs-lookup"><span data-stu-id="44d34-171">(This does not apply if the gateway server is running Windows Server 2012 R2; Windows PowerShell Web Access running on Windows Server 2012 R2 does allow multiple user sessions in new tabs in the same browser session.) For more information about how to use more than one active session on the same computer, see “Connecting to multiple target computers simultaneously” in the [Limitations of the web-based console](#BKMK_limits) section of this topic.</span></span>

-   <span data-ttu-id="44d34-172">No se hay ninguna actividad en la sesión durante 20 minutos.</span><span class="sxs-lookup"><span data-stu-id="44d34-172">20 minutes of inactivity in the session.</span></span> <span data-ttu-id="44d34-173">El administrador de la puerta de enlace puede personalizar el período de tiempo de espera de inactividad. Para obtener más información, vea [Session management](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt) (Administración de sesiones).</span><span class="sxs-lookup"><span data-stu-id="44d34-173">The gateway administrator can customize the inactivity time-out period; for more information, see [Session management](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt).</span></span>

    -   <span data-ttu-id="44d34-174">Si está desconectado de una sesión en la consola basada en web debido a un error de red u otros apagados o errores no planificados y no porque haya cerrado las sesiones usted mismo, las sesiones de Windows PowerShell Web Access continúan ejecutándose, conectadas al equipo de destino, hasta que venza el período de tiempo de espera del cliente.</span><span class="sxs-lookup"><span data-stu-id="44d34-174">If you are disconnected from a session in the web-based console because of a network error or other unplanned shutdown or failure, and not because you have closed the session yourself, the Windows PowerShell Web Access session continues to run, connected to the target computer, until the time-out period on the client side lapses.</span></span> <span data-ttu-id="44d34-175">De forma predeterminada, este período de tiempo de espera es de 20 minutos y lo configura el Administrador de puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="44d34-175">By default, this time-out period is 20 minutes, and is configured by the gateway administrator.</span></span> <span data-ttu-id="44d34-176">La sesión se desconecta después de los 20 minutos predeterminados o después del período de tiempo de espera especificado por el administrador de la puerta de enlace, el que sea más corto.</span><span class="sxs-lookup"><span data-stu-id="44d34-176">The session is disconnected after either the default 20 minutes, or after the time-out period specified by the gateway administrator, whichever is shorter.</span></span>

        <span data-ttu-id="44d34-177">Si el servidor de puerta de enlace está ejecutando Windows Server 2012 R2, Windows PowerShell Web Access permite a los usuarios volver a conectarse a las sesiones guardadas anteriormente, pero no puede ver o volver a conectarte a las sesiones guardadas hasta que haya vencido el período de tiempo de espera especificado por el administrador de la puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="44d34-177">If the gateway server is running Windows Server 2012 R2, Windows PowerShell Web Access lets users reconnect to saved sessions at a later time, but you cannot see or reconnect to saved sessions until after the time-out period specified by the gateway administrator has lapsed.</span></span>

-   <span data-ttu-id="44d34-178">Cierra la pestaña o ventana del explorador.</span><span class="sxs-lookup"><span data-stu-id="44d34-178">Closing the browser window or tab.</span></span>

-   <span data-ttu-id="44d34-179">Apaga el dispositivo cliente en el que se ejecuta el explorador o lo desconecta de la red.</span><span class="sxs-lookup"><span data-stu-id="44d34-179">Turning off the client device on which the browser is running, or disconnecting it from the network.</span></span>

-   <span data-ttu-id="44d34-180">Ejecuta el comando **Exit** en la consola web.</span><span class="sxs-lookup"><span data-stu-id="44d34-180">Running the **Exit** command in the web console.</span></span> <span data-ttu-id="44d34-181">Este comando no funciona si la configuración de sesión a la cual está conectado se ha establecido para admitir el modo [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) o se encuentra en un espacio de ejecución restringido.</span><span class="sxs-lookup"><span data-stu-id="44d34-181">This command does not work if the session configuration to which you are connected to is configured to support [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) mode, or is in a restricted runspace.</span></span>

<span data-ttu-id="44d34-182">Si desea volver a iniciar sesión, abra de nuevo la página web de Windows PowerShell Web Access e inicie sesión mediante los pasos descritos en [Para iniciar sesión en Windows PowerShell Web Access](#BKMK_signin) en este tema.</span><span class="sxs-lookup"><span data-stu-id="44d34-182">If you want to sign in again, open the Windows PowerShell Web Access web page again, and sign in by following the steps in [To sign in to Windows PowerShell Web Access](#BKMK_signin) in this topic.</span></span>

<a href="" id="BKMK_web"></a>

<span data-ttu-id="44d34-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Diferencias de la consola de Windows PowerShell basada en web</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="44d34-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Differences in the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="44d34-184">Tras iniciar sesión en Windows PowerShell Web Access, una consola de Windows PowerShell basada en web se abre en la pestaña o ventana del explorador.</span><span class="sxs-lookup"><span data-stu-id="44d34-184">After signing in to Windows PowerShell Web Access, a web-based Windows PowerShell console opens in your browser window or tab.</span></span> <span data-ttu-id="44d34-185">Puesto que la consola está conectada al equipo remoto especificado durante el proceso de inicio de sesión, solo aquellos cmdlets o scripts de Windows PowerShell que estén disponibles en el equipo remoto podrán usarse en la consola.</span><span class="sxs-lookup"><span data-stu-id="44d34-185">Because the console is connected to the remote computer that you specified during the sign-in process, only those Windows PowerShell cmdlets or scripts that are available on the remote computer can be used in the console.</span></span> <span data-ttu-id="44d34-186">Esta sección describe otras limitaciones de las consolas de Windows PowerShell Web Access y las diferencias entre las consolas de Windows PowerShell Web Access y la consola **PowerShell.exe** instalada.</span><span class="sxs-lookup"><span data-stu-id="44d34-186">This section describes other limitations of Windows PowerShell Web Access consoles, and differences between Windows PowerShell Web Access consoles and the installed **PowerShell.exe** console.</span></span>

###

<span data-ttu-id="44d34-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Diferencias funcionales con PowerShell.exe</span></a></span><span class="sxs-lookup"><span data-stu-id="44d34-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Functional disparity with PowerShell.exe</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="44d34-188">La mayoría de las funcionalidades del host de Windows PowerShell están disponibles en la consola de Windows PowerShell Web Access basada en web, pero hay algunas características que no se encuentran disponibles.</span><span class="sxs-lookup"><span data-stu-id="44d34-188">The majority of Windows PowerShell host functionality is available in the Windows PowerShell Web Access web-based console, but there are some features that are not available.</span></span>

-   <span data-ttu-id="44d34-189"><span class="label">Visualización del progreso anidado</span></span><span class="sxs-lookup"><span data-stu-id="44d34-189"><span class="label">Nested progress displays.</span></span></span>  <span data-ttu-id="44d34-190">Windows PowerShell Web Access muestra una GUI de progreso para los cmdlets que notifican el progreso, pero solo se muestra información de progreso de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="44d34-190">Windows PowerShell Web Access displays a progress GUI for cmdlets that report progress, but only top-level progress information is displayed.</span></span>

-   <span data-ttu-id="44d34-191"><span class="label">Modificación del color de entrada</span></span><span class="sxs-lookup"><span data-stu-id="44d34-191"><span class="label">Input color modification.</span></span></span>  <span data-ttu-id="44d34-192">No se puede cambiar el color de entrada (ni el del primer plano ni el del fondo).</span><span class="sxs-lookup"><span data-stu-id="44d34-192">The input color (both foreground and background) cannot be changed.</span></span> <span data-ttu-id="44d34-193">El estilo de los mensajes detallados, de resultados, de advertencia y de error se puede cambiar mediante la ejecución de un script.</span><span class="sxs-lookup"><span data-stu-id="44d34-193">The style of output, warning, verbose, and error messages can all be changed by running a script.</span></span>

-   <span data-ttu-id="44d34-194"><span class="label">PSHostRawUserInterface</span></span><span class="sxs-lookup"><span data-stu-id="44d34-194"><span class="label">PSHostRawUserInterface.</span></span></span>  <span data-ttu-id="44d34-195">Windows PowerShell Web Access se implementa a través de la administración remota de Windows PowerShell y utiliza un espacio de ejecución remoto.</span><span class="sxs-lookup"><span data-stu-id="44d34-195">Windows PowerShell Web Access is implemented over Windows PowerShell remote management, and uses a remote runspace.</span></span> <span data-ttu-id="44d34-196">Windows PowerShell Web Access no implementa algunos métodos en esta interfaz; por ejemplo, no implementa ningún comando que escriba en la consola Windows.</span><span class="sxs-lookup"><span data-stu-id="44d34-196">Windows PowerShell Web Access does not implement some methods in this interface; for example, any command that writes to the Windows console.</span></span> <span data-ttu-id="44d34-197">Los comandos como **PowerTab** no funcionan en Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="44d34-197">Commands such as **PowerTab** do not work in Windows PowerShell Web Access.</span></span>

-   <span data-ttu-id="44d34-198"><span class="label">Teclas de función</span></span><span class="sxs-lookup"><span data-stu-id="44d34-198"><span class="label">Function keys.</span></span></span>  <span data-ttu-id="44d34-199">Windows PowerShell Web Access no admite algunas teclas de función; en muchos casos, esto se debe a que los comandos están reservados por el explorador.</span><span class="sxs-lookup"><span data-stu-id="44d34-199">Windows PowerShell Web Access does not support some function keys, in many cases because the commands are reserved by the browser.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="44d34-200">Tecla de función no admitida</span><span class="sxs-lookup"><span data-stu-id="44d34-200">Unsupported Function Key</span></span></p></th>
<th><p><span data-ttu-id="44d34-201">Acción</span><span class="sxs-lookup"><span data-stu-id="44d34-201">Action</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="44d34-202">Ctrl+C</span><span class="sxs-lookup"><span data-stu-id="44d34-202">Ctrl+C</span></span></p></td>
<td><p><span data-ttu-id="44d34-203">En Windows PowerShell Web Access, la combinación de teclas <strong>Ctrl+C</strong> la utiliza el explorador para copiar contenido.</span><span class="sxs-lookup"><span data-stu-id="44d34-203">In Windows PowerShell Web Access, <strong>Ctrl+C</strong> is used by the browser to copy content.</span></span> <span data-ttu-id="44d34-204">La consola ofrece un botón <strong>Cancelar</strong> y los usuarios también pueden usar <strong>Ctrl+Q</strong> para cancelar comandos.</span><span class="sxs-lookup"><span data-stu-id="44d34-204">The console offers a <strong>Cancel</strong> button, and users can also use <strong>Ctrl+Q</strong> to cancel commands.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="44d34-205">Alt+Espacio, e, l</span><span class="sxs-lookup"><span data-stu-id="44d34-205">Alt-space, e, l</span></span></p></td>
<td><p><span data-ttu-id="44d34-206">Desplazarse por el búfer de pantalla</span><span class="sxs-lookup"><span data-stu-id="44d34-206">Scroll through the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="44d34-207">Alt+Espacio, e, f</span><span class="sxs-lookup"><span data-stu-id="44d34-207">Alt+Space, e, f</span></span></p></td>
<td><p><span data-ttu-id="44d34-208">Buscar texto en el búfer de pantalla</span><span class="sxs-lookup"><span data-stu-id="44d34-208">Search for text in the screen buffer</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="44d34-209">Alt+Espacio, e, k</span><span class="sxs-lookup"><span data-stu-id="44d34-209">Alt+Space, e, k</span></span></p></td>
<td><p><span data-ttu-id="44d34-210">Seleccionar texto para copiarlo desde el búfer de pantalla</span><span class="sxs-lookup"><span data-stu-id="44d34-210">Select text to be copied from the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="44d34-211">Alt+Espacio, e, p</span><span class="sxs-lookup"><span data-stu-id="44d34-211">Alt+Space, e, p</span></span></p></td>
<td><p><span data-ttu-id="44d34-212">Pegar contenido del Portapapeles en la consola de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="44d34-212">Paste clipboard contents into the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="44d34-213">Alt+Espacio, c</span><span class="sxs-lookup"><span data-stu-id="44d34-213">Alt+Space, c</span></span></p></td>
<td><p><span data-ttu-id="44d34-214">Cerrar la consola de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="44d34-214">Close the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="44d34-215">Ctrl+Inter</span><span class="sxs-lookup"><span data-stu-id="44d34-215">Ctrl+Break</span></span></p></td>
<td><p><span data-ttu-id="44d34-216">Forzar el cierre de la ventana de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="44d34-216">Force the Windows PowerShell window to close</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="44d34-217">Ctrl+Inicio</span><span class="sxs-lookup"><span data-stu-id="44d34-217">Ctrl+Home</span></span></p></td>
<td><p><span data-ttu-id="44d34-218">Eliminar desde el comienzo de la línea de comandos actual</span><span class="sxs-lookup"><span data-stu-id="44d34-218">Deletes from the beginning of the current command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="44d34-219">Ctrl+Fin</span><span class="sxs-lookup"><span data-stu-id="44d34-219">Ctrl+End</span></span></p></td>
<td><p><span data-ttu-id="44d34-220">Eliminar hasta el final de la línea de comandos</span><span class="sxs-lookup"><span data-stu-id="44d34-220">Deletes to end of the command line</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="44d34-221">F1</span><span class="sxs-lookup"><span data-stu-id="44d34-221">F1</span></span></p></td>
<td><p><span data-ttu-id="44d34-222">Mover el cursor un carácter a la derecha en la línea de comandos</span><span class="sxs-lookup"><span data-stu-id="44d34-222">Move cursor one character to the right on your command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="44d34-223">F2</span><span class="sxs-lookup"><span data-stu-id="44d34-223">F2</span></span></p></td>
<td><p><span data-ttu-id="44d34-224">Crear un nuevo comando copiando el último comando hasta el carácter que escriba</span><span class="sxs-lookup"><span data-stu-id="44d34-224">Creates a new command by copying your last command up to the character that you type</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="44d34-225">F3</span><span class="sxs-lookup"><span data-stu-id="44d34-225">F3</span></span></p></td>
<td><p><span data-ttu-id="44d34-226">Completar la línea de comandos con contenido de la última línea de comandos</span><span class="sxs-lookup"><span data-stu-id="44d34-226">Complete the command line with content from your last command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="44d34-227">F4</span><span class="sxs-lookup"><span data-stu-id="44d34-227">F4</span></span></p></td>
<td><p><span data-ttu-id="44d34-228">Eliminar caracteres desde la posición del cursor</span><span class="sxs-lookup"><span data-stu-id="44d34-228">Deletes characters from cursor position</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="44d34-229">F5</span><span class="sxs-lookup"><span data-stu-id="44d34-229">F5</span></span></p></td>
<td><p><span data-ttu-id="44d34-230">Examinar el historial de comandos hacia atrás.</span><span class="sxs-lookup"><span data-stu-id="44d34-230">Scan backward through your command history.</span></span> <span data-ttu-id="44d34-231">Para acceder a los comandos del historial de comandos en Windows PowerShell Web Access, haga clic en los botones de desplazamiento del <strong>Historial</strong> en la consola basada en web.</span><span class="sxs-lookup"><span data-stu-id="44d34-231">To access commands in the command history in Windows PowerShell Web Access, click the <strong>History</strong> scroll buttons in the web-based console.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="44d34-232">F7</span><span class="sxs-lookup"><span data-stu-id="44d34-232">F7</span></span></p></td>
<td><p><span data-ttu-id="44d34-233">Seleccionar de manera interactiva un comando del historial de comandos</span><span class="sxs-lookup"><span data-stu-id="44d34-233">Interactively select a command from your command history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="44d34-234">F8</span><span class="sxs-lookup"><span data-stu-id="44d34-234">F8</span></span></p></td>
<td><p><span data-ttu-id="44d34-235">Examinar el historial mostrando los comandos que coinciden con el texto actual</span><span class="sxs-lookup"><span data-stu-id="44d34-235">Scan history displaying commands that match current text</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="44d34-236">F9</span><span class="sxs-lookup"><span data-stu-id="44d34-236">F9</span></span></p></td>
<td><p><span data-ttu-id="44d34-237">Ejecutar un comando numerado específico desde el historial</span><span class="sxs-lookup"><span data-stu-id="44d34-237">Run a specific numbered command from history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="44d34-238">Re Pág</span><span class="sxs-lookup"><span data-stu-id="44d34-238">Page Up</span></span></p></td>
<td><p><span data-ttu-id="44d34-239">Ejecutar el primer comando del historial</span><span class="sxs-lookup"><span data-stu-id="44d34-239">Run the first command in the history</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="44d34-240">Av Pág</span><span class="sxs-lookup"><span data-stu-id="44d34-240">Page Down</span></span></p></td>
<td><p><span data-ttu-id="44d34-241">Ejecutar el último comando del historial</span><span class="sxs-lookup"><span data-stu-id="44d34-241">Run the last command in the history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="44d34-242">Alt+F7</span><span class="sxs-lookup"><span data-stu-id="44d34-242">Alt+F7</span></span></p></td>
<td><p><span data-ttu-id="44d34-243">Borrar la lista del historial de comandos</span><span class="sxs-lookup"><span data-stu-id="44d34-243">Clear the command history list</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="44d34-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Limitaciones de la consola basada en web</span></a></span><span class="sxs-lookup"><span data-stu-id="44d34-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Limitations of the web-based console</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="44d34-245"><span class="label">Salto doble</span></span><span class="sxs-lookup"><span data-stu-id="44d34-245"><span class="label">Double-hop.</span></span></span>   <span data-ttu-id="44d34-246">Puede encontrarse con la limitación del salto doble (o la conexión a un segundo equipo desde la primera conexión) si intenta crear una nueva sesión o trabajar en ella usando Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="44d34-246">You can encounter the double-hop (or connecting to a second computer from the first connection) limitation if you try to create or work on a new session by using Windows PowerShell Web Access.</span></span> <span data-ttu-id="44d34-247">Windows PowerShell Web Access usa un espacio de ejecución remoto y, actualmente, **PowerShell.exe** no admite el establecimiento de una conexión remota a un segundo equipo desde un espacio de ejecución remoto.</span><span class="sxs-lookup"><span data-stu-id="44d34-247">Windows PowerShell Web Access uses a remote runspace, and currently, **PowerShell.exe** does not support establishing a remote connection to a second computer from a remote runspace.</span></span> <span data-ttu-id="44d34-248">Si intenta conectarte a un segundo equipo remoto desde una conexión existente usando el cmdlet **Enter-PSSession**, por ejemplo, puede obtener varios errores, como “No se pueden obtener recursos de red.”.</span><span class="sxs-lookup"><span data-stu-id="44d34-248">If you attempt to connect to a second remote computer from an existing connection by using the **Enter-PSSession** cmdlet, for example, you can get various errors, such as “Cannot get network resources.”</span></span>

    <span data-ttu-id="44d34-249">Para evitar los errores de salto doble, el administrador debe configurar la autenticación CredSSP en el entorno de red de la organización.</span><span class="sxs-lookup"><span data-stu-id="44d34-249">To avoid double-hop errors, your administrator should configure CredSSP authentication in your organization’s network environment.</span></span> <span data-ttu-id="44d34-250">Para más información sobre la configuración de la autenticación CredSSP, consulte [CredSSP for second-hop remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) (CredSSP para comunicación remota de segundo salto) en el sitio web de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="44d34-250">For more information about configuring CredSSP authentication, see [CredSSP for second-hop remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) on the Microsoft website.</span></span> <span data-ttu-id="44d34-251">También puede proporcionar credenciales explícitas si desea administrar un segundo equipo remoto (es poco probable que las credenciales implícitas permitan el segundo salto).</span><span class="sxs-lookup"><span data-stu-id="44d34-251">You can also provide explicit credentials when you want to manage a second remote computer; implicit credentials are unlikely to allow the second hop.</span></span>

-   <span data-ttu-id="44d34-252">Windows PowerShell Web Access usa y tiene las mismas limitaciones que una sesión remota de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44d34-252">Windows PowerShell Web Access uses and has the same limitations as a remote Windows PowerShell session.</span></span> <span data-ttu-id="44d34-253">Los comandos que llaman directamente a las API de la consola Windows, por ejemplo, los comandos de editores basados en consola o de programas de menú basados en texto, no funcionan porque no leen o escriben en canalizaciones estándar de entrada, de salida o de error.</span><span class="sxs-lookup"><span data-stu-id="44d34-253">Commands that directly call Windows console APIs, such as those for console-based editors or text-based menu programs, do not work because the commands do not read or write to standard input, output, and error pipes.</span></span> <span data-ttu-id="44d34-254">Por lo tanto, los comandos que inician un archivo ejecutable, como **notepad.exe**, o muestran una GUI, como <span class="code">OpenGridView</span> u <span class="code">ogv</span>, no funcionan.</span><span class="sxs-lookup"><span data-stu-id="44d34-254">Therefore, commands that launch an executable file, such as **notepad.exe**, or display a GUI, such as <span class="code">OpenGridView</span> or <span class="code">ogv</span>, do not work.</span></span> <span data-ttu-id="44d34-255">Su experiencia se verá afectada por este comportamiento, ya que parecerá que Windows PowerShell Web Access no está respondiendo al comando.</span><span class="sxs-lookup"><span data-stu-id="44d34-255">Your experience is affected by this behavior; to you, it appears that Windows PowerShell Web Access is not responding to your command.</span></span>

-   <span data-ttu-id="44d34-256">La finalización con tabulación no funciona en una configuración de sesión con un espacio de ejecución restringido o en una que se encuentre en modo **NoLanguage**.</span><span class="sxs-lookup"><span data-stu-id="44d34-256">Tab completion does not work in a session configuration with a restricted runspace or one that is in **NoLanguage** mode.</span></span> <span data-ttu-id="44d34-257">Si bien los administradores pueden configurar una sesión para que admita la finalización con tabulación, esto se desaconseja por motivos de seguridad, dado que puede exponer la siguiente información a usuarios que no están autorizados.</span><span class="sxs-lookup"><span data-stu-id="44d34-257">Although administrators can configure a session to support tab completion, it is discouraged for security reasons, because it can expose the following information to unauthorized users.</span></span>

    -   <span data-ttu-id="44d34-258">Rutas de acceso internas del sistema de archivos</span><span class="sxs-lookup"><span data-stu-id="44d34-258">Internal file system paths</span></span>

    -   <span data-ttu-id="44d34-259">Carpetas compartidas en equipos internos</span><span class="sxs-lookup"><span data-stu-id="44d34-259">Shared folders on internal computers</span></span>

    -   <span data-ttu-id="44d34-260">Variables del espacio de ejecución</span><span class="sxs-lookup"><span data-stu-id="44d34-260">Variables in the runspace</span></span>

    -   <span data-ttu-id="44d34-261">Espacios de nombres de .NET Framework o tipos cargados</span><span class="sxs-lookup"><span data-stu-id="44d34-261">Loaded types or.NET Framework namespaces</span></span>

    -   <span data-ttu-id="44d34-262">Variables de entorno</span><span class="sxs-lookup"><span data-stu-id="44d34-262">Environment variables</span></span>

-   <span data-ttu-id="44d34-263">Los usuarios que han iniciado sesión en una configuración de sesión **NoLanguage** o en un espacio de ejecución restringido en Windows PowerShell Web Access no pueden ejecutar el comando **Exit** para finalizar la sesión.</span><span class="sxs-lookup"><span data-stu-id="44d34-263">Users who are signed in to a **NoLanguage** session configuration or a restricted runspace in Windows PowerShell Web Access cannot run the **Exit** command to end the session.</span></span> <span data-ttu-id="44d34-264">Para cerrar sesión, los usuarios deben hacer clic en **Cerrar sesión** en la página de la consola.</span><span class="sxs-lookup"><span data-stu-id="44d34-264">To sign out, users should click **Sign Out** on the console page.</span></span>

-   <span data-ttu-id="44d34-265"><span class="label">Conexión simultánea a varios equipos de destino</span></span><span class="sxs-lookup"><span data-stu-id="44d34-265"><span class="label">Connecting to multiple target computers simultaneously.</span></span></span>   <span data-ttu-id="44d34-266">Si se está ejecutando el servidor de puerta de enlace de Windows Server 2012, Windows PowerShell Web Access solo permite una conexión de equipo remoto por sesión del explorador. No permite a los usuarios iniciar sesión una vez y conectarse a varios equipos remotos mediante pestañas del explorador independientes.</span><span class="sxs-lookup"><span data-stu-id="44d34-266">If the gateway server is running Windows Server 2012, Windows PowerShell Web Access allows only one remote computer connection per browser session; it does not allow users to sign in once, and connect to multiple remote computers by using separate browser tabs.</span></span> <span data-ttu-id="44d34-267">Al abrir una nueva pestaña o ventana del explorador, Windows PowerShell Web Access le pedirá que desconecte su sesión actual e inicie una nueva sesión, para permitirle conectarse a un nuevo equipo remoto (o al mismo).</span><span class="sxs-lookup"><span data-stu-id="44d34-267">When you open a new tab or new browser window, Windows PowerShell Web Access prompts you to disconnect your current session and start a new session, so that you can connect to the new (or the same) remote computer.</span></span> <span data-ttu-id="44d34-268">No obstante, si desea iniciar sesión en dos o varias sesiones individuales en equipos remotos distintos, existe una característica de Internet Explorer que le permite crear una nueva sesión.</span><span class="sxs-lookup"><span data-stu-id="44d34-268">If two or more separate sessions to different remote computers are desired, however, a feature in Internet Explorer lets you create a new session.</span></span> <span data-ttu-id="44d34-269">Para iniciar una nueva sesión del explorador en Internet Explorer, presione **ALT**, abra el menú **Archivo** y luego seleccione **Nueva sesión**.</span><span class="sxs-lookup"><span data-stu-id="44d34-269">To start a new browser session in Internet Explorer, press **ALT**, open the **File** menu, and then select **New Session**.</span></span> <span data-ttu-id="44d34-270">Después, abra el sitio web de Windows PowerShell Web Access en una nueva sesión e inicie sesión para obtener acceso a otro equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="44d34-270">Then, open the Windows PowerShell Web Access website in the new session, and sign in to access another remote computer.</span></span>

    <span data-ttu-id="44d34-271">Cuando la puerta de enlace de Windows PowerShell Web Access se está ejecutando en Windows Server 2012 R2, los usuarios pueden abrir varias conexiones a equipos remotos en pestañas diferentes del explorador.</span><span class="sxs-lookup"><span data-stu-id="44d34-271">When the Windows PowerShell Web Access gateway is running on Windows Server 2012 R2, users can open multiple connections to remote computers in different browser tabs.</span></span> <span data-ttu-id="44d34-272">Si quiere abrir más de una conexión a un equipo remoto usando la consola de Windows PowerShell basada en web, póngase en contacto con su administrador de puerta de enlace de Windows PowerShell Web Access para ver si esta característica es compatible con el servidor de puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="44d34-272">If you want to open more than one connection to a remote computer by using the web-based Windows PowerShell console, check with your Windows PowerShell Web Access gateway administrator to see if this feature is supported by the gateway server.</span></span>

-   <span data-ttu-id="44d34-273"><span class="label">Sesiones persistentes de Windows PowerShell (reconexión)</span></span><span class="sxs-lookup"><span data-stu-id="44d34-273"><span class="label">Persistent Windows PowerShell sessions (Reconnection).</span></span></span>   <span data-ttu-id="44d34-274">Una vez agotado el tiempo de espera de la puerta de enlace de Windows PowerShell Web Access, se cierra la conexión remota entre esa puerta de enlace y el equipo de destino.</span><span class="sxs-lookup"><span data-stu-id="44d34-274">After you time out of the Windows PowerShell Web Access gateway, the remote connection between the gateway and the target computer is closed.</span></span> <span data-ttu-id="44d34-275">Esto detiene cualquier cmdlet o script que se encuentre en curso actualmente.</span><span class="sxs-lookup"><span data-stu-id="44d34-275">This stops any cmdlets or scripts that are currently in process.</span></span> <span data-ttu-id="44d34-276">Se recomienda usar la infraestructura **-Job** de Windows PowerShell al llevar a cabo tareas de ejecución prolongadas, para que pueda iniciar trabajos, desconectarse del equipo, volver a conectarte más tarde y hacer que los trabajos sean persistentes.</span><span class="sxs-lookup"><span data-stu-id="44d34-276">You are encouraged to use the Windows PowerShell **-Job** infrastructure when you are performing long-running tasks, so that you can start jobs, disconnect from the computer, reconnect later, and have jobs persist.</span></span> <span data-ttu-id="44d34-277">Otra ventaja de utilizar cmdlets **-Job** es que puede iniciarlos mediante Windows PowerShell Web Access, cerrar la sesión y volver a conectarse más tarde, ya sea mediante la ejecución de Windows PowerShell Web Access u otro host (como el Entorno de scripting integrado (ISE) de Windows PowerShell®).</span><span class="sxs-lookup"><span data-stu-id="44d34-277">Another benefit of using **-Job** cmdlets is that you can start them by using Windows PowerShell Web Access, sign out, and then reconnect later, either by running Windows PowerShell Web Access or another host (such as Windows PowerShell® Integrated Scripting Environment (ISE)).</span></span>

-   <span data-ttu-id="44d34-278"><span class="label">Cambiar el tamaño de la consola</span></span><span class="sxs-lookup"><span data-stu-id="44d34-278"><span class="label">Console resizing.</span></span></span>   <span data-ttu-id="44d34-279">Se puede cambiar el tamaño de la ventana de la consola de **PowerShell.exe** de las tres maneras siguientes.</span><span class="sxs-lookup"><span data-stu-id="44d34-279">The **PowerShell.exe** console window can be resized in the following three ways.</span></span>

    -   <span data-ttu-id="44d34-280">Arrastrar y ajustar el tamaño de la ventana de la consola con el mouse</span><span class="sxs-lookup"><span data-stu-id="44d34-280">Drag and adjust the console window size with a mouse</span></span>

    -   <span data-ttu-id="44d34-281">Cambiar las propiedades de alto y ancho mediante una GUI para propiedades de consola</span><span class="sxs-lookup"><span data-stu-id="44d34-281">Change the height and width properties by using a GUI for console properties</span></span>

    -   <span data-ttu-id="44d34-282">Cambiar el alto y el ancho de la ventana de la consola mediante un cmdlet</span><span class="sxs-lookup"><span data-stu-id="44d34-282">Changing the height and width of console windows with a cmdlet</span></span>

        <span data-ttu-id="44d34-283">La ventana de la consola de Windows PowerShell Web Access se puede configurar mediante cmdlets, de la siguiente manera.</span><span class="sxs-lookup"><span data-stu-id="44d34-283">The console window for Windows PowerShell Web Access can be configured by using the cmdlets as follows.</span></span> <span data-ttu-id="44d34-284">En el siguiente ejemplo, un usuario cambia el ancho de la consola de Windows PowerShell Web Access a **20**.</span><span class="sxs-lookup"><span data-stu-id="44d34-284">In the following example, a user changes the width of Windows PowerShell Web Access console to **20**.</span></span>

        [<span data-ttu-id="44d34-285">Copiar</span><span class="sxs-lookup"><span data-stu-id="44d34-285">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_778d5e55-9195-4bd7-b313-d1fbca7876e4'); "Copiar al Portapapeles.")

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        <span data-ttu-id="44d34-286">Puede cambiar el alto de la consola de modo similar.</span><span class="sxs-lookup"><span data-stu-id="44d34-286">You can change the height of the console in a similar manner.</span></span>

        <span data-ttu-id="44d34-287">En el [blog del equipo de Windows PowerShell](http://blogs.msdn.com/b/powershell/), encontrará más ejemplos para personalizar la visualización de la consola.</span><span class="sxs-lookup"><span data-stu-id="44d34-287">Additional examples for customizing the console view are available in the [Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/).</span></span>

<span data-ttu-id="44d34-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Consulte también</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="44d34-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="44d34-289">[Referencia sobre cmdlets de Windows PowerShell](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell en Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[Repositorio del centro de scripts de TechNet](http://gallery.technet.microsoft.com/scriptcenter)
[Centro de scripts: blog Hey, Scripting Guy!](https://technet.microsoft.com/scriptcenter)
[Blog del equipo de Windows PowerShell](http://blogs.msdn.com/b/powershell/)</span><span class="sxs-lookup"><span data-stu-id="44d34-289">[Windows PowerShell Cmdlet Reference](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell on Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[TechNet Script Center Repository](http://gallery.technet.microsoft.com/scriptcenter)
[Script Center - Hey, Scripting Guy!](https://technet.microsoft.com/scriptcenter)
[Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/)</span></span>

<span data-ttu-id="44d34-290"><span>Mostrar:</span> heredado protegido</span><span class="sxs-lookup"><span data-stu-id="44d34-290"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="44d34-291"><span class="stdr-votetitle">¿Le resultó útil esta página?</span></span><span class="sxs-lookup"><span data-stu-id="44d34-291"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="44d34-292">Sí No</span><span class="sxs-lookup"><span data-stu-id="44d34-292">Yes No</span></span>

<span data-ttu-id="44d34-293">¿Algún otro comentario?</span><span class="sxs-lookup"><span data-stu-id="44d34-293">Additional feedback?</span></span>

<span data-ttu-id="44d34-294"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caracteres restantes</span> Enviar Omitir esto</span><span class="sxs-lookup"><span data-stu-id="44d34-294"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="44d34-295"><span class="stdr-thankyou">Gracias.</span></span><span class="sxs-lookup"><span data-stu-id="44d34-295"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="44d34-296"><span class="stdr-appreciate">Apreciamos sus comentarios.</span></span><span class="sxs-lookup"><span data-stu-id="44d34-296"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="44d34-297">Administre su perfil</span><span class="sxs-lookup"><span data-stu-id="44d34-297">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="44d34-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span>Comentarios del sitio</a> Comentarios del sitio</span><span class="sxs-lookup"><span data-stu-id="44d34-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="44d34-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="44d34-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="44d34-300">Cuéntenos su experiencia...</span><span class="sxs-lookup"><span data-stu-id="44d34-300">Tell us about your experience...</span></span>

<span data-ttu-id="44d34-301">¿Se ha cargado rápido la página?</span><span class="sxs-lookup"><span data-stu-id="44d34-301">Did the page load quickly?</span></span>

<span data-ttu-id="44d34-302"><span> Sí<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="44d34-302"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="44d34-303">¿Le gusta el diseño de página?</span><span class="sxs-lookup"><span data-stu-id="44d34-303">Do you like the page design?</span></span>

<span data-ttu-id="44d34-304"><span> Sí<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="44d34-304"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="44d34-305">Más información</span><span class="sxs-lookup"><span data-stu-id="44d34-305">Tell us more</span></span>

-   [<span data-ttu-id="44d34-306">Boletín de Flash</span><span class="sxs-lookup"><span data-stu-id="44d34-306">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="44d34-307">Póngase en contacto con nosotros</span><span class="sxs-lookup"><span data-stu-id="44d34-307">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="44d34-308">Declaración de privacidad</span><span class="sxs-lookup"><span data-stu-id="44d34-308">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="44d34-309">Términos de uso</span><span class="sxs-lookup"><span data-stu-id="44d34-309">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="44d34-310">Marcas comerciales</span><span class="sxs-lookup"><span data-stu-id="44d34-310">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="44d34-311">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="44d34-311">© 2016 Microsoft</span></span>

<span data-ttu-id="44d34-312">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="44d34-312">© 2016 Microsoft</span></span>

<span data-ttu-id="44d34-313">Los scripts y el código de terceros vinculados a este sitio web o a los que este hace referencia se le ofrecen a usted bajo licencia de las partes propietarias de dicho código, no de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="44d34-313">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="44d34-314">Consulte los términos de uso de Ajax CDN para ASP.NET en http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="44d34-314">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

