---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Registro de configuraciones de JEA
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017716"
---
# <a name="registering-jea-configurations"></a>Registro de configuraciones de JEA

Una vez que ha creado las [funcionalidades de rol](role-capabilities.md) y el [archivo de configuración de sesión](session-configurations.md), el último paso consiste en registrar el punto de conexión de JEA. El registro del punto de conexión de JEA en el sistema pone a disposición el punto de conexión para que lo usen los motores de automatización y los usuarios.

## <a name="single-machine-configuration"></a>Configuración de la máquina sencilla

Para entornos pequeños, puede implementar JEA al registrar el archivo de configuración de sesión mediante el cmdlet [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration).

Antes de comenzar, asegúrese de que se cumplen los requisitos previos siguientes:

- Se han creado uno o varios roles, y se han colocado en la carpeta **RoleCapabilities** de un módulo de PowerShell.
- Se ha creado y probado un archivo de configuración de sesión.
- El usuario que registra la configuración de JEA tiene derechos de administrador en el sistema.
- Ha seleccionado un nombre para el punto de conexión de JEA.

El nombre del punto de conexión de JEA es obligatorio cuando los usuarios se conectan al sistema mediante JEA. El cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) enumera los nombres de los puntos de conexión de un sistema. Los puntos de conexión que empiezan por `microsoft` normalmente se entregan con Windows. El punto de conexión `microsoft.powershell` es el que se usa de manera predeterminada al conectarse a un punto de conexión remoto de PowerShell.

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Ejecute el comando siguiente para registrar el punto de conexión.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> El comando anterior reinicia el servicio WinRM en el sistema. Esto finaliza todas las sesiones de comunicación remota de PowerShell y todas las configuraciones de DSC en curso. Se recomienda desconectar las máquinas de producción antes de ejecutar el comando para evitar interrumpir las operaciones empresariales.

Después del registro, estará listo para [usar JEA](using-jea.md). Puede eliminar el archivo de configuración de sesión en cualquier momento. El archivo de configuración no se usa después del registro del punto de conexión.

## <a name="multi-machine-configuration-with-dsc"></a>Configuración de varios equipos con DSC

Al implementar JEA en varios equipos, el modelo de implementación más sencillo usa el recurso de [configuración de estado deseado (DSC)](/powershell/dsc/overview) de JEA para implementar JEA en todos los equipos de forma rápida y coherente.

Para implementar JEA con DSC, asegúrese de que se cumplen los requisitos previos siguientes:

- Se han creado una o varias funcionalidades de rol y se han agregado a un módulo de PowerShell.
- El módulo de PowerShell que contiene los roles se almacena en un recurso compartido de archivo (de solo lectura) al que pueden obtener acceso todos los equipos.
- Se ha determinado la configuración de la sesión. No es necesario crear un archivo de configuración de sesión cuando se usa el recurso DSC de JEA.
- Tiene credenciales que le permiten realizar acciones administrativas en todos los equipos, o bien tiene acceso al servidor de extracción de DSC que se usa para administrar los equipos.
- Ha descargado el [recurso de DSC de JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).

Cree una configuración de DSC para el punto de conexión de JEA en un equipo de destino o servidor de extracción. En esta configuración, el recurso de DSC **JustEnoughAdministration** define el archivo de configuración de sesión y el recurso **File** copia las funcionalidades de rol desde el recurso compartido de archivos.

Se pueden configurar las siguientes propiedades con el recurso de DSC:

- Definiciones de roles
- Grupos de cuenta virtual
- Nombre de cuenta de servicio administrada de grupo
- Directorio de transcripciones
- Unidad de usuario
- Reglas de acceso condicional
- Scripts de inicio de la sesión de JEA

La sintaxis de cada una de estas propiedades en una configuración de DSC es coherente con el archivo de configuración de sesión de PowerShell.

A continuación se muestra un ejemplo de configuración de DSC de un módulo de mantenimiento general del servidor. Supone que un módulo de PowerShell válido que contiene las funcionalidades de rol se encuentra en el recurso compartido de archivos `\\myfileshare\JEA`.

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

Después, esta configuración se aplica en un sistema mediante la invocación directa del [administrador de configuración local](/powershell/dsc/managing-nodes/metaConfig) o la actualización de la [configuración del servidor de extracción](/powershell/dsc/pull-server/pullServer).

El recurso de DSC también permite reemplazar el punto de conexión de **Microsoft.PowerShell** predeterminado. Cuando se reemplaza, el recurso registra de forma automática un punto de conexión de reserva denominado **Microsoft.PowerShell.Restricted**. El punto de conexión de reserva tiene la ACL de WinRM predeterminada que permite el acceso a los miembros del grupo Usuarios de administración remota y Administradores local.

## <a name="unregistering-jea-configurations"></a>Anular el registro de configuraciones de JEA

El cmdlet [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) quita un punto de conexión de JEA. Si anula el registro de un punto de conexión de JEA, evitará que nuevos usuarios creen sesiones de JEA en el sistema. También permite actualizar una configuración de JEA al volver a registrar un archivo de configuración de sesión actualizado con el mismo nombre de punto de conexión.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Anular el registro de un punto de conexión de JEA provocará que se reinicie el servicio WinRM. Esto interrumpe la mayoría de las operaciones de administración remotas en curso, incluidas otras sesiones de PowerShell, invocaciones de WMI y algunas herramientas de administración. Anule el registro de puntos de conexión de PowerShell solo durante ventanas de mantenimiento planificadas.

## <a name="next-steps"></a>Pasos siguientes

[Probar el punto de conexión de JEA](using-jea.md)
