---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Configuraciones de sesión de JEA
ms.openlocfilehash: 1b598522d43b2c1a26a739a67cee5181b21a7c32
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655470"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="36519-103">Configuraciones de sesión de JEA</span><span class="sxs-lookup"><span data-stu-id="36519-103">JEA Session Configurations</span></span>

> <span data-ttu-id="36519-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="36519-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="36519-105">Un punto de conexión de JEA se registra en un sistema al crear y registrar un archivo de configuración de sesión de PowerShell de una forma específica.</span><span class="sxs-lookup"><span data-stu-id="36519-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="36519-106">Las configuraciones de sesión determinan *quién* puede usar el punto de conexión de JEA y qué roles tendrán acceso a él.</span><span class="sxs-lookup"><span data-stu-id="36519-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="36519-107">También definen la configuración global que se aplica a los usuarios de cualquier rol en la sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="36519-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="36519-108">En este tema, se describe cómo crear un archivo de configuración de sesión de PowerShell y cómo registrar un punto de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="36519-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="36519-109">Crear un archivo de configuración de sesión</span><span class="sxs-lookup"><span data-stu-id="36519-109">Create a session configuration file</span></span>

<span data-ttu-id="36519-110">Para registrar un punto de conexión de JEA, debe especificar cómo se debe configurar ese punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="36519-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="36519-111">Hay muchas opciones que se deben tener en cuenta, la más importante de ellas es quién debe tener acceso al punto de conexión de JEA, qué roles se le asignarán, qué identidad usará JEA a un nivel más profundo y cuál será el nombre del punto de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="36519-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="36519-112">Todas ellas se definen en un archivo de configuración de sesión de PowerShell, que es un archivo de datos de PowerShell que finaliza con una extensión .pssc.</span><span class="sxs-lookup"><span data-stu-id="36519-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="36519-113">Para crear un archivo de configuración de sesión esqueleto para puntos de conexión de JEA, ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="36519-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="36519-114">En el archivo esqueleto solo se incluyen de forma predeterminada las opciones de configuración más comunes.</span><span class="sxs-lookup"><span data-stu-id="36519-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="36519-115">Use el conmutador `-Full` para incluir todas las opciones aplicables en el PSSC generado.</span><span class="sxs-lookup"><span data-stu-id="36519-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="36519-116">Puede abrir el archivo de configuración de sesión en cualquier editor de texto.</span><span class="sxs-lookup"><span data-stu-id="36519-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="36519-117">El campo `-SessionType RestrictedRemoteServer` indica que JEA usará la configuración de sesión para administrarla de forma segura.</span><span class="sxs-lookup"><span data-stu-id="36519-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="36519-118">Las sesiones configuradas de esta forma funcionarán en [modo NoLanguage](https://technet.microsoft.com/library/dn433292.aspx) y solo tendrán los siguientes 8 comandos (y alias) predeterminados disponibles:</span><span class="sxs-lookup"><span data-stu-id="36519-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="36519-119">Clear-Host (cls, clear)</span><span class="sxs-lookup"><span data-stu-id="36519-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="36519-120">Exit-PSSession (exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="36519-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="36519-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="36519-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="36519-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="36519-122">Get-FormatData</span></span>
- <span data-ttu-id="36519-123">Get-Help</span><span class="sxs-lookup"><span data-stu-id="36519-123">Get-Help</span></span>
- <span data-ttu-id="36519-124">Measure-Object (measure)</span><span class="sxs-lookup"><span data-stu-id="36519-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="36519-125">Out-Default</span><span class="sxs-lookup"><span data-stu-id="36519-125">Out-Default</span></span>
- <span data-ttu-id="36519-126">Select-Object (select)</span><span class="sxs-lookup"><span data-stu-id="36519-126">Select-Object (select)</span></span>

<span data-ttu-id="36519-127">No hay ningún proveedor de PowerShell disponible, ni tampoco ningún programa externo (ejecutables, scripts, etc.).</span><span class="sxs-lookup"><span data-stu-id="36519-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="36519-128">Hay otros campos que querrá configurar para la sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="36519-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="36519-129">Se tratan en las siguientes secciones.</span><span class="sxs-lookup"><span data-stu-id="36519-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="36519-130">Elegir la identidad de JEA</span><span class="sxs-lookup"><span data-stu-id="36519-130">Choose the JEA identity</span></span>

<span data-ttu-id="36519-131">En segundo plano, JEA necesita una identidad (cuenta) para usarla al ejecutar los comandos de un usuario conectado.</span><span class="sxs-lookup"><span data-stu-id="36519-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="36519-132">Usted decide qué identidad usará JEA en el archivo de configuración de sesión.</span><span class="sxs-lookup"><span data-stu-id="36519-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="36519-133">Cuenta virtual local</span><span class="sxs-lookup"><span data-stu-id="36519-133">Local Virtual Account</span></span>

<span data-ttu-id="36519-134">Si los roles compatibles con este punto de conexión de JEA se usan para administrar el equipo local y una cuenta de administrador local es suficiente para ejecutar los comandos correctamente, debe configurar JEA para que use una cuenta virtual local.</span><span class="sxs-lookup"><span data-stu-id="36519-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands succesfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="36519-135">Las cuentas virtuales son cuentas temporales que son únicas para un usuario específico y solo duran lo mismo que la sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36519-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="36519-136">En un servidor miembro o estación de trabajo, las cuentas virtuales pertenecen al grupo **Administradores** del equipo local y tienen acceso a la mayoría de recursos del sistema.</span><span class="sxs-lookup"><span data-stu-id="36519-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="36519-137">En un controlador de dominio de Active Directory, las cuentas virtuales pertenecen al grupo **Administradores de dominio**.</span><span class="sxs-lookup"><span data-stu-id="36519-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="36519-138">Si los roles compatibles con la configuración de sesión no requieren esos privilegios amplios, también puede especificar los grupos de seguridad a los que pertenecerá la cuenta virtual.</span><span class="sxs-lookup"><span data-stu-id="36519-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="36519-139">En un servidor miembro o estación de trabajo, los grupos de seguridad especificados deben ser grupos locales, no grupos de un dominio.</span><span class="sxs-lookup"><span data-stu-id="36519-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="36519-140">Cuando se especifiquen uno o varios grupos de seguridad, la cuenta virtual ya no pertenecerá al grupo de administradores local o de dominio.</span><span class="sxs-lookup"><span data-stu-id="36519-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```
> [!NOTE]
> <span data-ttu-id="36519-141">Las cuentas virtuales se conceden temporalmente el inicio de sesión como servicio en la directiva de seguridad del servidor local.</span><span class="sxs-lookup"><span data-stu-id="36519-141">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span>  <span data-ttu-id="36519-142">Si uno de los VirtualAccountGroups especificado ya se ha concedido este derecho en la directiva, la cuenta virtual individual ya no se agregará y se quitará de la directiva.</span><span class="sxs-lookup"><span data-stu-id="36519-142">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span>  <span data-ttu-id="36519-143">Esto puede ser útil en escenarios como los controladores de dominio donde estrechamente se auditan las revisiones de la directiva de seguridad del controlador de dominio.</span><span class="sxs-lookup"><span data-stu-id="36519-143">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span>  <span data-ttu-id="36519-144">Esto solo está disponible en Windows Server 2016 con la de noviembre de 2018 o paquete acumulativo de actualizaciones posteriores y Windows Server 2019 con la de enero de 2019 o paquete acumulativo de actualizaciones posteriores.</span><span class="sxs-lookup"><span data-stu-id="36519-144">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="36519-145">Cuenta de servicio administrada de grupo</span><span class="sxs-lookup"><span data-stu-id="36519-145">Group Managed Service Account</span></span>


<span data-ttu-id="36519-146">Para los escenarios que requieren que el usuario de JEA obtenga acceso a recursos de red como otros equipos o servicios web, la identidad más apropiada que se puede usar es una cuenta de servicio administrada de grupo (gMSA).</span><span class="sxs-lookup"><span data-stu-id="36519-146">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="36519-147">Las cuentas gMSA proporcionan una identidad de dominio que se puede usar para autenticarse en recursos en cualquier equipo del dominio.</span><span class="sxs-lookup"><span data-stu-id="36519-147">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="36519-148">Los derechos que le proporciona la cuenta gMSA se determinan según los recursos a los que obtenga acceso.</span><span class="sxs-lookup"><span data-stu-id="36519-148">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="36519-149">No tendrá derechos de administrador en los equipos o servicios de forma automática a menos que el administrador del equipo o servicio haya concedido de forma explícita privilegios de administrador a la cuenta gMSA.</span><span class="sxs-lookup"><span data-stu-id="36519-149">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="36519-150">Las cuentas gMSA solo deben usarse cuando se necesite acceso a recursos de red por diversas razones:</span><span class="sxs-lookup"><span data-stu-id="36519-150">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="36519-151">Es más difícil realizar un seguimiento de las acciones hasta el usuario al usar una cuenta gMSA ya que todos los usuarios comparten la misma identidad de ejecución.</span><span class="sxs-lookup"><span data-stu-id="36519-151">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="36519-152">Deberá consultar los registros y transcripciones de la sesión de PowerShell para poner en correlación a los usuarios con sus acciones.</span><span class="sxs-lookup"><span data-stu-id="36519-152">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="36519-153">La cuenta gMSA puede tener acceso a muchos recursos de red a los que el usuario que se conecta no necesita acceso.</span><span class="sxs-lookup"><span data-stu-id="36519-153">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="36519-154">Intente limitar siempre los permisos efectivos en una sesión de JEA para seguir el principio de privilegios mínimos.</span><span class="sxs-lookup"><span data-stu-id="36519-154">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="36519-155">Las cuentas de servicio administradas de grupo solo están disponibles en Windows PowerShell 5.1 o una versión posterior y en equipos unidos a un dominio.</span><span class="sxs-lookup"><span data-stu-id="36519-155">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>


#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="36519-156">Más información sobre los usuarios de ejecución</span><span class="sxs-lookup"><span data-stu-id="36519-156">More information about run as users</span></span>

<span data-ttu-id="36519-157">Puede encontrar información adicional sobre las identidades de ejecución y cómo encajan en la seguridad de una sesión de JEA en el artículo sobre [consideraciones de seguridad](security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="36519-157">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="36519-158">Transcripciones de sesión</span><span class="sxs-lookup"><span data-stu-id="36519-158">Session transcripts</span></span>

<span data-ttu-id="36519-159">Es recomendable que configure un archivo de configuración de sesión de JEA para registrar de forma automática las transcripciones de las sesiones de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="36519-159">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="36519-160">Las transcripciones de sesión de PowerShell contienen información sobre el usuario que se conecta, la identidad de ejecución asignada y los comandos que ha ejecutado el usuario.</span><span class="sxs-lookup"><span data-stu-id="36519-160">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="36519-161">Pueden ser útiles para un equipo de auditoría que necesite saber quién ha realizado un cambio específico en un sistema.</span><span class="sxs-lookup"><span data-stu-id="36519-161">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="36519-162">Para configurar la transcripción automática en el archivo de configuración de sesión, proporcione una ruta de acceso a una carpeta en que se almacenarán las transcripciones.</span><span class="sxs-lookup"><span data-stu-id="36519-162">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="36519-163">La carpeta especificada debe configurarse para evitar que los usuarios modifiquen o eliminen los datos en ella.</span><span class="sxs-lookup"><span data-stu-id="36519-163">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="36519-164">La cuenta de sistema local, que requiere acceso de lectura y escritura al directorio, escribe las transcripciones en la carpeta.</span><span class="sxs-lookup"><span data-stu-id="36519-164">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="36519-165">Los usuarios estándar no deben tener acceso a la carpeta y un conjunto limitado de administradores de seguridad debe tener acceso para auditar las transcripciones.</span><span class="sxs-lookup"><span data-stu-id="36519-165">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="36519-166">Unidad de usuario</span><span class="sxs-lookup"><span data-stu-id="36519-166">User drive</span></span>

<span data-ttu-id="36519-167">Si los usuarios que se conectan necesitan copiar archivos desde o al punto de conexión de JEA para ejecutar un comando, puede habilitar la unidad de usuario en el archivo de configuración de sesión.</span><span class="sxs-lookup"><span data-stu-id="36519-167">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="36519-168">La unidad de usuario es una [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) que se asigna a una carpeta única para cada usuario que se conecta.</span><span class="sxs-lookup"><span data-stu-id="36519-168">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="36519-169">Esta carpeta sirve como espacio para que puedan copiar archivos del o en el sistema, sin concederles acceso al sistema de archivos completo ni exponer el proveedor FileSystem.</span><span class="sxs-lookup"><span data-stu-id="36519-169">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="36519-170">El contenido de la unidad de usuario es persistente en todas las sesiones para adaptarse a situaciones en que se podría interrumpir la conectividad de red.</span><span class="sxs-lookup"><span data-stu-id="36519-170">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="36519-171">De manera predeterminada, la unidad de usuario le permite almacenar un máximo de 50 MB de datos por usuario.</span><span class="sxs-lookup"><span data-stu-id="36519-171">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="36519-172">Puede limitar la cantidad de datos que puede consumir un usuario con el campo *UserDriveMaximumSize*.</span><span class="sxs-lookup"><span data-stu-id="36519-172">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="36519-173">Si no quiere que los datos en la unidad de usuario sean persistentes, puede configurar una tarea programada en el sistema para limpiar la carpeta de forma automática cada noche.</span><span class="sxs-lookup"><span data-stu-id="36519-173">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="36519-174">La unidad de usuario solo está disponible en Windows PowerShell 5.1 o una versión posterior.</span><span class="sxs-lookup"><span data-stu-id="36519-174">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="36519-175">Definiciones de roles</span><span class="sxs-lookup"><span data-stu-id="36519-175">Role definitions</span></span>

<span data-ttu-id="36519-176">Las definiciones de roles en un archivo de configuración de sesión definen la asignación de *usuarios* a *roles*.</span><span class="sxs-lookup"><span data-stu-id="36519-176">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="36519-177">De forma automática, se le concederá permiso a cada usuario o grupo incluido en este campo al punto de conexión de JEA cuando se registre.</span><span class="sxs-lookup"><span data-stu-id="36519-177">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="36519-178">Cada usuario o grupo puede incluirse como una clave en la tabla hash solo una vez, pero se le pueden asignar varios roles.</span><span class="sxs-lookup"><span data-stu-id="36519-178">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="36519-179">El nombre de la funcionalidad de rol debe ser el nombre del archivo de funcionalidad de rol, sin la extensión .psrc.</span><span class="sxs-lookup"><span data-stu-id="36519-179">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="36519-180">Si un usuario pertenece a más de un grupo en la definición de rol, obtendrá acceso a los roles de cada uno.</span><span class="sxs-lookup"><span data-stu-id="36519-180">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="36519-181">Si dos roles conceden acceso a los mismos cmdlets, se concederá al usuario el conjunto de parámetros más permisivo.</span><span class="sxs-lookup"><span data-stu-id="36519-181">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="36519-182">Al especificar usuarios o grupos locales en el campo de las definiciones de rol, asegúrese de utilizar el nombre del equipo (no *localhost* o *.*) antes de la barra diagonal inversa.</span><span class="sxs-lookup"><span data-stu-id="36519-182">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="36519-183">Puede comprobar el nombre del equipo observando la variable `$env:computername`.</span><span class="sxs-lookup"><span data-stu-id="36519-183">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="36519-184">Orden de búsqueda de funcionalidad de rol</span><span class="sxs-lookup"><span data-stu-id="36519-184">Role capability search order</span></span>
<span data-ttu-id="36519-185">Tal como se muestra en el ejemplo anterior, el nombre sin formato (nombre de archivo sin la extensión) del archivo de funcionalidad de rol hace referencia a las funcionalidades de rol.</span><span class="sxs-lookup"><span data-stu-id="36519-185">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="36519-186">Si hay varias funcionalidades de rol disponibles en el sistema con el mismo nombre sin formato, PowerShell usará su orden de búsqueda implícito para seleccionar el archivo de funcionalidad de rol adecuado.</span><span class="sxs-lookup"><span data-stu-id="36519-186">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="36519-187">**No** proporcionará acceso a todos los archivos de funcionalidad de rol con el mismo nombre.</span><span class="sxs-lookup"><span data-stu-id="36519-187">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="36519-188">JEA utiliza la variable de entorno `$env:PSModulePath` para determinar qué rutas de acceso examinar para archivos de capacidad de rol.</span><span class="sxs-lookup"><span data-stu-id="36519-188">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="36519-189">Dentro de cada una de esas rutas de acceso, JEA buscará módulos válidos de PowerShell que contengan una subcarpeta "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="36519-189">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="36519-190">Al igual que con la importación de módulos, JEA prefiere funcionalidades de rol que se suministran con Windows a capacidades de rol personalizadas con el mismo nombre.</span><span class="sxs-lookup"><span data-stu-id="36519-190">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="36519-191">Para todos los demás conflictos de nomenclatura, la precedencia se determina por el orden en el que Windows enumera los archivos en el directorio (sin garantizar el orden alfabético).</span><span class="sxs-lookup"><span data-stu-id="36519-191">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="36519-192">El primer archivo de funcionalidad de rol que coincida con el nombre deseado se usará para el usuario que se conecta.</span><span class="sxs-lookup"><span data-stu-id="36519-192">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="36519-193">Puesto que el orden de búsqueda de la funcionalidad de rol no es determinista cuando dos o más funcionalidades de rol comparten el mismo nombre, se **recomienda encarecidamente** que se asegure de que las funcionalidades de rol tienen nombres únicos en el equipo.</span><span class="sxs-lookup"><span data-stu-id="36519-193">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="36519-194">Reglas de acceso condicional</span><span class="sxs-lookup"><span data-stu-id="36519-194">Conditional access rules</span></span>

<span data-ttu-id="36519-195">De forma automática, se concede acceso a los puntos de conexión de JEA a todos los usuarios y grupos incluidos en el campo RoleDefinitions.</span><span class="sxs-lookup"><span data-stu-id="36519-195">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="36519-196">Las reglas de acceso condicional le permiten restringir este acceso y requieren que los usuarios pertenezcan a grupos de seguridad adicionales que no afecten a los roles a los que están asignados.</span><span class="sxs-lookup"><span data-stu-id="36519-196">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="36519-197">Esto puede ser útil si quiere integrar una solución de administración de acceso con privilegios "Just-In-Time", autenticación de tarjeta inteligente u otra solución de autenticación multifactor con JEA.</span><span class="sxs-lookup"><span data-stu-id="36519-197">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="36519-198">Las reglas de acceso condicional se definen en el campo RequiredGroups en un archivo de configuración de sesión.</span><span class="sxs-lookup"><span data-stu-id="36519-198">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="36519-199">En él, puede proporcionar una tabla hash (opcionalmente anidada) que use las claves "And" y "Or" para construir las reglas.</span><span class="sxs-lookup"><span data-stu-id="36519-199">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="36519-200">Estos son algunos ejemplos sobre cómo sacar provecho de este campo:</span><span class="sxs-lookup"><span data-stu-id="36519-200">Here are some examples of how to leverage this field:</span></span>

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
> <span data-ttu-id="36519-201">Las reglas de acceso condicional solo están disponibles en Windows PowerShell 5.1 o una versión posterior.</span><span class="sxs-lookup"><span data-stu-id="36519-201">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="36519-202">Otras propiedades</span><span class="sxs-lookup"><span data-stu-id="36519-202">Other properties</span></span>
<span data-ttu-id="36519-203">Los archivos de configuración de sesión también pueden hacer lo mismo que un archivo de funcionalidad de rol, pero sin la capacidad de proporcionar acceso a los usuarios que se conectan a distintos comandos.</span><span class="sxs-lookup"><span data-stu-id="36519-203">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="36519-204">Si quiere permitir que todos los usuarios obtengan acceso a cmdlets, funciones o proveedores específicos, puede hacerlo directamente en el archivo de configuración de sesión.</span><span class="sxs-lookup"><span data-stu-id="36519-204">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="36519-205">Para obtener una lista completa de las propiedades que se admiten en el archivo de configuración de sesión, ejecute `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="36519-205">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="36519-206">Probar un archivo de configuración de sesión</span><span class="sxs-lookup"><span data-stu-id="36519-206">Testing a session configuration file</span></span>

<span data-ttu-id="36519-207">Puede probar una configuración de sesión con el cmdlet [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile).</span><span class="sxs-lookup"><span data-stu-id="36519-207">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="36519-208">Se recomienda encarecidamente que pruebe el archivo de configuración de sesión si se ha editado el archivo pssc de forma manual mediante un editor de texto para asegurarse de que la sintaxis sea correcta.</span><span class="sxs-lookup"><span data-stu-id="36519-208">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="36519-209">Si un archivo de configuración de sesión no supera esta prueba, no podrá registrarse correctamente en el sistema.</span><span class="sxs-lookup"><span data-stu-id="36519-209">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="36519-210">Archivo de configuración de sesión de ejemplo</span><span class="sxs-lookup"><span data-stu-id="36519-210">Sample session configuration file</span></span>

<span data-ttu-id="36519-211">A continuación hay un ejemplo completo que muestra cómo crear y validar una configuración de sesión para JEA.</span><span class="sxs-lookup"><span data-stu-id="36519-211">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="36519-212">Tenga en cuenta que las definiciones de roles se crean y almacenan en la variable `$roles` para su comodidad y legibilidad.</span><span class="sxs-lookup"><span data-stu-id="36519-212">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="36519-213">No es un requisito hacerlo.</span><span class="sxs-lookup"><span data-stu-id="36519-213">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="36519-214">Actualizar los archivos de configuración de sesión</span><span class="sxs-lookup"><span data-stu-id="36519-214">Updating session configuration files</span></span>

<span data-ttu-id="36519-215">Si necesita cambiar las propiedades de una configuración de sesión de JEA, incluida la asignación de usuarios a los roles, debe [anular el registro](register-jea.md#unregistering-jea-configurations) y [volver a registrar](register-jea.md) la configuración de sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="36519-215">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="36519-216">Al volver a registrar la configuración de sesión de JEA, use un archivo de configuración de sesión de PowerShell actualizado que incluya los cambios que quiera.</span><span class="sxs-lookup"><span data-stu-id="36519-216">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="36519-217">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="36519-217">Next steps</span></span>

- [<span data-ttu-id="36519-218">Registrar una configuración de JEA</span><span class="sxs-lookup"><span data-stu-id="36519-218">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="36519-219">Crear roles de JEA</span><span class="sxs-lookup"><span data-stu-id="36519-219">Author JEA roles</span></span>](role-capabilities.md)
