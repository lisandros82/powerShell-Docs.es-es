---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Auditoría y creación de informes en JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017796"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="f768f-103">Auditoría y creación de informes en JEA</span><span class="sxs-lookup"><span data-stu-id="f768f-103">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="f768f-104">Después de haber implementado JEA, tendrá que auditar la configuración de JEA de forma periódica.</span><span class="sxs-lookup"><span data-stu-id="f768f-104">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="f768f-105">La auditoría ayudar a evaluar si los usuarios adecuados tienen acceso al punto de conexión de JEA y sus roles asignados siguen siendo correctos.</span><span class="sxs-lookup"><span data-stu-id="f768f-105">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="f768f-106">Buscar sesiones de JEA registradas en un equipo</span><span class="sxs-lookup"><span data-stu-id="f768f-106">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="f768f-107">Para comprobar qué sesiones de JEA están registradas en un equipo, use el cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="f768f-107">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="f768f-108">Los derechos efectivos del punto de conexión se muestran en la propiedad **Permission**.</span><span class="sxs-lookup"><span data-stu-id="f768f-108">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="f768f-109">Estos usuarios tienen derecho a conectarse al punto de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="f768f-109">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="f768f-110">Pero los roles y los comandos a los que tienen acceso están determinados por la propiedad **RoleDefinitions** del [archivo de configuración de sesión](session-configurations.md) que se ha usado para registrar el punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="f768f-110">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="f768f-111">Expanda la propiedad **RoleDefinitions** para evaluar las asignaciones de rol en un punto de conexión de JEA registrado.</span><span class="sxs-lookup"><span data-stu-id="f768f-111">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="f768f-112">Buscar funcionalidades de rol disponibles en el equipo</span><span class="sxs-lookup"><span data-stu-id="f768f-112">Find available role capabilities on the machine</span></span>

<span data-ttu-id="f768f-113">JEA obtiene las funcionalidades de rol de los archivos `.psrc` almacenados en la carpeta **RoleCapabilities** dentro de un módulo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f768f-113">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="f768f-114">La función siguiente busca todas las funcionalidades de rol disponibles en un equipo.</span><span class="sxs-lookup"><span data-stu-id="f768f-114">The following function finds all role capabilities available on a computer.</span></span>

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="f768f-115">El orden de los resultados de esta función no es necesariamente el orden en que se seleccionarán las funcionalidades de rol si varias de ellas comparten el mismo nombre.</span><span class="sxs-lookup"><span data-stu-id="f768f-115">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="f768f-116">Comprobar los derechos efectivos de un usuario específico</span><span class="sxs-lookup"><span data-stu-id="f768f-116">Check effective rights for a specific user</span></span>

<span data-ttu-id="f768f-117">El cmdlet [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) enumera todos los comandos disponibles en un punto de conexión de JEA en función de las pertenencias a grupos del usuario.</span><span class="sxs-lookup"><span data-stu-id="f768f-117">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="f768f-118">La salida de `Get-PSSessionCapability` es idéntica a la del usuario especificado que ejecuta `Get-Command -CommandType All` en una sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="f768f-118">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="f768f-119">Si los usuarios no son miembros permanentes de grupos que les concederían derechos adicionales de JEA, es posible que este cmdlet no refleje esos permisos adicionales.</span><span class="sxs-lookup"><span data-stu-id="f768f-119">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="f768f-120">Esto sucede al usar sistemas de administración de acceso con privilegios Just-In-Time para permitir que los usuarios pertenezcan de forma temporal a un grupo de seguridad.</span><span class="sxs-lookup"><span data-stu-id="f768f-120">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="f768f-121">Evalúe con atención la asignación de usuarios a roles y funcionalidades para garantizar que los usuarios solo obtienen el nivel de acceso necesario para realizar su trabajo de forma correcta.</span><span class="sxs-lookup"><span data-stu-id="f768f-121">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="f768f-122">Registros de eventos de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f768f-122">PowerShell event logs</span></span>

<span data-ttu-id="f768f-123">Si ha habilitado el registro de bloques de script o de módulo en el sistema, puede ver eventos en los registros de eventos de Windows para cada comando que ejecute un usuario en una sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="f768f-123">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="f768f-124">Para buscar estos eventos, abra el registro de eventos **Microsoft-Windows-PowerShell/Operational** y busque eventos con el identificador **4104**.</span><span class="sxs-lookup"><span data-stu-id="f768f-124">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="f768f-125">En cada entrada del registro de eventos se incluye información sobre la sesión en la que se ha ejecutado el comando.</span><span class="sxs-lookup"><span data-stu-id="f768f-125">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="f768f-126">Para las sesiones de JEA, el evento incluye información sobre **ConnectedUser** y **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="f768f-126">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="f768f-127">**ConnectedUser** es el usuario actual que ha creado la sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="f768f-127">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="f768f-128">**RunAsUser** es la cuenta de JEA que se ha usado para ejecutar el comando.</span><span class="sxs-lookup"><span data-stu-id="f768f-128">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="f768f-129">En los registros de eventos de la aplicación se muestran los cambios realizados por **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="f768f-129">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="f768f-130">Por tanto, es necesario tener habilitado el registro de scripts y módulos para realizar el seguimiento de la invocación de un comando específico hasta **ConnectedUser**.</span><span class="sxs-lookup"><span data-stu-id="f768f-130">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="f768f-131">Registros de eventos de la aplicación</span><span class="sxs-lookup"><span data-stu-id="f768f-131">Application event logs</span></span>

<span data-ttu-id="f768f-132">Es posible que los comandos que se ejecutan en una sesión de JEA que interactúan con aplicaciones o servicios externos registren eventos en sus propios registros de eventos.</span><span class="sxs-lookup"><span data-stu-id="f768f-132">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="f768f-133">A diferencia de los registros y las transcripciones de PowerShell, otros mecanismos de registro no capturan el usuario conectado de la sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="f768f-133">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="f768f-134">En su lugar, esas aplicaciones solo registran el usuario de ejecución virtual.</span><span class="sxs-lookup"><span data-stu-id="f768f-134">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="f768f-135">Para determinar quién ha ejecutado el comando, tiene que consultar una [transcripción de sesión](#session-transcripts) o poner en correlación los registros de eventos de PowerShell con la hora y el usuario que se muestran en el registro de eventos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f768f-135">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="f768f-136">El registro de WinRM también puede ayudarle a poner en correlación a los usuarios de ejecución con el usuario que se conecta en un registro de eventos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f768f-136">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="f768f-137">El identificador de evento **193** del registro **operativo o de Administración remota de Windows de Microsoft Windows** registra el identificador de seguridad (SID) y el nombre de cuenta del usuario que se conecta y del usuario de ejecución en todas las sesiones de JEA nuevas.</span><span class="sxs-lookup"><span data-stu-id="f768f-137">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="f768f-138">Transcripciones de sesión</span><span class="sxs-lookup"><span data-stu-id="f768f-138">Session transcripts</span></span>

<span data-ttu-id="f768f-139">Si ha configurado JEA para crear una transcripción para cada sesión de usuario, se almacena una copia de texto de las acciones de todos los usuarios en la carpeta especificada.</span><span class="sxs-lookup"><span data-stu-id="f768f-139">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="f768f-140">El comando siguiente (como administrador) busca todos los directorios de transcripción.</span><span class="sxs-lookup"><span data-stu-id="f768f-140">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="f768f-141">Cada transcripción comienza con información sobre la hora en que se ha iniciado la sesión, qué usuario se ha conectado a la sesión y qué identidad de JEA se le ha asignado.</span><span class="sxs-lookup"><span data-stu-id="f768f-141">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="f768f-142">El cuerpo de la transcripción contiene información sobre cada comando que ha invocado el usuario.</span><span class="sxs-lookup"><span data-stu-id="f768f-142">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="f768f-143">La sintaxis exacta del comando que se usa no está disponible en las sesiones de JEA debido a la manera en que se transforman los comandos para la comunicación remota de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f768f-143">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="f768f-144">Pero todavía puede determinar el comando real que se ha ejecutado.</span><span class="sxs-lookup"><span data-stu-id="f768f-144">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="f768f-145">A continuación se muestra un fragmento de código de ejemplo de una transcripción de un usuario que ejecuta `Get-Service Dns` en una sesión de JEA:</span><span class="sxs-lookup"><span data-stu-id="f768f-145">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="f768f-146">Se escribe una línea **CommandInvocation** para cada comando que ejecuta un usuario.</span><span class="sxs-lookup"><span data-stu-id="f768f-146">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="f768f-147">En **ParameterBindings** se registran todos los parámetros y valores proporcionados con el comando.</span><span class="sxs-lookup"><span data-stu-id="f768f-147">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="f768f-148">En el ejemplo anterior, puede ver que al parámetro **Name** se le ha proporcionado el valor **Dns** para el cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="f768f-148">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="f768f-149">El resultado de cada comando también desencadenará una instancia de **CommandInvocation**, normalmente para `Out-Default`.</span><span class="sxs-lookup"><span data-stu-id="f768f-149">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="f768f-150">**InputObject** de `Out-Default` es el objeto de PowerShell que devuelve el comando.</span><span class="sxs-lookup"><span data-stu-id="f768f-150">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="f768f-151">Los detalles de ese objeto se imprimen unas líneas más adelante, imitando detenidamente lo que habría visto el usuario.</span><span class="sxs-lookup"><span data-stu-id="f768f-151">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="f768f-152">Vea también</span><span class="sxs-lookup"><span data-stu-id="f768f-152">See also</span></span>

[<span data-ttu-id="f768f-153">Entrada de blog sobre seguridad de *PowerShell ♥ the Blue Team*</span><span class="sxs-lookup"><span data-stu-id="f768f-153">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
