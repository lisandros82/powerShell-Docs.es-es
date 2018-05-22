---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Funcionalidades de rol de JEA
ms.openlocfilehash: 0531baa284e66a42a162329ea20ecfdca6d0b526
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="9077f-103">Funcionalidades de rol de JEA</span><span class="sxs-lookup"><span data-stu-id="9077f-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="9077f-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9077f-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="9077f-105">Al crear un punto de conexión de JEA, deberá definir una o varias "funcionalidades de rol" que describan *qué* puede hacer un usuario en una sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="9077f-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="9077f-106">Una funcionalidad de rol es un archivo de datos de PowerShell con la extensión .psrc que muestra los cmdlets, las funciones, los proveedores y los programas externos que deben estar disponibles para los usuarios que se conectan.</span><span class="sxs-lookup"><span data-stu-id="9077f-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="9077f-107">En este tema, se describe cómo crear un archivo de funcionalidad de rol de PowerShell para los usuarios de JEA.</span><span class="sxs-lookup"><span data-stu-id="9077f-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="9077f-108">Determinar los comandos permitidos</span><span class="sxs-lookup"><span data-stu-id="9077f-108">Determine which commands to allow</span></span>

<span data-ttu-id="9077f-109">El primer paso al crear un archivo de funcionalidad de rol es tener en cuenta a qué necesitarán acceso los usuarios a los que se les asigna el rol.</span><span class="sxs-lookup"><span data-stu-id="9077f-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="9077f-110">Este proceso de recopilación de requisitos puede llevar un tiempo, pero es un proceso muy importante.</span><span class="sxs-lookup"><span data-stu-id="9077f-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="9077f-111">Conceder acceso a los usuarios a muy pocos cmdlets y funciones puede impedirles llevar a cabo su trabajo.</span><span class="sxs-lookup"><span data-stu-id="9077f-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="9077f-112">Permitir el acceso a demasiados cmdlets y funciones puede ocasionar que los usuarios hagan más de lo esperado con sus privilegios de administrador implícitos, lo que empeora su posición en materia de seguridad.</span><span class="sxs-lookup"><span data-stu-id="9077f-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="9077f-113">La forma de afrontar este proceso dependerá de la organización y los objetivos, pero las siguientes sugerencias pueden ayudarle a asegurarse de ir por el buen camino.</span><span class="sxs-lookup"><span data-stu-id="9077f-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="9077f-114">**Identifique** los comandos que usan los usuarios para realizar su trabajo.</span><span class="sxs-lookup"><span data-stu-id="9077f-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="9077f-115">Esto puede implicar encuestar al personal de TI, comprobar los scripts de automatización o analizar registros o transcripciones de sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9077f-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="9077f-116">**Actualice** el uso de herramientas de línea de comandos por equivalentes de PowerShell, siempre que sea posible, para tener la mejor experiencia de personalización de JEA y auditoría.</span><span class="sxs-lookup"><span data-stu-id="9077f-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="9077f-117">No se pueden restringir programas externos con la misma minuciosidad que los cmdlets y las funciones que son nativos de PowerShell en JEA.</span><span class="sxs-lookup"><span data-stu-id="9077f-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="9077f-118">**Restrinja** el ámbito de los cmdlets si es necesario para permitir solo parámetros o valores de parámetros específicos.</span><span class="sxs-lookup"><span data-stu-id="9077f-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="9077f-119">Esto es especialmente importante si los usuarios solo deberían poder administrar parte de un sistema.</span><span class="sxs-lookup"><span data-stu-id="9077f-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="9077f-120">**Cree** funciones personalizadas para reemplazar comandos complejos o que sean difíciles de restringir en JEA.</span><span class="sxs-lookup"><span data-stu-id="9077f-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="9077f-121">Una función sencilla que encapsule un comando complejo o aplique lógica de validación adicional puede ofrecer un mayor control para simplificar los administradores y usuarios finales.</span><span class="sxs-lookup"><span data-stu-id="9077f-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="9077f-122">**Pruebe** la lista con ámbito de los comandos permitidos con los usuarios o los servicios de automatización y ajústela según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="9077f-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="9077f-123">Es importante recordar que los comandos en una sesión de JEA se ejecutan a menudo con privilegios de administrador o, si no, con privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="9077f-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="9077f-124">Es importante seleccionar los comandos disponibles para asegurarse de que el punto de conexión de JEA no permita que el usuario que se conecta eleve sus permisos.</span><span class="sxs-lookup"><span data-stu-id="9077f-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="9077f-125">A continuación se muestran algunos ejemplos de comandos que pueden usarse de forma malintencionada si se permiten en un estado sin restricciones.</span><span class="sxs-lookup"><span data-stu-id="9077f-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="9077f-126">Tenga en cuenta que esta lista no es exhaustiva y solo se debe usar a modo de precaución previa.</span><span class="sxs-lookup"><span data-stu-id="9077f-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="9077f-127">Ejemplos de comandos potencialmente peligrosos</span><span class="sxs-lookup"><span data-stu-id="9077f-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="9077f-128">Riesgo</span><span class="sxs-lookup"><span data-stu-id="9077f-128">Risk</span></span> | <span data-ttu-id="9077f-129">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="9077f-129">Example</span></span> | <span data-ttu-id="9077f-130">Comandos relacionados</span><span class="sxs-lookup"><span data-stu-id="9077f-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="9077f-131">Conceder al usuario que se conecta privilegios de administrador para omitir JEA</span><span class="sxs-lookup"><span data-stu-id="9077f-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="9077f-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="9077f-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="9077f-133">Ejecutar código arbitrario, como malware, vulnerabilidad de seguridad o scripts personalizados para omitir protecciones</span><span class="sxs-lookup"><span data-stu-id="9077f-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="9077f-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="9077f-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="9077f-135">Crear un archivo de funcionalidad de rol</span><span class="sxs-lookup"><span data-stu-id="9077f-135">Create a role capability file</span></span>

<span data-ttu-id="9077f-136">Puede crear un archivo de funcionalidad de rol de PowerShell con el cmdlet [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile).</span><span class="sxs-lookup"><span data-stu-id="9077f-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="9077f-137">El archivo de funcionalidad de rol resultante se puede abrir en un editor de texto y modificar para permitir los comandos que quiera para el rol.</span><span class="sxs-lookup"><span data-stu-id="9077f-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="9077f-138">La documentación de ayuda de PowerShell contiene varios ejemplos de cómo configurar el archivo.</span><span class="sxs-lookup"><span data-stu-id="9077f-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="9077f-139">Permitir funciones y cmdlets de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9077f-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="9077f-140">Para autorizar a los usuarios a ejecutar funciones o cmdlets de PowerShell, agregue el nombre del cmdlet o de la función en los campos VisibleCmdlets o VisibleFunctions.</span><span class="sxs-lookup"><span data-stu-id="9077f-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisbibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="9077f-141">Si no está seguro de si un comando es un cmdlet o una función, puede ejecutar `Get-Command <name>` y comprobar la propiedad "CommandType" de la salida.</span><span class="sxs-lookup"><span data-stu-id="9077f-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="9077f-142">A veces, el ámbito de un cmdlet o una función específicos es demasiado amplio para las necesidades de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="9077f-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="9077f-143">Por ejemplo, es probable que un administrador de DNS solo necesite acceso para reiniciar el servicio DNS.</span><span class="sxs-lookup"><span data-stu-id="9077f-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="9077f-144">En un entorno de varios inquilinos en el que a los inquilinos se les concede acceso a herramientas de administración de autoservicio, los inquilinos deberían limitarse a administrar con sus propios recursos.</span><span class="sxs-lookup"><span data-stu-id="9077f-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="9077f-145">En estos casos, puede restringir los parámetros que se exponen mediante la función o el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9077f-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="9077f-146">En escenarios más avanzados, es posible que también deba restringir los valores que puede proporcionar un usuario a estos parámetros.</span><span class="sxs-lookup"><span data-stu-id="9077f-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="9077f-147">Las funcionalidades de rol le permiten definir un conjunto de valores permitidos o un patrón de expresión regular que se evalúa para determinar si se permite una entrada específica.</span><span class="sxs-lookup"><span data-stu-id="9077f-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="9077f-148">Los [parámetros comunes de PowerShell](https://technet.microsoft.com/library/hh847884.aspx) se permiten siempre, incluso si restringe los parámetros disponibles.</span><span class="sxs-lookup"><span data-stu-id="9077f-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="9077f-149">No debería enumerarlos de forma explícita en el campo Parameters.</span><span class="sxs-lookup"><span data-stu-id="9077f-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="9077f-150">En la siguiente tabla, se describen las distintas formas en que puede personalizar un cmdlet o una función visibles.</span><span class="sxs-lookup"><span data-stu-id="9077f-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="9077f-151">Puede combinar cualquiera de los siguientes en el campo VisibleCmdlets.</span><span class="sxs-lookup"><span data-stu-id="9077f-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="9077f-152">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="9077f-152">Example</span></span>                                                                                      | <span data-ttu-id="9077f-153">Caso de uso</span><span class="sxs-lookup"><span data-stu-id="9077f-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="9077f-154">`'My-Func'` o `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="9077f-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="9077f-155">Permite al usuario ejecutar `My-Func` sin restricciones en los parámetros.</span><span class="sxs-lookup"><span data-stu-id="9077f-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="9077f-156">Permite al usuario ejecutar `My-Func` desde el módulo `MyModule` sin restricciones en los parámetros.</span><span class="sxs-lookup"><span data-stu-id="9077f-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="9077f-157">Permite al usuario ejecutar cualquier cmdlet o función con el verbo `My`.</span><span class="sxs-lookup"><span data-stu-id="9077f-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="9077f-158">Permite al usuario ejecutar cualquier cmdlet o función con el sustantivo `Func`.</span><span class="sxs-lookup"><span data-stu-id="9077f-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="9077f-159">Permite al usuario ejecutar `My-Func` con los parámetros `Param1` o `Param2`.</span><span class="sxs-lookup"><span data-stu-id="9077f-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="9077f-160">Para estos parámetros, se puede proporcionar cualquier valor.</span><span class="sxs-lookup"><span data-stu-id="9077f-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="9077f-161">Permite al usuario ejecutar `My-Func` con el parámetro `Param1`.</span><span class="sxs-lookup"><span data-stu-id="9077f-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="9077f-162">Para este parámetro, solo se pueden especificar "Value1" y "Value2".</span><span class="sxs-lookup"><span data-stu-id="9077f-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="9077f-163">Permite al usuario ejecutar `My-Func` con el parámetro `Param1`.</span><span class="sxs-lookup"><span data-stu-id="9077f-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="9077f-164">Para este parámetro, se puede especificar cualquier valor que comience por "contoso".</span><span class="sxs-lookup"><span data-stu-id="9077f-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>


> [!WARNING]
> <span data-ttu-id="9077f-165">En los mejores procedimientos recomendados de seguridad, se recomienda no usar caracteres comodín al definir cmdlets o funciones visibles.</span><span class="sxs-lookup"><span data-stu-id="9077f-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="9077f-166">En su lugar, debe enumerar de forma explícita cada comando de confianza para asegurarse de que ningún otro comando que comparta el mismo esquema de nombre se autorice de forma involuntaria.</span><span class="sxs-lookup"><span data-stu-id="9077f-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="9077f-167">No se pueden aplicar ValidatePattern y ValidateSet en el mismo cmdlet o función.</span><span class="sxs-lookup"><span data-stu-id="9077f-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="9077f-168">Si lo hace, ValidatePattern invalidará a ValidateSet.</span><span class="sxs-lookup"><span data-stu-id="9077f-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="9077f-169">Para obtener más información sobre ValidatePattern, consulte [esta publicación de *Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) y el contenido de referencia de las [expresiones regulares de PowerShell](https://technet.microsoft.com/library/hh847880.aspx).</span><span class="sxs-lookup"><span data-stu-id="9077f-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="9077f-170">Permitir comandos externos y scripts de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9077f-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="9077f-171">Para permitir que los usuarios ejecuten archivos ejecutables y scripts de PowerShell (.ps1) en una sesión de JEA, tendrá que agregar la ruta de acceso completa de cada programa en el campo VisibleExternalCommands.</span><span class="sxs-lookup"><span data-stu-id="9077f-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="9077f-172">Se aconseja, siempre que sea posible, que se usen equivalentes de función o cmdlet de PowerShell de los ejecutables externos que autorice, ya que tiene control sobre los parámetros que se permiten con funciones y cmdlets de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9077f-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="9077f-173">Muchos ejecutables le permiten leer el estado actual y, después, cambiarlo al proporcionar parámetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="9077f-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="9077f-174">Pongamos de ejemplo el rol de un administrador del servidor de archivos que quiera comprobar los recursos compartidos de red que se hospedan en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="9077f-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="9077f-175">Una forma de comprobarlo es usar `net share`.</span><span class="sxs-lookup"><span data-stu-id="9077f-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="9077f-176">En cambio, permitir net.exe es muy peligroso, ya que el administrador podría usar fácilmente el comando para obtener privilegios de administrador con `net group Administrators unprivilegedjeauser /add`.</span><span class="sxs-lookup"><span data-stu-id="9077f-176">However, allowing net.exe is very dangerous becuase the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="9077f-177">Un mejor enfoque es permitir [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx), que ofrece el mismo resultado pero con un ámbito mucho más limitado.</span><span class="sxs-lookup"><span data-stu-id="9077f-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="9077f-178">Al poner comandos externos a disposición de los usuarios en una sesión de JEA, especifique siempre la ruta de acceso completa al ejecutable para asegurarse de que no se ejecute en su lugar un programa con un nombre parecido (y potencialmente malintencionado) ubicado en otra parte del sistema.</span><span class="sxs-lookup"><span data-stu-id="9077f-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicous) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="9077f-179">Permitir el acceso a proveedores de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9077f-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="9077f-180">De manera predeterminada, no hay ningún proveedor de PowerShell disponible en las sesiones de JEA.</span><span class="sxs-lookup"><span data-stu-id="9077f-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="9077f-181">Esto es principalmente para reducir el riesgo de que se revele información confidencial y opciones de configuración al usuario que se conecta.</span><span class="sxs-lookup"><span data-stu-id="9077f-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="9077f-182">Cuando sea necesario, puede permitir el acceso a los proveedores de PowerShell mediante el comando `VisibleProviders`.</span><span class="sxs-lookup"><span data-stu-id="9077f-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="9077f-183">Para obtener una lista completa de proveedores, ejecute `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="9077f-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="9077f-184">Para realizar tareas sencillas que requieren acceso al sistema de archivos, el Registro, el almacén de certificados u otros proveedores de información confidencial, también puede escribir una función personalizada que sea adecuada para trabajar con el proveedor en nombre del usuario.</span><span class="sxs-lookup"><span data-stu-id="9077f-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="9077f-185">Los cmdlets, las funciones y los programas externos que están disponibles en una sesión de JEA no están sujetos a las mismas restricciones que JEA, pueden tener acceso a cualquier proveedor de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="9077f-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="9077f-186">Asimismo, considere el uso de la [unidad de usuario](session-configurations.md#user-drive) al copiar archivos desde/en un punto de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="9077f-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="9077f-187">Crear funciones personalizadas</span><span class="sxs-lookup"><span data-stu-id="9077f-187">Creating custom functions</span></span>

<span data-ttu-id="9077f-188">Puede crear funciones personalizadas en un archivo de funcionalidad de rol para simplificar tareas complejas para los usuarios finales.</span><span class="sxs-lookup"><span data-stu-id="9077f-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="9077f-189">Las funciones personalizadas también son útiles cuando se requiere una lógica de validación avanzada para los valores de parámetros de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9077f-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="9077f-190">Puede escribir funciones simples en el campo **FunctionDefinitions**:</span><span class="sxs-lookup"><span data-stu-id="9077f-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="9077f-191">No olvide agregar el nombre de las funciones personalizadas en el campo **VisibleFunctions** para que las puedan ejecutar los usuarios de JEA.</span><span class="sxs-lookup"><span data-stu-id="9077f-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>


<span data-ttu-id="9077f-192">El cuerpo (bloque de script) de las funciones personalizadas se ejecuta en el modo de lenguaje predeterminado del sistema y no está sujeto a restricciones de lenguaje de JEA.</span><span class="sxs-lookup"><span data-stu-id="9077f-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="9077f-193">Esto significa que las funciones pueden tener acceso al sistema de archivos y al Registro y ejecutar comandos que no se han hecho visibles en el archivo de funcionalidad de rol.</span><span class="sxs-lookup"><span data-stu-id="9077f-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="9077f-194">Tenga cuidado para evitar que se ejecute código arbitrario al usar parámetros y para evitar canalizar la entrada del usuario directamente en cmdlets como `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="9077f-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="9077f-195">En el ejemplo anterior, se habrá dado cuenta de que se usa el nombre de módulo completo (FQMN) `Microsoft.PowerShell.Utility\Select-Object` en lugar de la forma abreviada `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="9077f-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="9077f-196">Las funciones definidas en los archivos de funcionalidad de función siguen dependiendo del ámbito de las sesiones de JEA, que incluye las funciones de proxy que crea JEA para restringir comandos existentes.</span><span class="sxs-lookup"><span data-stu-id="9077f-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="9077f-197">Select-Object es un cmdlet restringido y predeterminado en todas las sesiones de JEA que no le permite seleccionar propiedades arbitrarias en objetos.</span><span class="sxs-lookup"><span data-stu-id="9077f-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="9077f-198">Para usar Select-Object sin restricciones en funciones, debe solicitar de forma explícita la implementación completa al especificar el FQMN.</span><span class="sxs-lookup"><span data-stu-id="9077f-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="9077f-199">Cualquier cmdlet sin restricciones en una sesión de JEA tendrá el mismo comportamiento que cuando se invoca desde una función, de acuerdo con la [precedencia de comando](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9077f-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="9077f-200">Si está escribiendo una gran cantidad de funciones personalizadas, puede ser más fácil colocarlas en un [módulo de script de PowerShell](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="9077f-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="9077f-201">Después, puede hacer visibles esas funciones en la sesión de JEA mediante el campo VisibleFunctions como lo haría con módulos integrados y de terceros.</span><span class="sxs-lookup"><span data-stu-id="9077f-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="9077f-202">Colocar funcionalidades de rol en un módulo</span><span class="sxs-lookup"><span data-stu-id="9077f-202">Place role capabilities in a module</span></span>

<span data-ttu-id="9077f-203">Para que PowerShell encuentre un archivo de funcionalidad de rol, debe estar almacenado en una carpeta "RoleCapabilities" de un módulo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9077f-203">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="9077f-204">El módulo se puede almacenar en cualquier carpeta incluida en la variable de entorno `$env:PSModulePath`, pero no debe colocarlo en System32 (reservado para módulos integrados) ni en una carpeta en que los usuarios que se conectan y no sean de confianza puedan modificar los archivos.</span><span class="sxs-lookup"><span data-stu-id="9077f-204">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="9077f-205">A continuación se muestra un ejemplo de cómo crear un módulo de script de PowerShell básico denominado *ContosoJEA* en la ruta de acceso "Archivos de programa".</span><span class="sxs-lookup"><span data-stu-id="9077f-205">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="9077f-206">Consulte [Understanding a PowerShell Module](https://msdn.microsoft.com/en-us/library/dd878324.aspx) (Descripción de un módulo de PowerShell) para obtener más información sobre la variable de entorno PSModulePath, los manifiestos de módulo y los módulos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9077f-206">See [Understanding a PowerShell Module](https://msdn.microsoft.com/en-us/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="9077f-207">Actualizar funcionalidades de rol</span><span class="sxs-lookup"><span data-stu-id="9077f-207">Updating role capabilities</span></span>


<span data-ttu-id="9077f-208">Puede actualizar un archivo de funcionalidad de rol en cualquier momento; para ello, solo tiene que guardar los cambios realizados en el archivo de funcionalidad de rol.</span><span class="sxs-lookup"><span data-stu-id="9077f-208">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="9077f-209">Cualquier sesión de JEA nueva iniciada después de que se haya actualizado la funcionalidad de rol reflejará las funcionalidades revisadas.</span><span class="sxs-lookup"><span data-stu-id="9077f-209">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="9077f-210">Por esto es tan importante controlar el acceso a la carpeta de funcionalidades de rol.</span><span class="sxs-lookup"><span data-stu-id="9077f-210">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="9077f-211">Solo los administradores de plena confianza deberían poder cambiar los archivos de funcionalidad de rol.</span><span class="sxs-lookup"><span data-stu-id="9077f-211">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="9077f-212">Si un usuario que no sea de confianza puede cambiar los archivos de funcionalidad de rol, puede proporcionarse acceso fácilmente a cmdlets que le permitan elevar sus privilegios.</span><span class="sxs-lookup"><span data-stu-id="9077f-212">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>


<span data-ttu-id="9077f-213">Para administradores que quieran bloquear el acceso a las funcionalidades de rol, asegúrese de que el sistema local tenga acceso de lectura a los archivos de funcionalidad de rol y a los módulos contenedores.</span><span class="sxs-lookup"><span data-stu-id="9077f-213">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="9077f-214">Cómo se combinan las funcionalidades de rol</span><span class="sxs-lookup"><span data-stu-id="9077f-214">How role capabilities are merged</span></span>

<span data-ttu-id="9077f-215">Se les puede conceder acceso a los usuarios a varias funcionalidades de rol cuando entran en una sesión de JEA según las asignaciones de rol del [archivo de configuración de sesión](session-configurations.md).</span><span class="sxs-lookup"><span data-stu-id="9077f-215">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="9077f-216">Cuando esto sucede, JEA intenta dar al usuario el conjunto de comandos *más permisivo* permitido por cualquiera de los roles.</span><span class="sxs-lookup"><span data-stu-id="9077f-216">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="9077f-217">**VisibleCmdlets y VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="9077f-217">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="9077f-218">La lógica de combinación más compleja afecta a los cmdlets y funciones, que pueden tener sus parámetros y valores de parámetro limitados en JEA.</span><span class="sxs-lookup"><span data-stu-id="9077f-218">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="9077f-219">Estas son las reglas:</span><span class="sxs-lookup"><span data-stu-id="9077f-219">The rules are as follows:</span></span>

1. <span data-ttu-id="9077f-220">Si un cmdlet solo está visible en un rol, será visible para el usuario con cualquier restricción de parámetro correspondiente.</span><span class="sxs-lookup"><span data-stu-id="9077f-220">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="9077f-221">Si un cmdlet está visible en más de un rol, y todos los roles tienen las mismas restricciones en el cmdlet, el cmdlet estará visible para el usuario con esas restricciones.</span><span class="sxs-lookup"><span data-stu-id="9077f-221">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="9077f-222">Si un cmdlet está visible en más de un rol, y todos los roles permiten un conjunto diferente de parámetros, el usuario podrá ver el cmdlet y todos los parámetros definidos en cada rol.</span><span class="sxs-lookup"><span data-stu-id="9077f-222">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="9077f-223">Si un rol no tiene restricciones en los parámetros, se permitirán todos los parámetros.</span><span class="sxs-lookup"><span data-stu-id="9077f-223">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="9077f-224">Si un rol define un conjunto o patrón validado para un parámetro de cmdlet y el otro rol permite el parámetro pero no restringe los valores de parámetro, se omitirá el patrón o conjunto validado.</span><span class="sxs-lookup"><span data-stu-id="9077f-224">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="9077f-225">Si se define un conjunto validado para el mismo parámetro de cmdlet en más de un rol, se permitirán todos los valores de todos los conjuntos validados.</span><span class="sxs-lookup"><span data-stu-id="9077f-225">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="9077f-226">Si se define un patrón validado para el mismo parámetro de cmdlet en más de un rol, se permitirán todos los valores que coincidan con cualquiera de los patrones.</span><span class="sxs-lookup"><span data-stu-id="9077f-226">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="9077f-227">Si se define un conjunto validado en uno o varios roles y se define un patrón validado en otro rol para el mismo parámetro de cmdlet, se omite el conjunto validado y se aplica la regla (6) a los demás patrones validados.</span><span class="sxs-lookup"><span data-stu-id="9077f-227">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="9077f-228">A continuación se muestra un ejemplo de cómo se combinan los roles según estas reglas:</span><span class="sxs-lookup"><span data-stu-id="9077f-228">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



<span data-ttu-id="9077f-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span><span class="sxs-lookup"><span data-stu-id="9077f-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="9077f-230">Todos los demás campos del archivo de funcionalidad de rol se agregan simplemente a un conjunto acumulativo de alias, proveedores, scripts de inicio y comandos externos permitidos.</span><span class="sxs-lookup"><span data-stu-id="9077f-230">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="9077f-231">Cualquier comando, alias, proveedor o script disponible en una funcionalidad de rol estará disponible para el usuario de JEA.</span><span class="sxs-lookup"><span data-stu-id="9077f-231">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="9077f-232">Asegúrese de que el conjunto combinado de proveedores de una funcionalidad de rol y cmdlets/funciones/comandos de otra no permitan que los usuarios que se conectan obtengan acceso involuntario a recursos del sistema.</span><span class="sxs-lookup"><span data-stu-id="9077f-232">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="9077f-233">Por ejemplo, si un rol permite el cmdlet `Remove-Item` y otro permite el proveedor `FileSystem`, corre el riesgo de que un usuario de JEA elimine archivos arbitrarios de su equipo.</span><span class="sxs-lookup"><span data-stu-id="9077f-233">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="9077f-234">Puede encontrar información adicional sobre cómo identificar los permisos efectivos de los usuarios en el [tema de auditoría de JEA](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="9077f-234">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9077f-235">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="9077f-235">Next steps</span></span>

- [<span data-ttu-id="9077f-236">Crear un archivo de configuración de sesión</span><span class="sxs-lookup"><span data-stu-id="9077f-236">Create a session configuration file</span></span>](session-configurations.md)