---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Configuraciones de sesión de JEA
ms.openlocfilehash: 3e5a663be8e7aba09a2592c278224cd892c89a20
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190101"
---
# <a name="jea-session-configurations"></a>Configuraciones de sesión de JEA

> Se aplica a: Windows PowerShell 5.0

Un punto de conexión de JEA se registra en un sistema al crear y registrar un archivo de configuración de sesión de PowerShell de una forma específica.
Las configuraciones de sesión determinan *quién* puede usar el punto de conexión de JEA y qué roles tendrán acceso a él.
También definen la configuración global que se aplica a los usuarios de cualquier rol en la sesión de JEA.

En este tema, se describe cómo crear un archivo de configuración de sesión de PowerShell y cómo registrar un punto de conexión de JEA.

## <a name="create-a-session-configuration-file"></a>Crear un archivo de configuración de sesión

Para registrar un punto de conexión de JEA, debe especificar cómo se debe configurar ese punto de conexión.
Hay muchas opciones que se deben tener en cuenta, la más importante de ellas es quién debe tener acceso al punto de conexión de JEA, qué roles se le asignarán, qué identidad usará JEA a un nivel más profundo y cuál será el nombre del punto de conexión de JEA.
Todas ellas se definen en un archivo de configuración de sesión de PowerShell, que es un archivo de datos de PowerShell que finaliza con una extensión .pssc.

Para crear un archivo de configuración de sesión esqueleto para puntos de conexión de JEA, ejecute el siguiente comando.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> En el archivo esqueleto solo se incluyen de forma predeterminada las opciones de configuración más comunes.
> Use el conmutador `-Full` para incluir todas las opciones aplicables en el PSSC generado.

Puede abrir el archivo de configuración de sesión en cualquier editor de texto.
El campo `-SessionType RestrictedRemoteServer` indica que JEA usará la configuración de sesión para administrarla de forma segura.
Las sesiones configuradas de esta forma funcionarán en [modo NoLanguage](https://technet.microsoft.com/library/dn433292.aspx) y solo tendrán los siguientes 8 comandos (y alias) predeterminados disponibles:

- Clear-Host (cls, clear)
- Exit-PSSession (exsn, exit)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Measure-Object (measure)
- Out-Default
- Select-Object (select)

No hay ningún proveedor de PowerShell disponible, ni tampoco ningún programa externo (ejecutables, scripts, etc.).

Hay otros campos que querrá configurar para la sesión de JEA.
Se tratan en las siguientes secciones.

### <a name="choose-the-jea-identity"></a>Elegir la identidad de JEA

En segundo plano, JEA necesita una identidad (cuenta) para usarla al ejecutar los comandos de un usuario conectado.
Usted decide qué identidad usará JEA en el archivo de configuración de sesión.

#### <a name="local-virtual-account"></a>Cuenta virtual local

Si los roles compatibles con este punto de conexión de JEA se usan para administrar el equipo local y una cuenta de administrador local es suficiente para ejecutar los comandos correctamente, debe configurar JEA para que use una cuenta virtual local.
Las cuentas virtuales son cuentas temporales que son únicas para un usuario específico y solo duran lo mismo que la sesión de PowerShell.
En un servidor miembro o estación de trabajo, las cuentas virtuales pertenecen al grupo **Administradores** del equipo local y tienen acceso a la mayoría de recursos del sistema.
En un controlador de dominio de Active Directory, las cuentas virtuales pertenecen al grupo **Administradores de dominio**.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Si los roles compatibles con la configuración de sesión no requieren esos privilegios amplios, también puede especificar los grupos de seguridad a los que pertenecerá la cuenta virtual.
En un servidor miembro o estación de trabajo, los grupos de seguridad especificados deben ser grupos locales, no grupos de un dominio.

Cuando se especifiquen uno o varios grupos de seguridad, la cuenta virtual ya no pertenecerá al grupo de administradores local o de dominio.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a>Cuenta de servicio administrada de grupo


Para los escenarios que requieren que el usuario de JEA obtenga acceso a recursos de red como otros equipos o servicios web, la identidad más apropiada que se puede usar es una cuenta de servicio administrada de grupo (gMSA).
Las cuentas gMSA proporcionan una identidad de dominio que se puede usar para autenticarse en recursos en cualquier equipo del dominio.
Los derechos que le proporciona la cuenta gMSA se determinan según los recursos a los que obtenga acceso.
No tendrá derechos de administrador en los equipos o servicios de forma automática a menos que el administrador del equipo o servicio haya concedido de forma explícita privilegios de administrador a la cuenta gMSA.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

Las cuentas gMSA solo deben usarse cuando se necesite acceso a recursos de red por diversas razones:

- Es más difícil realizar un seguimiento de las acciones hasta el usuario al usar una cuenta gMSA ya que todos los usuarios comparten la misma identidad de ejecución. Deberá consultar los registros y transcripciones de la sesión de PowerShell para poner en correlación a los usuarios con sus acciones.

- La cuenta gMSA puede tener acceso a muchos recursos de red a los que el usuario que se conecta no necesita acceso. Intente limitar siempre los permisos efectivos en una sesión de JEA para seguir el principio de privilegios mínimos.

> [!NOTE]
> Las cuentas de servicio administradas de grupo solo están disponibles en Windows PowerShell 5.1 o una versión posterior y en equipos unidos a un dominio.


#### <a name="more-information-about-run-as-users"></a>Más información sobre los usuarios de ejecución

Puede encontrar información adicional sobre las identidades de ejecución y cómo encajan en la seguridad de una sesión de JEA en el artículo sobre [consideraciones de seguridad](security-considerations.md).

### <a name="session-transcripts"></a>Transcripciones de sesión

Es recomendable que configure un archivo de configuración de sesión de JEA para registrar de forma automática las transcripciones de las sesiones de los usuarios.
Las transcripciones de sesión de PowerShell contienen información sobre el usuario que se conecta, la identidad de ejecución asignada y los comandos que ha ejecutado el usuario.
Pueden ser útiles para un equipo de auditoría que necesite saber quién ha realizado un cambio específico en un sistema.

Para configurar la transcripción automática en el archivo de configuración de sesión, proporcione una ruta de acceso a una carpeta en que se almacenarán las transcripciones.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

La carpeta especificada debe configurarse para evitar que los usuarios modifiquen o eliminen los datos en ella.
La cuenta de sistema local, que requiere acceso de lectura y escritura al directorio, escribe las transcripciones en la carpeta.
Los usuarios estándar no deben tener acceso a la carpeta y un conjunto limitado de administradores de seguridad debe tener acceso para auditar las transcripciones.

### <a name="user-drive"></a>Unidad de usuario

Si los usuarios que se conectan necesitan copiar archivos desde o al punto de conexión de JEA para ejecutar un comando, puede habilitar la unidad de usuario en el archivo de configuración de sesión.
La unidad de usuario es una [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) que se asigna a una carpeta única para cada usuario que se conecta.
Esta carpeta sirve como espacio para que puedan copiar archivos del o en el sistema, sin concederles acceso al sistema de archivos completo ni exponer el proveedor FileSystem.
El contenido de la unidad de usuario es persistente en todas las sesiones para adaptarse a situaciones en que se podría interrumpir la conectividad de red.

```powershell
MountUserDrive = $true
```

De manera predeterminada, la unidad de usuario le permite almacenar un máximo de 50 MB de datos por usuario.
Puede limitar la cantidad de datos que puede consumir un usuario con el campo *UserDriveMaximumSize*.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Si no quiere que los datos en la unidad de usuario sean persistentes, puede configurar una tarea programada en el sistema para limpiar la carpeta de forma automática cada noche.

> [!NOTE]
> La unidad de usuario solo está disponible en Windows PowerShell 5.1 o una versión posterior.

### <a name="role-definitions"></a>Definiciones de roles

Las definiciones de roles en un archivo de configuración de sesión definen la asignación de *usuarios* a *roles*.
De forma automática, se le concederá permiso a cada usuario o grupo incluido en este campo al punto de conexión de JEA cuando se registre.
Cada usuario o grupo puede incluirse como una clave en la tabla hash solo una vez, pero se le pueden asignar varios roles.
El nombre de la funcionalidad de rol debe ser el nombre del archivo de funcionalidad de rol, sin la extensión .psrc.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Si un usuario pertenece a más de un grupo en la definición de rol, obtendrá acceso a los roles de cada uno.
Si dos roles conceden acceso a los mismos cmdlets, se concederá al usuario el conjunto de parámetros más permisivo.

Al especificar usuarios o grupos locales en el campo de las definiciones de rol, asegúrese de utilizar el nombre del equipo (no *localhost* o *.*) antes de la barra diagonal inversa.
Puede comprobar el nombre del equipo observando la variable `$env:computername`.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Orden de búsqueda de funcionalidad de rol
Tal como se muestra en el ejemplo anterior, el nombre sin formato (nombre de archivo sin la extensión) del archivo de funcionalidad de rol hace referencia a las funcionalidades de rol.
Si hay varias funcionalidades de rol disponibles en el sistema con el mismo nombre sin formato, PowerShell usará su orden de búsqueda implícito para seleccionar el archivo de funcionalidad de rol adecuado.
**No** proporcionará acceso a todos los archivos de funcionalidad de rol con el mismo nombre.

JEA utiliza la variable de entorno `$env:PSModulePath` para determinar qué rutas de acceso examinar para archivos de capacidad de rol.
Dentro de cada una de esas rutas de acceso, JEA buscará módulos válidos de PowerShell que contengan una subcarpeta "RoleCapabilities".
Al igual que con la importación de módulos, JEA prefiere funcionalidades de rol que se suministran con Windows a capacidades de rol personalizadas con el mismo nombre.
Para todos los demás conflictos de nomenclatura, la precedencia se determina por el orden en el que Windows enumera los archivos en el directorio (sin garantizar el orden alfabético).
El primer archivo de funcionalidad de rol que coincida con el nombre deseado se usará para el usuario que se conecta.

Puesto que el orden de búsqueda de la funcionalidad de rol no es determinista cuando dos o más funcionalidades de rol comparten el mismo nombre, se **recomienda encarecidamente** que se asegure de que las funcionalidades de rol tienen nombres únicos en el equipo.

### <a name="conditional-access-rules"></a>Reglas de acceso condicional

De forma automática, se concede acceso a los puntos de conexión de JEA a todos los usuarios y grupos incluidos en el campo RoleDefinitions.
Las reglas de acceso condicional le permiten restringir este acceso y requieren que los usuarios pertenezcan a grupos de seguridad adicionales que no afecten a los roles a los que están asignados.
Esto puede ser útil si quiere integrar una solución de administración de acceso con privilegios "Just-In-Time", autenticación de tarjeta inteligente u otra solución de autenticación multifactor con JEA.

Las reglas de acceso condicional se definen en el campo RequiredGroups en un archivo de configuración de sesión.
En él, puede proporcionar una tabla hash (opcionalmente anidada) que use las claves "And" y "Or" para construir las reglas.
Estos son algunos ejemplos sobre cómo sacar provecho de este campo:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> Las reglas de acceso condicional solo están disponibles en Windows PowerShell 5.1 o una versión posterior.

### <a name="other-properties"></a>Otras propiedades
Los archivos de configuración de sesión también pueden hacer lo mismo que un archivo de funcionalidad de rol, pero sin la capacidad de proporcionar acceso a los usuarios que se conectan a distintos comandos.
Si quiere permitir que todos los usuarios obtengan acceso a cmdlets, funciones o proveedores específicos, puede hacerlo directamente en el archivo de configuración de sesión.
Para obtener una lista completa de las propiedades que se admiten en el archivo de configuración de sesión, ejecute `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Probar un archivo de configuración de sesión

Puede probar una configuración de sesión con el cmdlet [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile).
Se recomienda encarecidamente que pruebe el archivo de configuración de sesión si se ha editado el archivo pssc de forma manual mediante un editor de texto para asegurarse de que la sintaxis sea correcta.
Si un archivo de configuración de sesión no supera esta prueba, no podrá registrarse correctamente en el sistema.

## <a name="sample-session-configuration-file"></a>Archivo de configuración de sesión de ejemplo

A continuación hay un ejemplo completo que muestra cómo crear y validar una configuración de sesión para JEA.
Tenga en cuenta que las definiciones de roles se crean y almacenan en la variable `$roles` para su comodidad y legibilidad.
No es un requisito hacerlo.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>Actualizar los archivos de configuración de sesión

Si necesita cambiar las propiedades de una configuración de sesión de JEA, incluida la asignación de usuarios a los roles, debe [anular el registro](register-jea.md#unregistering-jea-configurations) y [volver a registrar](register-jea.md) la configuración de sesión de JEA.
Al volver a registrar la configuración de sesión de JEA, use un archivo de configuración de sesión de PowerShell actualizado que incluya los cambios que quiera.

## <a name="next-steps"></a>Pasos siguientes

- [Registrar una configuración de JEA](register-jea.md)
- [Crear roles de JEA](role-capabilities.md)