---
ms.date: 08/23/2017
keywords: powershell, cmdlet
title: Solución de problemas de acceso en Windows PowerShell Web Access
ms.openlocfilehash: 818beffaf7df55ae36a154b7b751f9201c5b4299
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870190"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="e0f81-103">Solución de problemas de acceso en Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="e0f81-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="e0f81-104">Actualizado: 24 de junio de 2013 (revisión: 23 de agosto de 2017)</span><span class="sxs-lookup"><span data-stu-id="e0f81-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="e0f81-105">Se aplica a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="e0f81-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="e0f81-106">En las siguientes secciones se identifican algunos problemas comunes que surgen al intentar conectarse a un equipo remoto mediante Windows PowerShell Web Access. También se incluyen sugerencias para resolver dichos problemas.</span><span class="sxs-lookup"><span data-stu-id="e0f81-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="e0f81-107">Error de inicio de sesión</span><span class="sxs-lookup"><span data-stu-id="e0f81-107">Sign-in failure</span></span>

<span data-ttu-id="e0f81-108">El error puede producirse por uno de los siguientes motivos.</span><span class="sxs-lookup"><span data-stu-id="e0f81-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="e0f81-109">Una regla de autorización que concede al usuario acceso al equipo, o a una configuración de sesión específica en un equipo remoto, no existe.</span><span class="sxs-lookup"><span data-stu-id="e0f81-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="e0f81-110">La seguridad de Windows PowerShell Web Access es restrictiva. Se debe conceder a los usuarios acceso a los equipos remotos de manera explícita mediante reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="e0f81-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="e0f81-111">Para más información sobre cómo crear reglas de autorización, vea [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md) (Reglas de autorización y características de seguridad de Windows PowerShell Web Access).</span><span class="sxs-lookup"><span data-stu-id="e0f81-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="e0f81-112">El usuario no tiene acceso autorizado al equipo de destino.</span><span class="sxs-lookup"><span data-stu-id="e0f81-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="e0f81-113">Este se determina mediante listas de control de acceso (ACL).</span><span class="sxs-lookup"><span data-stu-id="e0f81-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="e0f81-114">Para más información, vea [Para iniciar sesión en Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access) o el Blog del equipo de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0f81-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="e0f81-115">Es posible que la administración remota de Windows PowerShell no esté habilitada en el equipo de destino.</span><span class="sxs-lookup"><span data-stu-id="e0f81-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="e0f81-116">Compruebe que la administración remota esté habilitada en el equipo al que intenta conectarse el usuario.</span><span class="sxs-lookup"><span data-stu-id="e0f81-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="e0f81-117">Para más información, vea [How to Configure Your Computer for Remoting](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting) (Cómo configurar el equipo para la comunicación remota).</span><span class="sxs-lookup"><span data-stu-id="e0f81-117">For more information, see [How to Configure Your Computer for Remoting](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="e0f81-118">Internal Server Error</span><span class="sxs-lookup"><span data-stu-id="e0f81-118">Internal Server Error</span></span>

<span data-ttu-id="e0f81-119">Cuando los usuarios intentan iniciar sesión en Windows PowerShell Web Access en una ventana de Internet Explorer, aparecerá la página **Error interno del servidor**, o bien *Internet Explorer* dejará de responder.</span><span class="sxs-lookup"><span data-stu-id="e0f81-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="e0f81-120">Este problema es específico de Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e0f81-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="e0f81-121">Causa posible</span><span class="sxs-lookup"><span data-stu-id="e0f81-121">Possible cause</span></span>

<span data-ttu-id="e0f81-122">Esto puede ocurrir si el usuario ha iniciado sesión con un nombre de dominio que contiene caracteres en chino o si el nombre del servidor de puerta de enlace contiene uno o más caracteres en este idioma.</span><span class="sxs-lookup"><span data-stu-id="e0f81-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="e0f81-123">Solución alternativa</span><span class="sxs-lookup"><span data-stu-id="e0f81-123">Workaround</span></span>

1. <span data-ttu-id="e0f81-124">Instale y ejecute Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="e0f81-124">Install and run Internet Explorer 10</span></span>
1. <span data-ttu-id="e0f81-125">Cambie la configuración **Modo de documento** de Internet Explorer a *Estándar de IE10*.</span><span class="sxs-lookup"><span data-stu-id="e0f81-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="e0f81-126">Presione **F12** para abrir la consola Herramientas de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="e0f81-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="e0f81-127">En Internet Explorer 10, haga clic en **Modo de explorador** y, luego, seleccione *Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="e0f81-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="e0f81-128">Haga clic en **Modo de documento** y, luego, en *Estándar de IE10*.</span><span class="sxs-lookup"><span data-stu-id="e0f81-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="e0f81-129">Vuelva a presionar **F12** para cerrar la consola Herramientas de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="e0f81-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="e0f81-130">Deshabilite la configuración automática del proxy en Internet Explorer 10.</span><span class="sxs-lookup"><span data-stu-id="e0f81-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="e0f81-131">Haga clic en **Herramientas** y, a continuación, haga clic en **Opciones de Internet**.</span><span class="sxs-lookup"><span data-stu-id="e0f81-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="e0f81-132">En el cuadro de diálogo **Opciones de Internet**, en la pestaña **Conexiones**, haga clic en **Configuración de LAN**.</span><span class="sxs-lookup"><span data-stu-id="e0f81-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="e0f81-133">Desactive la casilla **Detectar la configuración automáticamente**.</span><span class="sxs-lookup"><span data-stu-id="e0f81-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="e0f81-134">Haga clic en**Aceptar** y, de nuevo, en **Aceptar** para cerrar el cuadro de diálogo *Opciones de Internet*.</span><span class="sxs-lookup"><span data-stu-id="e0f81-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="e0f81-135">Error al conectarse a un equipo de grupo de trabajo remoto</span><span class="sxs-lookup"><span data-stu-id="e0f81-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="e0f81-136">Si el equipo de destino pertenece a un grupo de trabajo, use la siguiente sintaxis para proporcionar su nombre de usuario e iniciar sesión en el equipo: `<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="e0f81-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="e0f81-137">No se encuentran las herramientas de administración de Servidor web (IIS) (aún cuando está instalado el rol)</span><span class="sxs-lookup"><span data-stu-id="e0f81-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="e0f81-138">Si instaló Windows PowerShell Web Access mediante el cmdlet `Install-WindowsFeature`, las herramientas de administración no se instalan, a menos que el parámetro **IncludeManagementTools** se agregue al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e0f81-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the **IncludeManagementTools** parameter is added to the cmdlet.</span></span>

<span data-ttu-id="e0f81-139">Para ver un ejemplo, vea [Para instalar Windows PowerShell Web Access mediante cmdlets de Windows PowerShell](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="e0f81-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="e0f81-140">Puede agregar la consola del Administrador de IIS y otras herramientas de administración de IIS que necesite; para ello, debe seleccionarlas en una sesión del **Asistente para agregar roles y características** destinada al servidor de puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="e0f81-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span> <span data-ttu-id="e0f81-141">El Asistente para agregar roles y características se abre en el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="e0f81-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="e0f81-142">No se puede obtener acceso al sitio web de Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="e0f81-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="e0f81-143">Si la opción Configuración de seguridad mejorada está habilitada en Internet Explorer (IE ESC), puede agregar el sitio web de Windows PowerShell Web Access a la lista de sitios de confianza.</span><span class="sxs-lookup"><span data-stu-id="e0f81-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="e0f81-144">Un enfoque que no se recomienda tanto (debido a los riesgos de seguridad) consistiría en deshabilitar IE ESC.</span><span class="sxs-lookup"><span data-stu-id="e0f81-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span> <span data-ttu-id="e0f81-145">Puede deshabilitar IE ESC en el icono Propiedades de la página Servidor Local en el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="e0f81-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="e0f81-146">Se produjo un error de autorización.</span><span class="sxs-lookup"><span data-stu-id="e0f81-146">An authorization failure occurred.</span></span> <span data-ttu-id="e0f81-147">Compruebe que está autorizado para conectarse al equipo de destino.</span><span class="sxs-lookup"><span data-stu-id="e0f81-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="e0f81-148">El mensaje de error anterior se muestra al intentar conectarse cuando el servidor de puerta de enlace es el equipo de destino y también se encuentra en un grupo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="e0f81-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="e0f81-149">En una situación como esta, especifique el nombre de usuario, el nombre de equipo y el nombre del grupo de usuarios.</span><span class="sxs-lookup"><span data-stu-id="e0f81-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span> <span data-ttu-id="e0f81-150">No use un punto (.) solo para representar el nombre de equipo.</span><span class="sxs-lookup"><span data-stu-id="e0f81-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="e0f81-151">Escenarios y valores adecuados</span><span class="sxs-lookup"><span data-stu-id="e0f81-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="e0f81-152">Todos los casos</span><span class="sxs-lookup"><span data-stu-id="e0f81-152">All cases</span></span>

  <span data-ttu-id="e0f81-153">Parámetro</span><span class="sxs-lookup"><span data-stu-id="e0f81-153">Parameter</span></span>   |                                        <span data-ttu-id="e0f81-154">Value</span><span class="sxs-lookup"><span data-stu-id="e0f81-154">Value</span></span>
------------- | -----------------------------------------------------------------------------------
<span data-ttu-id="e0f81-155">UserName</span><span class="sxs-lookup"><span data-stu-id="e0f81-155">UserName</span></span>      | `Server_name\user_name`<br/>`Localhost\user_name`<br/>`.\user_name`
<span data-ttu-id="e0f81-156">UserGroup</span><span class="sxs-lookup"><span data-stu-id="e0f81-156">UserGroup</span></span>     | `Server_name\user_group`<br/>`Localhost\user_group`<br/>`.\user_group`
<span data-ttu-id="e0f81-157">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="e0f81-157">ComputerGroup</span></span> | `Server_name\computer_group`<br/>`Localhost\computer_group`<br/>`.\computer_group`

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="e0f81-158">El servidor de puerta de enlace se encuentra en un dominio</span><span class="sxs-lookup"><span data-stu-id="e0f81-158">Gateway server is in a domain</span></span>

 <span data-ttu-id="e0f81-159">Parámetro</span><span class="sxs-lookup"><span data-stu-id="e0f81-159">Parameter</span></span>   |                        <span data-ttu-id="e0f81-160">Value</span><span class="sxs-lookup"><span data-stu-id="e0f81-160">Value</span></span>
------------ | ----------------------------------------------------
<span data-ttu-id="e0f81-161">ComputerName</span><span class="sxs-lookup"><span data-stu-id="e0f81-161">ComputerName</span></span> | <span data-ttu-id="e0f81-162">Nombre completo del servidor de puerta de enlace o localhost</span><span class="sxs-lookup"><span data-stu-id="e0f81-162">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="e0f81-163">El servidor de puerta de enlace se encuentra en un grupo de trabajo</span><span class="sxs-lookup"><span data-stu-id="e0f81-163">Gateway server is in a workgroup</span></span>

 <span data-ttu-id="e0f81-164">Parámetro</span><span class="sxs-lookup"><span data-stu-id="e0f81-164">Parameter</span></span>   |    <span data-ttu-id="e0f81-165">Value</span><span class="sxs-lookup"><span data-stu-id="e0f81-165">Value</span></span>
------------ | -----------
<span data-ttu-id="e0f81-166">ComputerName</span><span class="sxs-lookup"><span data-stu-id="e0f81-166">ComputerName</span></span> | <span data-ttu-id="e0f81-167">Nombre de servidor</span><span class="sxs-lookup"><span data-stu-id="e0f81-167">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="e0f81-168">Credenciales de puerta de enlace</span><span class="sxs-lookup"><span data-stu-id="e0f81-168">Gateway credentials</span></span>

<span data-ttu-id="e0f81-169">Inicie sesión en un servidor de puerta de enlace como equipo de destino con credenciales que tengan uno de los siguientes formatos.</span><span class="sxs-lookup"><span data-stu-id="e0f81-169">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- `Server_name\user_name`
- `Localhost\user_name`
- `.\user_name`

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="e0f81-170">En las reglas de autorización se muestra un identificador de seguridad (SID)</span><span class="sxs-lookup"><span data-stu-id="e0f81-170">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="e0f81-171">En la regla de autorización se muestra un identificador de seguridad (SID) en lugar de la sintaxis `user_name/computer_name`.</span><span class="sxs-lookup"><span data-stu-id="e0f81-171">A security identifier (SID) is displayed in an authorization rule instead of the syntax `user_name/computer_name`.</span></span>

<span data-ttu-id="e0f81-172">La regla ya no es válida o se produjo un error en la consulta de Servicios de dominio de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e0f81-172">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span> <span data-ttu-id="e0f81-173">Por lo general, una regla de autorización no es válida en escenarios donde el servidor de puerta de enlace en algún momento perteneció a un grupo de trabajo, pero más tarde se unió a un dominio.</span><span class="sxs-lookup"><span data-stu-id="e0f81-173">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="e0f81-174">No se puede iniciar sesión con una regla como dirección IPv6 con un dominio</span><span class="sxs-lookup"><span data-stu-id="e0f81-174">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="e0f81-175">No puede iniciar sesión en un equipo de destino que se ha especificado en las reglas de autorización como una dirección IPv6 con un dominio.</span><span class="sxs-lookup"><span data-stu-id="e0f81-175">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="e0f81-176">Las reglas de autorización no admiten direcciones IPv6 en forma de nombre de dominio.</span><span class="sxs-lookup"><span data-stu-id="e0f81-176">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="e0f81-177">Para especificar un equipo de destino mediante una dirección IPv6, use la dirección IPv6 original (que contiene caracteres de dos puntos) en la regla de autorización.</span><span class="sxs-lookup"><span data-stu-id="e0f81-177">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span> <span data-ttu-id="e0f81-178">Tanto las direcciones IPv6 de dominio como las numéricas (con caracteres de dos puntos) se admiten como nombre del equipo de destino en la página de inicio de sesión de Windows PowerShell Web Access, pero no en las reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="e0f81-178">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="e0f81-179">Para obtener más información sobre las direcciones IPv6, consulte [How IPv6 Works](/previous-versions/windows/it-pro/windows-server-2003/cc781672(v=ws.10)) (Funcionamiento de IPv6).</span><span class="sxs-lookup"><span data-stu-id="e0f81-179">For more information about IPv6 addresses, see [How IPv6 Works](/previous-versions/windows/it-pro/windows-server-2003/cc781672(v=ws.10)).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0f81-180">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e0f81-180">See Also</span></span>

- <span data-ttu-id="e0f81-181">[Reglas de autorización y características de seguridad de Windows PowerShell Web Access](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282394(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="e0f81-181">[Authorization Rules and Security Features of Windows PowerShell Web Access](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282394(v=ws.11))</span></span>
- <span data-ttu-id="e0f81-182">[Uso de la consola de Windows PowerShell basada en web](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="e0f81-182">[Use the Web-based Windows PowerShell Console](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11))</span></span>
- [<span data-ttu-id="e0f81-183">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="e0f81-183">about_Remote_Requirements</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
