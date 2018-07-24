---
ms.date: 08/23/2017
keywords: powershell, cmdlet
title: Instalación y uso de Windows PowerShell Web Access
ms.openlocfilehash: c14da421e372f6c4c4f203b16bbd37f28a9ba255
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094269"
---
# <a name="install-and-use-windows-powershell-web-access"></a>Instalación y uso de Windows PowerShell Web Access

Actualizado: 5 de noviembre de 2013 (editado: 23 de agosto de 2017)

Se aplica a: Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>Introducción

Windows PowerShell Web Access, que se introdujo por primera vez en Windows Server 2012, actúa como puerta de enlace de Windows PowerShell y proporciona una consola de Windows PowerShell basada en web dirigida a un equipo remoto. Permite a los profesionales de TI ejecutar comandos y scripts de Windows PowerShell desde una consola de Windows PowerShell en un explorador web, sin que sea necesario contar con Windows PowerShell, software de administración remota o la instalación de un complemento de explorador en el dispositivo cliente. Lo único que se necesita para ejecutar la consola de Windows PowerShell basada en web es una puerta de enlace de Windows PowerShell Web Access correctamente configurada y un explorador en el dispositivo cliente que admita JavaScript y acepte cookies.

Entre los dispositivos cliente se incluyen equipos portátiles, equipos que no son de trabajo, equipos prestados, Tablet PC, quioscos multimedia web, equipos que no ejecutan un sistema operativo Windows y exploradores de teléfono móvil. Los profesionales de TI pueden llevar a cabo tareas críticas de administración en servidores remotos basados en Windows desde dispositivos que cuenten con acceso a una conexión de Internet y un explorador web.

Después de instalar y configurar la puerta de enlace correctamente, los usuarios pueden obtener acceso a una consola de Windows PowerShell mediante un explorador web. Al abrir el sitio web protegido de Windows PowerShell Web Access y, una vez que se hayan autenticado correctamente, los usuarios podrán ejecutar una consola de Windows PowerShell basada en web.

El proceso de instalación y configuración de Windows PowerShell Web Access consta de tres pasos:

1. [Instalar Windows PowerShell Web Access](#install-windows-powershell-web-access)
1. [Configurar la puerta de enlace](#configure-the-gateway)
1. [Configurar una regla de autorización restrictiva](#configure-a-restrictive-authorization-rule)

Antes de instalar y configurar Windows PowerShell Web Access, se recomienda leer toda la guía, que incluye instrucciones sobre cómo instalar, proteger y desinstalar Windows PowerShell Web Access.
En el tema [Uso de la consola de Windows PowerShell basada en web](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11)) se describe cómo los usuarios inician sesión en la consola basada en web y se explican las limitaciones y diferencias entre la consola de Windows PowerShell basada en web y la consola de **powershell.exe**. Los usuarios finales de la consola basada en web deben leer [Uso de la consola de Windows PowerShell basada en web](use-the-web-based-windows-powershell-console.md), pero no es necesario que lean el resto de esta guía.

En este tema no se proporciona una guía de operaciones exhaustiva de servidor web de IIS, sino solo los pasos necesarios para configurar la puerta de enlace de Windows PowerShell Web Access. Para obtener más información sobre la configuración y protección de sitios web en IIS, vea los recursos de documentación de IIS en la sección Vea también.

En el siguiente diagrama se muestra cómo funciona Windows PowerShell Web Access.

![Diagrama de Windows PowerShell Web Access](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Requisitos para ejecutar Windows PowerShell Web Access

Windows PowerShell Web Access requiere que Servidor web (IIS), .NET Framework 4.5 y Windows PowerShell 3.0 o Windows PowerShell 4.0 se ejecuten en el servidor donde desea ejecutar la puerta de enlace. Puede instalar Windows PowerShell Web Access en un servidor que ejecuta Windows Server 2012 R2 o Windows Server 2012 mediante el uso del Asistente para agregar roles y características en el Administrador del servidor o de los cmdlets de implementación de Windows PowerShell para el Administrador del servidor. Al instalar Windows PowerShell Web Access mediante el Administrador del servidor o sus cmdlets de implementación, automáticamente se agregan los roles y las características necesarios como parte del proceso de instalación.

Windows PowerShell Web Access permite a los usuarios remotos obtener acceso a los equipos de la organización mediante Windows PowerShell en un explorador web. Si bien Windows PowerShell Web Access es una herramienta de administración eficaz y conveniente, el acceso web conlleva riesgos de seguridad, por lo que debe configurarse de la manera más segura posible. Se recomienda que los administradores que configuran la puerta de enlace de Windows PowerShell Web Access usen los niveles de seguridad disponibles, tanto las reglas de autorización basadas en cmdlets incluidas con Windows PowerShell Web Access como los niveles de seguridad disponibles en Servidor web (IIS) y en aplicaciones de terceros. En esta documentación se incluyen ejemplos que no son seguros, recomendados únicamente para entornos de prueba, así como ejemplos recomendados para implementaciones seguras.

## <a name="browser-and-client-device-support"></a>Compatibilidad con exploradores y dispositivos cliente

Windows PowerShell Web Access admite los siguientes exploradores de Internet.
Aunque los exploradores móviles no se admiten oficialmente, muchos de ellos pueden ejecutar la consola de Windows PowerShell basada en web. También se espera que funcionen otros exploradores que aceptan cookies y ejecutan JavaScript y sitios web HTTPS, pero no se han probado de manera oficial.

### <a name="supported-desktop-computer-browsers"></a>Exploradores de equipos de escritorio admitidos

- Windows Internet Explorer para Microsoft Windows 8.0, 9.0, 10.0 y 11.0
- Mozilla Firefox 10.0.2
- Google Chrome 17.0.963.56m para Windows
- Apple Safari 5.1.2 para Windows
- Apple Safari 5.1.2 para Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Exploradores o dispositivos móviles mínimamente probados

- Windows Phone 7 y 7.5
- Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)
- Apple Safari para sistema operativo iPhone 5.0.1
- Apple Safari para sistema operativo iPad 2 5.0.1

### <a name="browser-requirements"></a>Requisitos de explorador

Para usar la consola de Windows PowerShell Web Access basada en web, los exploradores deben poder hacer lo siguiente.

- Permitir cookies del sitio web de la puerta de enlace de Windows PowerShell Web Access.
- Abrir y leer páginas HTTPS.
- Abrir y ejecutar sitios web que usen JavaScript.

## <a name="recommended-quick-deployment"></a>Implementación recomendada (rápida)

Puede instalar la puerta de enlace de Windows PowerShell Web Access en un servidor que ejecuta Windows Server 2012 R2 o Windows Server 2012 mediante el uso de los cmdlets de Windows PowerShell o del Asistente para agregar roles y características que se abre desde el Administrador del servidor. Para la instalación y la configuración rápida, use cmdlets de Windows PowerShell, como se describe en esta sección.

1. [Instalar Windows PowerShell Web Access](#install-Windows-powershell-web-access)
1. [Configurar la puerta de enlace](#configure-the-gateway)
1. [Configurar una regla de autorización restrictiva](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access-using-powershell-cmdlets"></a>Instalación de Windows PowerShell Web Access usando cmdlets de PowerShell

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Para instalar Windows PowerShell Web Access mediante cmdlets de Windows PowerShell

1. Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell con derechos de usuario elevados.
   - En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell**, en la barra de tareas y, luego,en **Ejecutar como administrador**.
   - En la pantalla **Inicio** de Windows, haga clic con el botón derecho en **Windows PowerShell** y, luego, en **Ejecutar como administrador**.

   > **![Nota](images/note.jpeg) Nota** En Windows PowerShell 3.0 y 4.0, no es necesario importar el módulo de cmdlets del Administrador del servidor en la sesión de Windows PowerShell antes de ejecutar los cmdlets que forman parte del módulo. El módulo se importa automáticamente la primera vez que se ejecuta un cmdlet que es parte del módulo. Asimismo, los cmdlets de Windows PowerShell no distinguen mayúsculas de minúsculas.

1. Escriba lo siguiente y después presione **Entrar**, donde *computer_name* representa un equipo remoto en el cual desea instalar Windows PowerShell Web Access, si procede. El parámetro `-Restart` reinicia automáticamente los servidores de destino si es necesario.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   > **![Nota](images/note.jpeg) Nota**
   >
   > Al instalarse Windows PowerShell Web Access mediante el uso de los cmdlets de Windows PowerShell, no se agregan herramientas de administración de Servidor web (IIS) de forma predeterminada. Si quiere instalar las herramientas de administración en el mismo servidor que el de la puerta de enlace de Windows PowerShell Web Access, agregue el parámetro `-IncludeManagementTools` al comando de instalación (como se indica en este paso). Si administra el sitio web de Windows PowerShell Web Access desde un equipo remoto, instale el complemento Administrador de IIS mediante la instalación de las [Herramientas de administración remota del servidor para Windows 8.1](https://www.microsoft.com/en-us/download/details.aspx?id=39296) o [Herramientas de administración remota del servidor para Windows 8](https://www.microsoft.com/en-us/download/details.aspx?id=28972) en el equipo desde el que quiere administrar la puerta de enlace.

   Para instalar roles y características en un VHD sin conexión, debe agregar los parámetros `-ComputerName` y `-VHD`. El parámetro `-ComputerName` contiene el nombre del servidor en el que se montará el VHD y el parámetro `-VHD` contiene la ruta de acceso al archivo VHD en el servidor especificado.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. Una vez completada la instalación, compruebe que Windows PowerShell Web Access se haya instalado en los servidores de destino mediante la ejecución del cmdlet `Get-WindowsFeature` en un servidor de destino, en una consola de Windows PowerShell abierta con derechos de usuario elevados. Otro modo de comprobar que se haya instalado Windows PowerShell Web Access en la consola del Administrador del servidor consiste en seleccionar un servidor de destino en la página **Todos los servidores** y, a continuación, visualizar el icono **Roles y características** del servidor seleccionado. También puede ver el archivo Léame para Windows PowerShell Web Access.

1. Una vez instalado Windows PowerShell Web Access, se le pedirá que revise el archivo Léame, que contiene las instrucciones de configuración necesarias básicas para la puerta de enlace. Estas instrucciones de configuración también se encuentran en la sección siguiente, [Configurar la puerta de enlace](#configure-the-gateway). La ruta de acceso al archivo Léame es `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Configurar la puerta de enlace

El cmdlet **Install-PswaWebApplication** es un método rápido para configurar Windows PowerShell Web Access. Si bien puede agregar el parámetro `UseTestCertificate` al cmdlet `Install-PswaWebApplication` para instalar un certificado SSL autofirmado con fines de prueba, esto no es seguro. En un entorno de producción seguro, siempre use un certificado SSL válido firmado por una entidad de certificación (CA).
Los administradores pueden reemplazar el certificado de prueba por un certificado firmado de su elección mediante la consola del Administrador de IIS.

Puede completar la configuración de la aplicación web Windows PowerShell Web Access mediante la ejecución del cmdlet `Install-PswaWebApplication` o mediante los pasos de configuración basados en GUI del Administrador de IIS. De manera predeterminada, el cmdlet instala la aplicación web, **pswa** (y un grupo de aplicaciones, **pswa\_pool**), en el contenedor **Sitio web predeterminado**, como se muestra en el Administrador de IIS. Si lo desea, puede indicar al cmdlet que cambie el contenedor de sitio predeterminado de la aplicación web. El Administrador de IIS proporciona opciones de configuración que se encuentran disponibles para las aplicaciones web, como cambiar el número de puerto o el certificado de Capa de sockets seguros (SSL).

> **![Nota de seguridad](images/securitynote.jpeg) Nota de seguridad**
>
> Se recomienda encarecidamente que los administradores configuren la puerta de enlace para que use un certificado válido firmado por una CA.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>Para configurar la puerta de enlace de Windows PowerShell Web Access con un certificado de prueba mediante Install-PswaWebApplication

1. Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell.

   - En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell** en la barra de tareas.

   - En la pantalla **Inicio** de Windows, haga clic en **Windows PowerShell**.

2. Escriba lo siguiente y, después, presione **Entrar**.

   `Install-PswaWebApplication -UseTestCertificate`

   > **![Nota de seguridad](images/securitynote.jpeg) Nota de seguridad**
   >
   > El parámetro `UseTestCertificate` solo debe usarse en un entorno de prueba privado. Para un entorno de producción seguro, se recomienda usar un certificado válido firmado por una CA.

   La ejecución del cmdlet instala la aplicación web Windows PowerShell Web Access dentro del contenedor Sitio web predeterminado de IIS. El cmdlet crea la infraestructura necesaria para ejecutar Windows PowerShell Web Access en el sitio web predeterminado, `https://<server_name>/pswa`. Para instalar la aplicación web en otro sitio web, proporcione el nombre del sitio web mediante la adición del parámetro `WebSiteName`. Para cambiar el nombre de la aplicación web (el nombre predeterminado es `pswa`), agregue el parámetro `WebApplicationName` .

   La siguiente configuración se establece mediante la ejecución del cmdlet. Puede cambiarla de forma manual en la consola del Administrador de IIS, si lo desea.

   - Path: /pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: `%*windir*%/Web/PowerShellWebAccess/wwwroot`

     **Ejemplo**: `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

     En este ejemplo, el sitio web resultante para Windows PowerShell Web Access es `https://<server_name>/myWebApp`.

   > **![Nota](images/note.jpeg) Nota**
   >
   > No podrá iniciar sesión hasta que se haya concedido a los usuarios acceso al sitio web mediante la adición de reglas de autorización. Para más información, vea [Configurar una regla de autorización restrictiva](#configure-a-restrictive-authorization-rule) y [Reglas de autorización y características de seguridad de Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>Para configurar la puerta de enlace de Windows PowerShell Web Access con un certificado original mediante Install-PswaWebApplication y el Administrador de IIS

1. Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell.

   - En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell** en la barra de tareas.

   - En la pantalla **Inicio** de Windows, haga clic en **Windows PowerShell**.

2. Escriba lo siguiente y, después, presione **Entrar**.

   `Install-PswaWebApplication`

   La siguiente configuración de puerta de enlace se establece mediante la ejecución del cmdlet.
   Puede cambiarla de forma manual en la consola del Administrador de IIS, si lo desea.
   También puede especificar valores para los parámetros `WebsiteName` y `WebApplicationName` del cmdlet `Install-PswaWebApplication`.

   - Path: /pswa

   - ApplicationPool: pswa_pool

   - EnabledProtocols: http

   - PhysicalPath: `%*windir*%/Web/PowerShellWebAccess/wwwroot`

3. Abra la consola del Administrador de IIS mediante uno de los siguientes procedimientos.

   - En el escritorio de Windows, haga clic en **Administrador del servidor** en la barra de tareas de Windows para iniciar el Administrador del servidor. En el menú **Herramientas** del Administrador del servidor, haga clic en **Administrador de Internet Information Services (IIS)**.

   - En la pantalla **Inicio** de Windows, haga clic en **Administrador del servidor**.

4. En el panel del árbol del Administrador de IIS, expanda el nodo del servidor en el que está instalado Windows PowerShell Web Access hasta que aparezca la carpeta **Sitios**. Expanda la carpeta **Sitios**.

5. Seleccione el sitio web en el que ha instalado la aplicación web Windows PowerShell Web Access. En el panel **Acciones**, haga clic en **Enlaces**.

6. En el cuadro de diálogo **Enlaces de sitios**, haga clic en **Agregar**.

7. En el cuadro de diálogo **Agregar enlace de sitio**, en el campo **Tipo**, seleccione **https**.

8. En el campo **Certificado SSL**, seleccione su certificado firmado en el menú desplegable. Haga clic en **Aceptar**. Consulte [Para configurar un certificado SSL en el Administrador de IIS](#to-configure-an-ssl-certificate-in-iis-Manager) en este tema para obtener más información sobre cómo obtener un certificado.

   La aplicación web Windows PowerShell Web Access ya está configurada para usar su certificado SSL firmado.

   Para obtener acceso a Windows PowerShell Web Access, abra **https://\<nombre-servidor\>/pswa** en una ventana del explorador.

   > **![Nota](images/note.jpeg) Nota**
   >
   > No podrá iniciar sesión hasta que se haya concedido a los usuarios acceso al sitio web mediante la adición de reglas de autorización.
   > Para más información, vea [Configurar una regla de autorización restrictiva](#configure-a-restrictive-authorization-rule) en este tema y [Reglas de autorización y características de seguridad de Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>configurar una regla de autorización restrictiva

Una vez instalado Windows PowerShell Web Access y configurada la puerta de enlace, los usuarios podrán abrir la página de inicio de sesión en un explorador, pero no podrán iniciar sesión hasta que el administrador de Windows PowerShell Web Access les conceda acceso de manera explícita. El control de acceso de Windows PowerShell Web Access se administra mediante el conjunto de cmdlets de Windows PowerShell descrito en la siguiente tabla. No existe una GUI comparable para agregar o administrar reglas de autorización. Para obtener más información sobre los cmdlets de Windows PowerShell Web Access, consulte los temas de referencia de cmdlet, [Windows PowerShell Web Access Cmdlets](cmdlets/web-access-cmdlets.md) (Cmdlets de Windows PowerShell Web Access).

Para obtener más información sobre la seguridad y las reglas de autorización de Windows PowerShell Web Access, consulte [Reglas de autorización y características de seguridad de Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Para agregar una regla de autorización restrictiva

1. Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell con derechos de usuario elevados.

   - En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell**, en la barra de tareas y, luego,en **Ejecutar como administrador**.

   - En la pantalla **Inicio** de Windows, haga clic con el botón derecho en **Windows PowerShell** y, luego, en **Ejecutar como administrador**.

2. Paso opcional para restringir el acceso del usuario mediante configuraciones de sesión: Compruebe que las configuraciones de sesión que quiere usar en las reglas ya existen. Si aún no se han creado, use las instrucciones para crear configuraciones de sesión proporcionadas en [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Escriba lo siguiente y, después, presione **Entrar**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Esta regla de autorización concede a un usuario específico acceso a un equipo de la red al que tiene acceso normalmente, con acceso a una configuración de sesión determinada en el ámbito de las necesidades de cmdlet y scripting típicas del usuario.

   En el siguiente ejemplo, se concede acceso a un usuario llamado `JSmith` en el dominio `Contoso` para administrar el equipo `Contoso_214` y usar una configuración de sesión llamada `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Compruebe que la regla se haya creado mediante la ejecución del cmdlet `Get-PswaAuthorizationRule` o `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`.

5. Por ejemplo, `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Después de configurar una regla de autorización, está listo para que los usuarios autorizados inicien sesión en la consola basada en web y empiecen a usar Windows PowerShell Web Access.

## <a name="custom-deployment"></a>Implementación personalizada

Puede instalar la puerta de enlace de Windows PowerShell Web Access en un servidor que ejecuta Windows Server 2012 R2 o Windows Server 2012 mediante el uso del Asistente para agregar roles y características en el Administrador del servidor. Después de instalar Windows PowerShell Web Access, puede personalizar la configuración de la puerta de enlace en el Administrador de IIS.

### <a name="install-windows-powershell-web-access-using-the-add-roles-and-features-wizard"></a>Instalación de Windows PowerShell Web Access mediante el Asistente para agregar roles y características

1. Si ya se ha abierto el Administrador del servidor, vaya al siguiente paso. Si todavía no se ha abierto el Administrador del servidor, ábralo mediante una de las siguientes acciones.

   - En el escritorio de Windows, haga clic en **Administrador del servidor** en la barra de tareas de Windows para iniciar el Administrador del servidor.

   - En la pantalla **Inicio** de Windows, haga clic en **Administrador del servidor**.

2. En el menú **Administrar**, haga clic en **Agregar roles y características**.

3. En la página **Seleccionar tipo de instalación**, seleccione **Instalación basada en características o en roles**. Haga clic en **Siguiente**.

4. En la página **Seleccionar servidor de destino**, seleccione un servidor del grupo de servidores o un VHD sin conexión. Para seleccionar un VHD sin conexión como servidor de destino, primero seleccione el servidor en el que montará el VHD y, a continuación, seleccione el archivo VHD. Para obtener información sobre cómo agregar servidores al grupo de servidores, consulte la Ayuda del Administrador del servidor. Una vez seleccionado el servidor de destino, haga clic en **Siguiente**.

5. En la página **Seleccionar características** del asistente, expanda **Windows PowerShell** y seleccione **Windows PowerShell Web Access**.

6. Se le pedirá que agregue las características necesarias, como .NET Framework 4.5 y los servicios de rol de Servidor web (IIS). Agregue las características necesarias y continúe.

   > **![Nota](images/note.jpeg) Nota**
   >
   > Al instalar Windows PowerShell Web Access mediante el uso del Asistente para agregar roles y características también se instala Servidor web (IIS), incluido el complemento Administrador de IIS. El complemento y otras herramientas de administración de IIS se instalan de manera predeterminada si usa el Asistente para agregar roles y características. Si instala Windows PowerShell Web Access mediante cmdlets de Windows PowerShell, como se describe en el siguiente procedimiento, las herramientas de administración no se agregan de manera predeterminada.

7. En la página **Confirmar selecciones de instalación**, si los archivos de características para Windows PowerShell Web Access no están almacenados en el servidor de destino seleccionado en el paso 4, haga clic en **Especifique una ruta de acceso de origen alternativa** y proporcione la ruta de acceso a los archivos de características. De lo contrario, haga clic en **Instalar**.

8. Después de hacer clic en **Instalar**, la página **Progreso de la instalación** mostrará el progreso de la instalación, los resultados y diferentes mensajes, como advertencias, errores o los pasos de configuración posteriores a la instalación necesarios para Windows PowerShell Web Access. Una vez instalado Windows PowerShell Web Access, se le pedirá que revise el archivo Léame, que contiene las instrucciones de configuración necesarias básicas para la puerta de enlace. Estas instrucciones también se incluyen en este tema. La ruta de acceso al archivo Léame es `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>configurar la puerta de enlace

Las instrucciones de esta sección explican cómo instalar la aplicación web Windows PowerShell Web Access en un subdirectorio del sitio web, no en el directorio raíz. Este procedimiento es el equivalente basado en GUI de las acciones realizadas por el cmdlet `Install-PswaWebApplication`. En esta sección, también se incluyen instrucciones sobre cómo usar el Administrador de IIS para configurar la puerta de enlace de Windows PowerShell Web Access como un sitio web raíz.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>Para usar el Administrador de IIS para configurar la puerta de enlace en un sitio web existente

1. Abra la consola del Administrador de IIS mediante uno de los siguientes procedimientos.

   - En el escritorio de Windows, haga clic en **Administrador del servidor** en la barra de tareas de Windows para iniciar el Administrador del servidor. En el menú **Herramientas** del Administrador del servidor, haga clic en **Administrador de Internet Information Services (IIS)**.

   - En la pantalla **Inicio** de Windows, escriba cualquier parte del nombre **Administrador de Internet Information Services (IIS)**. Haga clic en el acceso directo cuando se muestre en los resultados de **Aplicaciones**.

2. Cree un nuevo grupo de aplicaciones para Windows PowerShell Web Access. Expanda el nodo del servidor de puerta de enlace en el panel del árbol del Administrador de IIS, seleccione **Grupos de aplicaciones** y haga clic en **Agregar grupo de aplicaciones** en el panel **Acciones**.

3. Agregue un nuevo grupo de aplicaciones con el nombre **pswa_pool** o proporcione otro nombre. Haga clic en **Aceptar**.

4. En el panel del árbol del Administrador de IIS, expanda el nodo del servidor en el que está instalado Windows PowerShell Web Access hasta que aparezca la carpeta **Sitios**. Seleccione la carpeta **Sitios**.

5. Haga clic con el botón derecho en el sitio web (por ejemplo, **Sitio web predeterminado**) en el que quiere agregar el sitio web de Windows PowerShell Web Access y, después, haga clic en **Agregar aplicación**.

6. En el campo **Alias**, escriba pswa o proporcione un alias diferente. El alias se convierte en el nombre de directorio virtual. Por ejemplo, **pswa** en la siguiente dirección URL representa el alias especificado en este paso: **https://\<nombre_servidor\>/pswa**.

7. En el campo **Grupo de aplicaciones**, seleccione el grupo de aplicaciones creado en el paso 3.

8. En el campo **Ruta de acceso física**, busque la ubicación de la aplicación. Puede usar la ubicación predeterminada %windir%/Web/PowerShellWebAccess/wwwroot. Haga clic en **Aceptar**.

9. Siga los pasos del procedimiento Para configurar un certificado SSL en el Administrador de IIS](#to-configure-an-ssl-certificate-in-iis-Manager) en este tema.

10. ![](images/SecurityNote.jpeg) Paso de seguridad opcional:

    Con el sitio web seleccionado en el panel del árbol, haga doble clic en **Configuración de SSL** en el panel de contenido.
    Seleccione **Requerir SSL** y, a continuación, en el panel **Acciones**, haga clic en **Aplicar**.
    De forma opcional, en el panel **Configuración de SSL**, puede requerir que los usuarios que se conecten al sitio web de Windows PowerShell Web Access tengan certificados de cliente. Los certificados de cliente ayudan a comprobar la identidad de un usuario del dispositivo cliente.
    Para más información sobre el modo en que se puede incrementar la seguridad de Windows PowerShell Web Access al requerir certificados de cliente, consulte [Reglas de autorización y características de seguridad de Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md) en esta guía.

11. Abra una sesión del explorador en un dispositivo cliente. Para más información sobre los dispositivos y exploradores admitidos, consulte [Compatibilidad con exploradores y dispositivos cliente](#browser-and-client-device-support) en este tema.

12. Abra el nuevo sitio web de Windows PowerShell Web Access, **https://\<*nombre-servidor-puerta-enlace*\>/pswa**.

    El explorador debe mostrar la página de inicio de sesión de la consola de Windows PowerShell Web Access.

    > **![Nota](images/note.jpeg) Nota**
    >
    > No podrá iniciar sesión hasta que se haya concedido a los usuarios acceso al sitio web mediante la adición de reglas de autorización.
    > Para más información, vea [Configurar una regla de autorización restrictiva](#configure-a-restrictive-authorization-rule) en este tema y [Reglas de autorización y características de seguridad de Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. En una sesión de Windows PowerShell abierta con derechos de usuario elevados (Ejecutar como administrador), ejecute el siguiente script, en el que *application_pool_name* representa el nombre del grupo de aplicaciones creado en el paso 3, para conceder al grupo de aplicaciones derechos de acceso en el archivo de autorización.

    ```
    $applicationPoolName = "<application_pool_name>"
    $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
    c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
    ```

    Para ver los derechos de acceso existentes en el archivo de autorización, ejecute el siguiente comando:

    ```
    c:\windows\system32\icacls.exe $authorizationFile
    ```

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>Para usar el Administrador de IIS para configurar la puerta de enlace como sitio web raíz con un certificado de prueba

1. Abra la consola del Administrador de IIS mediante uno de los siguientes procedimientos.

   - En el escritorio de Windows, haga clic en **Administrador del servidor** en la barra de tareas de Windows para iniciar el Administrador del servidor. En el menú **Herramientas** del Administrador del servidor, haga clic en **Administrador de Internet Information Services (IIS)**.

   - En la pantalla **Inicio** de Windows, escriba cualquier parte del nombre **Administrador de Internet Information Services (IIS)**. Haga clic en el acceso directo cuando se muestre en los resultados de **Aplicaciones**.

1. En el panel del árbol del Administrador de IIS, expanda el nodo del servidor en el que está instalado Windows PowerShell Web Access hasta que aparezca la carpeta **Sitios**. Seleccione la carpeta **Sitios**.

1. En el panel **Acciones**, haga clic en **Agregar sitio web**.

1. Escriba un nombre para el sitio web, como **Windows PowerShell Web Access**.

1. Se creará automáticamente un grupo de aplicaciones para el nuevo sitio web. Para usar un grupo de aplicaciones diferente, haga clic en **Seleccionar** para seleccionar un grupo de aplicaciones a fin de asociarlo con el nuevo sitio web. Seleccione el grupo de aplicaciones alternativo en el cuadro de diálogo **Seleccionar grupo de aplicaciones** y, después, haga clic en **Aceptar**.

1. En el cuadro de texto **Ruta de acceso física**, vaya a %*windir*%/Web/PowerShellWebAccess/wwwroot.

1. En el campo **Tipo** del área **Enlace**, seleccione **https**.

1. Asigne al sitio web un número de puerto que no esté en uso por otro sitio o aplicación. Para encontrar puertos abiertos, puede ejecutar el comando **netstat** en una ventana del símbolo del sistema. El número de puerto predeterminado es 443.

   Cambie el puerto predeterminado si otro sitio web ya está usando el 443 o por algún otro motivo de seguridad. Si otro sitio web que se ejecuta en el servidor de puerta de enlace está usando el puerto seleccionado, se mostrará una advertencia cuando haga clic en **Aceptar** en el cuadro de diálogo **Agregar sitio web**. Debe usar un puerto que no esté en uso para ejecutar Windows PowerShell Web Access.

1. De forma opcional, si es necesario en su organización, especifique un nombre de host que tenga sentido para la organización y los usuarios, como **www.contoso.com**. Haga clic en **Aceptar**.

1. En un entorno de producción más seguro, se recomienda encarecidamente proporcionar un certificado válido firmado por una CA. Debe proporcionar un certificado SSL, porque los usuarios solo se pueden conectar a Windows PowerShell Web Access a través de un sitio web HTTPS. Vea [Para configurar un certificado SSL en el Administrador de IIS](#to-configure-an-ssl-certificate-in-iis-Manager) en este tema para más información sobre cómo obtener un certificado.

1. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Agregar sitio web**.

1. En una sesión de Windows PowerShell abierta con derechos de usuario elevados (Ejecutar como administrador), ejecute el siguiente script, en el que _application_pool_name_ representa el nombre del grupo de aplicaciones creado en el paso 4, para conceder al grupo de aplicaciones derechos de acceso en el archivo de autorización.

    ```    
    $applicationPoolName = "<application_pool_name>"
    $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
    c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
    ```

    Para ver los derechos de acceso existentes en el archivo de autorización, ejecute el siguiente comando:

    ```
    c:\windows\system32\icacls.exe $authorizationFile
    ```

1. Con el nuevo sitio web seleccionado en el panel del árbol del Administrador de IIS, haga clic en **Inicio** en el panel **Acciones** para iniciar el sitio web.

1. Abra una sesión del explorador en un dispositivo cliente. Para más información sobre los dispositivos y exploradores admitidos, consulte [Compatibilidad con exploradores y dispositivos cliente](#browser-and-client-device-support) en este documento.

1. Abra el nuevo sitio web de Windows PowerShell Web Access.

    Como el sitio web raíz apunta a la carpeta de Windows PowerShell Web Access, el explorador debería mostrar la página de inicio de sesión de Windows PowerShell Web Access cuando abra **https://\<*nombre-servidor-puerta-enlace*\>**. No será necesario que agregue **/pswa** a la dirección URL.

    > **![Nota](images/note.jpeg) Nota**
    >
    > No podrá iniciar sesión hasta que se haya concedido a los usuarios acceso al sitio web mediante la adición de reglas de autorización.
    > Para más información, vea [Configurar una regla de autorización restrictiva](#configure-a-restrictive-authorization-rule) en este tema y [Reglas de autorización y características de seguridad de Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configuring-a-restrictive-authorization-rule"></a>Configuración de una regla de autorización restrictiva

Una vez instalado Windows PowerShell Web Access y configurada la puerta de enlace, los usuarios podrán abrir la página de inicio de sesión en un explorador, pero no podrán iniciar sesión hasta que el administrador de Windows PowerShell Web Access les conceda acceso de manera explícita. El control de acceso de Windows PowerShell Web Access se administra mediante el conjunto de cmdlets de Windows PowerShell descrito en la siguiente tabla. No existe una GUI comparable para agregar o administrar reglas de autorización. Para obtener más información sobre los cmdlets de Windows PowerShell Web Access, consulte los temas de referencia de cmdlet, [Windows PowerShell Web Access Cmdlets](cmdlets/web-access-cmdlets.md) (Cmdlets de Windows PowerShell Web Access).

Para obtener más información sobre la seguridad y las reglas de autorización de Windows PowerShell Web Access, consulte [Reglas de autorización y características de seguridad de Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="adding-a-restrictive-authorization-rule"></a>Adición de una regla de autorización restrictiva

1. Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell con derechos de usuario elevados.

   - En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell**, en la barra de tareas y, luego,en **Ejecutar como administrador**.

   - En la pantalla **Inicio** de Windows, haga clic con el botón derecho en **Windows PowerShell** y, luego, en **Ejecutar como administrador**.

1. ![Nota de seguridad](images/SecurityNote.jpeg) Paso opcional para restringir el acceso de usuario con el uso de configuraciones de sesión:

   Compruebe que las configuraciones de sesión que quiere usar en las reglas ya existen. Si aún no se han creado, use las instrucciones para crear configuraciones de sesión proporcionadas en [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Escriba lo siguiente y, después, presione **Entrar**.

   Add-PswaAuthorizationRule -UserName <dominio\usuario | equipo\usuario> -ComputerName <nombre_equipo> -ConfigurationName <nombre_configuración_sesión>

   Esta regla de autorización concede a un usuario específico acceso a un equipo de la red al que tiene acceso normalmente, con acceso a una configuración de sesión determinada en el ámbito de las necesidades de cmdlet y scripting típicas del usuario.

   En el siguiente ejemplo, se concede acceso a un usuario llamado `JSmith` en el dominio `Contoso` para administrar el equipo `Contoso_214` y usar una configuración de sesión llamada `NewAdminsOnly`.

   Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

1. Compruebe que la regla se haya creado mediante la ejecución del cmdlet `Get-PswaAuthorizationRule` o `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`.

   Por ejemplo, `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

   Después de configurar una regla de autorización, está listo para que los usuarios autorizados inicien sesión en la consola basada en web y empiecen a usar Windows PowerShell Web Access.

## <a name="configure-a-genuine-certificate"></a>Configurar un certificado original

Para un entorno de producción seguro, se recomienda usar un certificado SSL válido firmado por una entidad de certificación (CA). En el procedimiento descrito en esta sección se explica cómo obtener y aplicar un certificado SSL válido de una CA.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>Para configurar un certificado SSL en el Administrador de IIS

1. En el panel del árbol del Administrador de IIS, seleccione el servidor en el que está instalado Windows PowerShell Web Access.

1. En el panel de contenido, haga doble clic en **Certificados de servidor**.

1. En el panel **Acciones**, realice una de las acciones siguientes. Para obtener más información sobre la configuración de certificados de servidor en IIS, consulte [Configurar certificados de servidor en IIS 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).

   - Haga clic en **Importar** para importar un certificado válido existente desde una ubicación de la red.

   - Haga clic en **Crear una solicitud de certificado** para solicitar un certificado de una entidad de certificación como [VeriSign](http://www.verisign.com/), [Thawte](https://www.thawte.com/) o [GeoTrust](https://www.geotrust.com/). El nombre común del certificado debe coincidir con el encabezado host de la solicitud.

   Por ejemplo, si el explorador del cliente solicita http://www.contoso.com/, el nombre común también deberá ser http://www.contoso.com/. Esta es la opción más segura y recomendada para proporcionar la puerta de enlace de Windows PowerShell Web Access con un certificado.

   - Haga clic en **Crear un certificado autofirmado** para crear un certificado para usarlo inmediatamente y, más tarde, hágalo firmar por una CA, si lo desea. Especifique un nombre descriptivo para el certificado autofirmado, como **Windows PowerShell Web Access**. Esta opción no se considera segura y solo se recomienda para un entorno de prueba privado.

1. Una vez creado u obtenido el certificado, seleccione el sitio web al que se aplicará (por ejemplo, **Sitio web predeterminado**) en el panel del árbol del Administrador de IIS y, a continuación, haga clic en **Enlaces** en el panel **Acciones**.

1. En el cuadro de diálogo **Agregar enlace de sitio**, agregue un enlace **https** para el sitio, si aún no se muestra ninguno. Si no usa un certificado autofirmado, especifique el nombre de host del paso 3 de este procedimiento. Si usa un certificado autofirmado, este paso no es necesario.

1. Seleccione el certificado obtenido o creado en el paso 3 de este procedimiento y, después, haga clic en **Aceptar**.

## <a name="using-the-web-based-windows-powershell-console"></a>Uso de la consola de Windows PowerShell basada en web

Una vez instalado Windows PowerShell Web Access y configurada la puerta de enlace como se describe en este tema, la consola de Windows PowerShell basada en web estará lista para usarse. Para obtener más información sobre la introducción a la consola basada en web, consulte [Uso de la consola de Windows PowerShell basada en web](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Véase también

[Documentación de Internet Information Services (IIS) 7.0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753433(v=ws.10))

[Ayuda del Administrador de IIS 7.0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732664(v=ws.11))

[Configurar la seguridad de Servidor web (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731278(v=ws.10))

[Recursos de implementación de IPsec](/previous-versions/windows/it-pro/windows-server-2003/cc776369(v=ws.10))