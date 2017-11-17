---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Ayuda para la línea de comandos de PowerShell.exe"
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c2583dac14f32db414f0a4377b1694ab7fa7523b
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="6bbcb-103">Ayuda de línea de comandos de PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="6bbcb-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="6bbcb-104">Inicia una sesión de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-104">Starts a Windows PowerShell session.</span></span> <span data-ttu-id="6bbcb-105">Puede usar PowerShell.exe para iniciar una sesión de Windows PowerShell desde la línea de comandos de otra herramienta, como Cmd.exe, o usarlo en la línea de comandos de Windows PowerShell para iniciar una nueva sesión.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-105">You can use PowerShell.exe to start a Windows PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the Windows PowerShell command line to start a new session.</span></span> <span data-ttu-id="6bbcb-106">Use los parámetros para personalizar la sesión.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="6bbcb-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="6bbcb-107">Syntax</span></span>

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
       [-PSConsoleFile <FilePath> | -Version <Windows PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]
        

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="6bbcb-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="6bbcb-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="6bbcb-109">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="6bbcb-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="6bbcb-110">Acepta una versión de cadena con codificación Base 64 de un comando.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="6bbcb-111">Use este parámetro para enviar comandos a Windows PowerShell que requieran comillas complejas o llaves.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-111">Use this parameter to submit commands to Windows PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="6bbcb-112">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="6bbcb-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="6bbcb-113">Establece la directiva de ejecución predeterminada para la sesión actual y la guarda en la variable de entorno $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="6bbcb-114">Este parámetro no modifica la directiva de ejecución de Windows PowerShell establecida en el Registro.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-114">This parameter does not change the Windows PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="6bbcb-115">Para más información sobre las directivas de ejecución de Windows PowerShell, incluida una lista de los valores válidos, vea about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span><span class="sxs-lookup"><span data-stu-id="6bbcb-115">For information about Windows PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="6bbcb-116">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="6bbcb-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="6bbcb-117">Ejecuta el script especificado en el ámbito local ("origen de puntos"), para que las funciones y variables que crea el script estén disponibles en la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="6bbcb-118">Escriba la ruta de acceso del archivo de script y los parámetros.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="6bbcb-119">**File** debe ser el último parámetro del comando, puesto que todos los caracteres escritos después del nombre de parámetro **File** se interpretan como la ruta de acceso de archivo de script seguido de los parámetros de los parámetros del script y sus valores.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="6bbcb-120">Puede incluir los parámetros de un script, así como los valores de parámetro, en el valor del parámetro **File**.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="6bbcb-121">Por ejemplo: `-File .\Get-Script.ps1 -Domain Central`. Debe tenerse en cuenta que los parámetros que se pasan al script lo hacen como cadenas literales (una vez interpretados por el shell actual).</span><span class="sxs-lookup"><span data-stu-id="6bbcb-121">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="6bbcb-122">Por ejemplo, si se está en cmd.exe y se quiere pasar un valor de la variable de entorno, se usará la sintaxis de cmd.exe: `powershell -File .\test.ps1 -Sample %windir%`. En caso de usar la sintaxis de PowerShell, el script en este ejemplo recibirá el literal "$env:windir" en lugar del valor de esa variable de entorno: `powershell -File .\test.ps1 -Sample $env:windir`.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-122">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="6bbcb-123">Normalmente, los parámetros de modificador de un script se incluyen o se omiten.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-123">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="6bbcb-124">Por ejemplo, el siguiente comando usa el parámetro **All** del archivo de script Get-Script.ps1: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="6bbcb-124">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="6bbcb-125">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="6bbcb-125">\-InputFormat {Text | XML}</span></span>
<span data-ttu-id="6bbcb-126">Describe el formato de los datos que se envían a Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-126">Describes the format of data sent to Windows PowerShell.</span></span> <span data-ttu-id="6bbcb-127">Los valores válidos son "Text" (cadenas de texto) o "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="6bbcb-127">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="6bbcb-128">-Mta</span><span class="sxs-lookup"><span data-stu-id="6bbcb-128">-Mta</span></span>
<span data-ttu-id="6bbcb-129">Inicia Windows PowerShell con un contenedor multiproceso.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-129">Starts Windows PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="6bbcb-130">Este parámetro se incorporó en Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-130">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="6bbcb-131">En Windows PowerShell 3.0, el valor predeterminado es el contenedor uniproceso (STA).</span><span class="sxs-lookup"><span data-stu-id="6bbcb-131">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="6bbcb-132">En Windows PowerShell 2.0, el valor predeterminado es el contenedor multiproceso (MTA).</span><span class="sxs-lookup"><span data-stu-id="6bbcb-132">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="6bbcb-133">-NoExit</span><span class="sxs-lookup"><span data-stu-id="6bbcb-133">-NoExit</span></span>
<span data-ttu-id="6bbcb-134">No se cierra después de ejecutar comandos de inicio.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-134">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="6bbcb-135">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="6bbcb-135">-NoLogo</span></span>
<span data-ttu-id="6bbcb-136">Oculta la pancarta de copyright al inicio.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-136">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="6bbcb-137">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="6bbcb-137">-NonInteractive</span></span>
<span data-ttu-id="6bbcb-138">No presenta un aviso interactivo al usuario.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-138">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="6bbcb-139">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="6bbcb-139">-NoProfile</span></span>
<span data-ttu-id="6bbcb-140">No carga el perfil de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-140">Does not load the Windows PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="6bbcb-141">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="6bbcb-141">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="6bbcb-142">Determina cómo se formatea la salida de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-142">Determines how output from Windows PowerShell is formatted.</span></span> <span data-ttu-id="6bbcb-143">Los valores válidos son "Text" (cadenas de texto) o "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="6bbcb-143">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="6bbcb-144">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="6bbcb-144">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="6bbcb-145">Carga el archivo de consola de Windows PowerShell especificado.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-145">Loads the specified Windows PowerShell console file.</span></span> <span data-ttu-id="6bbcb-146">Escriba la ruta de acceso y el nombre del archivo de consola.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-146">Enter the path and name of the console file.</span></span> <span data-ttu-id="6bbcb-147">Para crear un archivo de consola, use el cmdlet [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-147">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in Windows PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="6bbcb-148">-Sta</span><span class="sxs-lookup"><span data-stu-id="6bbcb-148">-Sta</span></span>
<span data-ttu-id="6bbcb-149">Inicia Windows PowerShell con un contenedor uniproceso.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-149">Starts Windows PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="6bbcb-150">En Windows PowerShell 3.0, el valor predeterminado es el contenedor uniproceso (STA).</span><span class="sxs-lookup"><span data-stu-id="6bbcb-150">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="6bbcb-151">En Windows PowerShell 2.0, el valor predeterminado es el contenedor multiproceso (MTA).</span><span class="sxs-lookup"><span data-stu-id="6bbcb-151">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-windows-powershell-version"></a><span data-ttu-id="6bbcb-152">-Version <Windows PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="6bbcb-152">-Version <Windows PowerShell Version></span></span>
<span data-ttu-id="6bbcb-153">Inicia la versión especificada de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-153">Starts the specified version of Windows PowerShell.</span></span> <span data-ttu-id="6bbcb-154">La versión que especifique debe estar instalada en el sistema.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-154">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="6bbcb-155">Si Windows PowerShell 3.0 está instalado en el equipo, los valores válidos son "2.0" y "3.0".</span><span class="sxs-lookup"><span data-stu-id="6bbcb-155">If Windows PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="6bbcb-156">El valor predeterminado es "3.0".</span><span class="sxs-lookup"><span data-stu-id="6bbcb-156">The default value is "3.0".</span></span>

<span data-ttu-id="6bbcb-157">Si Windows PowerShell 3.0 no está instalado, el único valor válido es "2.0".</span><span class="sxs-lookup"><span data-stu-id="6bbcb-157">If Windows PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="6bbcb-158">Otros valores se omiten.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-158">Other values are ignored.</span></span>

<span data-ttu-id="6bbcb-159">Para más información, consulte "Instalación de Windows PowerShell" en [Introducción a Windows PowerShell [antiguo MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span><span class="sxs-lookup"><span data-stu-id="6bbcb-159">For more information, see "Installing Windows PowerShell" in the [Getting Started with Windows PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="6bbcb-160">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="6bbcb-160">-WindowStyle <Window style></span></span>
<span data-ttu-id="6bbcb-161">Establece el estilo de ventana de la sesión.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-161">Sets the window style for the session.</span></span> <span data-ttu-id="6bbcb-162">Los valores válidos son Normal, Minimizada, Maximizada y Oculta.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-162">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="6bbcb-163">-Command</span><span class="sxs-lookup"><span data-stu-id="6bbcb-163">-Command</span></span>
<span data-ttu-id="6bbcb-164">Ejecuta los comandos especificados (y todos los parámetros) como si se hubiesen escrito en el símbolo del sistema de Windows PowerShell y, después, se cierra, a menos que se especifique el parámetro NoExit.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-164">Executes the specified commands (and any parameters) as though they were typed at the Windows PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="6bbcb-165">Básicamente, cualquier texto situado tras `-Command` se envía como una sola línea de comandos a PowerShell (esto es diferente a cómo `-File` controla los parámetros que se envían a un script).</span><span class="sxs-lookup"><span data-stu-id="6bbcb-165">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="6bbcb-166">El valor del comando puede ser "-", una cadena.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="6bbcb-167">o un bloque de scripts.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-167">or a script block.</span></span> <span data-ttu-id="6bbcb-168">Si el valor de Command es "-", el texto del comando se lee de la entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="6bbcb-169">Los bloques de scripts deben incluirse entre llaves ({}).</span><span class="sxs-lookup"><span data-stu-id="6bbcb-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="6bbcb-170">Puede especificar un bloque de scripts solo cuando ejecute PowerShell.exe en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-170">You can specify a script block only when running PowerShell.exe in Windows PowerShell.</span></span> <span data-ttu-id="6bbcb-171">Los resultados del script se devuelven al shell principal como objetos XML deserializados, no como objetos activos.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="6bbcb-172">Si el valor de Command es una cadena, **Command** debe ser el último parámetro del comando, porque los caracteres escritos después del comando se interpretan como argumentos del comando.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-172">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="6bbcb-173">Para escribir una cadena que ejecute un comando de Windows PowerShell, use el formato:</span><span class="sxs-lookup"><span data-stu-id="6bbcb-173">To write a string that runs a Windows PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="6bbcb-174">donde las comillas indican una cadena y el operador de invocación (&) hace que se ejecute el comando.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="6bbcb-175">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="6bbcb-175">-Help, -?, /?</span></span>
<span data-ttu-id="6bbcb-176">Muestra este mensaje.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-176">Shows this message.</span></span> <span data-ttu-id="6bbcb-177">Si está escribiendo un comando de PowerShell.exe en Windows PowerShell, anteponga a los parámetros del comando un guion (-), no una barra diagonal (/).</span><span class="sxs-lookup"><span data-stu-id="6bbcb-177">If you are typing a PowerShell.exe command in Windows PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="6bbcb-178">Puede usar un guion o una barra diagonal en Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="6bbcb-179">Nota de solución de problemas: En Windows PowerShell 2.0, al iniciar algunos programas en la consola de Windows PowerShell, se produce un error LastExitCode 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="6bbcb-179">Troubleshooting Note: In Windows PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="6bbcb-180">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="6bbcb-180">EXAMPLES</span></span>

```
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a Powerhell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate wayh to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

