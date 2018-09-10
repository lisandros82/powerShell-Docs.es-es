---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Ayuda para la línea de comandos de PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c7f35511e876e8e5189d8a2b949555603d43f731
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133122"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="e2975-103">Ayuda de línea de comandos de PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="e2975-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="e2975-104">Puede usar PowerShell.exe para iniciar una sesión de PowerShell desde la línea de comandos de otra herramienta (como Cmd.exe) o usarlo en la línea de comandos de PowerShell para iniciar una nueva sesión.</span><span class="sxs-lookup"><span data-stu-id="e2975-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="e2975-105">Use los parámetros para personalizar la sesión.</span><span class="sxs-lookup"><span data-stu-id="e2975-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="e2975-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e2975-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="e2975-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e2975-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="e2975-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="e2975-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="e2975-109">Acepta una versión de cadena con codificación Base 64 de un comando.</span><span class="sxs-lookup"><span data-stu-id="e2975-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="e2975-110">Use este parámetro para enviar comandos a PowerShell que requieran comillas complejas o llaves.</span><span class="sxs-lookup"><span data-stu-id="e2975-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="e2975-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="e2975-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="e2975-112">Establece la directiva de ejecución predeterminada para la sesión actual y la guarda en la variable de entorno $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="e2975-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="e2975-113">Este parámetro no modifica la directiva de ejecución de PowerShell establecida en el Registro.</span><span class="sxs-lookup"><span data-stu-id="e2975-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="e2975-114">Para obtener más información sobre las directivas de ejecución de PowerShell, incluida una lista de los valores válidos, vea [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="e2975-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="e2975-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="e2975-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="e2975-116">Ejecuta el script especificado en el ámbito local ("origen de puntos"), para que las funciones y variables que crea el script estén disponibles en la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="e2975-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="e2975-117">Escriba la ruta de acceso del archivo de script y los parámetros.</span><span class="sxs-lookup"><span data-stu-id="e2975-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="e2975-118">**File** debe ser el último parámetro del comando.</span><span class="sxs-lookup"><span data-stu-id="e2975-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="e2975-119">Todos los valores que se han escrito después del parámetro **-File** se interpretan como la ruta de acceso del archivo de script y los parámetros que se pasan a ese script.</span><span class="sxs-lookup"><span data-stu-id="e2975-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="e2975-120">Los parámetros que se pasan al script lo hacen como cadenas literales (una vez interpretados por el shell actual).</span><span class="sxs-lookup"><span data-stu-id="e2975-120">Parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span> <span data-ttu-id="e2975-121">Por ejemplo, si se está en cmd.exe y se quiere pasar un valor de la variable de entorno, se usará la sintaxis de cmd.exe: `powershell -File .\test.ps1 -Sample %windir%`. En este ejemplo, el script recibe la cadena literal `$env:windir` en lugar del valor de esa variable de entorno: `powershell -File .\test.ps1 -Sample $env:windir`.</span><span class="sxs-lookup"><span data-stu-id="e2975-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` In this example, the script receives the literal string `$env:windir` and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="e2975-122">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="e2975-122">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="e2975-123">Describe el formato de los datos que se envían a PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2975-123">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="e2975-124">Los valores válidos son "Text" (cadenas de texto) o "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="e2975-124">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="e2975-125">-Mta</span><span class="sxs-lookup"><span data-stu-id="e2975-125">-Mta</span></span>

<span data-ttu-id="e2975-126">Inicia PowerShell con un contenedor multiproceso.</span><span class="sxs-lookup"><span data-stu-id="e2975-126">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="e2975-127">Este parámetro se incorporó en PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="e2975-127">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="e2975-128">En PowerShell 3.0, el valor predeterminado es el contenedor uniproceso (STA).</span><span class="sxs-lookup"><span data-stu-id="e2975-128">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="e2975-129">En PowerShell 2.0, el valor predeterminado es el contenedor multiproceso (MTA).</span><span class="sxs-lookup"><span data-stu-id="e2975-129">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="e2975-130">-NoExit</span><span class="sxs-lookup"><span data-stu-id="e2975-130">-NoExit</span></span>

<span data-ttu-id="e2975-131">No se cierra después de ejecutar comandos de inicio.</span><span class="sxs-lookup"><span data-stu-id="e2975-131">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="e2975-132">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="e2975-132">-NoLogo</span></span>

<span data-ttu-id="e2975-133">Oculta la pancarta de copyright al inicio.</span><span class="sxs-lookup"><span data-stu-id="e2975-133">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="e2975-134">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="e2975-134">-NonInteractive</span></span>

<span data-ttu-id="e2975-135">No presenta un aviso interactivo al usuario.</span><span class="sxs-lookup"><span data-stu-id="e2975-135">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="e2975-136">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="e2975-136">-NoProfile</span></span>

<span data-ttu-id="e2975-137">No carga el perfil de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2975-137">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="e2975-138">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="e2975-138">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="e2975-139">Determina cómo se formatea la salida de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2975-139">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="e2975-140">Los valores válidos son "Text" (cadenas de texto) o "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="e2975-140">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="e2975-141">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="e2975-141">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="e2975-142">Carga el archivo de consola de PowerShell especificado.</span><span class="sxs-lookup"><span data-stu-id="e2975-142">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="e2975-143">Escriba la ruta de acceso y el nombre del archivo de consola.</span><span class="sxs-lookup"><span data-stu-id="e2975-143">Enter the path and name of the console file.</span></span> <span data-ttu-id="e2975-144">Para crear un archivo de consola, use el cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2975-144">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="e2975-145">-Sta</span><span class="sxs-lookup"><span data-stu-id="e2975-145">-Sta</span></span>

<span data-ttu-id="e2975-146">Inicia PowerShell con un contenedor uniproceso.</span><span class="sxs-lookup"><span data-stu-id="e2975-146">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="e2975-147">En PowerShell 3.0, el valor predeterminado es el contenedor uniproceso (STA).</span><span class="sxs-lookup"><span data-stu-id="e2975-147">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="e2975-148">En PowerShell 2.0, el valor predeterminado es el contenedor multiproceso (MTA).</span><span class="sxs-lookup"><span data-stu-id="e2975-148">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="e2975-149">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="e2975-149">-Version <PowerShell Version></span></span>

<span data-ttu-id="e2975-150">Inicia la versión especificada de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2975-150">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="e2975-151">La versión que especifique debe estar instalada en el sistema.</span><span class="sxs-lookup"><span data-stu-id="e2975-151">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="e2975-152">Si PowerShell 3.0 está instalado en el equipo, los valores válidos son "2.0" y "3.0".</span><span class="sxs-lookup"><span data-stu-id="e2975-152">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="e2975-153">El valor predeterminado es "3.0".</span><span class="sxs-lookup"><span data-stu-id="e2975-153">The default value is "3.0".</span></span>

<span data-ttu-id="e2975-154">Si PowerShell 3.0 no está instalado, el único valor válido es "2.0".</span><span class="sxs-lookup"><span data-stu-id="e2975-154">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="e2975-155">Otros valores se omiten.</span><span class="sxs-lookup"><span data-stu-id="e2975-155">Other values are ignored.</span></span>

<span data-ttu-id="e2975-156">Para obtener más información, consulte [Instalar Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="e2975-156">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="e2975-157">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="e2975-157">-WindowStyle <Window style></span></span>

<span data-ttu-id="e2975-158">Establece el estilo de ventana de la sesión.</span><span class="sxs-lookup"><span data-stu-id="e2975-158">Sets the window style for the session.</span></span> <span data-ttu-id="e2975-159">Los valores válidos son Normal, Minimizada, Maximizada y Oculta.</span><span class="sxs-lookup"><span data-stu-id="e2975-159">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="e2975-160">-Command</span><span class="sxs-lookup"><span data-stu-id="e2975-160">-Command</span></span>

<span data-ttu-id="e2975-161">Ejecuta los comandos especificados (con todos los parámetros) como si se hubiesen escrito en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2975-161">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span> <span data-ttu-id="e2975-162">Después de la ejecución, PowerShell se cierra a menos que se especifique el parámetro `-NoExit`.</span><span class="sxs-lookup"><span data-stu-id="e2975-162">After execution, PowerShell exits unless the `-NoExit` parameter is specified.</span></span>
<span data-ttu-id="e2975-163">Cualquier texto después de `-Command` se envía como una sola línea de comandos a PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2975-163">Any text after `-Command` is sent as a single command line to PowerShell.</span></span> <span data-ttu-id="e2975-164">Esto es diferente de cómo `-File` controla los parámetros enviados a un script.</span><span class="sxs-lookup"><span data-stu-id="e2975-164">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="e2975-165">El valor del comando puede ser "-", una cadena.</span><span class="sxs-lookup"><span data-stu-id="e2975-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="e2975-166">o un bloque de scripts.</span><span class="sxs-lookup"><span data-stu-id="e2975-166">or a script block.</span></span> <span data-ttu-id="e2975-167">Si el valor de Command es "-", el texto del comando se lee de la entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="e2975-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="e2975-168">Los bloques de scripts deben incluirse entre llaves ({}).</span><span class="sxs-lookup"><span data-stu-id="e2975-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="e2975-169">Puede especificar un bloque de scripts solo cuando ejecute PowerShell.exe en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2975-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="e2975-170">Los resultados del script se devuelven al shell principal como objetos XML deserializados, no como objetos activos.</span><span class="sxs-lookup"><span data-stu-id="e2975-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="e2975-171">Si el valor de Command es una cadena, **Command** debe ser el último parámetro del comando, porque los caracteres escritos después del comando se interpretan como argumentos del comando.</span><span class="sxs-lookup"><span data-stu-id="e2975-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="e2975-172">Para escribir una cadena que ejecute un comando de PowerShell, use el siguiente formato:</span><span class="sxs-lookup"><span data-stu-id="e2975-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="e2975-173">Las comillas indican una cadena y el operador de invocación (&) hace que se ejecute el comando.</span><span class="sxs-lookup"><span data-stu-id="e2975-173">The quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="e2975-174">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="e2975-174">-Help, -?, /?</span></span>

<span data-ttu-id="e2975-175">Muestra la sintaxis de powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="e2975-175">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="e2975-176">Si está escribiendo un comando de PowerShell.exe en PowerShell, anteponga a los parámetros del comando un guion (-), no una barra diagonal (/).</span><span class="sxs-lookup"><span data-stu-id="e2975-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="e2975-177">Puede usar un guion o una barra diagonal en Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="e2975-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="e2975-178">Nota de solución de problemas: En PowerShell 2.0, al iniciar algunos programas en la consola de Windows PowerShell, se produce un error LastExitCode 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="e2975-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="e2975-179">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="e2975-179">EXAMPLES</span></span>

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
