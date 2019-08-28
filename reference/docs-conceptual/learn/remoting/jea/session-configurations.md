---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Configuraciones de sesión de JEA
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017736"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="80ade-103">Configuraciones de sesión de JEA</span><span class="sxs-lookup"><span data-stu-id="80ade-103">JEA Session Configurations</span></span>

<span data-ttu-id="80ade-104">Un punto de conexión de JEA se registra en un sistema mediante la creación y el registro de un archivo de configuración de sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80ade-104">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="80ade-105">Las configuraciones de sesión definen quién puede usar el punto de conexión de JEA y qué roles tienen acceso a él.</span><span class="sxs-lookup"><span data-stu-id="80ade-105">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="80ade-106">También definen la configuración global que se aplica a todos los usuarios de la sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="80ade-106">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="80ade-107">Crear un archivo de configuración de sesión</span><span class="sxs-lookup"><span data-stu-id="80ade-107">Create a session configuration file</span></span>

<span data-ttu-id="80ade-108">Para registrar un punto de conexión de JEA, debe especificar cómo se configura ese punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="80ade-108">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="80ade-109">Hay muchas opciones que tener en cuenta.</span><span class="sxs-lookup"><span data-stu-id="80ade-109">There are many options to consider.</span></span> <span data-ttu-id="80ade-110">Las más importantes son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="80ade-110">The most important options are:</span></span>

- <span data-ttu-id="80ade-111">Quién tiene acceso al punto de conexión de JEA</span><span class="sxs-lookup"><span data-stu-id="80ade-111">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="80ade-112">Qué roles se les ha asignado</span><span class="sxs-lookup"><span data-stu-id="80ade-112">Which roles they be assigned</span></span>
- <span data-ttu-id="80ade-113">Qué identidad de JEA se usa en segundo plano</span><span class="sxs-lookup"><span data-stu-id="80ade-113">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="80ade-114">El nombre del punto de conexión de JEA</span><span class="sxs-lookup"><span data-stu-id="80ade-114">The name of the JEA endpoint</span></span>

<span data-ttu-id="80ade-115">Estas opciones se definen en un archivo de datos de PowerShell con una extensión `.pssc`, denominado archivo de configuración de sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80ade-115">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="80ade-116">El archivo de configuración de sesión se puede modificar en cualquier editor de texto.</span><span class="sxs-lookup"><span data-stu-id="80ade-116">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="80ade-117">Ejecute el comando siguiente para crear un archivo de configuración de plantilla en blanco.</span><span class="sxs-lookup"><span data-stu-id="80ade-117">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="80ade-118">De forma predeterminada, en el archivo de plantilla solo se incluyen las opciones de configuración más comunes.</span><span class="sxs-lookup"><span data-stu-id="80ade-118">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="80ade-119">Use el conmutador `-Full` para incluir todas las opciones aplicables en el PSSC generado.</span><span class="sxs-lookup"><span data-stu-id="80ade-119">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="80ade-120">El campo `-SessionType RestrictedRemoteServer` indica que JEA usa la configuración de sesión para la administración segura.</span><span class="sxs-lookup"><span data-stu-id="80ade-120">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="80ade-121">Las sesiones de este tipo funcionan en modo **NoLanguage** y solo tienen acceso a los comandos (y alias) predeterminados siguientes:</span><span class="sxs-lookup"><span data-stu-id="80ade-121">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="80ade-122">Clear-Host (cls, clear)</span><span class="sxs-lookup"><span data-stu-id="80ade-122">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="80ade-123">Exit-PSSession (exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="80ade-123">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="80ade-124">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="80ade-124">Get-Command (gcm)</span></span>
- <span data-ttu-id="80ade-125">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="80ade-125">Get-FormatData</span></span>
- <span data-ttu-id="80ade-126">Get-Help</span><span class="sxs-lookup"><span data-stu-id="80ade-126">Get-Help</span></span>
- <span data-ttu-id="80ade-127">Measure-Object (measure)</span><span class="sxs-lookup"><span data-stu-id="80ade-127">Measure-Object (measure)</span></span>
- <span data-ttu-id="80ade-128">Out-Default</span><span class="sxs-lookup"><span data-stu-id="80ade-128">Out-Default</span></span>
- <span data-ttu-id="80ade-129">Select-Object (select)</span><span class="sxs-lookup"><span data-stu-id="80ade-129">Select-Object (select)</span></span>

<span data-ttu-id="80ade-130">No hay ningún proveedor de PowerShell disponible, ni tampoco ningún programa externo (ejecutables o scripts).</span><span class="sxs-lookup"><span data-stu-id="80ade-130">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="80ade-131">Para obtener más información sobre los modos de lenguaje, vea [Acerca de los modos de lenguaje](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span><span class="sxs-lookup"><span data-stu-id="80ade-131">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="80ade-132">Elegir la identidad de JEA</span><span class="sxs-lookup"><span data-stu-id="80ade-132">Choose the JEA identity</span></span>

<span data-ttu-id="80ade-133">En segundo plano, JEA necesita una identidad (cuenta) para usarla al ejecutar los comandos de un usuario conectado.</span><span class="sxs-lookup"><span data-stu-id="80ade-133">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="80ade-134">En el archivo de configuración de sesión se define qué identidad usa JEA.</span><span class="sxs-lookup"><span data-stu-id="80ade-134">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="80ade-135">Cuenta virtual local</span><span class="sxs-lookup"><span data-stu-id="80ade-135">Local Virtual Account</span></span>

<span data-ttu-id="80ade-136">Las cuentas virtuales locales son útiles cuando todos los roles definidos para el punto de conexión de JEA se usan para administrar el equipo local y una cuenta de administrador local es suficiente para ejecutar los comandos de forma correcta.</span><span class="sxs-lookup"><span data-stu-id="80ade-136">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="80ade-137">Las cuentas virtuales son cuentas temporales que son únicas para un usuario específico y solo duran lo mismo que la sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80ade-137">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="80ade-138">En un servidor miembro o estación de trabajo, las cuentas virtuales pertenecen al grupo **Administradores** del equipo local.</span><span class="sxs-lookup"><span data-stu-id="80ade-138">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="80ade-139">En un controlador de dominio de Active Directory, las cuentas virtuales pertenecen al grupo **Administradores de dominio**.</span><span class="sxs-lookup"><span data-stu-id="80ade-139">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="80ade-140">Si los roles definidos por la configuración de sesión no requieren privilegios administrativos completos, puede especificar los grupos de seguridad a los que pertenecerá la cuenta virtual.</span><span class="sxs-lookup"><span data-stu-id="80ade-140">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="80ade-141">En un servidor miembro o estación de trabajo, los grupos de seguridad especificados deben ser grupos locales, no grupos de un dominio.</span><span class="sxs-lookup"><span data-stu-id="80ade-141">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="80ade-142">Cuando se especifican uno o varios grupos de seguridad, la cuenta virtual no se asigna al grupo de administradores local o de dominio.</span><span class="sxs-lookup"><span data-stu-id="80ade-142">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="80ade-143">Las cuentas virtuales se conceden temporalmente en el inicio de sesión como derecho de servicio en la directiva de seguridad del servidor local.</span><span class="sxs-lookup"><span data-stu-id="80ade-143">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="80ade-144">Si a uno de los VirtualAccountGroups especificados ya se le ha concedido este derecho en la directiva, la cuenta virtual individual ya no se agregará y se quitará de la directiva.</span><span class="sxs-lookup"><span data-stu-id="80ade-144">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="80ade-145">Esto puede ser útil en escenarios como los controladores de dominio, donde se auditan estrechamente las revisiones de la directiva de seguridad del controlador de dominio.</span><span class="sxs-lookup"><span data-stu-id="80ade-145">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="80ade-146">Esto solo está disponible en Windows Server 2016 con el paquete acumulativo de revisiones de noviembre de 2018 o un paquete posterior y en Windows Server 2019 con el paquete acumulativo de revisiones de enero de 2019 o un paquete posterior.</span><span class="sxs-lookup"><span data-stu-id="80ade-146">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="80ade-147">Cuenta de servicio administrada de grupo</span><span class="sxs-lookup"><span data-stu-id="80ade-147">Group-managed service account</span></span>

<span data-ttu-id="80ade-148">Una cuenta de servicio administrada de grupo (GMSA) es la identidad adecuada para usarla cuando los usuarios de JEA tienen que acceder a recursos de red como recursos compartidos de archivos y servicios web.</span><span class="sxs-lookup"><span data-stu-id="80ade-148">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="80ade-149">Las cuentas GMSA proporcionan una identidad de dominio que se usa para autenticarse con recursos de cualquier equipo del dominio.</span><span class="sxs-lookup"><span data-stu-id="80ade-149">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="80ade-150">Los derechos que proporciona una GMSA están determinados por los recursos a los que se accede.</span><span class="sxs-lookup"><span data-stu-id="80ade-150">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="80ade-151">No tiene derechos de administrador en ningún equipo o servicio a menos que el administrador del equipo o servicio haya concedido de forma explícita esos privilegios a la cuenta GMSA.</span><span class="sxs-lookup"><span data-stu-id="80ade-151">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="80ade-152">Las GMSA solo se deben usar cuando sea necesario:</span><span class="sxs-lookup"><span data-stu-id="80ade-152">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="80ade-153">Cuando se usa una GMSA, es difícil realizar el seguimiento de las acciones hasta un usuario.</span><span class="sxs-lookup"><span data-stu-id="80ade-153">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="80ade-154">Todos los usuarios comparten la misma identidad de ejecución.</span><span class="sxs-lookup"><span data-stu-id="80ade-154">Every user shares the same run-as identity.</span></span> <span data-ttu-id="80ade-155">Tendrá que revisar los registros y las transcripciones de la sesión de PowerShell para poner en correlación a los usuarios individuales con sus acciones.</span><span class="sxs-lookup"><span data-stu-id="80ade-155">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="80ade-156">La GMSA puede tener acceso a muchos recursos de red a los que el usuario que se conecta no necesita acceso.</span><span class="sxs-lookup"><span data-stu-id="80ade-156">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="80ade-157">Intente limitar siempre los permisos efectivos en una sesión de JEA para seguir el principio de privilegios mínimos.</span><span class="sxs-lookup"><span data-stu-id="80ade-157">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="80ade-158">Las cuentas de servicio administradas de grupo solo están disponibles en equipos unidos a un dominio en los que se usa PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="80ade-158">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="80ade-159">Para obtener más información sobre cómo proteger una sesión de JEA, vea el artículo sobre [consideraciones de seguridad](security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="80ade-159">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="80ade-160">Transcripciones de sesión</span><span class="sxs-lookup"><span data-stu-id="80ade-160">Session transcripts</span></span>

<span data-ttu-id="80ade-161">Es recomendable configurar un punto de conexión de JEA para registrar de forma automática las transcripciones de las sesiones de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="80ade-161">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="80ade-162">Las transcripciones de sesión de PowerShell contienen información sobre el usuario que se conecta, la identidad de ejecución asignada y los comandos que ha ejecutado el usuario.</span><span class="sxs-lookup"><span data-stu-id="80ade-162">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="80ade-163">Pueden ser útiles para un equipo de auditoría que necesite saber quién ha realizado un cambio específico en un sistema.</span><span class="sxs-lookup"><span data-stu-id="80ade-163">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="80ade-164">Para configurar la transcripción automática en el archivo de configuración de sesión, proporcione una ruta de acceso a una carpeta en que se almacenarán las transcripciones.</span><span class="sxs-lookup"><span data-stu-id="80ade-164">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="80ade-165">La cuenta de **sistema local**, que requiere acceso de lectura y escritura al directorio, escribe las transcripciones en la carpeta.</span><span class="sxs-lookup"><span data-stu-id="80ade-165">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="80ade-166">Los usuarios estándar no deben tener acceso a la carpeta.</span><span class="sxs-lookup"><span data-stu-id="80ade-166">Standard users should have no access to the folder.</span></span> <span data-ttu-id="80ade-167">Limite el número de administradores de seguridad que tienen acceso para auditar las transcripciones.</span><span class="sxs-lookup"><span data-stu-id="80ade-167">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="80ade-168">Unidad de usuario</span><span class="sxs-lookup"><span data-stu-id="80ade-168">User drive</span></span>

<span data-ttu-id="80ade-169">Si los usuarios que se conectan necesitan copiar archivos desde o al punto de conexión de JEA, puede habilitar la unidad de usuario en el archivo de configuración de sesión.</span><span class="sxs-lookup"><span data-stu-id="80ade-169">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="80ade-170">La unidad de usuario es una **PSDrive** que se asigna a una carpeta única para cada usuario que se conecta.</span><span class="sxs-lookup"><span data-stu-id="80ade-170">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="80ade-171">Esta carpeta permite a los usuarios copiar archivos en o desde el sistema, sin concederles acceso al sistema de archivos completo ni exponer el proveedor FileSystem.</span><span class="sxs-lookup"><span data-stu-id="80ade-171">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="80ade-172">El contenido de la unidad de usuario es persistente en todas las sesiones para adaptarse a situaciones en que se podría interrumpir la conectividad de red.</span><span class="sxs-lookup"><span data-stu-id="80ade-172">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="80ade-173">De manera predeterminada, la unidad de usuario le permite almacenar un máximo de 50 MB de datos por usuario.</span><span class="sxs-lookup"><span data-stu-id="80ade-173">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="80ade-174">Puede limitar la cantidad de datos que puede consumir un usuario con el campo *UserDriveMaximumSize*.</span><span class="sxs-lookup"><span data-stu-id="80ade-174">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="80ade-175">Si no quiere que los datos de la unidad de usuario sean persistentes, puede configurar una tarea programada en el sistema para limpiar la carpeta de forma automática cada noche.</span><span class="sxs-lookup"><span data-stu-id="80ade-175">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="80ade-176">La unidad de usuario solo está disponible en PowerShell 5.1 o una versión posterior.</span><span class="sxs-lookup"><span data-stu-id="80ade-176">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="80ade-177">Para obtener más información sobre unidades de PowerShell, vea [Administración de unidades de PowerShell](/powershell/scripting/samples/managing-windows-powershell-drives).</span><span class="sxs-lookup"><span data-stu-id="80ade-177">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="80ade-178">Definiciones de roles</span><span class="sxs-lookup"><span data-stu-id="80ade-178">Role definitions</span></span>

<span data-ttu-id="80ade-179">Las definiciones de roles en un archivo de configuración de sesión definen la asignación de **usuarios** a **roles**.</span><span class="sxs-lookup"><span data-stu-id="80ade-179">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="80ade-180">A todos los usuarios o grupos incluidos en este campo se les asigna permiso al punto de conexión de JEA cuando se registra.</span><span class="sxs-lookup"><span data-stu-id="80ade-180">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="80ade-181">Cada usuario o grupo puede incluirse como una clave en la tabla hash solo una vez, pero se le pueden asignar varios roles.</span><span class="sxs-lookup"><span data-stu-id="80ade-181">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="80ade-182">El nombre de la funcionalidad de rol debe ser el nombre del archivo de funcionalidad de rol, sin la extensión `.psrc`.</span><span class="sxs-lookup"><span data-stu-id="80ade-182">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="80ade-183">Si un usuario pertenece a más de un grupo en la definición de rol, obtiene acceso a los roles de cada uno.</span><span class="sxs-lookup"><span data-stu-id="80ade-183">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="80ade-184">Si dos roles conceden acceso a los mismos cmdlets, se concede al usuario el conjunto de parámetros más permisivo.</span><span class="sxs-lookup"><span data-stu-id="80ade-184">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="80ade-185">Al especificar usuarios o grupos locales en el campo de definiciones de rol, asegúrese de usar el nombre del equipo, no **localhost** ni comodines.</span><span class="sxs-lookup"><span data-stu-id="80ade-185">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="80ade-186">Puede comprobar el nombre del equipo observando la variable `$env:COMPUTERNAME`.</span><span class="sxs-lookup"><span data-stu-id="80ade-186">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="80ade-187">Orden de búsqueda de funcionalidad de rol</span><span class="sxs-lookup"><span data-stu-id="80ade-187">Role capability search order</span></span>

<span data-ttu-id="80ade-188">Como se ha mostrado en el ejemplo anterior, el nombre base del archivo de funcionalidad de rol hace referencia a las funcionalidades de rol.</span><span class="sxs-lookup"><span data-stu-id="80ade-188">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="80ade-189">El nombre base de un archivo es el nombre de archivo sin la extensión.</span><span class="sxs-lookup"><span data-stu-id="80ade-189">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="80ade-190">Si hay varias funcionalidades de rol disponibles en el sistema con el mismo nombre, PowerShell usa su orden de búsqueda implícito para seleccionar el archivo de funcionalidad de rol efectivo.</span><span class="sxs-lookup"><span data-stu-id="80ade-190">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="80ade-191">JEA **no** proporciona acceso a todos los archivos de funcionalidad de rol con el mismo nombre.</span><span class="sxs-lookup"><span data-stu-id="80ade-191">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="80ade-192">JEA utiliza la variable de entorno `$env:PSModulePath` para determinar qué rutas de acceso examinar para archivos de capacidad de rol.</span><span class="sxs-lookup"><span data-stu-id="80ade-192">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="80ade-193">Dentro de cada una de esas rutas de acceso, JEA busca módulos de PowerShell válidos que contengan una subcarpeta "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="80ade-193">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="80ade-194">Al igual que con la importación de módulos, JEA prefiere funcionalidades de rol que se suministran con Windows a capacidades de rol personalizadas con el mismo nombre.</span><span class="sxs-lookup"><span data-stu-id="80ade-194">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="80ade-195">Para todos los demás conflictos de nomenclatura, la precedencia se determina por el orden en el que Windows enumera los archivos en el directorio.</span><span class="sxs-lookup"><span data-stu-id="80ade-195">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="80ade-196">No se garantiza que el orden sea alfabético.</span><span class="sxs-lookup"><span data-stu-id="80ade-196">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="80ade-197">Para el usuario que se conecta se usa el primer archivo de funcionalidad de rol que coincide con el nombre especificado.</span><span class="sxs-lookup"><span data-stu-id="80ade-197">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="80ade-198">Como el orden de búsqueda de funcionalidad de rol no es determinista, se **recomienda encarecidamente** que las funcionalidades de rol tengan nombres de archivo únicos.</span><span class="sxs-lookup"><span data-stu-id="80ade-198">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="80ade-199">Reglas de acceso condicional</span><span class="sxs-lookup"><span data-stu-id="80ade-199">Conditional access rules</span></span>

<span data-ttu-id="80ade-200">De forma automática, se concede acceso a los puntos de conexión de JEA a todos los usuarios y grupos incluidos en el campo **RoleDefinitions**.</span><span class="sxs-lookup"><span data-stu-id="80ade-200">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="80ade-201">Las reglas de acceso condicional permiten ajustar este acceso y requieren que los usuarios pertenezcan a grupos de seguridad adicionales que no afecten a los roles a los que están asignados.</span><span class="sxs-lookup"><span data-stu-id="80ade-201">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="80ade-202">Esto es útil cuando se quiere integrar una solución de administración de acceso con privilegios "Just-In-Time", autenticación de tarjeta inteligente u otra solución de autenticación multifactor con JEA.</span><span class="sxs-lookup"><span data-stu-id="80ade-202">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="80ade-203">Las reglas de acceso condicional se definen en el campo RequiredGroups en un archivo de configuración de sesión.</span><span class="sxs-lookup"><span data-stu-id="80ade-203">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="80ade-204">En él, puede proporcionar una tabla hash (opcionalmente anidada) que use las claves "And" y "Or" para construir las reglas.</span><span class="sxs-lookup"><span data-stu-id="80ade-204">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="80ade-205">Estos son algunos ejemplos sobre cómo usar este campo:</span><span class="sxs-lookup"><span data-stu-id="80ade-205">Here are some examples of how to use this field:</span></span>

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
> <span data-ttu-id="80ade-206">Las reglas de acceso condicional solo están disponibles en PowerShell 5.1 o versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="80ade-206">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="80ade-207">Otras propiedades</span><span class="sxs-lookup"><span data-stu-id="80ade-207">Other properties</span></span>

<span data-ttu-id="80ade-208">Los archivos de configuración de sesión también pueden hacer lo mismo que un archivo de funcionalidad de rol, pero sin la capacidad de proporcionar acceso a los usuarios que se conectan a distintos comandos.</span><span class="sxs-lookup"><span data-stu-id="80ade-208">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="80ade-209">Si quiere permitir que todos los usuarios obtengan acceso a cmdlets, funciones o proveedores específicos, puede hacerlo directamente en el archivo de configuración de sesión.</span><span class="sxs-lookup"><span data-stu-id="80ade-209">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="80ade-210">Para obtener una lista completa de las propiedades que se admiten en el archivo de configuración de sesión, ejecute `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="80ade-210">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="80ade-211">Probar un archivo de configuración de sesión</span><span class="sxs-lookup"><span data-stu-id="80ade-211">Testing a session configuration file</span></span>

<span data-ttu-id="80ade-212">Puede probar una configuración de sesión con el cmdlet [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile).</span><span class="sxs-lookup"><span data-stu-id="80ade-212">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="80ade-213">Se recomienda probar el archivo de configuración de sesión si se ha editado manualmente el archivo `.pssc`.</span><span class="sxs-lookup"><span data-stu-id="80ade-213">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="80ade-214">Las pruebas garantizan que la sintaxis sea correcta.</span><span class="sxs-lookup"><span data-stu-id="80ade-214">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="80ade-215">Si un archivo de configuración de sesión no supera esta prueba, no se puede registrar en el sistema.</span><span class="sxs-lookup"><span data-stu-id="80ade-215">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="80ade-216">Archivo de configuración de sesión de ejemplo</span><span class="sxs-lookup"><span data-stu-id="80ade-216">Sample session configuration file</span></span>

<span data-ttu-id="80ade-217">En el ejemplo siguiente se muestra cómo crear y validar una configuración de sesión para JEA.</span><span class="sxs-lookup"><span data-stu-id="80ade-217">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="80ade-218">Para que resulte cómodo y legible, las definiciones de roles se crean y almacenan en la variable `$roles`.</span><span class="sxs-lookup"><span data-stu-id="80ade-218">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="80ade-219">Pero no es obligatorio hacerlo.</span><span class="sxs-lookup"><span data-stu-id="80ade-219">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="80ade-220">Actualizar los archivos de configuración de sesión</span><span class="sxs-lookup"><span data-stu-id="80ade-220">Updating session configuration files</span></span>

<span data-ttu-id="80ade-221">Para cambiar las propiedades de una configuración de sesión de JEA, incluida la asignación de usuarios a los roles, debe [anular el registro](register-jea.md#unregistering-jea-configurations).</span><span class="sxs-lookup"><span data-stu-id="80ade-221">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="80ade-222">Después, [vuelva a registrar](register-jea.md) la configuración de sesión JEA mediante un archivo de configuración de sesión actualizado.</span><span class="sxs-lookup"><span data-stu-id="80ade-222">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="80ade-223">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="80ade-223">Next steps</span></span>

- [<span data-ttu-id="80ade-224">Registrar una configuración de JEA</span><span class="sxs-lookup"><span data-stu-id="80ade-224">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="80ade-225">Crear roles de JEA</span><span class="sxs-lookup"><span data-stu-id="80ade-225">Author JEA roles</span></span>](role-capabilities.md)
