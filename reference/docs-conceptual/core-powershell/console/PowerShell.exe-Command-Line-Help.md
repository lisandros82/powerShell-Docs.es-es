---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Ayuda para la línea de comandos de PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 60b6a7e310821a4092b0972b7abbdae0e2d5f738
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="9394e-103">Ayuda de línea de comandos de PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="9394e-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="9394e-104">Puede usar PowerShell.exe para iniciar una sesión de PowerShell desde la línea de comandos de otra herramienta (como Cmd.exe) o usarlo en la línea de comandos de PowerShell para iniciar una nueva sesión.</span><span class="sxs-lookup"><span data-stu-id="9394e-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="9394e-105">Use los parámetros para personalizar la sesión.</span><span class="sxs-lookup"><span data-stu-id="9394e-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="9394e-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9394e-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="9394e-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9394e-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="9394e-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="9394e-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="9394e-109">Acepta una versión de cadena con codificación Base 64 de un comando.</span><span class="sxs-lookup"><span data-stu-id="9394e-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="9394e-110">Use este parámetro para enviar comandos a PowerShell que requieran comillas complejas o llaves.</span><span class="sxs-lookup"><span data-stu-id="9394e-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="9394e-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="9394e-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="9394e-112">Establece la directiva de ejecución predeterminada para la sesión actual y la guarda en la variable de entorno $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="9394e-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="9394e-113">Este parámetro no modifica la directiva de ejecución de PowerShell establecida en el Registro.</span><span class="sxs-lookup"><span data-stu-id="9394e-113">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="9394e-114">Para obtener más información sobre las directivas de ejecución de PowerShell, incluida una lista de los valores válidos, vea [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="9394e-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="9394e-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="9394e-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="9394e-116">Ejecuta el script especificado en el ámbito local ("origen de puntos"), para que las funciones y variables que crea el script estén disponibles en la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="9394e-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="9394e-117">Escriba la ruta de acceso del archivo de script y los parámetros.</span><span class="sxs-lookup"><span data-stu-id="9394e-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="9394e-118">**File** debe ser el último parámetro del comando, puesto que todos los caracteres escritos después del nombre de parámetro **File** se interpretan como la ruta de acceso de archivo de script seguido de los parámetros de los parámetros del script y sus valores.</span><span class="sxs-lookup"><span data-stu-id="9394e-118">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="9394e-119">Puede incluir los parámetros de un script, así como los valores de parámetro, en el valor del parámetro **File**.</span><span class="sxs-lookup"><span data-stu-id="9394e-119">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="9394e-120">Por ejemplo: `-File .\Get-Script.ps1 -Domain Central`. Debe tenerse en cuenta que los parámetros que se pasan al script lo hacen como cadenas literales (una vez interpretados por el shell actual).</span><span class="sxs-lookup"><span data-stu-id="9394e-120">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="9394e-121">Por ejemplo, si se está en cmd.exe y se quiere pasar un valor de la variable de entorno, se usará la sintaxis de cmd.exe: `powershell -File .\test.ps1 -Sample %windir%`. En caso de usar la sintaxis de PowerShell, el script en este ejemplo recibirá el literal "$env:windir" en lugar del valor de esa variable de entorno: `powershell -File .\test.ps1 -Sample $env:windir`.</span><span class="sxs-lookup"><span data-stu-id="9394e-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="9394e-122">Normalmente, los parámetros de modificador de un script se incluyen o se omiten.</span><span class="sxs-lookup"><span data-stu-id="9394e-122">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="9394e-123">Por ejemplo, el siguiente comando usa el parámetro **All** del archivo de script Get-Script.ps1: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="9394e-123">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="9394e-124">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="9394e-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="9394e-125">Describe el formato de los datos que se envían a PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9394e-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="9394e-126">Los valores válidos son "Text" (cadenas de texto) o "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="9394e-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="9394e-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="9394e-127">-Mta</span></span>

<span data-ttu-id="9394e-128">Inicia PowerShell con un contenedor multiproceso.</span><span class="sxs-lookup"><span data-stu-id="9394e-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="9394e-129">Este parámetro se incorporó en PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="9394e-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="9394e-130">En PowerShell 3.0, el valor predeterminado es el contenedor uniproceso (STA).</span><span class="sxs-lookup"><span data-stu-id="9394e-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="9394e-131">En PowerShell 2.0, el valor predeterminado es el contenedor multiproceso (MTA).</span><span class="sxs-lookup"><span data-stu-id="9394e-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="9394e-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="9394e-132">-NoExit</span></span>

<span data-ttu-id="9394e-133">No se cierra después de ejecutar comandos de inicio.</span><span class="sxs-lookup"><span data-stu-id="9394e-133">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="9394e-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="9394e-134">-NoLogo</span></span>

<span data-ttu-id="9394e-135">Oculta la pancarta de copyright al inicio.</span><span class="sxs-lookup"><span data-stu-id="9394e-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="9394e-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="9394e-136">-NonInteractive</span></span>

<span data-ttu-id="9394e-137">No presenta un aviso interactivo al usuario.</span><span class="sxs-lookup"><span data-stu-id="9394e-137">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="9394e-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="9394e-138">-NoProfile</span></span>

<span data-ttu-id="9394e-139">No carga el perfil de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9394e-139">Does not load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="9394e-140">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="9394e-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="9394e-141">Determina cómo se formatea la salida de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9394e-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="9394e-142">Los valores válidos son "Text" (cadenas de texto) o "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="9394e-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="9394e-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="9394e-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="9394e-144">Carga el archivo de consola de PowerShell especificado.</span><span class="sxs-lookup"><span data-stu-id="9394e-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="9394e-145">Escriba la ruta de acceso y el nombre del archivo de consola.</span><span class="sxs-lookup"><span data-stu-id="9394e-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="9394e-146">Para crear un archivo de consola, use el cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9394e-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="9394e-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="9394e-147">-Sta</span></span>

<span data-ttu-id="9394e-148">Inicia PowerShell con un contenedor uniproceso.</span><span class="sxs-lookup"><span data-stu-id="9394e-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="9394e-149">En PowerShell 3.0, el valor predeterminado es el contenedor uniproceso (STA).</span><span class="sxs-lookup"><span data-stu-id="9394e-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="9394e-150">En PowerShell 2.0, el valor predeterminado es el contenedor multiproceso (MTA).</span><span class="sxs-lookup"><span data-stu-id="9394e-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="9394e-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="9394e-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="9394e-152">Inicia la versión especificada de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9394e-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="9394e-153">La versión que especifique debe estar instalada en el sistema.</span><span class="sxs-lookup"><span data-stu-id="9394e-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="9394e-154">Si PowerShell 3.0 está instalado en el equipo, los valores válidos son "2.0" y "3.0".</span><span class="sxs-lookup"><span data-stu-id="9394e-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="9394e-155">El valor predeterminado es "3.0".</span><span class="sxs-lookup"><span data-stu-id="9394e-155">The default value is "3.0".</span></span>

<span data-ttu-id="9394e-156">Si PowerShell 3.0 no está instalado, el único valor válido es "2.0".</span><span class="sxs-lookup"><span data-stu-id="9394e-156">If PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="9394e-157">Otros valores se omiten.</span><span class="sxs-lookup"><span data-stu-id="9394e-157">Other values are ignored.</span></span>

<span data-ttu-id="9394e-158">Para obtener más información, vea "[Installing Windows PowerShell](../../setup/installing-windows-powershell.md)" (Instalación de Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="9394e-158">For more information, see "[Installing Windows PowerShell](../../setup/installing-windows-powershell.md)".</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="9394e-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="9394e-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="9394e-160">Establece el estilo de ventana de la sesión.</span><span class="sxs-lookup"><span data-stu-id="9394e-160">Sets the window style for the session.</span></span> <span data-ttu-id="9394e-161">Los valores válidos son Normal, Minimizada, Maximizada y Oculta.</span><span class="sxs-lookup"><span data-stu-id="9394e-161">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="9394e-162">-Command</span><span class="sxs-lookup"><span data-stu-id="9394e-162">-Command</span></span>

<span data-ttu-id="9394e-163">Ejecuta los comandos especificados (y todos los parámetros) como si se hubiesen escrito en el símbolo del sistema de PowerShell y, después, se cierra, a menos que se especifique el parámetro NoExit.</span><span class="sxs-lookup"><span data-stu-id="9394e-163">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="9394e-164">Básicamente, cualquier texto situado tras `-Command` se envía como una sola línea de comandos a PowerShell (esto es diferente a cómo `-File` controla los parámetros que se envían a un script).</span><span class="sxs-lookup"><span data-stu-id="9394e-164">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="9394e-165">El valor del comando puede ser "-", una cadena.</span><span class="sxs-lookup"><span data-stu-id="9394e-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="9394e-166">o un bloque de scripts.</span><span class="sxs-lookup"><span data-stu-id="9394e-166">or a script block.</span></span> <span data-ttu-id="9394e-167">Si el valor de Command es "-", el texto del comando se lee de la entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="9394e-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="9394e-168">Los bloques de scripts deben incluirse entre llaves ({}).</span><span class="sxs-lookup"><span data-stu-id="9394e-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="9394e-169">Puede especificar un bloque de scripts solo cuando ejecute PowerShell.exe en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9394e-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="9394e-170">Los resultados del script se devuelven al shell principal como objetos XML deserializados, no como objetos activos.</span><span class="sxs-lookup"><span data-stu-id="9394e-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="9394e-171">Si el valor de Command es una cadena, **Command** debe ser el último parámetro del comando, porque los caracteres escritos después del comando se interpretan como argumentos del comando.</span><span class="sxs-lookup"><span data-stu-id="9394e-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="9394e-172">Para escribir una cadena que ejecute un comando de PowerShell, use el siguiente formato:</span><span class="sxs-lookup"><span data-stu-id="9394e-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="9394e-173">donde las comillas indican una cadena y el operador de invocación (&) hace que se ejecute el comando.</span><span class="sxs-lookup"><span data-stu-id="9394e-173">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="9394e-174">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="9394e-174">-Help, -?, /?</span></span>

<span data-ttu-id="9394e-175">Muestra este mensaje.</span><span class="sxs-lookup"><span data-stu-id="9394e-175">Shows this message.</span></span> <span data-ttu-id="9394e-176">Si está escribiendo un comando de PowerShell.exe en PowerShell, anteponga a los parámetros del comando un guion (-), no una barra diagonal (/).</span><span class="sxs-lookup"><span data-stu-id="9394e-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="9394e-177">Puede usar un guion o una barra diagonal en Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="9394e-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="9394e-178">Nota de solución de problemas: En PowerShell 2.0, al iniciar algunos programas en la consola de Windows PowerShell, se produce un error LastExitCode 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="9394e-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="9394e-179">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="9394e-179">EXAMPLES</span></span>

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