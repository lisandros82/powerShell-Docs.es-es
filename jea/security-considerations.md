---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Consideraciones de seguridad de JEA
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726586"
---
# <a name="jea-security-considerations"></a>Consideraciones de seguridad de JEA

JEA le ayuda a mejorar su posición en materia de seguridad, ya que reduce el número de administradores permanentes de sus equipos. En JEA se usa una configuración de sesión de PowerShell para crear un punto de entrada con el fin de que los usuarios administren el sistema. A los usuarios que necesiten acceso con privilegios elevados, pero no ilimitado, al equipo para realizar tareas administrativas se les puede conceder acceso al punto de conexión de JEA. Como JEA permite a estos usuarios ejecutar comandos de administrador sin tener acceso de administrador completo, después puede quitar a esos usuarios de los grupos de seguridad con privilegios elevados.

## <a name="run-as-account"></a>Cuenta de ejecución

Cada punto de conexión de JEA tiene una cuenta de **ejecución** designada. Es la cuenta bajo la que se ejecutan las acciones del usuario que se conecta. Esta cuenta se puede configurar en el [archivo de configuración de sesión](session-configurations.md), y la cuenta que elija influye de forma significativa en la seguridad del punto de conexión.

Las **cuentas virtuales** son la forma recomendada de configurar la cuenta de **ejecución**. Las cuentas virtuales son cuentas locales únicas y temporales creadas por el usuario que se conecta para usarlas durante la sesión de JEA. Una vez finalizada la sesión, la cuenta virtual se destruye y ya no se puede volver a usar. El usuario que se conecta desconoce las credenciales de la cuenta virtual. La cuenta virtual no se puede usar para acceder al sistema a través de otros medios como Escritorio remoto o un punto de conexión de PowerShell sin restricciones.

De manera predeterminada, las cuentas virtuales pertenecen al grupo de **administradores** locales del equipo. Esto les otorga derechos completos para administrar todo en el sistema, pero no les otorga ningún derecho para administrar recursos de la red.
Para la autenticación con otros equipos, el contexto de usuario es el de la cuenta de equipo local, no la cuenta virtual.

Los controladores de dominio son un caso especial ya que no hay ningún grupo de **administradores** local. En su lugar, las cuentas virtuales pertenecen a **Administradores de dominio** y pueden administrar los servicios de directorio en el controlador de dominio. La identidad de dominio sigue estando restringida para su uso en el controlador de dominio donde se ha creado la instancia de la sesión de JEA. En su lugar, cualquier acceso de red parece proceder del objeto de equipo de controlador de dominio.

En ambos casos, puede definir de forma explícita a qué grupos de seguridad pertenece la cuenta virtual. Es un procedimiento recomendado cuando la tarea se puede realizar sin privilegios de administrador local o de dominio. Si ya tiene un grupo de seguridad definido para los administradores, conceda la pertenencia a la cuenta virtual a ese grupo. La pertenencia al grupo de la cuenta virtual se limita a los grupos de seguridad locales en servidores miembro y estaciones de trabajo. En los controladores de dominio, las cuentas virtuales deben ser miembros de grupos de seguridad de dominio.
Una vez agregada la cuenta virtual a uno o varios grupos de seguridad, ya no pertenece a los grupos predeterminados (administradores de dominio o locales).

En la tabla siguiente se resumen las posibles opciones de configuración y los permisos resultantes de las cuentas virtuales:

|        Tipo de equipo         | Configuración del grupo de cuenta virtual |                   Contexto de usuario local                    | Contexto de usuario de red |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| Controlador de dominio            | Valor predeterminado                             | Usuario de dominio, miembro de "*DOMINIO*\Administradores de domino"         | Cuenta de equipo     |
| Controlador de dominio            | Grupos de dominio A y B               | Usuario de dominio, miembro de "*DOMINIO*\A", "*DOMINIO*\B"       | Cuenta de equipo     |
| Servidor miembro o estación de trabajo | Valor predeterminado                             | Usuario local, miembro de "*BUILTIN*\Administradores"        | Cuenta de equipo     |
| Servidor miembro o estación de trabajo | Grupos locales C y D                | Usuario local, miembro de "*EQUIPO*\C" y "*EQUIPO*\D" | Cuenta de equipo     |

Al examinar los eventos de auditoría de seguridad y los registros de eventos de la aplicación, puede ver que cada sesión de usuario de JEA tiene una cuenta virtual única. Esta cuenta única ayuda a realizar el seguimiento de las acciones del usuario en un punto de conexión de JEA hasta el usuario original que ha ejecutado el comando. Los nombres de cuenta virtual siguen el formato `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>`. Por ejemplo, si el usuario **Alice** del dominio **Contoso** reinicia un servicio en un punto de conexión de JEA, el nombre de usuario asociado con todos los eventos del administrador de control de servicio sería `WinRM Virtual Users\WinRM_VA_1_contoso_alice`.

Las **cuentas de servicio administradas de grupo (gMSA)** son útiles cuando un servidor miembro necesita tener acceso a recursos de red en la sesión de JEA. Por ejemplo, cuando se usa un punto de conexión de JEA para controlar el acceso a una API REST hospedada en otro equipo. Es fácil escribir funciones para invocar las API REST, pero se necesita una identidad de red para autenticarse con la API. El uso de una cuenta de servicio administrada de grupo posibilita el segundo salto, mientras se conserva el control sobre los equipos que pueden usar la cuenta. Los permisos efectivos de la gMSA se definen mediante los grupos de seguridad, ya sean locales o de dominio, a los que pertenece la cuenta gMSA.

Cuando un punto de conexión de JEA se configura para usar una cuenta gMSA, parece que las acciones de todos los usuarios de JEA provienen de la misma gMSA. La única manera de realizar el seguimiento de las acciones hasta un usuario específico consiste en identificar el conjunto de comandos que se ejecutan en una transcripción de la sesión de PowerShell.

**Las credenciales de paso a través** se usan cuando no se especifica una cuenta de **ejecución**. PowerShell usa las credenciales del usuario que se conecta para ejecutar comandos en el servidor remoto. Esto requiere que se conceda al usuario de conexión acceso directo a grupos de administración con privilegios. Esta configuración **no** se recomienda para JEA. Si el usuario que se conecta ya tiene privilegios de administrador, puede evitar JEA y administrar el sistema a través de otro medio sin restricciones. Para obtener más información, vea la sección siguiente sobre cómo [JEA no protege frente a administradores](#jea-doesnt-protect-against-admins).

Las **cuentas de ejecución estándar** permiten especificar cualquier cuenta de usuario bajo la que se ejecuta toda la sesión de PowerShell. Las configuraciones de sesión en las que se usan cuentas de **ejecución** fijas (con el parámetro `-RunAsCredential`) no son compatibles con JEA. Las definiciones de roles ya no funcionan según lo previsto. A todos los usuarios autorizados para acceder al punto de conexión se les asigna el mismo rol.

No se debe usar un elemento **RunAsCredential** en un punto de conexión de JEA, ya que dificulta el seguimiento de las acciones hasta usuarios específicos y carece de compatibilidad para asignar usuarios a roles.

## <a name="winrm-endpoint-acl"></a>ACL de punto de conexión de WinRM

Como sucede con los puntos de conexión de comunicación remota de PowerShell normales, cada punto de conexión de JEA tiene una lista de control de acceso (ACL) independiente que controla quién se puede autenticar con el punto de conexión de JEA. Si no se ha configurado correctamente, es posible que los usuarios de confianza no puedan acceder al punto de conexión de JEA y que los usuarios que no son de confianza sí. La ACL de WinRM no afecta a la asignación de usuarios a roles de JEA. La asignación se controla mediante el campo **RoleDefinitions** del archivo de configuración de sesión que se ha usado para registrar el punto de conexión.

De forma predeterminada, cuando un punto de conexión de JEA tiene varias funcionalidades de rol, la ACL de WinRM se configura para permitir el acceso a todos los usuarios asignados. Por ejemplo, una sesión de JEA configurada con los comandos siguientes concede acceso total a `CONTOSO\JEA_Lev1` y `CONTOSO\JEA_Lev2`.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Puede auditar los permisos de usuario con el cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration).

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Para cambiar los usuarios que tienen acceso, ejecute `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` para obtener un aviso interactivo o `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` para actualizar los permisos. Los usuarios necesitan al menos *derechos de invocación* para tener acceso al punto de conexión de JEA.

Es posible crear un punto de conexión de JEA que no asigne un rol definido a todos los usuarios que tienen acceso. Estos usuarios pueden iniciar una sesión de JEA, pero solo tienen acceso a los cmdlets predeterminados. Puede auditar los permisos de usuario en un punto de conexión de JEA ejecutando `Get-PSSessionCapability`. Para obtener más información, vea [Auditoría y creación de informes en JEA](audit-and-report.md).

## <a name="least-privilege-roles"></a>Roles con privilegios mínimos

Al diseñar roles de JEA, es importante recordar que la cuenta de servicio administrada de grupo y la cuenta virtual que se ejecutan en segundo plano pueden tener acceso sin restricciones al equipo local. Las funcionalidades de rol de JEA ayudan a limitar los comandos y las aplicaciones que se pueden ejecutar en ese contexto con privilegios.
Los roles diseñados de manera incorrecta pueden permitir comandos peligrosos que autoricen a un usuario a salir de los límites de JEA u obtener acceso a información confidencial.

Por ejemplo, observe la siguiente entrada de funcionalidad de rol:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Esta funcionalidad de rol permite a los usuarios ejecutar cualquier cmdlet de PowerShell con el nombre **Process** del módulo **Microsoft.PowerShell.Management**. Es posible que los usuarios necesiten acceder a cmdlets como `Get-Process` para ver qué aplicaciones se ejecutan en el sistema y `Stop-Process` para eliminar cualquier aplicación que no responda. En cambio, esta entrada también permite `Start-Process`, que se puede usar para iniciar un programa arbitrario con permisos de administrador total. No es necesario instalar el programa de forma local en el sistema. Un usuario conectado podría iniciar un programa desde un recurso compartido de archivos que proporciona al usuario privilegios de administrador local, ejecuta software malintencionado y mucho más.

Una versión más segura de esta misma funcionalidad de rol tendría el siguiente aspecto:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Evite usar caracteres comodín en las funcionalidades de rol. No olvide [auditar los permisos de usuario efectivos](audit-and-report.md#check-effective-rights-for-a-specific-user) de forma periódica para comprender qué comandos son accesibles para el usuario.

## <a name="jea-doesnt-protect-against-admins"></a>JEA no protege frente a administradores

Uno de los principios básicos de JEA es que permite a los usuarios que no son administradores realizar algunas tareas administrativas. JEA no protege frente a los usuarios que ya tienen privilegios de administrador. Los usuarios que pertenecen a los grupos **Admins. del dominio**, **Administradores** local o a otros grupos con privilegios elevados pueden eludir las protecciones de JEA mediante otros medios. Por ejemplo, podrían iniciar sesión con RDP, usar consolas MMC remotas o conectarse a puntos de conexión de PowerShell sin restricciones. Además, los administradores locales de un sistema pueden modificar las configuraciones de JEA para permitir usuarios adicionales o cambiar una funcionalidad de rol para ampliar el ámbito de lo que puede realizar un usuario en su sesión de JEA. Es importante evaluar los permisos extendidos de los usuarios de JEA para ver si hay otras formas de obtener acceso con privilegios al sistema.

Un procedimiento común consiste en usar JEA para el mantenimiento diario habitual y tener una solución de administración de acceso con privilegios "Just-In-Time" que permita que los usuarios se conviertan de forma temporal en administradores locales en situaciones de emergencia. Esto ayuda a garantizar que los usuarios no sean administradores de forma permanente en el sistema, pero puedan obtener esos derechos si, y solo cuando, completen un flujo de trabajo en el que se documente el uso que hacen de esos permisos.
