---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Ayuda para la línea de comandos de PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 03c7672ee72698fe88a73e99702ceaadf87e702f
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51691837"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="9456b-103">Ayuda de línea de comandos de PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="9456b-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="9456b-104">Puede usar PowerShell.exe para iniciar una sesión de PowerShell desde la línea de comandos de otra herramienta (como Cmd.exe) o usarlo en la línea de comandos de PowerShell para iniciar una nueva sesión.</span><span class="sxs-lookup"><span data-stu-id="9456b-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="9456b-105">Use los parámetros para personalizar la sesión.</span><span class="sxs-lookup"><span data-stu-id="9456b-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="9456b-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9456b-106">Syntax</span></span>

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="9456b-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9456b-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="9456b-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="9456b-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="9456b-109">Acepta una versión de cadena con codificación Base 64 de un comando.</span><span class="sxs-lookup"><span data-stu-id="9456b-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="9456b-110">Use este parámetro para enviar comandos a PowerShell que requieran comillas complejas o llaves.</span><span class="sxs-lookup"><span data-stu-id="9456b-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="9456b-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="9456b-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="9456b-112">Establece la directiva de ejecución predeterminada para la sesión actual y la guarda en la variable de entorno $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="9456b-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="9456b-113">Este parámetro no modifica la directiva de ejecución de PowerShell establecida en el Registro.</span><span class="sxs-lookup"><span data-stu-id="9456b-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="9456b-114">Para obtener más información sobre las directivas de ejecución de PowerShell, incluida una lista de los valores válidos, vea [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="9456b-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="9456b-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="9456b-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="9456b-116">Ejecuta el script especificado en el ámbito local ("origen de puntos"), para que las funciones y variables que crea el script estén disponibles en la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="9456b-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="9456b-117">Escriba la ruta de acceso del archivo de script y los parámetros.</span><span class="sxs-lookup"><span data-stu-id="9456b-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="9456b-118">**File** debe ser el último parámetro del comando.</span><span class="sxs-lookup"><span data-stu-id="9456b-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="9456b-119">Todos los valores que se han escrito después del parámetro **-File** se interpretan como la ruta de acceso del archivo de script y los parámetros que se pasan a ese script.</span><span class="sxs-lookup"><span data-stu-id="9456b-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="9456b-120">Los parámetros que se pasan al script lo hacen como cadenas literales (una vez interpretados por el shell actual).</span><span class="sxs-lookup"><span data-stu-id="9456b-120">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="9456b-121">Por ejemplo, si encuentra en cmd.exe y va a pasar un valor de la variable de entorno, usaría la sintaxis de cmd.exe: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="9456b-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="9456b-122">En cambio, ejecuta `powershell.exe -File .\test.ps1 -TestParam $env:windir` en los resultados de cmd.exe en el script de recibir la cadena literal `$env:windir` porque no tiene ningún significado especial en el shell de cmd.exe actual.</span><span class="sxs-lookup"><span data-stu-id="9456b-122">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe results in the script receiving the literal string `$env:windir` because it has no special meaning to the current cmd.exe shell.</span></span>
<span data-ttu-id="9456b-123">El `$env:windir` estilo de referencia de variable de entorno _puede_ utilizarse dentro de un `-Command` parámetro, ya que no existe se interpretará como código de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9456b-123">The `$env:windir` style of environment variable reference _can_ be used inside a `-Command` parameter, since there it will be interpreted as PowerShell code.</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="9456b-124">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="9456b-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="9456b-125">Describe el formato de los datos que se envían a PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9456b-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="9456b-126">Los valores válidos son "Text" (cadenas de texto) o "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="9456b-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="9456b-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="9456b-127">-Mta</span></span>

<span data-ttu-id="9456b-128">Inicia PowerShell con un contenedor multiproceso.</span><span class="sxs-lookup"><span data-stu-id="9456b-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="9456b-129">Este parámetro se incorporó en PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="9456b-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="9456b-130">En PowerShell 3.0, el valor predeterminado es el contenedor uniproceso (STA).</span><span class="sxs-lookup"><span data-stu-id="9456b-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="9456b-131">En PowerShell 2.0, el valor predeterminado es el contenedor multiproceso (MTA).</span><span class="sxs-lookup"><span data-stu-id="9456b-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="9456b-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="9456b-132">-NoExit</span></span>

<span data-ttu-id="9456b-133">No se cierra después de ejecutar comandos de inicio.</span><span class="sxs-lookup"><span data-stu-id="9456b-133">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="9456b-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="9456b-134">-NoLogo</span></span>

<span data-ttu-id="9456b-135">Oculta la pancarta de copyright al inicio.</span><span class="sxs-lookup"><span data-stu-id="9456b-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="9456b-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="9456b-136">-NonInteractive</span></span>

<span data-ttu-id="9456b-137">No presenta un aviso interactivo al usuario.</span><span class="sxs-lookup"><span data-stu-id="9456b-137">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="9456b-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="9456b-138">-NoProfile</span></span>

<span data-ttu-id="9456b-139">No carga el perfil de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9456b-139">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="9456b-140">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="9456b-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="9456b-141">Determina cómo se formatea la salida de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9456b-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="9456b-142">Los valores válidos son "Text" (cadenas de texto) o "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="9456b-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="9456b-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="9456b-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="9456b-144">Carga el archivo de consola de PowerShell especificado.</span><span class="sxs-lookup"><span data-stu-id="9456b-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="9456b-145">Escriba la ruta de acceso y el nombre del archivo de consola.</span><span class="sxs-lookup"><span data-stu-id="9456b-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="9456b-146">Para crear un archivo de consola, use el cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9456b-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="9456b-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="9456b-147">-Sta</span></span>

<span data-ttu-id="9456b-148">Inicia PowerShell con un contenedor uniproceso.</span><span class="sxs-lookup"><span data-stu-id="9456b-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="9456b-149">En PowerShell 3.0, el valor predeterminado es el contenedor uniproceso (STA).</span><span class="sxs-lookup"><span data-stu-id="9456b-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="9456b-150">En PowerShell 2.0, el valor predeterminado es el contenedor multiproceso (MTA).</span><span class="sxs-lookup"><span data-stu-id="9456b-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="9456b-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="9456b-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="9456b-152">Inicia la versión especificada de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9456b-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="9456b-153">La versión que especifique debe estar instalada en el sistema.</span><span class="sxs-lookup"><span data-stu-id="9456b-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="9456b-154">Si PowerShell 3.0 está instalado en el equipo, los valores válidos son "2.0" y "3.0".</span><span class="sxs-lookup"><span data-stu-id="9456b-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="9456b-155">El valor predeterminado es "3.0".</span><span class="sxs-lookup"><span data-stu-id="9456b-155">The default value is "3.0".</span></span>

<span data-ttu-id="9456b-156">Si PowerShell 3.0 no está instalado, el único valor válido es "2.0".</span><span class="sxs-lookup"><span data-stu-id="9456b-156">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="9456b-157">Otros valores se omiten.</span><span class="sxs-lookup"><span data-stu-id="9456b-157">Other values are ignored.</span></span>

<span data-ttu-id="9456b-158">Para obtener más información, consulte [Instalar Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="9456b-158">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="9456b-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="9456b-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="9456b-160">Establece el estilo de ventana de la sesión.</span><span class="sxs-lookup"><span data-stu-id="9456b-160">Sets the window style for the session.</span></span> <span data-ttu-id="9456b-161">Los valores válidos son Normal, Minimizada, Maximizada y Oculta.</span><span class="sxs-lookup"><span data-stu-id="9456b-161">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="9456b-162">-Command</span><span class="sxs-lookup"><span data-stu-id="9456b-162">-Command</span></span>

<span data-ttu-id="9456b-163">Ejecuta los comandos especificados (con todos los parámetros) como si se hubiesen escrito en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9456b-163">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span>
<span data-ttu-id="9456b-164">Después de la ejecución, PowerShell se cierra, a menos que el **NoExit** se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="9456b-164">After execution, PowerShell exits unless the **NoExit** parameter is specified.</span></span>
<span data-ttu-id="9456b-165">Cualquier texto después de `-Command` se envía como una sola línea de comandos a PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9456b-165">Any text after `-Command` is sent as a single command line to PowerShell.</span></span>
<span data-ttu-id="9456b-166">Esto es diferente de cómo `-File` controla los parámetros enviados a un script.</span><span class="sxs-lookup"><span data-stu-id="9456b-166">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="9456b-167">El valor de `-Command` puede ser "-", una cadena o un bloque de script.</span><span class="sxs-lookup"><span data-stu-id="9456b-167">The value of `-Command` can be "-", a string, or a script block.</span></span>
<span data-ttu-id="9456b-168">Los resultados del comando se devuelven al shell principal como objetos XML deserializados, los objetos no activos.</span><span class="sxs-lookup"><span data-stu-id="9456b-168">The results of the command are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="9456b-169">Si el valor de `-Command` es "-", el texto de comando se lee de la entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="9456b-169">If the value of `-Command` is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="9456b-170">Cuando el valor de `-Command` es una cadena, **comando** _debe_ ser el último parámetro especificado porque los caracteres escritos después del comando se interpretan como argumentos del comando.</span><span class="sxs-lookup"><span data-stu-id="9456b-170">When the value of `-Command` is a string, **Command** _must_ be the last parameter specified because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="9456b-171">El **comando** parámetro solo acepta un bloque de script para la ejecución puede reconocer el valor pasado a `-Command` como un tipo de bloque de script.</span><span class="sxs-lookup"><span data-stu-id="9456b-171">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to `-Command` as a ScriptBlock type.</span></span>
<span data-ttu-id="9456b-172">Se trata de _sólo_ posible cuando ejecute PowerShell.exe desde otro host de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9456b-172">This is _only_ possible when running PowerShell.exe from another PowerShell host.</span></span>
<span data-ttu-id="9456b-173">Hospedar el bloque de script tipo puede estar incluido en una variable, devuelto por una expresión o analizada por PowerShell existentes como un bloque de script literal entre llaves `{}`, antes de que se pasan a PowerShell.exe.</span><span class="sxs-lookup"><span data-stu-id="9456b-173">The ScriptBlock type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to PowerShell.exe.</span></span>

<span data-ttu-id="9456b-174">En cmd.exe, no hay nada como un bloque de script (o el tipo de bloque de script), por lo que el valor pasado a **comando** le _siempre_ sea una cadena.</span><span class="sxs-lookup"><span data-stu-id="9456b-174">In cmd.exe, there is no such thing as a script block (or ScriptBlock type), so the value passed to **Command** will _always_ be a string.</span></span>
<span data-ttu-id="9456b-175">Puede escribir un bloque de script dentro de una cadena, pero en lugar de que se está ejecutando, se comporta exactamente como si lo hubiera escrito en un símbolo del sistema de PowerShell típico, imprimir el contenido de la secuencia de comandos Bloquear nuevo para usted.</span><span class="sxs-lookup"><span data-stu-id="9456b-175">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="9456b-176">Una cadena pasada a `-Command` todavía se ejecutará como PowerShell, por lo que las llaves de cierre del bloque de script a menudo no son necesarias en primer lugar cuando se ejecuta desde cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="9456b-176">A string passed to `-Command` will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from cmd.exe.</span></span>
<span data-ttu-id="9456b-177">Para ejecutar un bloque de scripts alineado definido dentro de una cadena, el [operador de llamada](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` se puede usar:</span><span class="sxs-lookup"><span data-stu-id="9456b-177">To execute an inline script block defined inside a string, the [call operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` can be used:</span></span>

```console
"& {<command>}"
```

### <a name="-help---"></a><span data-ttu-id="9456b-178">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="9456b-178">-Help, -?, /?</span></span>

<span data-ttu-id="9456b-179">Muestra la sintaxis de powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="9456b-179">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="9456b-180">Si está escribiendo un comando de PowerShell.exe en PowerShell, anteponga a los parámetros del comando un guion (-), no una barra diagonal (/).</span><span class="sxs-lookup"><span data-stu-id="9456b-180">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="9456b-181">Puede usar un guion o una barra diagonal en Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="9456b-181">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="9456b-182">Nota de solución de problemas: En PowerShell 2.0, al iniciar algunos programas en la consola de Windows PowerShell, se produce un error LastExitCode 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="9456b-182">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="9456b-183">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="9456b-183">EXAMPLES</span></span>

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
