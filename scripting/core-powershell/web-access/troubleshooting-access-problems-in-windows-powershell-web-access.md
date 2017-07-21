---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Solución de problemas de acceso en Windows PowerShell Web Access"
ms.openlocfilehash: c10e19b177110ff62d44f28b6a523380b55b79e0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
#  <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="6f877-103">Solución de problemas de acceso en Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="6f877-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="6f877-104">Actualizado: 24 de junio de 2013</span><span class="sxs-lookup"><span data-stu-id="6f877-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="6f877-105">Se aplica a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="6f877-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<a href="" id="BKMK_trouble"></a>

------------------------------------------------------------------------

<span data-ttu-id="6f877-106">En la siguiente tabla, se identifican algunos problemas comunes que pueden experimentar los usuarios cuando intentan conectarse a un equipo remoto mediante Windows PowerShell Web Access y se incluyen sugerencias para resolverlos.</span><span class="sxs-lookup"><span data-stu-id="6f877-106">The following table identifies some common problems that users might experience when they are attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="6f877-107">Problema</span><span class="sxs-lookup"><span data-stu-id="6f877-107">Problem</span></span></p></th>
<th><p><span data-ttu-id="6f877-108">Causa y solución posibles</span><span class="sxs-lookup"><span data-stu-id="6f877-108">Possible cause and solution</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="6f877-109">Error de inicio de sesión</span><span class="sxs-lookup"><span data-stu-id="6f877-109">Sign-in failure</span></span></p></td>
<td><p><span data-ttu-id="6f877-110">El error puede producirse por uno de los siguientes motivos.</span><span class="sxs-lookup"><span data-stu-id="6f877-110">Failure could occur because of any of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="6f877-111">Una regla de autorización que concede al usuario acceso al equipo, o a una configuración de sesión específica en un equipo remoto, no existe.</span><span class="sxs-lookup"><span data-stu-id="6f877-111">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span> <span data-ttu-id="6f877-112">La seguridad de Windows PowerShell Web Access es restrictiva. Se debe conceder a los usuarios acceso a los equipos remotos de manera explícita mediante reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="6f877-112">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span> <span data-ttu-id="6f877-113">Para más información sobre la creación de reglas de autorización, consulte <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a> (Reglas de autorización y características de seguridad de Windows PowerShell Web Access) en esta guía.</span><span class="sxs-lookup"><span data-stu-id="6f877-113">For more information about creating authorization rules, see <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a> in this guide.</span></span></p></li>
<li><p><span data-ttu-id="6f877-114">El usuario no tiene acceso autorizado al equipo de destino.</span><span class="sxs-lookup"><span data-stu-id="6f877-114">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="6f877-115">Este se determina mediante listas de control de acceso (ACL).</span><span class="sxs-lookup"><span data-stu-id="6f877-115">This is determined by access control lists (ACLs).</span></span> <span data-ttu-id="6f877-116">Para obtener más información, consulte Inicio de sesión en Windows PowerShell Web Access en <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Uso de la consola de Windows PowerShell basada en web</a> o visite el <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">blog del equipo de Windows PowerShell</a>.</span><span class="sxs-lookup"><span data-stu-id="6f877-116">For more information, see “Signing in to Windows PowerShell Web Access” in <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Use the Web-based Windows PowerShell Console</a>, or the <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell Team Blog</a>.</span></span></p>
<ul>
<li><p><span data-ttu-id="6f877-117">Es posible que la administración remota de Windows PowerShell no esté habilitada en el equipo de destino.</span><span class="sxs-lookup"><span data-stu-id="6f877-117">Windows PowerShell remote management might not be enabled on the destination computer.</span></span> <span data-ttu-id="6f877-118">Compruebe que esté habilitada en el equipo al que intenta conectarse el usuario.</span><span class="sxs-lookup"><span data-stu-id="6f877-118">Verify that it is enabled on the computer to which the user is trying to connect.</span></span> <span data-ttu-id="6f877-119">Para más información, consulte "Cómo configurar el equipo para la comunicación remota" en <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> en los temas de Ayuda conceptual de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f877-119">For more information, see “How to Configure Your Computer for Remoting” in <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> in the Windows PowerShell About Help Topics.</span></span></p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6f877-120">Cuando los usuarios intentan iniciar sesión en Windows PowerShell Web Access en una ventana de Internet Explorer, aparecerá la página <strong>Error interno del servidor</strong>, o bien Internet Explorer dejará de responder.</span><span class="sxs-lookup"><span data-stu-id="6f877-120">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an <strong>Internal Server Error</strong> page, or Internet Explorer stops responding.</span></span> <span data-ttu-id="6f877-121">Este problema es específico de Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="6f877-121">This issue is specific to Internet Explorer.</span></span></p></td>
<td><p><span data-ttu-id="6f877-122">Esto puede ocurrir si el usuario ha iniciado sesión con un nombre de dominio que contiene caracteres en chino o si el nombre del servidor de puerta de enlace contiene uno o más caracteres en este idioma.</span><span class="sxs-lookup"><span data-stu-id="6f877-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span> <span data-ttu-id="6f877-123">Para solucionar este problema, el usuario debe <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">instalar y ejecutar Internet Explorer 10</a> y luego llevar a cabo los siguientes pasos.</span><span class="sxs-lookup"><span data-stu-id="6f877-123">To work around this issue, the user should <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">install and run Internet Explorer 10</a>, and then perform the following steps.</span></span></p>
<ol>
<li><p><span data-ttu-id="6f877-124">Cambie la configuración <strong>Modo de documento</strong> de Internet Explorer a <strong>Estándar de IE10</strong>.</span><span class="sxs-lookup"><span data-stu-id="6f877-124">Change the Internet Explorer <strong>Document Mode</strong> setting to <strong>IE10 standards</strong>.</span></span></p>
<ol>
<li><p><span data-ttu-id="6f877-125">Presione <strong>F12</strong> para abrir la consola Herramientas de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="6f877-125">Press <strong>F12</strong> to open the Developer Tools console.</span></span></p></li>
<li><p><span data-ttu-id="6f877-126">En Internet Explorer 10, haga clic en <strong>Modo de explorador</strong> y, luego, seleccione <strong>Internet Explorer 10</strong>.</span><span class="sxs-lookup"><span data-stu-id="6f877-126">In Internet Explorer 10, click <strong>Browser Mode</strong>, and then select <strong>Internet Explorer 10</strong>.</span></span></p></li>
<li><p><span data-ttu-id="6f877-127">Haga clic en <strong>Modo de documento</strong> y, luego, en <strong>Estándar de IE10</strong>.</span><span class="sxs-lookup"><span data-stu-id="6f877-127">Click <strong>Document Mode</strong>, and then click <strong>IE10 standards</strong>.</span></span></p></li>
<li><p><span data-ttu-id="6f877-128">Vuelva a presionar <strong>F12</strong> para cerrar la consola Herramientas de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="6f877-128">Press <strong>F12</strong> again to close the Developer Tools console.</span></span></p></li>
</ol></li>
<li><p><span data-ttu-id="6f877-129">Deshabilite la configuración automática de servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="6f877-129">Disable automatic proxy configuration.</span></span></p>
<ol>
<li><p><span data-ttu-id="6f877-130">En Internet Explorer 10, haga clic en <strong>Herramientas</strong> y, luego, en <strong>Opciones de Internet</strong>.</span><span class="sxs-lookup"><span data-stu-id="6f877-130">In Internet Explorer 10, click <strong>Tools</strong>, and then click <strong>Internet Options</strong>.</span></span></p></li>
<li><p><span data-ttu-id="6f877-131">En el cuadro de diálogo <strong>Opciones de Internet</strong>, en la pestaña <strong>Conexiones</strong>, haga clic en <strong>Configuración de LAN</strong>.</span><span class="sxs-lookup"><span data-stu-id="6f877-131">In the <strong>Internet Options</strong> dialog box, on the <strong>Connections</strong> tab, click <strong>LAN settings</strong>.</span></span></p></li>
<li><p><span data-ttu-id="6f877-132">Desactive la casilla <strong>Detectar la configuración automáticamente</strong>.</span><span class="sxs-lookup"><span data-stu-id="6f877-132">Clear the <strong>Automatically detect settings</strong> check box.</span></span> <span data-ttu-id="6f877-133">Haga clic en<strong>Aceptar</strong> y, de nuevo, en <strong>Aceptar</strong> para cerrar el cuadro de diálogo <strong>Opciones de Internet</strong>.</span><span class="sxs-lookup"><span data-stu-id="6f877-133">Click <strong>OK</strong>, and then click <strong>OK</strong> again to close the <strong>Internet Options</strong> dialog box.</span></span></p></li>
</ol></li>
</ol></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6f877-134">Error al conectarse a un equipo de grupo de trabajo remoto</span><span class="sxs-lookup"><span data-stu-id="6f877-134">Cannot connect to a remote workgroup computer</span></span></p></td>
<td><p><span data-ttu-id="6f877-135">Si el equipo de destino es miembro de un grupo de trabajo, use la siguiente sintaxis para especificar su nombre de usuario e iniciar sesión en el equipo: &lt;<em>nombre_grupo_de_trabajo</em>&gt;\&It;<em>nombre_de_usuario</em>&gt;</span><span class="sxs-lookup"><span data-stu-id="6f877-135">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: &lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6f877-136">No se encuentran las herramientas de administración de Servidor web (IIS) (aún cuando está instalado el rol)</span><span class="sxs-lookup"><span data-stu-id="6f877-136">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span></p></td>
<td><p><span data-ttu-id="6f877-137">Si instaló Windows PowerShell Web Access mediante el cmdlet <span class="code">Install-WindowsFeature</span>, las herramientas de administración no se instalan, a menos que el parámetro <span class="code">IncludeManagementTools</span> se agregue al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6f877-137">If you installed Windows PowerShell Web Access by using the <span class="code">Install-WindowsFeature</span> cmdlet, management tools are not installed unless the <span class="code">IncludeManagementTools</span> parameter is added to the cmdlet.</span></span> <span data-ttu-id="6f877-138">Para ver un ejemplo, consulte el procedimiento sobre cómo instalar Windows PowerShell Web Access mediante cmdlets de Windows PowerShell en <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Instalación y uso de Windows PowerShell Web Access</a>.</span><span class="sxs-lookup"><span data-stu-id="6f877-138">For an example, see “To install Windows PowerShell Web Access by using Windows PowerShell cmdlets” in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access</a>.</span></span> <span data-ttu-id="6f877-139">Puede agregar la consola del Administrador de IIS y otras herramientas de administración de IIS que necesite; para ello, debe seleccionarlas en una sesión del Asistente para agregar roles y características destinada al servidor de puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="6f877-139">You can add the IIS Manager console and other IIS management tools that you need by selecting the tools in an Add Roles and Features Wizard session that is targeted at the gateway server.</span></span> <span data-ttu-id="6f877-140">El Asistente para agregar roles y características se abre en el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="6f877-140">The Add Roles and Features Wizard is opened from within Server Manager.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6f877-141">El sitio web de Windows PowerShell Web Access no es accesible</span><span class="sxs-lookup"><span data-stu-id="6f877-141">The Windows PowerShell Web Access website is not accessible</span></span></p></td>
<td><p><span data-ttu-id="6f877-142">Si la opción Configuración de seguridad mejorada está habilitada en Internet Explorer (IE ESC), puede agregar el sitio web de Windows PowerShell Web Access a la lista de sitios de confianza, o bien puede deshabilitar IE ESC.</span><span class="sxs-lookup"><span data-stu-id="6f877-142">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites, or disable IE ESC.</span></span> <span data-ttu-id="6f877-143">Puede deshabilitar IE ESC en el icono <strong>Propiedades</strong> de la página <strong>Servidor Local</strong> en el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="6f877-143">You can disable IE ESC in the <strong>Properties</strong> tile on the <strong>Local Server</strong> page in Server Manager.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6f877-144">Se muestra el siguiente mensaje de error al intentar establecer la conexión si el servidor de puerta de enlace es el equipo de destino y, además, se encuentra en un grupo de trabajo: <strong>Error de autorización. Compruebe que está autorizado para conectarse al equipo de destino.</strong></span><span class="sxs-lookup"><span data-stu-id="6f877-144">The following error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup: <strong>An authorization failure occurred. Verify that you are authorized to connect to the destination computer.</strong></span></span></p></td>
<td><p><span data-ttu-id="6f877-145">En una situación como esta, especifique el nombre de usuario, el nombre de equipo y el nombre del grupo de usuarios, tal como se muestra en la siguiente tabla.</span><span class="sxs-lookup"><span data-stu-id="6f877-145">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name as shown in the following table.</span></span> <span data-ttu-id="6f877-146">No use un punto (.) solo para representar el nombre de equipo.</span><span class="sxs-lookup"><span data-stu-id="6f877-146">Do not use a dot (.) by itself to represent the computer name.</span></span></p>
<div>
<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="6f877-147">Escenario</span><span class="sxs-lookup"><span data-stu-id="6f877-147">Scenario</span></span></p></th>
<th><p><span data-ttu-id="6f877-148">Parámetro UserName</span><span class="sxs-lookup"><span data-stu-id="6f877-148">UserName Parameter</span></span></p></th>
<th><p><span data-ttu-id="6f877-149">Parámetro UserGroup</span><span class="sxs-lookup"><span data-stu-id="6f877-149">UserGroup Parameter</span></span></p></th>
<th><p><span data-ttu-id="6f877-150">Parámetro ComputerName</span><span class="sxs-lookup"><span data-stu-id="6f877-150">ComputerName Parameter</span></span></p></th>
<th><p><span data-ttu-id="6f877-151">Parámetro ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="6f877-151">ComputerGroup Parameter</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="6f877-152">El servidor de puerta de enlace se encuentra en un dominio</span><span class="sxs-lookup"><span data-stu-id="6f877-152">Gateway server is in a domain</span></span></p></td>
<td><p><span data-ttu-id="6f877-153"><em>Nombre_servidor</em>\<em>nombre_usuario</em>, Localhost\<em>nombre_usuario</em> o .\<em>nombre_usuario</em></span><span class="sxs-lookup"><span data-stu-id="6f877-153"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="6f877-154"><em>Nombre_servidor</em>\<em>grupo_usuarios</em>, Localhost\<em>grupo_usuarios</em> o .\<em>grupo_usuarios</em></span><span class="sxs-lookup"><span data-stu-id="6f877-154"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em>, or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="6f877-155">Nombre completo del servidor de puerta de enlace o localhost</span><span class="sxs-lookup"><span data-stu-id="6f877-155">Fully qualified name of gateway server, or Localhost</span></span></p></td>
<td><p><span data-ttu-id="6f877-156"><em>Nombre_servidor</em>\<em>grupo_equipos</em>, Localhost\<em>grupo_equipos</em> o .\<em>grupo_equipos</em></span><span class="sxs-lookup"><span data-stu-id="6f877-156"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em>, or .\<em>computer_group</em></span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6f877-157">El servidor de puerta de enlace se encuentra en un grupo de trabajo</span><span class="sxs-lookup"><span data-stu-id="6f877-157">Gateway server is in a workgroup</span></span></p></td>
<td><p><span data-ttu-id="6f877-158"><em>Nombre_servidor</em>\<em>nombre_usuario</em>, Localhost\<em>nombre_usuario</em> o .\<em>nombre_usuario</em></span><span class="sxs-lookup"><span data-stu-id="6f877-158"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="6f877-159"><em>Nombre_servidor</em>\<em>grupo_usuarios</em>, Localhost\<em>grupo_usuarios</em> o .\<em>grupo_usuarios</em></span><span class="sxs-lookup"><span data-stu-id="6f877-159"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="6f877-160">Nombre del servidor</span><span class="sxs-lookup"><span data-stu-id="6f877-160">Server name</span></span></p></td>
<td><p><span data-ttu-id="6f877-161"><em>Nombre_servidor</em>\<em>grupo_equipos</em>, Localhost\<em>grupo_equipos</em> o .\<em>grupo_equipos</em></span><span class="sxs-lookup"><span data-stu-id="6f877-161"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> or .\<em>computer_group</em></span></span></p></td>
</tr>
</tbody>
</table>
</div>
<p><span data-ttu-id="6f877-162">Inicie sesión en un servidor de puerta de enlace como equipo de destino con credenciales que tengan uno de los siguientes formatos.</span><span class="sxs-lookup"><span data-stu-id="6f877-162">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="6f877-163"><em>Nombre_servidor</em>\<em>nombre_usuario</em></span><span class="sxs-lookup"><span data-stu-id="6f877-163"><em>Server_name</em>\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="6f877-164">Localhost\<em>nombre_usuario</em></span><span class="sxs-lookup"><span data-stu-id="6f877-164">Localhost\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="6f877-165">.\<em>nombre_usuario</em></span><span class="sxs-lookup"><span data-stu-id="6f877-165">.\<em>user_name</em></span></span></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6f877-166">En las reglas de autorización se muestra un identificador de seguridad (SID) en lugar de la sintaxis <em>nombre_usuario</em>/<em>nombre_equipo</em> </span><span class="sxs-lookup"><span data-stu-id="6f877-166">A security identifier (SID) is displayed in an authorization rule instead of the syntax <em>user_name</em>/<em>computer_name</em> </span></span></p></td>
<td><p><span data-ttu-id="6f877-167">La regla ya no es válida o se produjo un error en la consulta de Servicios de dominio de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6f877-167">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span> <span data-ttu-id="6f877-168">Por lo general, una regla de autorización no es válida en escenarios donde el servidor de puerta de enlace en algún momento perteneció a un grupo de trabajo, pero más tarde se unió a un dominio.</span><span class="sxs-lookup"><span data-stu-id="6f877-168">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6f877-169">No puede iniciar sesión en un equipo de destino que se ha especificado en las reglas de autorización como una dirección IPv6 con un dominio.</span><span class="sxs-lookup"><span data-stu-id="6f877-169">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span></p></td>
<td><p><span data-ttu-id="6f877-170">Las reglas de autorización no admiten direcciones IPv6 en forma de nombre de dominio.</span><span class="sxs-lookup"><span data-stu-id="6f877-170">Authorization rules do not support an IPv6 address in form of a domain name.</span></span> <span data-ttu-id="6f877-171">Para especificar un equipo de destino mediante una dirección IPv6, use la dirección IPv6 original (que contiene caracteres de dos puntos) en la regla de autorización.</span><span class="sxs-lookup"><span data-stu-id="6f877-171">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span> <span data-ttu-id="6f877-172">Tanto las direcciones IPv6 de dominio como las numéricas (con caracteres de dos puntos) se admiten como nombre del equipo de destino en la página de inicio de sesión de Windows PowerShell Web Access, pero no en las reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="6f877-172">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span> <span data-ttu-id="6f877-173">Para obtener más información sobre las direcciones IPv6, consulte <a href="https://technet.microsoft.com/library/cc781672.aspx">How IPv6 Works</a> (Funcionamiento de IPv6).</span><span class="sxs-lookup"><span data-stu-id="6f877-173">For more information about IPv6 addresses, see <a href="https://technet.microsoft.com/library/cc781672.aspx">How IPv6 Works</a>.</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="6f877-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Consulte también</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="6f877-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="6f877-175">[Reglas de autorización y características de seguridad de Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Uso de la consola de Windows PowerShell basada en web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about\_Remote\_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span><span class="sxs-lookup"><span data-stu-id="6f877-175">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span></span>

<span data-ttu-id="6f877-176"><span>Mostrar:</span> heredado protegido</span><span class="sxs-lookup"><span data-stu-id="6f877-176"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="6f877-177"><span class="stdr-votetitle">¿Le resultó útil esta página?</span></span><span class="sxs-lookup"><span data-stu-id="6f877-177"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="6f877-178">Sí No</span><span class="sxs-lookup"><span data-stu-id="6f877-178">Yes No</span></span>

<span data-ttu-id="6f877-179">¿Algún otro comentario?</span><span class="sxs-lookup"><span data-stu-id="6f877-179">Additional feedback?</span></span>

<span data-ttu-id="6f877-180"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caracteres restantes</span> Enviar Omitir esto</span><span class="sxs-lookup"><span data-stu-id="6f877-180"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="6f877-181"><span class="stdr-thankyou">Gracias.</span></span><span class="sxs-lookup"><span data-stu-id="6f877-181"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="6f877-182"><span class="stdr-appreciate">Apreciamos sus comentarios.</span></span><span class="sxs-lookup"><span data-stu-id="6f877-182"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="6f877-183">Administre su perfil</span><span class="sxs-lookup"><span data-stu-id="6f877-183">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="6f877-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span>Comentarios del sitio</a> Comentarios del sitio</span><span class="sxs-lookup"><span data-stu-id="6f877-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="6f877-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="6f877-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="6f877-186">Cuéntenos su experiencia...</span><span class="sxs-lookup"><span data-stu-id="6f877-186">Tell us about your experience...</span></span>

<span data-ttu-id="6f877-187">¿Se ha cargado rápido la página?</span><span class="sxs-lookup"><span data-stu-id="6f877-187">Did the page load quickly?</span></span>

<span data-ttu-id="6f877-188"><span> Sí<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="6f877-188"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="6f877-189">¿Le gusta el diseño de página?</span><span class="sxs-lookup"><span data-stu-id="6f877-189">Do you like the page design?</span></span>

<span data-ttu-id="6f877-190"><span> Sí<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="6f877-190"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="6f877-191">Más información</span><span class="sxs-lookup"><span data-stu-id="6f877-191">Tell us more</span></span>

-   [<span data-ttu-id="6f877-192">Boletín de Flash</span><span class="sxs-lookup"><span data-stu-id="6f877-192">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="6f877-193">Póngase en contacto con nosotros</span><span class="sxs-lookup"><span data-stu-id="6f877-193">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="6f877-194">Declaración de privacidad</span><span class="sxs-lookup"><span data-stu-id="6f877-194">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="6f877-195">Términos de uso</span><span class="sxs-lookup"><span data-stu-id="6f877-195">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="6f877-196">Marcas comerciales</span><span class="sxs-lookup"><span data-stu-id="6f877-196">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="6f877-197">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="6f877-197">© 2016 Microsoft</span></span>

<span data-ttu-id="6f877-198">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="6f877-198">© 2016 Microsoft</span></span>

<span data-ttu-id="6f877-199">Los scripts y el código de terceros vinculados a este sitio web o a los que este hace referencia se le ofrecen a usted bajo licencia de las partes propietarias de dicho código, no de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6f877-199">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="6f877-200">Consulte los términos de uso de Ajax CDN para ASP.NET en http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="6f877-200">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

