---
ms.date: 2017-08-23
keywords: powershell,cmdlet
title: "desinstalación de Windows PowerShell Web Access"
ms.openlocfilehash: 7c71a245be244c1883598cdcddbf35e43c0fc7b0
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="6cdb9-103">Desinstalar Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="6cdb9-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="6cdb9-104">Actualizado: 24 de junio de 2013</span><span class="sxs-lookup"><span data-stu-id="6cdb9-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="6cdb9-105">Se aplica a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="6cdb9-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="6cdb9-106">Los pasos descritos en este tema quitan el sitio web de Windows PowerShell Web Access y la aplicación correspondiente del servidor de puerta de enlace en el que están instalados.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="6cdb9-107">Notificar a los usuarios</span><span class="sxs-lookup"><span data-stu-id="6cdb9-107">Notify users</span></span>

<span data-ttu-id="6cdb9-108">Antes de comenzar, notifique a los usuarios de la consola basada en web de que quitará el sitio web.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>


<span data-ttu-id="6cdb9-109">Antes de desinstalar Windows PowerShell Web Access del servidor de puerta de enlace, ejecute el cmdlet `Uninstall-PswaWebApplication` para quitar el sitio web y las aplicaciones web de Windows PowerShell Web Access, o bien use el procedimiento del Administrador de IIS, [para eliminar el sitio web y las aplicaciones web de Windows PowerShell Web Access mediante el Administrador de IIS]().</span><span class="sxs-lookup"><span data-stu-id="6cdb9-109">Before you uninstall Windows PowerShell Web Access from the gateway server, either run the `Uninstall-PswaWebApplication` cmdlet to remove the website and Windows PowerShell Web Access web applications, or use the IIS Manager procedure, [to delete the windows powershell web access website and web applications by using iis manager]().</span></span>

<span data-ttu-id="6cdb9-110">Al desinstalar Windows PowerShell Web Access, no se desinstalan IIS ni las demás características que se instalaron automáticamente porque eran necesarias para la ejecución de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-110">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="6cdb9-111">El proceso de desinstalación deja instaladas las características de las cuales dependía Windows PowerShell Web Access. Si necesita desinstalarlas, puede hacerlo de manera individual.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-111">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="6cdb9-112">Desinstalación (rápida) recomendada</span><span class="sxs-lookup"><span data-stu-id="6cdb9-112">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="6cdb9-113">Los procedimientos de esta sección le ayudarán a desinstalar:</span><span class="sxs-lookup"><span data-stu-id="6cdb9-113">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="6cdb9-114">la aplicación web de Windows PowerShell Web Access; y</span><span class="sxs-lookup"><span data-stu-id="6cdb9-114">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="6cdb9-115">la característica de Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="6cdb9-115">the Windows PowerShell Web Access feature</span></span>
 
<span data-ttu-id="6cdb9-116">usando cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-116">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="6cdb9-117">Paso 1: Eliminar la aplicación web usando cmdlets</span><span class="sxs-lookup"><span data-stu-id="6cdb9-117">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="6cdb9-118">Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-118">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="6cdb9-119">En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell** en la barra de tareas.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-119">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="6cdb9-120">En la pantalla **Inicio** de Windows, haga clic en **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-120">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="6cdb9-121">Escriba `Uninstall-PswaWebApplication` y, luego, presione **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-121">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="6cdb9-122">Si ha especificado su propio nombre de sitio web personalizado, agregue el parámetro `-WebsiteName` a su comando y especifique el nombre del sitio web.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-122">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="6cdb9-123">Si ha usado una aplicación web personalizada (no la aplicación predeterminada, **pswa**), agregue el parámetro `-WebApplicationName` a su comando y especifique el nombre de la aplicación web.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-123">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="6cdb9-124">Si usa un certificado de prueba, agregue el parámetro `DeleteTestCertificate` al cmdlet, como se muestra en el siguiente ejemplo.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-124">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="6cdb9-125">Paso 2: Desinstalar Windows PowerShell Web Access usando cmdlets</span><span class="sxs-lookup"><span data-stu-id="6cdb9-125">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="6cdb9-126">Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell con derechos de usuario elevados.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-126">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="6cdb9-127">Si ya se ha abierto una sesión, vaya al siguiente paso.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-127">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="6cdb9-128">En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell** en la barra de tareas y luego haga clic en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-128">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="6cdb9-129">En la pantalla **Inicio** de Windows, haga clic con el botón derecho en **Windows PowerShell** y, luego, en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-129">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="6cdb9-130">Escriba lo siguiente y luego presione **Entrar**, donde *computer_name* representa un servidor remoto del que desea quitar Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-130">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="6cdb9-131">El parámetro `-Restart` reinicia automáticamente los servidores de destino, si es necesario para la eliminación.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-131">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="6cdb9-132">Para quitar roles y características de un VHD sin conexión, debe agregar los parámetros `-ComputerName` y `-VHD`.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-132">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="6cdb9-133">El parámetro `-ComputerName` contiene el nombre del servidor en el que se montará el VHD y el parámetro `-VHD` contiene la ruta de acceso al archivo VHD en el servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-133">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="6cdb9-134">Para comprobar la eliminación de Windows PowerShell Web Access una vez finalizada, abra la página **Todos los servidores** del Administrador del servidor, seleccione un servidor del cual se haya quitado la característica y visualice el icono **Roles y características** en la página del servidor seleccionado.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-134">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="6cdb9-135">También puede ejecutar el cmdlet `Get-WindowsFeature` destinado al servidor seleccionado (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) para ver una lista de los roles y características instalados en el servidor.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-135">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="6cdb9-136">Desinstalación personalizada</span><span class="sxs-lookup"><span data-stu-id="6cdb9-136">Custom uninstallation</span></span>

<span data-ttu-id="6cdb9-137">Los procedimientos de esta sección le ayudarán a desinstalar tanto la aplicación web como la característica de Windows PowerShell Web Access mediante el Asistente para quitar roles y características del Administrador del servidor y la consola de Administrador de IIS.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-137">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="6cdb9-138">Paso 1: Eliminar la aplicación web mediante el Administrador de IIS</span><span class="sxs-lookup"><span data-stu-id="6cdb9-138">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="6cdb9-139">Abra la consola del Administrador de IIS mediante uno de los siguientes procedimientos.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-139">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="6cdb9-140">Si ya se ha abierto, vaya al siguiente paso.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-140">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="6cdb9-141">En el escritorio de Windows, haga clic en **Administrador del servidor** en la barra de tareas de Windows para iniciar el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-141">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="6cdb9-142">En el menú **Herramientas** del Administrador del servidor, haga clic en **Administrador de Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-142">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="6cdb9-143">En la pantalla **Inicio** de Windows, escriba cualquier parte del nombre **Administrador de Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-143">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="6cdb9-144">Haga clic en el acceso directo cuando se muestre en los resultados de **Aplicaciones**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-144">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="6cdb9-145">En el panel del árbol del Administrador de IIS, seleccione el sitio web que ejecuta la aplicación web de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-145">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="6cdb9-146">En el panel **Acciones**, en **Administrar sitio web**, haga clic en **Detener**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-146">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="6cdb9-147">En el panel del árbol, haga clic con el botón derecho en la aplicación web del sitio web que ejecuta la aplicación web de Windows PowerShell Web Access y, luego, haga clic en **Quitar**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-147">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="6cdb9-148">En el panel del árbol, seleccione **Grupos de aplicaciones**, seleccione la carpeta del grupo de aplicaciones de Windows PowerShell Web Access, haga clic en **Detener** en el panel **Acciones** y luego haga clic en **Quitar** en el panel de contenido.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-148">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="6cdb9-149">Cierre el Administrador de IIS.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-149">Close IIS Manager.</span></span>

> <span data-ttu-id="6cdb9-150">![Nota de advertencia](images/SecurityNote.jpeg)**Nota**:</span><span class="sxs-lookup"><span data-stu-id="6cdb9-150">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="6cdb9-151">El certificado no se elimina durante la desinstalación.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-151">The certificate is not deleted during uninstallation.</span></span> 
>
> <span data-ttu-id="6cdb9-152">Si creó un certificado autofirmado o usó un certificado de prueba y desea quitarlo, hágalo en el Administrador de IIS.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-152">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span> 

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="6cdb9-153">Paso 2: Desinstalar Windows PowerShell Web Access mediante el Asistente para quitar roles y características</span><span class="sxs-lookup"><span data-stu-id="6cdb9-153">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="6cdb9-154">Si ya se ha abierto el Administrador del servidor, vaya al siguiente paso.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-154">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="6cdb9-155">Si todavía no se ha abierto el Administrador del servidor, ábralo mediante una de las siguientes acciones.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-155">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="6cdb9-156">En el escritorio de Windows, haga clic en **Administrador del servidor** en la barra de tareas de Windows para iniciar el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-156">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="6cdb9-157">En la pantalla **Inicio** de Windows, haga clic en **Administrador del servidor**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-157">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="6cdb9-158">En el menú **Administrar**, haga clic en **Quitar roles y funciones**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-158">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="6cdb9-159">En la página **Seleccionar servidor de destino**, seleccione el servidor o VHD sin conexión del cual desea quitar la característica.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-159">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="6cdb9-160">Para seleccionar un VHD sin conexión, primero seleccione el servidor en el que montará el VHD y después seleccione el archivo VHD.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-160">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="6cdb9-161">Una vez seleccionado el servidor de destino, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-161">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="6cdb9-162">Vuelva a hacer clic en **Siguiente** para ir directamente a la página **Quitar características**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-162">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="6cdb9-163">Desactive la casilla **Windows PowerShell Web Access** y luego haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-163">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="6cdb9-164">En la página **Confirmar selecciones de eliminación**, haga clic en **Quitar**.</span><span class="sxs-lookup"><span data-stu-id="6cdb9-164">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="6cdb9-165">Véase también</span><span class="sxs-lookup"><span data-stu-id="6cdb9-165">See Also</span></span>

- [<span data-ttu-id="6cdb9-166">Instalación y uso de Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="6cdb9-166">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="6cdb9-167">Ayuda del Administrador de IIS 7.0</span><span class="sxs-lookup"><span data-stu-id="6cdb9-167">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)
