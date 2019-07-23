---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Registro de configuraciones de JEA
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726613"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="52433-103">Registro de configuraciones de JEA</span><span class="sxs-lookup"><span data-stu-id="52433-103">Registering JEA Configurations</span></span>

<span data-ttu-id="52433-104">Una vez que ha creado las [funcionalidades de rol](role-capabilities.md) y el [archivo de configuración de sesión](session-configurations.md), el último paso consiste en registrar el punto de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="52433-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="52433-105">El registro del punto de conexión de JEA en el sistema pone a disposición el punto de conexión para que lo usen los motores de automatización y los usuarios.</span><span class="sxs-lookup"><span data-stu-id="52433-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="52433-106">Configuración de la máquina sencilla</span><span class="sxs-lookup"><span data-stu-id="52433-106">Single machine configuration</span></span>

<span data-ttu-id="52433-107">Para entornos pequeños, puede implementar JEA al registrar el archivo de configuración de sesión mediante el cmdlet [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="52433-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="52433-108">Antes de comenzar, asegúrese de que se cumplen los requisitos previos siguientes:</span><span class="sxs-lookup"><span data-stu-id="52433-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="52433-109">Se han creado uno o varios roles, y se han colocado en la carpeta **RoleCapabilities** de un módulo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52433-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="52433-110">Se ha creado y probado un archivo de configuración de sesión.</span><span class="sxs-lookup"><span data-stu-id="52433-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="52433-111">El usuario que registra la configuración de JEA tiene derechos de administrador en el sistema.</span><span class="sxs-lookup"><span data-stu-id="52433-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="52433-112">Ha seleccionado un nombre para el punto de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="52433-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="52433-113">El nombre del punto de conexión de JEA es obligatorio cuando los usuarios se conectan al sistema mediante JEA.</span><span class="sxs-lookup"><span data-stu-id="52433-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="52433-114">El cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) enumera los nombres de los puntos de conexión de un sistema.</span><span class="sxs-lookup"><span data-stu-id="52433-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="52433-115">Los puntos de conexión que empiezan por `microsoft` normalmente se entregan con Windows.</span><span class="sxs-lookup"><span data-stu-id="52433-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="52433-116">El punto de conexión `microsoft.powershell` es el que se usa de manera predeterminada al conectarse a un punto de conexión remoto de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52433-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

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

<span data-ttu-id="52433-117">Ejecute el comando siguiente para registrar el punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="52433-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="52433-118">El comando anterior reinicia el servicio WinRM en el sistema.</span><span class="sxs-lookup"><span data-stu-id="52433-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="52433-119">Esto finaliza todas las sesiones de comunicación remota de PowerShell y todas las configuraciones de DSC en curso.</span><span class="sxs-lookup"><span data-stu-id="52433-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="52433-120">Se recomienda desconectar las máquinas de producción antes de ejecutar el comando para evitar interrumpir las operaciones empresariales.</span><span class="sxs-lookup"><span data-stu-id="52433-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="52433-121">Después del registro, estará listo para [usar JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="52433-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="52433-122">Puede eliminar el archivo de configuración de sesión en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="52433-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="52433-123">El archivo de configuración no se usa después del registro del punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="52433-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="52433-124">Configuración de varios equipos con DSC</span><span class="sxs-lookup"><span data-stu-id="52433-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="52433-125">Al implementar JEA en varios equipos, el modelo de implementación más sencillo usa el recurso de [configuración de estado deseado (DSC)](/powershell/dsc/overview) de JEA para implementar JEA en todos los equipos de forma rápida y coherente.</span><span class="sxs-lookup"><span data-stu-id="52433-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="52433-126">Para implementar JEA con DSC, asegúrese de que se cumplen los requisitos previos siguientes:</span><span class="sxs-lookup"><span data-stu-id="52433-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="52433-127">Se han creado una o varias funcionalidades de rol y se han agregado a un módulo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52433-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="52433-128">El módulo de PowerShell que contiene los roles se almacena en un recurso compartido de archivo (de solo lectura) al que pueden obtener acceso todos los equipos.</span><span class="sxs-lookup"><span data-stu-id="52433-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="52433-129">Se ha determinado la configuración de la sesión.</span><span class="sxs-lookup"><span data-stu-id="52433-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="52433-130">No es necesario crear un archivo de configuración de sesión cuando se usa el recurso DSC de JEA.</span><span class="sxs-lookup"><span data-stu-id="52433-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="52433-131">Tiene credenciales que le permiten realizar acciones administrativas en todos los equipos, o bien tiene acceso al servidor de extracción de DSC que se usa para administrar los equipos.</span><span class="sxs-lookup"><span data-stu-id="52433-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="52433-132">Ha descargado el [recurso de DSC de JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span><span class="sxs-lookup"><span data-stu-id="52433-132">You've downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="52433-133">Cree una configuración de DSC para el punto de conexión de JEA en un equipo de destino o servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="52433-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="52433-134">En esta configuración, el recurso de DSC **JustEnoughAdministration** define el archivo de configuración de sesión y el recurso **File** copia las funcionalidades de rol desde el recurso compartido de archivos.</span><span class="sxs-lookup"><span data-stu-id="52433-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="52433-135">Se pueden configurar las siguientes propiedades con el recurso de DSC:</span><span class="sxs-lookup"><span data-stu-id="52433-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="52433-136">Definiciones de roles</span><span class="sxs-lookup"><span data-stu-id="52433-136">Role Definitions</span></span>
- <span data-ttu-id="52433-137">Grupos de cuenta virtual</span><span class="sxs-lookup"><span data-stu-id="52433-137">Virtual account groups</span></span>
- <span data-ttu-id="52433-138">Nombre de cuenta de servicio administrada de grupo</span><span class="sxs-lookup"><span data-stu-id="52433-138">Group-managed service account name</span></span>
- <span data-ttu-id="52433-139">Directorio de transcripciones</span><span class="sxs-lookup"><span data-stu-id="52433-139">Transcript directory</span></span>
- <span data-ttu-id="52433-140">Unidad de usuario</span><span class="sxs-lookup"><span data-stu-id="52433-140">User drive</span></span>
- <span data-ttu-id="52433-141">Reglas de acceso condicional</span><span class="sxs-lookup"><span data-stu-id="52433-141">Conditional access rules</span></span>
- <span data-ttu-id="52433-142">Scripts de inicio de la sesión de JEA</span><span class="sxs-lookup"><span data-stu-id="52433-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="52433-143">La sintaxis de cada una de estas propiedades en una configuración de DSC es coherente con el archivo de configuración de sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52433-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="52433-144">A continuación se muestra un ejemplo de configuración de DSC de un módulo de mantenimiento general del servidor.</span><span class="sxs-lookup"><span data-stu-id="52433-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="52433-145">Supone que un módulo de PowerShell válido que contiene las funcionalidades de rol se encuentra en el recurso compartido de archivos `\\myfileshare\JEA`.</span><span class="sxs-lookup"><span data-stu-id="52433-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

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

<span data-ttu-id="52433-146">Después, esta configuración se aplica en un sistema mediante la invocación directa del [administrador de configuración local](/powershell/dsc/managing-nodes/metaConfig) o la actualización de la [configuración del servidor de extracción](/powershell/dsc/pull-server/pullServer).</span><span class="sxs-lookup"><span data-stu-id="52433-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="52433-147">El recurso de DSC también permite reemplazar el punto de conexión de **Microsoft.PowerShell** predeterminado.</span><span class="sxs-lookup"><span data-stu-id="52433-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="52433-148">Cuando se reemplaza, el recurso registra de forma automática un punto de conexión de reserva denominado **Microsoft.PowerShell.Restricted**.</span><span class="sxs-lookup"><span data-stu-id="52433-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="52433-149">El punto de conexión de reserva tiene la ACL de WinRM predeterminada que permite el acceso a los miembros del grupo Usuarios de administración remota y Administradores local.</span><span class="sxs-lookup"><span data-stu-id="52433-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="52433-150">Anular el registro de configuraciones de JEA</span><span class="sxs-lookup"><span data-stu-id="52433-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="52433-151">El cmdlet [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) quita un punto de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="52433-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="52433-152">Si anula el registro de un punto de conexión de JEA, evitará que nuevos usuarios creen sesiones de JEA en el sistema.</span><span class="sxs-lookup"><span data-stu-id="52433-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="52433-153">También permite actualizar una configuración de JEA al volver a registrar un archivo de configuración de sesión actualizado con el mismo nombre de punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="52433-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="52433-154">Anular el registro de un punto de conexión de JEA provocará que se reinicie el servicio WinRM.</span><span class="sxs-lookup"><span data-stu-id="52433-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="52433-155">Esto interrumpe la mayoría de las operaciones de administración remotas en curso, incluidas otras sesiones de PowerShell, invocaciones de WMI y algunas herramientas de administración.</span><span class="sxs-lookup"><span data-stu-id="52433-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="52433-156">Anule el registro de puntos de conexión de PowerShell solo durante ventanas de mantenimiento planificadas.</span><span class="sxs-lookup"><span data-stu-id="52433-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="52433-157">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="52433-157">Next steps</span></span>

[<span data-ttu-id="52433-158">Probar el punto de conexión de JEA</span><span class="sxs-lookup"><span data-stu-id="52433-158">Test the JEA endpoint</span></span>](using-jea.md)
