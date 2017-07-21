---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,security
title: "Auditoría y creación de informes en JEA"
ms.openlocfilehash: 60bc7a4213c75735628207bb21078bf90f7b1ca3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="7743d-103">Auditoría y creación de informes en JEA</span><span class="sxs-lookup"><span data-stu-id="7743d-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="7743d-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7743d-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="7743d-105">Después de haber implementado JEA, querrá auditar la configuración de JEA de forma periódica.</span><span class="sxs-lookup"><span data-stu-id="7743d-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="7743d-106">Esto le ayudará a evaluar si las personas adecuadas tienen acceso al punto de conexión de JEA y si sus roles asignados siguen siendo correctos.</span><span class="sxs-lookup"><span data-stu-id="7743d-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="7743d-107">En este tema, se describen las distintas formas en que puede auditar un punto de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="7743d-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="7743d-108">Buscar sesiones de JEA registradas en un equipo</span><span class="sxs-lookup"><span data-stu-id="7743d-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="7743d-109">Para comprobar qué sesiones de JEA están registradas en un equipo, use el cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="7743d-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="7743d-110">Los derechos efectivos del punto de conexión se muestran en la propiedad "Permission".</span><span class="sxs-lookup"><span data-stu-id="7743d-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="7743d-111">Estos usuarios tienen derecho a conectarse al punto de conexión de JEA, pero a qué roles (y, por extensión, comandos) tienen acceso viene determinado por el campo "RoleDefinitions" del [archivo de configuración de sesión](session-configurations.md) que se ha usado para registrar el punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="7743d-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="7743d-112">Puede evaluar las asignaciones de rol en un punto de conexión de JEA registrado al expandir los datos de la propiedad "RoleDefinitions".</span><span class="sxs-lookup"><span data-stu-id="7743d-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="7743d-113">Buscar funcionalidades de rol disponibles en el equipo</span><span class="sxs-lookup"><span data-stu-id="7743d-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="7743d-114">JEA solo usará los archivos de funcionalidad de rol si se almacenan en una carpeta "RoleCapabilities" dentro de un módulo de PowerShell válido.</span><span class="sxs-lookup"><span data-stu-id="7743d-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="7743d-115">Puede encontrar todas las funcionalidades de rol disponibles en un equipo al buscar la lista de módulos disponibles.</span><span class="sxs-lookup"><span data-stu-id="7743d-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="7743d-116">El orden de los resultados de esta función no es necesariamente el orden en que se seleccionarán las funcionalidades de rol si varias de ellas comparten el mismo nombre.</span><span class="sxs-lookup"><span data-stu-id="7743d-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="7743d-117">Comprobar los derechos efectivos de un usuario específico</span><span class="sxs-lookup"><span data-stu-id="7743d-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="7743d-118">Una vez que ha configurado un punto de conexión de JEA, es posible que quiera comprobar qué comandos están disponibles para un usuario específico en una sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="7743d-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="7743d-119">Puede usar [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) para enumerar todos los comandos aplicables a un usuario si fuera a iniciar una sesión de JEA con los miembros de su grupo actual.</span><span class="sxs-lookup"><span data-stu-id="7743d-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="7743d-120">La salida de `Get-PSSessionCapability` es idéntica a la del usuario especificado que ejecuta `Get-Command -CommandType All` en una sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="7743d-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="7743d-121">Si los usuarios no son miembros permanentes de grupos que les concederían derechos adicionales de JEA, es posible que este cmdlet no refleje esos permisos adicionales.</span><span class="sxs-lookup"><span data-stu-id="7743d-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="7743d-122">Este suele ser el caso al usar sistemas de administración de acceso con privilegios Just-In-Time para permitir que los usuarios pertenezcan de forma temporal a un grupo de seguridad.</span><span class="sxs-lookup"><span data-stu-id="7743d-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="7743d-123">Evalúe siempre cuidadosamente la asignación de usuarios a roles y el contenido de cada rol para asegurarse de que los usuarios solo obtienen acceso a la menor cantidad de comandos necesarios para realizar su trabajo correctamente.</span><span class="sxs-lookup"><span data-stu-id="7743d-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="7743d-124">Registros de eventos de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7743d-124">PowerShell event logs</span></span>

<span data-ttu-id="7743d-125">Si ha habilitado el registro de bloques de script o módulo en el sistema, podrá buscar eventos en los registros de eventos de Windows para cada comando que haya ejecutado un usuario en sus sesiones de JEA.</span><span class="sxs-lookup"><span data-stu-id="7743d-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="7743d-126">Para buscar estos eventos, abra el Visor de eventos de Windows, vaya al registro de eventos **Microsoft-Windows-PowerShell/Operational** y busque eventos con el identificador **4104**.</span><span class="sxs-lookup"><span data-stu-id="7743d-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="7743d-127">Cada entrada de registro de eventos incluirá información sobre la sesión en que se ha ejecutado el comando.</span><span class="sxs-lookup"><span data-stu-id="7743d-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="7743d-128">Para las sesiones de JEA, esto incluye información importante sobre el **ConnectedUser**, que es el usuario actual que ha creado la sesión de JEA, así como el **RunAsUser** que identifica la cuenta de JEA usada para ejecutar el comando.</span><span class="sxs-lookup"><span data-stu-id="7743d-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="7743d-129">Los registros de eventos de la aplicación mostrarán cambios realizados por el RunAsUser, por lo que tener el registro de script/módulo o transcripciones habilitado es fundamental para poder realizar un seguimiento de una invocación de comando específica hasta un usuario.</span><span class="sxs-lookup"><span data-stu-id="7743d-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="7743d-130">Registros de eventos de la aplicación</span><span class="sxs-lookup"><span data-stu-id="7743d-130">Application event logs</span></span>

<span data-ttu-id="7743d-131">Al ejecutar un comando en una sesión de JEA que interactúa con un servicio o aplicación externos, esas aplicaciones pueden registrar eventos en sus propios registros de eventos.</span><span class="sxs-lookup"><span data-stu-id="7743d-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="7743d-132">A diferencia de los registros y transcripciones de PowerShell, otros mecanismos de registro no capturarán al usuario conectado de la sesión de JEA y solo registrarán en su lugar al usuario de ejecución virtual o la cuenta de servicio administrada de grupo.</span><span class="sxs-lookup"><span data-stu-id="7743d-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="7743d-133">Para determinar quién ha ejecutado el comando, deberá consultar una [transcripción de sesión](#session-transcripts) o poner en correlación los registros de eventos de PowerShell con la hora y el usuario que aparecen en el registro de eventos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7743d-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="7743d-134">Asimismo, el registro de WinRM puede ayudarle a poner en correlación a los usuarios de ejecución en un registro de eventos de la aplicación con el usuario que se conecta.</span><span class="sxs-lookup"><span data-stu-id="7743d-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="7743d-135">El identificador de evento **193** en el registro **Microsoft-Windows-Administración remota de Windows/Operational** registra el identificador de seguridad (SID) y el nombre de cuenta del usuario que se conecta y del usuario de ejecución cada vez que se crea una sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="7743d-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="7743d-136">Transcripciones de sesión</span><span class="sxs-lookup"><span data-stu-id="7743d-136">Session transcripts</span></span>

<span data-ttu-id="7743d-137">Si ha configurado JEA para crear una transcripción para cada sesión de usuario, se almacenará una copia del texto de las acciones de todos los usuarios en la carpeta especificada.</span><span class="sxs-lookup"><span data-stu-id="7743d-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="7743d-138">Para buscar todos los directorios de transcripciones, ejecute el siguiente comando como administrador en el equipo configurado con JEA:</span><span class="sxs-lookup"><span data-stu-id="7743d-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="7743d-139">Cada transcripción comienza con información sobre la hora en que se ha iniciado la sesión, qué usuario se ha conectado a la sesión y qué identidad de JEA se le ha asignado.</span><span class="sxs-lookup"><span data-stu-id="7743d-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="7743d-140">En el cuerpo de la transcripción, se registra información sobre cada comando que ha invocado el usuario.</span><span class="sxs-lookup"><span data-stu-id="7743d-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="7743d-141">La sintaxis exacta del comando que ha ejecutado el usuario no está disponible en las sesiones de JEA debido a la forma en que se transforman los comandos para la comunicación remota de PowerShell, pero aún puede determinar el comando real que se ha ejecutado.</span><span class="sxs-lookup"><span data-stu-id="7743d-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="7743d-142">A continuación se muestra un fragmento de código de ejemplo de una transcripción de un usuario que ejecuta `Get-Service Dns` en una sesión de JEA:</span><span class="sxs-lookup"><span data-stu-id="7743d-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="7743d-143">Para cada comando que ejecuta un usuario, se escribirá una línea "CommandInvocation", que describe el cmdlet o función que ha invocado el usuario.</span><span class="sxs-lookup"><span data-stu-id="7743d-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="7743d-144">ParameterBindings sigue a cada CommandInvocation para informarle sobre cada parámetro y valor que se ha proporcionado con el comando.</span><span class="sxs-lookup"><span data-stu-id="7743d-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="7743d-145">En el ejemplo anterior, puede ver que el parámetro "Name" ha proporcionado el valor "Dns" para el cmdlet "Get-Service".</span><span class="sxs-lookup"><span data-stu-id="7743d-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="7743d-146">El resultado de cada comando también desencadenará un CommandInvocation, normalmente para Out-Default.</span><span class="sxs-lookup"><span data-stu-id="7743d-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span> <span data-ttu-id="7743d-147">El InputObject de Out-Default es el objeto de PowerShell que devuelve el comando.</span><span class="sxs-lookup"><span data-stu-id="7743d-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="7743d-148">Los detalles de ese objeto se imprimen unas líneas más adelante, imitando detenidamente lo que habría visto el usuario.</span><span class="sxs-lookup"><span data-stu-id="7743d-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="7743d-149">Vea también</span><span class="sxs-lookup"><span data-stu-id="7743d-149">See also</span></span>

- [<span data-ttu-id="7743d-150">Auditar acciones del usuario en una sesión JEA</span><span class="sxs-lookup"><span data-stu-id="7743d-150">Audit user actions in a JEA session</span></span>](audit-and-report.md)
- [<span data-ttu-id="7743d-151">Entrada de blog sobre seguridad de *PowerShell ♥ the Blue Team*</span><span class="sxs-lookup"><span data-stu-id="7743d-151">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

