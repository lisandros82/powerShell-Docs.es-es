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
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Solución de problemas de acceso en Windows PowerShell Web Access

Actualizado: 24 de junio de 2013 (revisión: 23 de agosto de 2017)

Se aplica a: Windows Server 2012 R2, Windows Server 2012

En las siguientes secciones se identifican algunos problemas comunes que surgen al intentar conectarse a un equipo remoto mediante Windows PowerShell Web Access. También se incluyen sugerencias para resolver dichos problemas.

## <a name="sign-in-failure"></a>Error de inicio de sesión

El error puede producirse por uno de los siguientes motivos.

- Una regla de autorización que concede al usuario acceso al equipo, o a una configuración de sesión específica en un equipo remoto, no existe.

  La seguridad de Windows PowerShell Web Access es restrictiva. Se debe conceder a los usuarios acceso a los equipos remotos de manera explícita mediante reglas de autorización.

  Para más información sobre cómo crear reglas de autorización, vea [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md) (Reglas de autorización y características de seguridad de Windows PowerShell Web Access).

- El usuario no tiene acceso autorizado al equipo de destino. Este se determina mediante listas de control de acceso (ACL).

  Para más información, vea [Para iniciar sesión en Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access) o el Blog del equipo de Windows PowerShell.

- Es posible que la administración remota de Windows PowerShell no esté habilitada en el equipo de destino.

  Compruebe que la administración remota esté habilitada en el equipo al que intenta conectarse el usuario.

  Para más información, vea [How to Configure Your Computer for Remoting](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting) (Cómo configurar el equipo para la comunicación remota).

## <a name="internal-server-error"></a>Internal Server Error

Cuando los usuarios intentan iniciar sesión en Windows PowerShell Web Access en una ventana de Internet Explorer, aparecerá la página **Error interno del servidor**, o bien *Internet Explorer* dejará de responder.

Este problema es específico de Internet Explorer.

### <a name="possible-cause"></a>Causa posible

Esto puede ocurrir si el usuario ha iniciado sesión con un nombre de dominio que contiene caracteres en chino o si el nombre del servidor de puerta de enlace contiene uno o más caracteres en este idioma.

#### <a name="workaround"></a>Solución alternativa

1. Instale y ejecute Internet Explorer 10
1. Cambie la configuración **Modo de documento** de Internet Explorer a *Estándar de IE10*.
   1. Presione **F12** para abrir la consola Herramientas de desarrollo.
   1. En Internet Explorer 10, haga clic en **Modo de explorador** y, luego, seleccione *Internet Explorer 10*.
   1. Haga clic en **Modo de documento** y, luego, en *Estándar de IE10*.
   1. Vuelva a presionar **F12** para cerrar la consola Herramientas de desarrollo.
1. Deshabilite la configuración automática del proxy en Internet Explorer 10.
   1. Haga clic en **Herramientas** y, a continuación, haga clic en **Opciones de Internet**.
   1. En el cuadro de diálogo **Opciones de Internet**, en la pestaña **Conexiones**, haga clic en **Configuración de LAN**.
   1. Desactive la casilla **Detectar la configuración automáticamente**. Haga clic en**Aceptar** y, de nuevo, en **Aceptar** para cerrar el cuadro de diálogo *Opciones de Internet*.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Error al conectarse a un equipo de grupo de trabajo remoto

Si el equipo de destino pertenece a un grupo de trabajo, use la siguiente sintaxis para proporcionar su nombre de usuario e iniciar sesión en el equipo: `<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>No se encuentran las herramientas de administración de Servidor web (IIS) (aún cuando está instalado el rol)

Si instaló Windows PowerShell Web Access mediante el cmdlet `Install-WindowsFeature`, las herramientas de administración no se instalan, a menos que el parámetro **IncludeManagementTools** se agregue al cmdlet.

Para ver un ejemplo, vea [Para instalar Windows PowerShell Web Access mediante cmdlets de Windows PowerShell](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).

Puede agregar la consola del Administrador de IIS y otras herramientas de administración de IIS que necesite; para ello, debe seleccionarlas en una sesión del **Asistente para agregar roles y características** destinada al servidor de puerta de enlace. El Asistente para agregar roles y características se abre en el Administrador del servidor.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>No se puede obtener acceso al sitio web de Windows PowerShell Web Access

Si la opción Configuración de seguridad mejorada está habilitada en Internet Explorer (IE ESC), puede agregar el sitio web de Windows PowerShell Web Access a la lista de sitios de confianza.

Un enfoque que no se recomienda tanto (debido a los riesgos de seguridad) consistiría en deshabilitar IE ESC. Puede deshabilitar IE ESC en el icono Propiedades de la página Servidor Local en el Administrador del servidor.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Se produjo un error de autorización. Compruebe que está autorizado para conectarse al equipo de destino.

El mensaje de error anterior se muestra al intentar conectarse cuando el servidor de puerta de enlace es el equipo de destino y también se encuentra en un grupo de trabajo.

En una situación como esta, especifique el nombre de usuario, el nombre de equipo y el nombre del grupo de usuarios. No use un punto (.) solo para representar el nombre de equipo.

### <a name="scenarios-and-proper-values"></a>Escenarios y valores adecuados

#### <a name="all-cases"></a>Todos los casos

  Parámetro   |                                        Value
------------- | -----------------------------------------------------------------------------------
UserName      | `Server_name\user_name`<br/>`Localhost\user_name`<br/>`.\user_name`
UserGroup     | `Server_name\user_group`<br/>`Localhost\user_group`<br/>`.\user_group`
ComputerGroup | `Server_name\computer_group`<br/>`Localhost\computer_group`<br/>`.\computer_group`

#### <a name="gateway-server-is-in-a-domain"></a>El servidor de puerta de enlace se encuentra en un dominio

 Parámetro   |                        Value
------------ | ----------------------------------------------------
ComputerName | Nombre completo del servidor de puerta de enlace o localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>El servidor de puerta de enlace se encuentra en un grupo de trabajo

 Parámetro   |    Value
------------ | -----------
ComputerName | Nombre de servidor

### <a name="gateway-credentials"></a>Credenciales de puerta de enlace

Inicie sesión en un servidor de puerta de enlace como equipo de destino con credenciales que tengan uno de los siguientes formatos.

- `Server_name\user_name`
- `Localhost\user_name`
- `.\user_name`

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>En las reglas de autorización se muestra un identificador de seguridad (SID)

En la regla de autorización se muestra un identificador de seguridad (SID) en lugar de la sintaxis `user_name/computer_name`.

La regla ya no es válida o se produjo un error en la consulta de Servicios de dominio de Active Directory. Por lo general, una regla de autorización no es válida en escenarios donde el servidor de puerta de enlace en algún momento perteneció a un grupo de trabajo, pero más tarde se unió a un dominio.

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>No se puede iniciar sesión con una regla como dirección IPv6 con un dominio

No puede iniciar sesión en un equipo de destino que se ha especificado en las reglas de autorización como una dirección IPv6 con un dominio.

Las reglas de autorización no admiten direcciones IPv6 en forma de nombre de dominio.

Para especificar un equipo de destino mediante una dirección IPv6, use la dirección IPv6 original (que contiene caracteres de dos puntos) en la regla de autorización. Tanto las direcciones IPv6 de dominio como las numéricas (con caracteres de dos puntos) se admiten como nombre del equipo de destino en la página de inicio de sesión de Windows PowerShell Web Access, pero no en las reglas de autorización.

Para obtener más información sobre las direcciones IPv6, consulte [How IPv6 Works](/previous-versions/windows/it-pro/windows-server-2003/cc781672(v=ws.10)) (Funcionamiento de IPv6).

## <a name="see-also"></a>Consulte también

- [Reglas de autorización y características de seguridad de Windows PowerShell Web Access](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282394(v=ws.11))
- [Uso de la consola de Windows PowerShell basada en web](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11))
- [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
