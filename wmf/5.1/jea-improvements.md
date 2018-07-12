---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: ryanpu
title: Mejoras de Just Enough Administration (JEA)
ms.openlocfilehash: 79271e77a539764e7a18842efd919413cdc8ab9f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892727"
---
# <a name="improvements-to-just-enough-administration-jea"></a>Mejoras de Just Enough Administration (JEA)

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>Copia restringida de archivos a o desde puntos de conexión JEA

Ahora puede copiar remotamente archivos a o desde un punto de conexión JEA sin tener que preocuparse por si el usuario que se conecta puede copiar *cualquier otro* archivo del sistema.
Esto se puede realizar si configura el archivo PSSC para que monte una unidad de usuario para los usuarios que se conectan.
La unidad de usuario es un PSDrive nuevo único para cada usuario que se conecta y que se mantiene conectado entre sesiones.
Cuando se usa `Copy-Item` para copiar archivos a o desde una sesión JEA, se restringe para que solo permita el acceso a la unidad de usuario.
Si intenta copiar archivos a cualquier otro PSDrive, se producirá un error.

Para configurar la unidad de usuario en el archivo de configuración de la sesión JEA, use los siguientes campos nuevos:

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

La carpeta de respaldo de la unidad de usuario se creará en `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Para usar la unidad de usuario y copiar archivos a o desde un punto de conexión JEA configurado para exponer la unidad de usuario, use los parámetros `-ToSession` y `-FromSession` en `Copy-Item`.

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

Después, puede escribir funciones personalizadas para procesar los datos almacenados en la unidad de usuario y ponerlas a disposición de los usuarios en el archivo de funcionalidad de roles.

## <a name="support-for-group-managed-service-accounts"></a>Compatibilidad con las cuentas de servicio administradas de grupo

En algunos casos, puede que una tarea que tenga que realizar un usuario en una sesión JEA necesite acceso a recursos más allá de la máquina local.
Cuando una sesión JEA está configurada para usar una cuenta virtual, cualquier intento de tener acceso a esos recursos parecerá que proviene de la identidad de la máquina local, y no de la cuenta virtual ni del usuario conectado.
En TP5, hemos habilitado la compatibilidad para ejecutar JEA en el contexto de una [cuenta de servicio administrada de grupo](https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), lo que facilita el acceso a recursos de red mediante una identidad de dominio.

Para configurar una sesión JEA para que se ejecute en una cuenta de gMSA, use la siguiente clave nueva en el archivo PSSC:

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> Las cuentas de servicio administradas de grupo no permiten el ámbito limitado o de aislamiento de las cuentas virtuales.
> Cada usuario que se conecta compartirá la misma identidad de gMSA, que puede tener permisos en toda la empresa.
> Tenga mucho cuidado al seleccionar la opción de usar una gMSA; siempre son preferibles las cuentas virtuales que están limitadas a la máquina local cuando sea posible.

## <a name="conditional-access-policies"></a>Directivas de acceso condicional

JEA es ideal para limitar lo que alguien puede hacer cuando está conectado a un sistema para administrarlo, pero ¿qué sucede si también quiere limitar *el momento* en que alguien puede usar JEA?
Hemos agregado opciones de configuración en los archivos de configuración de sesión (.pssc) para permitirle especificar grupos de seguridad a los que debe pertenecer un usuario para establecer una sesión JEA.
Esto puede resultar especialmente útil si tiene un sistema Just In Time (JIT) en su entorno y quiere que sus usuarios eleven los privilegios antes de acceder a un punto de conexión JEA con privilegios elevados.

El nuevo campo *RequiredGroups* en el archivo PSSC le permite especificar la lógica para determinar si un usuario puede conectarse a JEA.
Consiste en especificar una tabla hash (opcionalmente anidada) que use las claves "And" y "Or" para construir las reglas.
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

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Solucionado: las cuentas virtuales ahora son compatibles con Windows Server 2008 R2

En WMF 5.1, ahora puede usar cuentas virtuales en Windows Server 2008 R2, lo que permite configuraciones coherentes y paridad de funcionalidades en Windows Server 2008 R2 - 2016.
Las cuentas virtuales siguen sin admitirse al usar JEA en Windows 7.