---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,security
title: Registro de configuraciones de JEA
ms.openlocfilehash: 0684a1c7acffbccbedab9dba4689611a24c8ae25
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="4a3c4-103">Registro de configuraciones de JEA</span><span class="sxs-lookup"><span data-stu-id="4a3c4-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="4a3c4-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4a3c4-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4a3c4-105">El último paso antes de poder usar JEA una vez que ha creado las [funcionalidades de rol](role-capabilities.md) y el [archivo de configuración de sesión](session-configurations.md) es registrar el punto de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-105">The last step before you can use JEA once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created is to register the JEA endpoint.</span></span>
<span data-ttu-id="4a3c4-106">Este proceso aplica la información de configuración de sesión en el sistema y pone el punto de conexión a disposición de los usuarios y los motores de automatización.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-106">This process applies the session configuration information to the system and makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="4a3c4-107">Configuración de la máquina sencilla</span><span class="sxs-lookup"><span data-stu-id="4a3c4-107">Single machine configuration</span></span>

<span data-ttu-id="4a3c4-108">Para entornos pequeños, puede implementar JEA al registrar el archivo de configuración de sesión mediante el cmdlet [Register-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="4a3c4-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="4a3c4-109">Antes de comenzar, asegúrese de que se cumplen los requisitos previos siguientes:</span><span class="sxs-lookup"><span data-stu-id="4a3c4-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="4a3c4-110">Se han creado uno o varios roles y se han colocado en la carpeta "RoleCapabilities" de un módulo de PowerShell válido.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="4a3c4-111">Se ha creado y probado un archivo de configuración de sesión.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="4a3c4-112">El usuario que registra la configuración de JEA tiene derechos de administrador en los sistemas.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="4a3c4-113">También debe seleccionar un nombre para el punto de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-113">You will also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="4a3c4-114">El nombre del punto de conexión de JEA será necesario cuando los usuarios quieran conectarse al sistema mediante JEA.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-114">The name of the JEA endpoint will be required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="4a3c4-115">Puede usar el cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) para comprobar los nombres de los puntos de conexión existentes en el sistema.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="4a3c4-116">Los puntos de conexión que empiezan por "microsoft" se entregan normalmente con Windows.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="4a3c4-117">El punto de conexión "microsoft.powershell" es el que se usa de manera predeterminada al conectarse a un punto de conexión remoto de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="4a3c4-118">Cuando haya determinado un nombre adecuado para el punto de conexión de JEA, ejecute el siguiente comando para registrarlo.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="4a3c4-119">El comando anterior reiniciará el servicio WinRM en el sistema.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-119">The above command will restart the WinRM service on the system.</span></span>
> <span data-ttu-id="4a3c4-120">Esto finalizará todas las sesiones de comunicación remota de PowerShell, así como las configuraciones de DSC en curso.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-120">This will terminate all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="4a3c4-121">Se recomienda que desconecte todas las máquinas de producción antes de ejecutar el comando para evitar interrumpir operaciones empresariales.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="4a3c4-122">Si el registro se realiza correctamente, está listo para [usar JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="4a3c4-122">If registration was successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="4a3c4-123">Puede eliminar el archivo de configuración de sesión en cualquier momento; no se usará después del registro.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-123">You may delete the session configuration file at any time; it is not used after registration.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="4a3c4-124">Configuración de varios equipos con DSC</span><span class="sxs-lookup"><span data-stu-id="4a3c4-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="4a3c4-125">Si va a implementar JEA en varios equipos, el modelo de implementación más sencillo es usar el recurso de [configuración de estado deseado](https://msdn.microsoft.com/en-us/powershell/dsc/overview) de JEA para implementar JEA en todos los equipos de forma rápida y coherente.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/en-us/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="4a3c4-126">Para implementar JEA con DSC, debe asegurarse de que se cumplen los requisitos previos siguientes:</span><span class="sxs-lookup"><span data-stu-id="4a3c4-126">To deploy JEA with DSC, you will need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="4a3c4-127">Se han creado una o varias funcionalidades de rol y se han agregado a un módulo de PowerShell válido.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="4a3c4-128">El módulo de PowerShell que contiene los roles se almacena en un recurso compartido de archivo (de solo lectura) al que pueden obtener acceso todos los equipos.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="4a3c4-129">Se ha determinado la configuración de la sesión.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="4a3c4-130">No es necesario crear un archivo de configuración de sesión cuando se usa el recurso DSC de JEA.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="4a3c4-131">Tiene credenciales que le permitirán realizar acciones administrativas en todos los equipos, o tiene acceso a un servidor de extracción de DSC usado para administrar los equipos.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-131">You have credentials that will allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="4a3c4-132">Ha descargado el [recurso de DSC de JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span><span class="sxs-lookup"><span data-stu-id="4a3c4-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="4a3c4-133">En un equipo de destino (o servidor de incorporación de cambios, si usa uno), cree una configuración de DSC para el punto de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="4a3c4-134">En esta configuración, usará el recurso de DSC JustEnoughAdministration para configurar el archivo de configuración de sesión y el recurso de archivos para copiar a través de las funcionalidades de rol desde el recurso compartido de archivos.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-134">In this configuration, you will use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="4a3c4-135">Se pueden configurar las siguientes propiedades con el recurso de DSC:</span><span class="sxs-lookup"><span data-stu-id="4a3c4-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="4a3c4-136">Definiciones de roles</span><span class="sxs-lookup"><span data-stu-id="4a3c4-136">Role Definitions</span></span>
- <span data-ttu-id="4a3c4-137">Grupos de cuenta virtual</span><span class="sxs-lookup"><span data-stu-id="4a3c4-137">Virtual Account groups</span></span>
- <span data-ttu-id="4a3c4-138">Nombre de cuenta de servicio administrada de grupo</span><span class="sxs-lookup"><span data-stu-id="4a3c4-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="4a3c4-139">Directorio de transcripciones</span><span class="sxs-lookup"><span data-stu-id="4a3c4-139">Transcript directory</span></span>
- <span data-ttu-id="4a3c4-140">Unidad de usuario</span><span class="sxs-lookup"><span data-stu-id="4a3c4-140">User drive</span></span>
- <span data-ttu-id="4a3c4-141">Reglas de acceso condicional</span><span class="sxs-lookup"><span data-stu-id="4a3c4-141">Conditional access rules</span></span>
- <span data-ttu-id="4a3c4-142">Scripts de inicio de la sesión de JEA</span><span class="sxs-lookup"><span data-stu-id="4a3c4-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="4a3c4-143">La sintaxis de cada una de estas propiedades en una configuración de DSC es coherente con el archivo de configuración de sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="4a3c4-144">A continuación se muestra un ejemplo de configuración de DSC de un módulo de mantenimiento general del servidor.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="4a3c4-145">Supone que un módulo de PowerShell válido que contiene las funcionalidades de rol en una subcarpeta "RoleCapabilities" se encuentra en el recurso compartido de archivos "\\\\mirecursocompartidodearchivos\\JEA".</span><span class="sxs-lookup"><span data-stu-id="4a3c4-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="4a3c4-146">Después, se puede aplicar esta configuración en un sistema al [invocar directamente el administrador de configuración local](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) o actualizar la [configuración del servidor de incorporación de cambios](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).</span><span class="sxs-lookup"><span data-stu-id="4a3c4-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="4a3c4-147">El recurso de DSC también permite reemplazar el punto de conexión de comunicación remota Microsoft.PowerShell predeterminado.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="4a3c4-148">Si lo hace, el recurso registrará de forma automática un punto de conexión sin restricciones de copia de seguridad denominado "Microsoft.PowerShell.Restricted", que tiene la ACL de WinRM predeterminada (que permite que los miembros del grupo de administradores locales y Usuarios de administración remota obtengan acceso a él).</span><span class="sxs-lookup"><span data-stu-id="4a3c4-148">If you do this, the resource will automatically register a backup unconstrainted endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="4a3c4-149">Anular el registro de configuraciones de JEA</span><span class="sxs-lookup"><span data-stu-id="4a3c4-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="4a3c4-150">Para quitar un punto de conexión de JEA de un sistema, use el cmdlet [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration).</span><span class="sxs-lookup"><span data-stu-id="4a3c4-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="4a3c4-151">Si anula el registro de un punto de conexión de JEA, evitará que nuevos usuarios creen nuevas sesiones de JEA en el sistema.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-151">Unregistering a JEA endpoint will prevent new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="4a3c4-152">También permite actualizar una configuración de JEA al volver a registrar un archivo de configuración de sesión actualizado con el mismo nombre de punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="4a3c4-153">Anular el registro de un punto de conexión de JEA provocará que se reinicie el servicio WinRM.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-153">Unregistering a JEA endpoint will cause the WinRM service to restart.</span></span>
> <span data-ttu-id="4a3c4-154">Esto interrumpirá la mayoría de las operaciones de administración remotas en curso, incluidas otras sesiones de PowerShell, invocaciones de WMI y algunas herramientas de administración.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-154">This will interrupt most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="4a3c4-155">Anule el registro de puntos de conexión de PowerShell solo durante ventanas de mantenimiento planificadas.</span><span class="sxs-lookup"><span data-stu-id="4a3c4-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4a3c4-156">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="4a3c4-156">Next steps</span></span>

- [<span data-ttu-id="4a3c4-157">Probar el punto de conexión de JEA</span><span class="sxs-lookup"><span data-stu-id="4a3c4-157">Test the JEA endpoint</span></span>](using-jea.md)

