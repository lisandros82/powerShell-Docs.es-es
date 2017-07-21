---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "desinstalación de Windows PowerShell Web Access"
ms.openlocfilehash: 7231d5eadceda8e3b28d9a81c2b5dcbe43680ff2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
#  <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="87cb1-103">Desinstalar Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="87cb1-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="87cb1-104">Actualizado: 24 de junio de 2013</span><span class="sxs-lookup"><span data-stu-id="87cb1-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="87cb1-105">Se aplica a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="87cb1-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="87cb1-106">Siga los pasos facilitados en este tema para eliminar el sitio web y la aplicación de Windows PowerShell Web Access del servidor de puerta de enlace en el que se está ejecutando Windows Server 2012 R2 o Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="87cb1-106">Follow steps in this topic to delete the Windows PowerShell Web Access website and application from the gateway server that is running either Windows Server 2012 R2 or Windows Server 2012.</span></span> <span data-ttu-id="87cb1-107">Antes de comenzar, notifique a los usuarios de la consola basada en web de que quitará el sitio web.</span><span class="sxs-lookup"><span data-stu-id="87cb1-107">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<a href="" id="BKMK_uninstall"></a>

------------------------------------------------------------------------

<span data-ttu-id="87cb1-108">Antes de desinstalar Windows PowerShell Web Access del servidor de puerta de enlace, ejecute el cmdlet <span class="code">Uninstall-PswaWebApplication</span> para quitar el sitio web y las aplicaciones web de Windows PowerShell Web Access, o bien use el procedimiento del Administrador de IIS, [para eliminar el sitio web y las aplicaciones web de Windows PowerShell Web Access mediante el Administrador de IIS](#BKMK_delsite).</span><span class="sxs-lookup"><span data-stu-id="87cb1-108">Before you uninstall Windows PowerShell Web Access from the gateway server, either run the <span class="code">Uninstall-PswaWebApplication</span> cmdlet to remove the website and Windows PowerShell Web Access web applications, or use the IIS Manager procedure, [To delete the Windows PowerShell Web Access website and web applications by using IIS Manager](#BKMK_delsite).</span></span>

<span data-ttu-id="87cb1-109">Al desinstalar Windows PowerShell Web Access, no se desinstalan IIS ni las demás características que se instalaron automáticamente porque eran necesarias para la ejecución de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="87cb1-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="87cb1-110">El proceso de desinstalación deja instaladas las características de las cuales dependía Windows PowerShell Web Access. Si necesita desinstalarlas, puede hacerlo de manera individual.</span><span class="sxs-lookup"><span data-stu-id="87cb1-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

<span data-ttu-id="87cb1-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Desinstalación (rápida) recomendada</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="87cb1-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="87cb1-112">Los procedimientos de esta sección le ayudarán a desinstalar tanto la aplicación web como la característica de Windows PowerShell Web Access mediante cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="87cb1-112">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using Windows PowerShell cmdlets.</span></span>

###

<span data-ttu-id="87cb1-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Paso 1: Eliminar la aplicación web</span></a></span><span class="sxs-lookup"><span data-stu-id="87cb1-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="87cb1-114">Si ha especificado su propio nombre de sitio web personalizado, agregue el parámetro <span class="code">WebsiteName</span> a su comando y especifique el nombre del sitio web.</span><span class="sxs-lookup"><span data-stu-id="87cb1-114">If you have specified your own, custom website name, add the <span class="code">WebsiteName</span> parameter to your command, and specify the website name.</span></span> <span data-ttu-id="87cb1-115">Si ha usado una aplicación web personalizada (no la aplicación predeterminada, **pswa**, agregue el parámetro <span class="code">WebApplicationName</span> a su comando y especifique el nombre de la aplicación web.</span><span class="sxs-lookup"><span data-stu-id="87cb1-115">If you have used a custom web application (not the default application, **pswa**, add the <span class="code">WebApplicationName</span> parameter to your command, and specify the name of the web application.</span></span>

#### <a name="to-delete-the-website-and-web-applications-by-using-the-uninstall-pswawebapplication-cmdlet"></a><span data-ttu-id="87cb1-116">Para quitar el sitio web y las aplicaciones web mediante el cmdlet Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="87cb1-116">To delete the website and web applications by using the Uninstall-PswaWebApplication cmdlet</span></span>

1.  <span data-ttu-id="87cb1-117">Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="87cb1-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="87cb1-118">En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell** en la barra de tareas.</span><span class="sxs-lookup"><span data-stu-id="87cb1-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="87cb1-119">En la pantalla **Inicio** de Windows, haga clic en **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="87cb1-120">Escriba **Uninstall-PswaWebApplication** y después haga clic en **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-120">Type **Uninstall-PswaWebApplication**, and then press **Enter**.</span></span>

3.  <span data-ttu-id="87cb1-121">Si usa un certificado de prueba, agregue el parámetro <span class="code">DeleteTestCertificate</span> al cmdlet, como se muestra en el siguiente ejemplo.</span><span class="sxs-lookup"><span data-stu-id="87cb1-121">If you are using a test certificate, add the <span class="code">DeleteTestCertificate</span> parameter to the cmdlet, as shown in the following example.</span></span>

    [<span data-ttu-id="87cb1-122">Copiar</span><span class="sxs-lookup"><span data-stu-id="87cb1-122">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_28147344-ab2f-49e7-b1c2-6dbe649d4366'); "Copiar al Portapapeles.")

        Uninstall-PswaWebApplication -DeleteTestCertificate

###

<span data-ttu-id="87cb1-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Paso 2: Desinstalar Windows PowerShell Web Access</span></a></span><span class="sxs-lookup"><span data-stu-id="87cb1-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="87cb1-124">Para desinstalar Windows PowerShell Web Access mediante cmdlets de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="87cb1-124">To uninstall Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="87cb1-125">Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell con derechos de usuario elevados.</span><span class="sxs-lookup"><span data-stu-id="87cb1-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="87cb1-126">Si ya se ha abierto una sesión, vaya al siguiente paso.</span><span class="sxs-lookup"><span data-stu-id="87cb1-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="87cb1-127">En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell** en la barra de tareas y luego haga clic en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="87cb1-128">En la pantalla **Inicio** de Windows, haga clic con el botón derecho en **Windows PowerShell** y, luego, en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="87cb1-129">Escriba lo siguiente y luego presione **Entrar**, donde *computer_name* representa un servidor remoto del que desea quitar Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="87cb1-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="87cb1-130">El parámetro <span class="code">-Restart</span> reinicia automáticamente los servidores de destino, si es necesario para la eliminación.</span><span class="sxs-lookup"><span data-stu-id="87cb1-130">The <span class="code">-Restart</span> parameter automatically restarts destination servers if required by the removal.</span></span>

    [<span data-ttu-id="87cb1-131">Copiar</span><span class="sxs-lookup"><span data-stu-id="87cb1-131">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7b534520-f292-471f-89e3-a1079c03e369'); "Copiar al Portapapeles.")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="87cb1-132">Para quitar roles y características de un VHD sin conexión, debe agregar los parámetros <span class="code">-ComputerName</span> y <span class="code">-VHD</span> .</span><span class="sxs-lookup"><span data-stu-id="87cb1-132">To remove roles and features from an offline VHD, you must add both the <span class="code">-ComputerName</span> parameter and the <span class="code">-VHD</span> parameter.</span></span> <span data-ttu-id="87cb1-133">El parámetro <span class="code">-ComputerName</span> contiene el nombre del servidor en el que se montará el VHD y el parámetro <span class="code">-VHD</span> contiene la ruta de acceso al archivo VHD en el servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="87cb1-133">The <span class="code">-ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">-VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="87cb1-134">Copiar</span><span class="sxs-lookup"><span data-stu-id="87cb1-134">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_5d8f91ee-b91a-4653-b7df-e745187fd72d'); "Copiar al Portapapeles.")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

3.  <span data-ttu-id="87cb1-135">Para comprobar la eliminación de Windows PowerShell Web Access una vez finalizada, abra la página **Todos los servidores** del Administrador del servidor, seleccione un servidor del cual se haya quitado la característica y visualice el icono **Roles y características** en la página del servidor seleccionado.</span><span class="sxs-lookup"><span data-stu-id="87cb1-135">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span> <span data-ttu-id="87cb1-136">También puede ejecutar el cmdlet <span class="code">Get-WindowsFeature</span> destinado al servidor seleccionado (Get-WindowsFeature -ComputerName &lt;*computer\_name*&gt;) para ver una lista de los roles y las características instalados en el servidor.</span><span class="sxs-lookup"><span data-stu-id="87cb1-136">You can also run the <span class="code">Get-WindowsFeature</span> cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

<span data-ttu-id="87cb1-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Desinstalación personalizada</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="87cb1-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="87cb1-138">Los procedimientos de esta sección le ayudarán a desinstalar tanto la aplicación web como la característica de Windows PowerShell Web Access mediante el Asistente para quitar roles y características del Administrador del servidor y la consola de Administrador de IIS.</span><span class="sxs-lookup"><span data-stu-id="87cb1-138">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

###

<span data-ttu-id="87cb1-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Paso 1: Eliminar la aplicación web</span></a></span><span class="sxs-lookup"><span data-stu-id="87cb1-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-delete-the-windows-powershell-web-access-website-and-web-applications-by-using-iis-manager"></a><span data-ttu-id="87cb1-140">Para eliminar el sitio web y las aplicaciones web de Windows PowerShell Web Access mediante el Administrador de IIS</span><span class="sxs-lookup"><span data-stu-id="87cb1-140">To delete the Windows PowerShell Web Access website and web applications by using IIS Manager</span></span>

1.  <span data-ttu-id="87cb1-141">Abra la consola del Administrador de IIS mediante uno de los siguientes procedimientos.</span><span class="sxs-lookup"><span data-stu-id="87cb1-141">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="87cb1-142">Si ya se ha abierto, vaya al siguiente paso.</span><span class="sxs-lookup"><span data-stu-id="87cb1-142">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="87cb1-143">En el escritorio de Windows, haga clic en **Administrador del servidor** en la barra de tareas de Windows para iniciar el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="87cb1-143">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="87cb1-144">En el menú **Herramientas** del Administrador del servidor, haga clic en **Administrador de Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-144">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="87cb1-145">En la pantalla **Inicio** de Windows, escriba cualquier parte del nombre **Administrador de Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-145">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="87cb1-146">Haga clic en el acceso directo cuando se muestre en los resultados de **Aplicaciones**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-146">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="87cb1-147">En el panel del árbol del Administrador de IIS, seleccione el sitio web que ejecuta la aplicación web de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="87cb1-147">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

3.  <span data-ttu-id="87cb1-148">En el panel **Acciones**, en **Administrar sitio web**, haga clic en **Detener**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-148">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

4.  <span data-ttu-id="87cb1-149">En el panel del árbol, haga clic con el botón derecho en la aplicación web del sitio web que ejecuta la aplicación web de Windows PowerShell Web Access y, luego, haga clic en **Quitar**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-149">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

5.  <span data-ttu-id="87cb1-150">En el panel del árbol, seleccione **Grupos de aplicaciones**, seleccione la carpeta del grupo de aplicaciones de Windows PowerShell Web Access, haga clic en **Detener** en el panel **Acciones** y luego haga clic en **Quitar** en el panel de contenido.</span><span class="sxs-lookup"><span data-stu-id="87cb1-150">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

6.  <span data-ttu-id="87cb1-151">Cierre el Administrador de IIS.</span><span class="sxs-lookup"><span data-stu-id="87cb1-151">Close IIS Manager.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="87cb1-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="87cb1-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="87cb1-153">El certificado no se elimina durante la desinstalación.</span><span class="sxs-lookup"><span data-stu-id="87cb1-153">The certificate is not deleted during uninstallation.</span></span> <span data-ttu-id="87cb1-154">Si creó un certificado autofirmado o usó un certificado de prueba y desea quitarlo, hágalo en el Administrador de IIS.</span><span class="sxs-lookup"><span data-stu-id="87cb1-154">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="87cb1-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Paso 2: Desinstalar Windows PowerShell Web Access</span></a></span><span class="sxs-lookup"><span data-stu-id="87cb1-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="87cb1-156">Para desinstalar Windows PowerShell Web Access mediante el Asistente para quitar roles y características</span><span class="sxs-lookup"><span data-stu-id="87cb1-156">To uninstall Windows PowerShell Web Access by using the Remove Roles and Features Wizard</span></span>

1.  <span data-ttu-id="87cb1-157">Si ya se ha abierto el Administrador del servidor, vaya al siguiente paso.</span><span class="sxs-lookup"><span data-stu-id="87cb1-157">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="87cb1-158">Si todavía no se ha abierto el Administrador del servidor, ábralo mediante una de las siguientes acciones.</span><span class="sxs-lookup"><span data-stu-id="87cb1-158">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="87cb1-159">En el escritorio de Windows, haga clic en **Administrador del servidor** en la barra de tareas de Windows para iniciar el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="87cb1-159">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="87cb1-160">En la pantalla **Inicio** de Windows, haga clic en **Administrador del servidor**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-160">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="87cb1-161">En el menú **Administrar**, haga clic en **Quitar roles y funciones**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-161">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

3.  <span data-ttu-id="87cb1-162">En la página **Seleccionar servidor de destino**, seleccione el servidor o VHD sin conexión del cual desea quitar la característica.</span><span class="sxs-lookup"><span data-stu-id="87cb1-162">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="87cb1-163">Para seleccionar un VHD sin conexión, primero seleccione el servidor en el que montará el VHD y después seleccione el archivo VHD.</span><span class="sxs-lookup"><span data-stu-id="87cb1-163">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="87cb1-164">Una vez seleccionado el servidor de destino, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-164">After you have selected the destination server, click **Next**.</span></span>

4.  <span data-ttu-id="87cb1-165">Vuelva a hacer clic en **Siguiente** para ir directamente a la página **Quitar características**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-165">Click **Next** again to skip to the **Remove features** page.</span></span>

5.  <span data-ttu-id="87cb1-166">Desactive la casilla **Windows PowerShell Web Access** y luego haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-166">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

6.  <span data-ttu-id="87cb1-167">En la página **Confirmar selecciones de eliminación**, haga clic en **Quitar**.</span><span class="sxs-lookup"><span data-stu-id="87cb1-167">On the **Confirm removal selections** page, click **Remove**.</span></span>

<span data-ttu-id="87cb1-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Consulte también</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="87cb1-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="87cb1-169">[Instalación y uso de Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[Ayuda del Administrador de IIS 7.0](https://technet.microsoft.com/library/cc732664.aspx)</span><span class="sxs-lookup"><span data-stu-id="87cb1-169">[Install and Use Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)</span></span>

<span data-ttu-id="87cb1-170"><span>Mostrar:</span> heredado protegido</span><span class="sxs-lookup"><span data-stu-id="87cb1-170"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="87cb1-171"><span class="stdr-votetitle">¿Le resultó útil esta página?</span></span><span class="sxs-lookup"><span data-stu-id="87cb1-171"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="87cb1-172">Sí No</span><span class="sxs-lookup"><span data-stu-id="87cb1-172">Yes No</span></span>

<span data-ttu-id="87cb1-173">¿Algún otro comentario?</span><span class="sxs-lookup"><span data-stu-id="87cb1-173">Additional feedback?</span></span>

<span data-ttu-id="87cb1-174"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caracteres restantes</span> Enviar Omitir esto</span><span class="sxs-lookup"><span data-stu-id="87cb1-174"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="87cb1-175"><span class="stdr-thankyou">Gracias.</span></span><span class="sxs-lookup"><span data-stu-id="87cb1-175"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="87cb1-176"><span class="stdr-appreciate">Apreciamos sus comentarios.</span></span><span class="sxs-lookup"><span data-stu-id="87cb1-176"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="87cb1-177">Administre su perfil</span><span class="sxs-lookup"><span data-stu-id="87cb1-177">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="87cb1-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span>Comentarios del sitio</a> Comentarios del sitio</span><span class="sxs-lookup"><span data-stu-id="87cb1-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="87cb1-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="87cb1-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="87cb1-180">Cuéntenos su experiencia...</span><span class="sxs-lookup"><span data-stu-id="87cb1-180">Tell us about your experience...</span></span>

<span data-ttu-id="87cb1-181">¿Se ha cargado rápido la página?</span><span class="sxs-lookup"><span data-stu-id="87cb1-181">Did the page load quickly?</span></span>

<span data-ttu-id="87cb1-182"><span> Sí<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="87cb1-182"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="87cb1-183">¿Le gusta el diseño de página?</span><span class="sxs-lookup"><span data-stu-id="87cb1-183">Do you like the page design?</span></span>

<span data-ttu-id="87cb1-184"><span> Sí<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="87cb1-184"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="87cb1-185">Más información</span><span class="sxs-lookup"><span data-stu-id="87cb1-185">Tell us more</span></span>

-   [<span data-ttu-id="87cb1-186">Boletín de Flash</span><span class="sxs-lookup"><span data-stu-id="87cb1-186">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="87cb1-187">Póngase en contacto con nosotros</span><span class="sxs-lookup"><span data-stu-id="87cb1-187">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="87cb1-188">Declaración de privacidad</span><span class="sxs-lookup"><span data-stu-id="87cb1-188">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="87cb1-189">Términos de uso</span><span class="sxs-lookup"><span data-stu-id="87cb1-189">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="87cb1-190">Marcas comerciales</span><span class="sxs-lookup"><span data-stu-id="87cb1-190">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="87cb1-191">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="87cb1-191">© 2016 Microsoft</span></span>

<span data-ttu-id="87cb1-192">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="87cb1-192">© 2016 Microsoft</span></span>

<span data-ttu-id="87cb1-193">Los scripts y el código de terceros vinculados a este sitio web o a los que este hace referencia se le ofrecen a usted bajo licencia de las partes propietarias de dicho código, no de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="87cb1-193">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="87cb1-194">Consulte los términos de uso de Ajax CDN para ASP.NET en http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="87cb1-194">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

