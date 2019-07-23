---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Configuraciones de sesión de JEA
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726552"
---
# <a name="jea-session-configurations"></a>Configuraciones de sesión de JEA

Un punto de conexión de JEA se registra en un sistema mediante la creación y el registro de un archivo de configuración de sesión de PowerShell. Las configuraciones de sesión definen quién puede usar el punto de conexión de JEA y qué roles tienen acceso a él. También definen la configuración global que se aplica a todos los usuarios de la sesión de JEA.

## <a name="create-a-session-configuration-file"></a>Crear un archivo de configuración de sesión

Para registrar un punto de conexión de JEA, debe especificar cómo se configura ese punto de conexión. Hay muchas opciones que tener en cuenta. Las más importantes son las siguientes:

- Quién tiene acceso al punto de conexión de JEA
- Qué roles se les ha asignado
- Qué identidad de JEA se usa en segundo plano
- El nombre del punto de conexión de JEA

Estas opciones se definen en un archivo de datos de PowerShell con una extensión `.pssc`, denominado archivo de configuración de sesión de PowerShell. El archivo de configuración de sesión se puede modificar en cualquier editor de texto.

Ejecute el comando siguiente para crear un archivo de configuración de plantilla en blanco.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> De forma predeterminada, en el archivo de plantilla solo se incluyen las opciones de configuración más comunes. Use el conmutador `-Full` para incluir todas las opciones aplicables en el PSSC generado.

El campo `-SessionType RestrictedRemoteServer` indica que JEA usa la configuración de sesión para la administración segura. Las sesiones de este tipo funcionan en modo **NoLanguage** y solo tienen acceso a los comandos (y alias) predeterminados siguientes:

- Clear-Host (cls, clear)
- Exit-PSSession (exsn, exit)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Measure-Object (measure)
- Out-Default
- Select-Object (select)

No hay ningún proveedor de PowerShell disponible, ni tampoco ningún programa externo (ejecutables o scripts).

Para obtener más información sobre los modos de lenguaje, vea [Acerca de los modos de lenguaje](/powershell/module/microsoft.powershell.core/about/about_language_modes).

### <a name="choose-the-jea-identity"></a>Elegir la identidad de JEA

En segundo plano, JEA necesita una identidad (cuenta) para usarla al ejecutar los comandos de un usuario conectado.
En el archivo de configuración de sesión se define qué identidad usa JEA.

#### <a name="local-virtual-account"></a>Cuenta virtual local

Las cuentas virtuales locales son útiles cuando todos los roles definidos para el punto de conexión de JEA se usan para administrar el equipo local y una cuenta de administrador local es suficiente para ejecutar los comandos de forma correcta.
Las cuentas virtuales son cuentas temporales que son únicas para un usuario específico y solo duran lo mismo que la sesión de PowerShell. En un servidor miembro o estación de trabajo, las cuentas virtuales pertenecen al grupo **Administradores** del equipo local. En un controlador de dominio de Active Directory, las cuentas virtuales pertenecen al grupo **Administradores de dominio**.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Si los roles definidos por la configuración de sesión no requieren privilegios administrativos completos, puede especificar los grupos de seguridad a los que pertenecerá la cuenta virtual. En un servidor miembro o estación de trabajo, los grupos de seguridad especificados deben ser grupos locales, no grupos de un dominio.

Cuando se especifican uno o varios grupos de seguridad, la cuenta virtual no se asigna al grupo de administradores local o de dominio.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> Las cuentas virtuales se conceden temporalmente en el inicio de sesión como derecho de servicio en la directiva de seguridad del servidor local. Si a uno de los VirtualAccountGroups especificados ya se le ha concedido este derecho en la directiva, la cuenta virtual individual ya no se agregará y se quitará de la directiva. Esto puede ser útil en escenarios como los controladores de dominio, donde se auditan estrechamente las revisiones de la directiva de seguridad del controlador de dominio. Esto solo está disponible en Windows Server 2016 con el paquete acumulativo de revisiones de noviembre de 2018 o un paquete posterior y en Windows Server 2019 con el paquete acumulativo de revisiones de enero de 2019 o un paquete posterior.

#### <a name="group-managed-service-account"></a>Cuenta de servicio administrada de grupo

Una cuenta de servicio administrada de grupo (GMSA) es la identidad adecuada para usarla cuando los usuarios de JEA tienen que acceder a recursos de red como recursos compartidos de archivos y servicios web. Las cuentas GMSA proporcionan una identidad de dominio que se usa para autenticarse con recursos de cualquier equipo del dominio. Los derechos que proporciona una GMSA están determinados por los recursos a los que se accede. No tiene derechos de administrador en ningún equipo o servicio a menos que el administrador del equipo o servicio haya concedido de forma explícita esos privilegios a la cuenta GMSA.

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

Las GMSA solo se deben usar cuando sea necesario:

- Cuando se usa una GMSA, es difícil realizar el seguimiento de las acciones hasta un usuario. Todos los usuarios comparten la misma identidad de ejecución. Tendrá que revisar los registros y las transcripciones de la sesión de PowerShell para poner en correlación a los usuarios individuales con sus acciones.

- La GMSA puede tener acceso a muchos recursos de red a los que el usuario que se conecta no necesita acceso. Intente limitar siempre los permisos efectivos en una sesión de JEA para seguir el principio de privilegios mínimos.

> [!NOTE]
> Las cuentas de servicio administradas de grupo solo están disponibles en equipos unidos a un dominio en los que se usa PowerShell 5.1.

Para obtener más información sobre cómo proteger una sesión de JEA, vea el artículo sobre [consideraciones de seguridad](security-considerations.md).

### <a name="session-transcripts"></a>Transcripciones de sesión

Es recomendable configurar un punto de conexión de JEA para registrar de forma automática las transcripciones de las sesiones de los usuarios. Las transcripciones de sesión de PowerShell contienen información sobre el usuario que se conecta, la identidad de ejecución asignada y los comandos que ha ejecutado el usuario. Pueden ser útiles para un equipo de auditoría que necesite saber quién ha realizado un cambio específico en un sistema.

Para configurar la transcripción automática en el archivo de configuración de sesión, proporcione una ruta de acceso a una carpeta en que se almacenarán las transcripciones.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

La cuenta de **sistema local**, que requiere acceso de lectura y escritura al directorio, escribe las transcripciones en la carpeta. Los usuarios estándar no deben tener acceso a la carpeta. Limite el número de administradores de seguridad que tienen acceso para auditar las transcripciones.

### <a name="user-drive"></a>Unidad de usuario

Si los usuarios que se conectan necesitan copiar archivos desde o al punto de conexión de JEA, puede habilitar la unidad de usuario en el archivo de configuración de sesión. La unidad de usuario es una **PSDrive** que se asigna a una carpeta única para cada usuario que se conecta. Esta carpeta permite a los usuarios copiar archivos en o desde el sistema, sin concederles acceso al sistema de archivos completo ni exponer el proveedor FileSystem. El contenido de la unidad de usuario es persistente en todas las sesiones para adaptarse a situaciones en que se podría interrumpir la conectividad de red.

```powershell
MountUserDrive = $true
```

De manera predeterminada, la unidad de usuario le permite almacenar un máximo de 50 MB de datos por usuario. Puede limitar la cantidad de datos que puede consumir un usuario con el campo *UserDriveMaximumSize*.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Si no quiere que los datos de la unidad de usuario sean persistentes, puede configurar una tarea programada en el sistema para limpiar la carpeta de forma automática cada noche.

> [!NOTE]
> La unidad de usuario solo está disponible en PowerShell 5.1 o una versión posterior.

Para obtener más información sobre unidades de PowerShell, vea [Administración de unidades de PowerShell](/powershell/scripting/samples/managing-windows-powershell-drives).

### <a name="role-definitions"></a>Definiciones de roles

Las definiciones de roles en un archivo de configuración de sesión definen la asignación de **usuarios** a **roles**. A todos los usuarios o grupos incluidos en este campo se les asigna permiso al punto de conexión de JEA cuando se registra.
Cada usuario o grupo puede incluirse como una clave en la tabla hash solo una vez, pero se le pueden asignar varios roles. El nombre de la funcionalidad de rol debe ser el nombre del archivo de funcionalidad de rol, sin la extensión `.psrc`.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Si un usuario pertenece a más de un grupo en la definición de rol, obtiene acceso a los roles de cada uno. Si dos roles conceden acceso a los mismos cmdlets, se concede al usuario el conjunto de parámetros más permisivo.

Al especificar usuarios o grupos locales en el campo de definiciones de rol, asegúrese de usar el nombre del equipo, no **localhost** ni comodines. Puede comprobar el nombre del equipo observando la variable `$env:COMPUTERNAME`.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Orden de búsqueda de funcionalidad de rol

Como se ha mostrado en el ejemplo anterior, el nombre base del archivo de funcionalidad de rol hace referencia a las funcionalidades de rol. El nombre base de un archivo es el nombre de archivo sin la extensión. Si hay varias funcionalidades de rol disponibles en el sistema con el mismo nombre, PowerShell usa su orden de búsqueda implícito para seleccionar el archivo de funcionalidad de rol efectivo. JEA **no** proporciona acceso a todos los archivos de funcionalidad de rol con el mismo nombre.

JEA utiliza la variable de entorno `$env:PSModulePath` para determinar qué rutas de acceso examinar para archivos de capacidad de rol. Dentro de cada una de esas rutas de acceso, JEA busca módulos de PowerShell válidos que contengan una subcarpeta "RoleCapabilities". Al igual que con la importación de módulos, JEA prefiere funcionalidades de rol que se suministran con Windows a capacidades de rol personalizadas con el mismo nombre.

Para todos los demás conflictos de nomenclatura, la precedencia se determina por el orden en el que Windows enumera los archivos en el directorio. No se garantiza que el orden sea alfabético. Para el usuario que se conecta se usa el primer archivo de funcionalidad de rol que coincide con el nombre especificado. Como el orden de búsqueda de funcionalidad de rol no es determinista, se **recomienda encarecidamente** que las funcionalidades de rol tengan nombres de archivo únicos.

### <a name="conditional-access-rules"></a>Reglas de acceso condicional

De forma automática, se concede acceso a los puntos de conexión de JEA a todos los usuarios y grupos incluidos en el campo **RoleDefinitions**. Las reglas de acceso condicional permiten ajustar este acceso y requieren que los usuarios pertenezcan a grupos de seguridad adicionales que no afecten a los roles a los que están asignados. Esto es útil cuando se quiere integrar una solución de administración de acceso con privilegios "Just-In-Time", autenticación de tarjeta inteligente u otra solución de autenticación multifactor con JEA.

Las reglas de acceso condicional se definen en el campo RequiredGroups en un archivo de configuración de sesión.
En él, puede proporcionar una tabla hash (opcionalmente anidada) que use las claves "And" y "Or" para construir las reglas. Estos son algunos ejemplos sobre cómo usar este campo:

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
> Las reglas de acceso condicional solo están disponibles en PowerShell 5.1 o versiones posteriores.

### <a name="other-properties"></a>Otras propiedades

Los archivos de configuración de sesión también pueden hacer lo mismo que un archivo de funcionalidad de rol, pero sin la capacidad de proporcionar acceso a los usuarios que se conectan a distintos comandos. Si quiere permitir que todos los usuarios obtengan acceso a cmdlets, funciones o proveedores específicos, puede hacerlo directamente en el archivo de configuración de sesión.
Para obtener una lista completa de las propiedades que se admiten en el archivo de configuración de sesión, ejecute `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Probar un archivo de configuración de sesión

Puede probar una configuración de sesión con el cmdlet [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile). Se recomienda probar el archivo de configuración de sesión si se ha editado manualmente el archivo `.pssc`. Las pruebas garantizan que la sintaxis sea correcta. Si un archivo de configuración de sesión no supera esta prueba, no se puede registrar en el sistema.

## <a name="sample-session-configuration-file"></a>Archivo de configuración de sesión de ejemplo

En el ejemplo siguiente se muestra cómo crear y validar una configuración de sesión para JEA. Para que resulte cómodo y legible, las definiciones de roles se crean y almacenan en la variable `$roles`. Pero no es obligatorio hacerlo.

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

Para cambiar las propiedades de una configuración de sesión de JEA, incluida la asignación de usuarios a los roles, debe [anular el registro](register-jea.md#unregistering-jea-configurations). Después, [vuelva a registrar](register-jea.md) la configuración de sesión JEA mediante un archivo de configuración de sesión actualizado.

## <a name="next-steps"></a>Pasos siguientes

- [Registrar una configuración de JEA](register-jea.md)
- [Crear roles de JEA](role-capabilities.md)
