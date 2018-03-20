---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,security
title: Consideraciones de seguridad de JEA
ms.openlocfilehash: 69bbe50fb1a7580c32d657a0f084cc80c28825c7
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="jea-security-considerations"></a>Consideraciones de seguridad de JEA

> Se aplica a: Windows PowerShell 5.0

JEA le ayuda a mejorar su posición en materia de seguridad, ya que reduce el número de administradores permanentes de sus equipos.
Lo hace mediante la creación de un nuevo punto de entrada para que los usuarios administren el sistema (una configuración de sesión de PowerShell) que, además, está bien bloqueado de manera predeterminada para evitar el uso indebido.
A los usuarios que necesitan algún acceso, pero no ilimitado, al equipo para realizar tareas administrativas se les puede conceder acceso al punto de conexión de JEA.
Como JEA les permite ejecutar comandos de administrador sin tener directamente acceso de administrador, después puede quitar a dichos usuarios de grupos de seguridad con privilegios elevados, es decir, convertirlos en usuarios estándar.

En este tema, se describen el modelo de seguridad de JEA y los procedimientos recomendados con más detalle.

## <a name="run-as-account"></a>cuenta de identificación

Cada punto de conexión de JEA tiene una cuenta de "ejecución" designada, que es la cuenta en la que se realizan las acciones del usuario que se conecta.
Esta cuenta se puede configurar en el [archivo de configuración de sesión](session-configurations.md), y la cuenta que elija influye de forma significativa en la seguridad del punto de conexión.

Las **cuentas virtuales** son la forma recomendada de configurar la cuenta de ejecución.
Las cuentas virtuales son cuentas locales únicas y temporales creadas por el usuario que se conecta para usarlas durante la sesión de JEA.
Una vez finalizada la sesión, la cuenta virtual se destruirá y no se podrá volver a usar.
El usuario que se conecta no conoce las credenciales de la cuenta virtual y no puede usarla para tener acceso al sistema por otros medios, como el Escritorio remoto o un punto de conexión de PowerShell sin restricciones.

De manera predeterminada, las cuentas virtuales pertenecen al grupo de administradores locales del equipo.
Esto les otorga derechos completos para administrar todo en el sistema, pero no les otorga ningún derecho para administrar recursos de la red.
Para la autenticación con otros equipos, el contexto de usuario será el de la cuenta de equipo local, no la cuenta virtual.

Los controladores de dominio son un caso especial porque no hay ningún concepto de un grupo de administradores local.
En su lugar, las cuentas virtuales pertenecen a administradores de dominio y pueden administrar los servicios de directorio en el controlador de dominio.
La identidad de dominio se limita a utilizarse en el controlador de dominio donde se creó una instancia de la sesión JEA, y cualquier acceso a la red parecerá provenir del objeto de equipo del controlador de dominio.

En ambos casos, también puede definir de forma explícita los grupos de seguridad a los que debe pertenecer la cuenta virtual.
Este es un procedimiento recomendado cuando la tarea que está realizando puede llevarse a cabo sin privilegios de administrador local o de dominio.
Si ya tiene un grupo de seguridad definido para los administradores, simplemente puede conceder la pertenencia a la cuenta virtual a ese grupo para otorgarle los permisos que necesita.
La pertenencia al grupo de cuenta virtual se limita a los grupos de seguridad locales en servidores miembro y estaciones de trabajo, pero en un controlador de dominio solo pueden ser miembros de grupos de seguridad de dominio.
Después de especificar uno o varios grupos de seguridad para que la cuenta virtual pertenezca a ellos, dejará de pertenecer a los grupos predeterminados (administrador local o administrador de dominio).

En la tabla siguiente, se resumen las posibles opciones de configuración y los permisos resultantes de las cuentas virtuales.

Tipo de equipo                | Configuración del grupo de cuenta virtual | Contexto de usuario local                                      | Contexto de usuario de red
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Controlador de dominio            | Valor predeterminado                             | Usuario de dominio, miembro de "*DOMINIO*\Administradores de domino"         | Cuenta de equipo
Controlador de dominio            | Grupos de dominio A y B               | Usuario de dominio, miembro de "*DOMINIO*\A", "*DOMINIO*\B"       | Cuenta de equipo
Servidor miembro o estación de trabajo | Valor predeterminado                             | Usuario local, miembro de "*BUILTIN*\Administradores"        | Cuenta de equipo
Servidor miembro o estación de trabajo | Grupos locales C y D                | Usuario local, miembro de "*EQUIPO*\C" y "*EQUIPO*\D" | Cuenta de equipo

Al examinar los eventos de auditoría de seguridad y los registros de eventos de la aplicación, verá que cada sesión de usuario de JEA tiene una cuenta virtual única.
Esto le ayuda a realizar un seguimiento de las acciones del usuario en un punto de conexión de JEA hasta el usuario original que ha ejecutado el comando.
Los nombres de cuenta virtual siguen el formato "Usuarios virtuales WinRM\\WinRM\_CUENTAVIRTUAL\_*NÚMEROCUENTA*\_*DOMINIO*\_*NombreCuentaSAM*". Por ejemplo, si el usuario "Alice" del dominio "Contoso" reinicia un servicio en un punto de conexión de JEA, el nombre de usuario asociado con todos los eventos del administrador de control de servicio sería "Usuarios virtuales WinRM\\WinRM\_CUENTAVIRTUAL\_1\_contoso\_alice".


Las **cuentas de servicio administradas de grupo (gMSA)** son útiles cuando un servidor miembro necesita tener acceso a recursos de red en la sesión de JEA.
Un caso de uso de ejemplo es un punto de conexión de JEA que se usa para controlar el acceso a una API de REST hospedada en un equipo diferente.
Es fácil escribir funciones para realizar las invocaciones que quiera en la API de REST, pero para autenticarse en la API se necesita una identidad de red.
Mediante una cuenta de servicio administrada de grupo, el "segundo salto" es posible mientras se conserva el control sobre los equipos que pueden usar la cuenta.
Los permisos efectivos de la gMSA se definen mediante los grupos de seguridad, ya sean locales o de dominio, a los que pertenece la cuenta gMSA.

Cuando un punto de conexión de JEA se configura para usar una cuenta gMSA, parecerá que las acciones de todos los usuarios de JEA vienen de la misma cuenta de servicio administrada de grupo.
La única manera de realizar un seguimiento de las acciones hasta un usuario específico es identificar el conjunto de comandos que se ejecutan en una transcripción de la sesión de PowerShell.

Las **credenciales de paso a través** se usan cuando no especifica una cuenta de ejecución y desea que PowerShell use las credenciales del usuario que se conecta para ejecutar comandos en el servidor remoto.
Esta configuración *no* se recomienda para JEA, ya que requeriría conceder acceso directo al usuario que se conecta a grupos de administración con privilegios.
Si el usuario que se conecta ya tiene privilegios de administrador, puede evitar JEA por completo y administrar el sistema a través de otro medio sin restricciones.
Para obtener más información, consulte la sección siguiente en la que se detalla que [JEA no protege frente a administradores](#jea-does-not-protect-against-admins).

Las **cuentas de ejecución estándar** le permiten especificar cualquier cuenta de usuario en la que se ejecutará toda la sesión de PowerShell.
Se trata de una distinción importante, ya que una configuración de sesión establecida para usar una cuenta de ejecución fija (con el parámetro `-RunAsCredential`) no es compatible con JEA.
Esto significa que las definiciones de rol ya no funcionan según lo previsto, y a cada usuario autorizado para tener acceso al punto de conexión se le asignará el mismo rol.

No conviene usar el elemento RunAsCredential en un punto de conexión de JEA, ya que la dificultad de seguir las acciones hasta usuarios específicos y la falta de compatibilidad para asignar usuarios a roles es importante.

## <a name="winrm-endpoint-acl"></a>ACL de punto de conexión de WinRM

Al igual que con los puntos de conexión de comunicación remota de PowerShell normales, cada punto de conexión de JEA tiene una lista de control de acceso (ACL) independiente establecida en la configuración de WinRM que controla quién se puede autenticar con el punto de conexión de JEA.
Si no se ha configurado correctamente, es posible que los usuarios de confianza no puedan tener acceso al punto de conexión de JEA, o bien que puedan hacerlo otros usuarios que no sean de confianza.
En cambio, la ACL de WinRM no afecta a la asignación de usuarios a roles de JEA.
Esta se controla mediante el campo *RoleDefinitions* del archivo de configuración de sesión que se ha registrado en el sistema.

De manera predeterminada, al registrar un punto de conexión de JEA mediante un archivo de configuración de sesión y una o varias funcionalidades de rol, la ACL de WinRM se configurará para permitir que todos los usuarios asignados a uno o varios roles tengan acceso al punto de conexión.
Por ejemplo, una sesión de JEA configurada con los comandos siguientes concederá acceso total a *CONTOSO\JEA\_Lev1* y *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Puede auditar los permisos de usuario con el cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration).

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Para cambiar los usuarios que tienen acceso, ejecute `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` para obtener un aviso interactivo o `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` para actualizar los permisos.
Los usuarios necesitan al menos *derechos de invocación* para tener acceso al punto de conexión de JEA.

Si se les concede acceso a otros usuarios al punto de conexión de JEA pero no entran dentro de ninguno de los roles definidos en el archivo de configuración de sesión, podrán iniciar una sesión de JEA, pero solo con acceso a los cmdlets predeterminados.
Puede auditar los permisos de usuario en un punto de conexión de JEA ejecutando `Get-PSSessionCapability`.
Consulte el artículo [Auditoría y creación de informes en JEA](audit-and-report.md) para obtener más información sobre la auditoría y los comandos a los que tiene acceso un usuario en un punto de conexión de JEA.

## <a name="least-privilege-roles"></a>Roles con privilegios mínimos

Al diseñar roles de JEA, es importante recordar que la cuenta de servicio administrada de grupo o virtual que se ejecuta en segundo plano a menudo tiene acceso sin restricciones para administrar el equipo local.
Las funcionalidades de rol de JEA ayudan a restringir para qué se puede usar esa cuenta al limitar los comandos y las aplicaciones que se pueden ejecutar con ese contexto privilegiado.
Los roles diseñados de manera incorrecta pueden permitir que se ejecuten comandos peligrosos que autoricen a un usuario a salir de los límites de JEA u obtener acceso a información confidencial.

Por ejemplo, observe la siguiente entrada de funcionalidad de rol:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Esta funcionalidad de rol permite a los usuarios ejecutar cualquier cmdlet de PowerShell con el nombre "Process" desde el módulo Microsoft.PowerShell.Management.
Es posible que los usuarios necesiten tener acceso a cmdlets como `Get-Process` para comprender las aplicaciones que se ejecutan en el sistema y `Stop-Process` para eliminar cualquier aplicación bloqueada.
En cambio, esta entrada también permite `Start-Process`, que se puede usar para iniciar un programa arbitrario con permisos de administrador total.
El programa no tiene que estar instalado de forma local en el sistema, por lo que alguien ajeno podría simplemente iniciar un programa en un recurso compartido de archivos que proporcione al usuario que se conecta privilegios de administrador local, ejecute malware, etc.

Una versión más segura de esta misma funcionalidad de rol tendría el siguiente aspecto:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Evite usar caracteres comodín en las funcionalidades de rol y asegúrese de [auditar los permisos de usuario efectivos](audit-and-report.md#check-effective-rights-for-a-specific-user) con regularidad para comprender los comandos a los que tiene acceso un usuario.

## <a name="jea-does-not-protect-against-admins"></a>JEA no protege frente a administradores

Uno de los principios básicos de JEA es que permite a los usuarios que no son administradores realizar *algunas* tareas administrativas.
JEA no protege frente a aquellos que ya tengan privilegios de administrador.
Los usuarios que pertenezcan a los grupos "administradores de dominio", "administradores locales" u otros con muchos privilegios en su entorno podrán eludir las protecciones de JEA iniciando sesión en el equipo por otros medios.
Por ejemplo, pueden iniciar sesión con RDP, usar consolas remotas de MMC o conectarse a puntos de conexión de PowerShell sin restricciones.
Los administradores locales del sistema también pueden modificar las configuraciones de JEA para permitir que usuarios adicionales administren el sistema o cambien una funcionalidad de rol para ampliar el ámbito de lo que puede realizar un usuario en su sesión de JEA.
Por tanto, es importante evaluar los permisos extendidos de los usuarios de JEA para ver si hay otras formas de obtener acceso con privilegios al sistema.

Un procedimiento común es usar JEA para realizar el mantenimiento diario habitual y tener una solución de administración de acceso con privilegios "Just-In-Time" que permita que los usuarios se conviertan de forma temporal en administradores locales en situaciones de emergencia.
Esto ayuda a garantizar que los usuarios no sean administradores de forma permanente en el sistema, pero pueden obtener esos derechos si, y solo cuando, completan un flujo de trabajo que documente su uso de estos permisos.

