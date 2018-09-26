---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Registro de configuraciones de JEA
ms.openlocfilehash: 2c4a8f64c966903a6eb8fcabe4cd25ae7f98b2c4
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522861"
---
# <a name="registering-jea-configurations"></a>Registro de configuraciones de JEA

> Se aplica a: Windows PowerShell 5.0

El último paso antes de poder usar JEA una vez que ha creado las [funcionalidades de rol](role-capabilities.md) y el [archivo de configuración de sesión](session-configurations.md) es registrar el punto de conexión de JEA.
Este proceso aplica la información de configuración de sesión en el sistema y pone el punto de conexión a disposición de los usuarios y los motores de automatización.

## <a name="single-machine-configuration"></a>Configuración de la máquina sencilla

Para entornos pequeños, puede implementar JEA al registrar el archivo de configuración de sesión mediante el cmdlet [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration).

Antes de comenzar, asegúrese de que se cumplen los requisitos previos siguientes:
- Se han creado uno o varios roles y se han colocado en la carpeta "RoleCapabilities" de un módulo de PowerShell válido.
- Se ha creado y probado un archivo de configuración de sesión.
- El usuario que registra la configuración de JEA tiene derechos de administrador en los sistemas.

También debe seleccionar un nombre para el punto de conexión de JEA.
El nombre del punto de conexión de JEA será necesario cuando los usuarios quieran conectarse al sistema mediante JEA.
Puede usar el cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) para comprobar los nombres de los puntos de conexión existentes en el sistema.
Los puntos de conexión que empiezan por "microsoft" se entregan normalmente con Windows.
El punto de conexión "microsoft.powershell" es el que se usa de manera predeterminada al conectarse a un punto de conexión remoto de PowerShell.

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Cuando haya determinado un nombre adecuado para el punto de conexión de JEA, ejecute el siguiente comando para registrarlo.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> El comando anterior reiniciará el servicio WinRM en el sistema.
> Esto finalizará todas las sesiones de comunicación remota de PowerShell, así como las configuraciones de DSC en curso.
> Se recomienda que desconecte todas las máquinas de producción antes de ejecutar el comando para evitar interrumpir operaciones empresariales.

Si el registro se realiza correctamente, está listo para [usar JEA](using-jea.md).
Puede eliminar el archivo de configuración de sesión en cualquier momento; no se usará después del registro.

## <a name="multi-machine-configuration-with-dsc"></a>Configuración de varios equipos con DSC

Si va a implementar JEA en varios equipos, el modelo de implementación más sencillo es usar el recurso de [configuración de estado deseado](https://msdn.microsoft.com/powershell/dsc/overview) de JEA para implementar JEA en todos los equipos de forma rápida y coherente.

Para implementar JEA con DSC, debe asegurarse de que se cumplen los requisitos previos siguientes:
- Se han creado una o varias funcionalidades de rol y se han agregado a un módulo de PowerShell válido.
- El módulo de PowerShell que contiene los roles se almacena en un recurso compartido de archivo (de solo lectura) al que pueden obtener acceso todos los equipos.
- Se ha determinado la configuración de la sesión. No es necesario crear un archivo de configuración de sesión cuando se usa el recurso DSC de JEA.
- Tiene credenciales que le permitirán realizar acciones administrativas en todos los equipos, o tiene acceso a un servidor de extracción de DSC usado para administrar los equipos.
- Ha descargado el [recurso de DSC de JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).

En un equipo de destino (o servidor de incorporación de cambios, si usa uno), cree una configuración de DSC para el punto de conexión de JEA.
En esta configuración, usará el recurso de DSC JustEnoughAdministration para configurar el archivo de configuración de sesión y el recurso de archivos para copiar a través de las funcionalidades de rol desde el recurso compartido de archivos.

Se pueden configurar las siguientes propiedades con el recurso de DSC:
- Definiciones de roles
- Grupos de cuenta virtual
- Nombre de cuenta de servicio administrada de grupo
- Directorio de transcripciones
- Unidad de usuario
- Reglas de acceso condicional
- Scripts de inicio de la sesión de JEA

La sintaxis de cada una de estas propiedades en una configuración de DSC es coherente con el archivo de configuración de sesión de PowerShell.

A continuación se muestra un ejemplo de configuración de DSC de un módulo de mantenimiento general del servidor.

Supone que un módulo de PowerShell válido que contiene las funcionalidades de rol en una subcarpeta "RoleCapabilities" se encuentra en el recurso compartido de archivos "\\\\mirecursocompartidodearchivos\\JEA".


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

Después, se puede aplicar esta configuración en un sistema al [invocar directamente el administrador de configuración local](https://msdn.microsoft.com/powershell/dsc/metaconfig) o actualizar la [configuración del servidor de incorporación de cambios](https://msdn.microsoft.com/powershell/dsc/pullserver).

El recurso de DSC también permite reemplazar el punto de conexión de comunicación remota Microsoft.PowerShell predeterminado.
Si lo hace, el recurso registrará de forma automática un punto de conexión sin restricciones de copia de seguridad denominado "Microsoft.PowerShell.Restricted", que tiene la ACL de WinRM predeterminada (que permite que los miembros del grupo de administradores locales y Usuarios de administración remota obtengan acceso a él).

## <a name="unregistering-jea-configurations"></a>Anular el registro de configuraciones de JEA

Para quitar un punto de conexión de JEA de un sistema, use el cmdlet [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration).
Si anula el registro de un punto de conexión de JEA, evitará que nuevos usuarios creen nuevas sesiones de JEA en el sistema.
También permite actualizar una configuración de JEA al volver a registrar un archivo de configuración de sesión actualizado con el mismo nombre de punto de conexión.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Anular el registro de un punto de conexión de JEA provocará que se reinicie el servicio WinRM.
> Esto interrumpirá la mayoría de las operaciones de administración remotas en curso, incluidas otras sesiones de PowerShell, invocaciones de WMI y algunas herramientas de administración.
> Anule el registro de puntos de conexión de PowerShell solo durante ventanas de mantenimiento planificadas.

## <a name="next-steps"></a>Pasos siguientes

- [Probar el punto de conexión de JEA](using-jea.md)