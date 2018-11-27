---
ms.date: 06/27/2017
keywords: powershell, cmdlet
title: Reglas de autorización y características de seguridad de Windows PowerShell Web Access
ms.openlocfilehash: 95c61d3a0431cda9dee738d1c9f5ec843c1209f3
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52321091"
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Reglas de autorización y características de seguridad de Windows PowerShell Web Access

Actualizado: 24 de junio de 2013

Se aplica a: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell Web Access en Windows Server 2012 R2 y Windows Server 2012 tienen un modelo de seguridad restrictiva. Los usuarios tienen que tener el acceso concedido explícitamente antes de iniciar sesión en la puerta de enlace de Windows PowerShell ISE y usar la consola basada en web de Windows PowerShell.

## <a name="configuring-authorization-rules-and-site-security"></a>Configurar las reglas de autorización y la seguridad del sitio

Una vez instalado Windows PowerShell Web Access y configurada la puerta de enlace, los usuarios podrán abrir la página de inicio de sesión en un explorador, pero no podrán iniciar sesión hasta que el administrador de Windows PowerShell Web Access les conceda acceso de manera explícita. El control de acceso de Windows PowerShell Web Access se administra mediante el conjunto de cmdlets de Windows PowerShell descrito en la siguiente tabla. No existe una GUI comparable para agregar o administrar reglas de autorización.
Vea [Windows PowerShell Web Access Cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps) (Cmdlets de Windows PowerShell Web Access).

Los administradores pueden definir entre `{0-n}` reglas de autenticación para Windows PowerShell Web Access. La seguridad predeterminada es restrictiva más que permisiva; si no se define ninguna regla de autenticación, ningún usuario tendrá acceso a ningún sitio.

[Add-PswaAuthorizationRule](/powershell/module/powershellwebaccess/add-pswaauthorizationrule?view=winserver2012r2-ps) y [Test-PswaAuthorizationRule](/powershell/module/powershellwebaccess/test-pswaauthorizationrule?view=winserver2012r2-ps) de Windows Server 2012 R2 incluyen un parámetro de credenciales que le permite agregar y probar reglas de autorización de Windows PowerShell Web Access desde un equipo remoto o desde una sesión activa de Windows PowerShell Web Access. Como ocurre con otros cmdlets de Windows PowerShell que tienen un parámetro de credenciales, puede especificar un objeto PSCredential como valor del parámetro. Para crear un objeto PSCredential que contenga las credenciales que quiere pasar a un equipo remoto, ejecute el cmdlet [Get-Credential](/powershell/module/microsoft.powershell.security/Get-Credential).

Las reglas de autenticación de Windows PowerShell Web Access son reglas de la lista blanca. Cada regla es una definición de una conexión permitida entre usuarios, equipos de destino y [configuraciones de sesión](/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-5.1) de Windows PowerShell determinadas (también denominadas puntos de conexión o _espacios de ejecución_) en equipos de destino especificados.
Para ver una explicación sobre los **espacios de ejecución**, vea [Uso inicial de los espacios de ejecución de PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)

> [!IMPORTANT]
> Un usuario solo necesita que una regla sea verdadera para obtener el acceso. Si a un usuario se le concede acceso a un equipo con acceso de lenguaje completo o acceso únicamente a los cmdlets de administración remota de Windows PowerShell, desde la consola basada en web, el usuario puede saltar a otros equipos conectados al primer equipo de destino e iniciar sesión en ellos. El modo más seguro de configurar Windows PowerShell Web Access consiste en permitir a los usuarios acceder únicamente a configuraciones de sesión restringidas que les permitan llevar a cabo tareas específicas que, por lo general, deben realizar de forma remota.

Los cmdlets a los que se hace referencia en [Cmdlets de Windows PowerShell Web Access](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps) permiten crear un conjunto de reglas de acceso que se usan para autorizar a un usuario en la puerta de enlace de Windows PowerShell Web Access. Las reglas difieren de las listas de control de acceso (ACL) en el equipo de destino y proporcionan un nivel de seguridad adicional para el acceso web. En la siguiente sección, se proporcionan más detalles sobre la seguridad.

Si los usuarios no pueden pasar alguno de los niveles de seguridad anteriores, recibirán un mensaje de "acceso denegado" genérico en la ventana del explorador. Si bien los detalles de seguridad se registran en el servidor de puerta de enlace, los usuarios finales no verán ninguna información acerca de cuántos niveles de seguridad pasaron ni en qué nivel se produjo el error de autenticación o de inicio de sesión.

Para más información sobre cómo configurar las reglas de autorización, vea [Configuración de reglas de autorización](#configuring-authorization-rules-and-site-security) en este tema.

### <a name="security"></a>Seguridad

El modelo de seguridad de Windows PowerShell Web Access tiene cuatro niveles entre un usuario final de la consola basada en web y un equipo de destino. Los administradores de Windows PowerShell Web Access pueden agregar niveles de seguridad mediante configuración adicional en la consola del Administrador de IIS. Para más información sobre la protección de sitios web en la consola del Administrador de IIS, consulte [Configurar la seguridad de los servidores web (IIS 7)](https://technet.microsoft.com/library/cc731278).

Para más información sobre los procedimientos recomendados de IIS y la prevención de ataques por denegación de servicio, consulte [Best Practices for Preventing DoS/Denial of Service Attacks](https://technet.microsoft.com/library/cc750213) (Procedimientos recomendados para impedir ataques por denegación de servicio (DoS)).
Los administradores también pueden comprar e instalar software de autenticación de venta minorista adicional.

En la siguiente tabla, se describen los cuatro niveles de seguridad entre los usuarios finales y los equipos de destino.

|Nivel|Nivel|
|-|-|
|1|[características de seguridad de servidor web de IIS](#iis-web-server-security-features)|
|2|[autenticación de puerta de enlace basada en formularios de Windows PowerShell Web Access](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[reglas de autorización de Windows PowerShell Web Access](#windows-powershell-web-access-authorization-rules)|
|4|[reglas de autorización y autenticación de destino](#target-authentication-and-authorization-rules)|

En los siguientes encabezados encontrará información detallada sobre cada nivel:

#### <a name="iis-web-server-security-features"></a>Características de seguridad de Servidor web de IIS

Los usuarios de Windows PowerShell Web Access siempre deben proporcionar un nombre de usuario y una contraseña para autenticar sus cuentas en la puerta de enlace. Pero los administradores de Windows PowerShell Web Access también pueden activar o desactivar la autenticación de certificados de cliente opcional (consulte [Instalación y uso de Windows PowerShell Web Access](install-and-use-windows-powershell-web-access.md) para habilitar un certificado de prueba y luego configurar un certificado original).

La característica de certificado de cliente opcional, que forma parte de la configuración de Servidor web (IIS), requiere que los usuarios finales tengan un certificado de cliente válido, además de sus nombres de usuario y contraseñas. Cuando el nivel de certificado de cliente está habilitado, la página de inicio de sesión de Windows PowerShell Web Access solicita a los usuarios que proporcionen certificados válidos antes de evaluar sus credenciales de inicio de sesión. La autenticación de certificados de cliente comprueba automáticamente si existe un certificado de cliente. Si no se encuentra un certificado válido, Windows PowerShell Web Access lo notifica a los usuarios para que lo proporcionen. En el caso de que sí se encuentre uno, Windows PowerShell Web Access abre la página de inicio de sesión para que los usuarios proporcionen sus nombres de usuario y contraseñas.

A continuación se muestra un ejemplo de una configuración de seguridad adicional proporcionada por Servidor web de IIS. Para más información sobre otras características de seguridad de IIS, vea [Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278) (Configurar la seguridad de los servidores web, IIS 7).

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Autenticación de puerta de enlace basada en formularios de Windows PowerShell Web Access

La página de inicio de sesión de Windows PowerShell Web Access requiere un conjunto de credenciales (nombre de usuario y contraseña) y ofrece a los usuarios la opción de proporcionar distintas credenciales para el equipo de destino.
Si el usuario no proporciona credenciales alternativas, el nombre de usuario y la contraseña principales usados para la conexión con la puerta de enlace también se usarán para la conexión con el equipo de destino.

Las credenciales requeridas se autentican en la puerta de enlace de Windows PowerShell Web Access. Estas credenciales deben ser cuentas de usuario válidas en el servidor de puerta de enlace de Windows PowerShell Web Access local o en Active Directory.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Reglas de autorización de Windows PowerShell Web Access

Una vez autenticado un usuario en la puerta de enlace, Windows PowerShell Web Access comprueba las reglas de autorización para averiguar si el usuario tiene acceso al equipo de destino solicitado. Una vez completada la autorización correctamente, las credenciales del usuario se pasan al equipo de destino.

Estas reglas solo se evalúan una vez que la puerta de enlace ha autenticado al usuario y antes de que el usuario pueda autenticarse en el equipo de destino.

#### <a name="target-authentication-and-authorization-rules"></a>Reglas de autorización y autenticación de destino

El nivel de seguridad final de Windows PowerShell Web Access es la configuración de seguridad propia del equipo de destino. Los usuarios deben tener configurados los derechos de acceso correspondientes en el equipo de destino, y en la reglas de autorización de Windows PowerShell Web Access, para ejecutar una consola de Windows PowerShell basada en web que afecte a un equipo de destino mediante Windows PowerShell Web Access.

Este nivel ofrece los mismos mecanismos de seguridad que evaluarían los intentos de conexión si los usuarios intentaran crear una sesión remota de Windows PowerShell a un equipo de destino desde dentro de Windows PowerShell mediante la ejecución de los cmdlets [Enter-PSSession](/powershell/module/microsoft.powershell.core/Enter-PSSession) o [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession).

De manera predeterminada, Windows PowerShell Web Access usa el nombre de usuario y la contraseña principales para la autenticación, tanto en la puerta de enlace como en el equipo de destino. La página de inicio de sesión basada en web, en una sección titulada **Configuración de conexión opcional**, ofrece a los usuarios la opción de proporcionar distintas credenciales para el equipo de destino, en caso de que sean necesarias. Si el usuario no proporciona credenciales alternativas, el nombre de usuario y la contraseña principales usados para la conexión con la puerta de enlace también se usarán para la conexión con el equipo de destino.

Las reglas de autorización se pueden usar para conceder a los usuarios acceso a una configuración de sesión determinada. Puede crear configuraciones de sesión o _espacios de ejecución restringidos_ para Windows PowerShell Web Access y permitir a usuarios específicos conectarse únicamente a configuraciones de sesión determinadas cuando inician sesión en Windows PowerShell Web Access. Puede usar listas de control de acceso (ACL) para determinar qué usuarios tendrán acceso a extremos específicos y para restringir aún más el acceso al extremo para un conjunto específico de usuarios mediante las reglas de autorización descritas en esta sección. Para más información sobre los espacios de ejecución restringidos, vea [Creating a constrained runspace](https://msdn.microsoft.com/library/dn614668) (Crear un espacio de ejecución restringido).

### <a name="configuring-authorization-rules"></a>Configuración de reglas de autorización

Es probable que los administradores deseen usar para los usuarios de Windows PowerShell Web Access la misma regla de autorización que ya está definida en su entorno para la administración remota de Windows PowerShell. El primer procedimiento de esta sección describe cómo agregar una regla de autorización segura que conceda acceso a un usuario que inicia sesión para administrar un equipo dentro de una sola configuración de sesión. El segundo procedimiento describe cómo quitar una regla de autorización que ya no se necesita.

Si planea usar configuraciones de sesión personalizadas para permitir a usuarios específicos trabajar solo dentro de espacios de ejecución restringidos en Windows PowerShell Web Access, cree sus propias configuraciones de sesión personalizadas antes de agregar reglas de autorización que hagan referencia a ellas. No se pueden usar los cmdlets de Windows PowerShell Web Access para crear configuraciones de sesión personalizadas. Para más información sobre cómo crear configuraciones de sesión personalizadas, vea [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

Los cmdlets de Windows PowerShell Web Access admiten un carácter comodín: un asterisco (\*). No se admiten los caracteres comodín dentro de las cadenas. Use un solo asterisco por propiedad (usuarios, equipos o configuraciones de sesión).

> [!NOTE]
> Para conocer otros modos de usar las reglas de autorización para conceder acceso a los usuarios y ayudar a proteger el entorno de Windows PowerShell Web Access, vea [Otros ejemplos de escenarios de reglas de autorización](#other-authorization-rule-scenario-examples) en este tema.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Para agregar una regla de autorización restrictiva

1. Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell con derechos de usuario elevados.

   - En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell**, en la barra de tareas y, luego,en **Ejecutar como administrador**.

   - En la pantalla **Inicio** de Windows, haga clic con el botón derecho en **Windows PowerShell** y, luego, en **Ejecutar como administrador**.

2. **Paso opcional** Para restringir el acceso de usuario mediante configuraciones de sesión:

   Compruebe que las configuraciones de sesión que quiere usar ya existen en las reglas.

   Si aún no se han creado, use las instrucciones para crear configuraciones de sesión proporcionadas en [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

3. Esta regla de autorización concede a un usuario específico acceso a un equipo de la red al que tiene acceso normalmente, con acceso a una configuración de sesión determinada en el ámbito de las necesidades de cmdlet y scripting típicas del usuario. Escriba lo siguiente y, después, presione **Entrar**.

   ```
   Add-PswaAuthorizationRule -UserName <domain\user | computer\user> `
      -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
   ```

   - En el siguiente ejemplo, se concede acceso a un usuario llamado _JSmith_ en el dominio _Contoso_ para administrar el equipo _Contoso_214_ y usar una configuración de sesión llamada _NewAdminsOnly_.

   ```powershell
   Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' `
      -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
   ```

4. Compruebe que la regla se haya creado mediante la ejecución del cmdlet **Get-PswaAuthorizationRule** o `Test-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName** <computer_name>`.
   Por ejemplo, `Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214`.

#### <a name="to-remove-an-authorization-rule"></a>Para quitar una regla de autorización

1. Si aún no tiene abierta ninguna sesión de Windows PowerShell, vea el paso 1 de [Agregar una regla de autorización restrictiva](#to-add-a-restrictive-authorization-rule) de esta sección.

2. Escriba lo siguiente y, a continuación, presione **Entrar**, donde *identificador de regla* representa el número de identificación único de la regla que desea quitar.

   ```
   Remove-PswaAuthorizationRule -ID <rule ID>
   ```

   Como alternativa, si no conoces el número de identificación, pero sabes el nombre descriptivo de la regla que quieres quitar, puedes conseguir el nombre de la regla y canalizarlo en el cmdlet `Remove-PswaAuthorizationRule` para eliminar la regla, como se muestra en el ejemplo siguiente:

   ```
   Get-PswaAuthorizationRule `
      -RuleName <rule-name> | Remove-PswaAuthorizationRule
   ```

> [!NOTE]
> No se le pedirá confirmación para eliminar la regla de autorización especificada; esta se eliminará al presionar **Entrar**. Asegúrese de que realmente desea quitar la regla antes de ejecutar el cmdlet `Remove-PswaAuthorizationRule`.

#### <a name="other-authorization-rule-scenario-examples"></a>Ejemplos de otros escenarios de reglas de autorización

Cada sesión de Windows PowerShell usa una configuración de sesión. Si esta no se especifica para una sesión, Windows PowerShell usa la configuración de sesión de Windows PowerShell integrada predeterminada, que se llama Microsoft.PowerShell. La configuración de sesión predeterminada incluye todos los cmdlets que se encuentran disponibles en un equipo. Los administradores pueden restringir el acceso a todos los equipos mediante la definición de una configuración de sesión con un espacio de ejecución restringido (una variedad limitada de cmdlets y tareas que los usuarios finales pueden realizar). Un usuario al que se le concede acceso a un equipo con acceso de lenguaje completo o acceso únicamente a los cmdlets de administración remota de Windows PowerShell puede conectarse a otros equipos conectados al primer equipo. La definición de un espacio de ejecución restringido puede impedir que los usuarios obtengan acceso a otros equipos desde su espacio de ejecución de Windows PowerShell permitido y mejora la seguridad del entorno de Windows PowerShell Web Access. La configuración de sesión se puede distribuir (mediante la directiva de grupo) a todos los equipos que los administradores desean que sean accesibles mediante Windows PowerShell Web Access. Para más información sobre las configuraciones de sesión, vea [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) (Acerca de las configuraciones de sesión). A continuación, se proporcionan algunos ejemplos de este escenario.

- Un administrador crea un punto de conexión, llamado **PswaEndpoint**, con un espacio de ejecución restringido. Después, crea una regla, `*,*,PswaEndpoint`, y distribuye el punto de conexión a otros equipos. La regla permite a todos los usuarios obtener acceso a todos los equipos con el punto de conexión **PswaEndpoint**.
  Si esta es la única regla de autorización definida en el conjunto de reglas, no se podrá obtener acceso a los equipos que no tengan ese extremo.

- Un administrador ha creado un punto de conexión con un espacio de ejecución restringido, llamado **PswaEndpoint**, y desea restringir el acceso a usuarios específicos. El administrador crea un grupo de usuarios llamado **Level1Support** y define la siguiente regla: **Level1Support,\*,PswaEndpoint**. La regla concede a cualquier usuario del grupo **Level1Support** acceso a todos los equipos con la configuración **PswaEndpoint**. De modo semejante, se puede restringir el acceso a un conjunto específico de equipos.

- Algunos administradores proporcionan a determinados usuarios más acceso que a otros. Por ejemplo, un administrador crea dos grupos de usuarios, **Admins** y **BasicSupport**. También crea un punto de conexión con un espacio de ejecución restringido llamado **PswaEndpoint** y define las dos reglas siguientes: **Admins,\*,\*** y **BasicSupport,\*,PswaEndpoint**. La primera regla proporciona a todos los usuarios del grupo **Admin** acceso a todos los equipos y la segunda regla proporciona a todos los usuarios del grupo **BasicSupport** acceso únicamente a los equipos con **PswaEndpoint**.

- Un administrador ha configurado un entorno de prueba privado y desea conceder a todos los usuarios de red autorizados acceso a todos los equipos de la red a los que tienen acceso normalmente, con acceso a todas las configuraciones de sesión a las que tienen acceso normalmente. Como se trata de un entorno de prueba privado, el administrador crea una regla de autorización que no es segura. - Ejecuta el cmdlet `Add-PswaAuthorizationRule * * *`, que usa el carácter comodín **\*** para representar todos los usuarios, todos los equipos y todas las configuraciones. - Esta regla equivale a lo siguiente: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  > [!NOTE]
  > Esta regla no se recomienda en un entorno seguro, ya que omite el nivel de seguridad de reglas de autorización proporcionado por Windows PowerShell Web Access.

- Un administrador debe permitir a los usuarios conectarse a los equipos de destino en un entorno que incluye tanto grupos de trabajo como dominios, en el que los equipos de los grupos de trabajo ocasionalmente se usan para conectar con equipos de destino de los dominios, y los equipos de los dominios ocasionalmente se usan para conectar con equipos de destino de los grupos de trabajo. El administrador tiene un servidor de puerta de enlace, llamado *PswaServer*, en un grupo de trabajo, y el equipo de destino *srv1.contoso.com* se encuentra en un dominio. El usuario *Chris* es un usuario local autorizado tanto en el servidor de puerta de enlace del grupo de trabajo como en el equipo de destino. Su nombre de usuario en el servidor del grupo de trabajo es *chrisLocal* y su nombre de usuario en el equipo de destino es *contoso\\chris*. Para autorizar el acceso de Chris a srv1.contoso.com, el administrador agrega la regla siguiente.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal `
   -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

En el ejemplo de regla anterior, se autentica a Chris en el servidor de puerta de enlace y, a continuación, se autoriza su acceso a *srv1*. En la página de inicio de sesión, Chris debe proporcionar un segundo conjunto de credenciales en el área **Configuración de conexión opcional** (*contoso\\chris*). El servidor de puerta de enlace usa el conjunto de credenciales adicional para autenticarlo en el equipo de destino, *srv1.contoso.com*.

En el escenario anterior, Windows PowerShell Web Access solo establecerá una conexión correcta con el equipo de destino una vez que se hayan completado correctamente los siguientes procesos (y estos se hayan permitido mediante una regla de autorización como mínimo).

1. Autenticación en el servidor de puerta de enlace del grupo de trabajo mediante la adición de un nombre de usuario, con el formato *nombre_servidor*\\*nombre_usuario* a la regla de autorización.

2. Autenticación en el equipo cliente mediante credenciales alternativas proporcionadas en la página de inicio de sesión, en el área **Configuración de conexión opcional**

   > [!NOTE]
   > Si los equipos de destino y de la puerta de enlace se encuentran en grupos de trabajo o dominios diferentes, se debe establecer una relación de confianza entre los dos equipos del grupo de trabajo, entre los dos dominios o entre el grupo de trabajo y el dominio. Esta relación no se puede configurar mediante los cmdlets de reglas de autorización de Windows PowerShell Web Access. Las reglas de autorización no definen una relación de confianza entre equipos; solo pueden autorizar a los usuarios para que se conecten a equipos de destino y configuraciones de sesión específicos. Para más información sobre el modo de configurar una relación de confianza entre dominios diferentes, consulte [Creating Domain and Forest Trusts](https://technet.microsoft.com/library/cc794775.aspx) (Creación de confianzas entre dominios y bosques).
   > Para obtener más información sobre el modo de agregar equipos del grupo de trabajo a una lista de hosts de confianza, consulta el tema [Administración remota con el Administrador del servidor](https://technet.microsoft.com/library/dd759202.aspx).

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Uso de un solo conjunto de reglas de autorización para varios sitios

Las reglas de autorización se almacenan en un archivo XML. De forma predeterminada, el nombre de la ruta de acceso del archivo XML es `%windir%\Web\PowershellWebAccess\data\AuthorizationRules.xml`.

La ruta de acceso al archivo XML de reglas de autorización se almacena en el archivo **powwa.config**, que se encuentra en `%windir%\Web\PowershellWebAccess\data`. El administrador tiene flexibilidad para cambiar la referencia a la ruta de acceso predeterminada en **powwa.config** para satisfacer preferencias o cumplir requisitos. Al permitir al administrador cambiar la ubicación del archivo, se permite que varias puertas de enlace de Windows PowerShell Web Access usen las mismas reglas de autorización, en el caso de que se desee este tipo de configuración.

## <a name="session-management"></a>Administración de sesiones

De forma predeterminada, Windows PowerShell Web Access limita a los usuarios a tres sesiones al mismo tiempo. Puede editar el archivo **web.config** de la aplicación web en el Administrador de IIS para permitir un número diferente de sesiones por usuario. El archivo **web.config** es `$Env:Windir\Web\PowerShellWebAccess\wwwroot\Web.config`.

De forma predeterminada, el Servidor web de IIS está configurado para reiniciar el grupo de aplicaciones si se edita alguna configuración. Por ejemplo, el grupo de aplicaciones se reinicia si se realizan cambios en el archivo **web.config**. >Como **Windows PowerShell Web Access** usa estados de sesión en memoria, los usuarios que han iniciado sesiones en **Windows PowerShell Web Access** las pierden cuando el grupo de aplicaciones se reinicia.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Establecer parámetros predeterminados en la página de inicio de sesión

Si la puerta de enlace de Windows PowerShell Web Access se ejecuta en Windows Server 2012 R2, puede definir valores predeterminados para la configuración que se muestra en la página de inicio de sesión de Windows PowerShell Web Access. Puede configurar valores en el archivo **web.config** que se describe en el párrafo anterior. Los valores predeterminados para la configuración de la página de inicio de sesión se encuentran en la sección **appSettings** del archivo web.config; a continuación se muestra un ejemplo de la sección **appSettings**. Los valores válidos para muchas de estas opciones son los mismos que para los parámetros correspondientes del cmdlet [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) de Windows PowerShell.

Por ejemplo, la clave `defaultApplicationName`, como se muestra en el siguiente bloque de código, es el valor de la variable de preferencia **$PSSessionApplicationName** del equipo de destino.

```xml
  <appSettings>
      <add key="maxSessionsAllowedPerUser" value="3"/>
      <add key="defaultPortNumber" value="5985"/>
      <add key="defaultSSLPortNumber" value="5986"/>
      <add key="defaultApplicationName" value="WSMAN"/>
      <add key="defaultUseSslSelection" value="0"/>
      <add key="defaultAuthenticationType" value="0"/>
      <add key="defaultAllowRedirection" value="0"/>
      <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
  </appSettings>
```

### <a name="time-outs-and-unplanned-disconnections"></a>Tiempos de espera y desconexiones no planeadas

Tiempo de espera de las sesiones de Windows PowerShell Web Access. En Windows PowerShell Web Access cuando se ejecuta en Windows Server 2012 se muestra un mensaje de tiempo de espera agotado cuando los usuarios conectados no han realizado ninguna actividad en la sesión en 15 minutos. Si el usuario no responde dentro de los cinco minutos posteriores al envío del mensaje, la sesión del usuario se cerrará. Puede cambiar los períodos de tiempo de espera de las sesiones en la configuración del sitio web en el Administrador de IIS.

En Windows PowerShell Web Access cuando se ejecuta en Windows Server 2012 R2, se agota el tiempo de espera de las sesiones después de 20 minutos de inactividad. Si los usuarios están desconectados de sesiones en la consola basada en web debido a errores de red u otros apagados o errores no planificados, y no porque se hayan cerrado las sesiones ellas mismas, las sesiones de Windows PowerShell Web Access continúan ejecutándose, conectadas a equipos de destino, hasta que vence el período de tiempo de espera del cliente. La sesión se desconecta después de los 20 minutos predeterminados o después del período de tiempo de espera especificado por el administrador de la puerta de enlace, el que sea más corto.

Si el servidor de puerta de enlace está ejecutando Windows Server 2012 R2, Windows PowerShell Web Access permite a los usuarios volver a conectarse a las sesiones guardadas en otro momento, pero cuando errores de red, apagados no planificados u otros errores desconectan las sesiones, los usuarios no pueden ver o volver a conectarse a las sesiones guardadas hasta que haya vencido el período de tiempo de espera especificado por el administrador de la puerta de enlace.

## <a name="see-also"></a>Véase también

[Instalación y uso de Windows PowerShell Web Access](https://technet.microsoft.com/library/hh831611(v=ws.11).aspx)

[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)

[Cmdlets de Windows PowerShell Web Access](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)
