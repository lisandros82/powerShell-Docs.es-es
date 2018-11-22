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
# <a name="powershellexe-command-line-help"></a>Ayuda de línea de comandos de PowerShell.exe

Puede usar PowerShell.exe para iniciar una sesión de PowerShell desde la línea de comandos de otra herramienta (como Cmd.exe) o usarlo en la línea de comandos de PowerShell para iniciar una nueva sesión. Use los parámetros para personalizar la sesión.

## <a name="syntax"></a>Sintaxis

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

## <a name="parameters"></a>Parámetros

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>

Acepta una versión de cadena con codificación Base 64 de un comando. Use este parámetro para enviar comandos a PowerShell que requieran comillas complejas o llaves.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Establece la directiva de ejecución predeterminada para la sesión actual y la guarda en la variable de entorno $env:PSExecutionPolicyPreference. Este parámetro no modifica la directiva de ejecución de PowerShell establecida en el Registro. Para obtener más información sobre las directivas de ejecución de PowerShell, incluida una lista de los valores válidos, vea [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-File <FilePath> \[<Parameters>]

Ejecuta el script especificado en el ámbito local ("origen de puntos"), para que las funciones y variables que crea el script estén disponibles en la sesión actual. Escriba la ruta de acceso del archivo de script y los parámetros. **File** debe ser el último parámetro del comando. Todos los valores que se han escrito después del parámetro **-File** se interpretan como la ruta de acceso del archivo de script y los parámetros que se pasan a ese script.

Los parámetros que se pasan al script lo hacen como cadenas literales (una vez interpretados por el shell actual). Por ejemplo, si encuentra en cmd.exe y va a pasar un valor de la variable de entorno, usaría la sintaxis de cmd.exe: `powershell.exe -File .\test.ps1 -TestParam %windir%`

En cambio, ejecuta `powershell.exe -File .\test.ps1 -TestParam $env:windir` en los resultados de cmd.exe en el script de recibir la cadena literal `$env:windir` porque no tiene ningún significado especial en el shell de cmd.exe actual.
El `$env:windir` estilo de referencia de variable de entorno _puede_ utilizarse dentro de un `-Command` parámetro, ya que no existe se interpretará como código de PowerShell.

### <a name="-inputformat-text--xml"></a>\-InputFormat {Text | XML}

Describe el formato de los datos que se envían a PowerShell. Los valores válidos son "Text" (cadenas de texto) o "XML" (formato CLIXML serializado).

### <a name="-mta"></a>-Mta

Inicia PowerShell con un contenedor multiproceso. Este parámetro se incorporó en PowerShell 3.0. En PowerShell 3.0, el valor predeterminado es el contenedor uniproceso (STA). En PowerShell 2.0, el valor predeterminado es el contenedor multiproceso (MTA).

### <a name="-noexit"></a>-NoExit

No se cierra después de ejecutar comandos de inicio.

### <a name="-nologo"></a>-NoLogo

Oculta la pancarta de copyright al inicio.

### <a name="-noninteractive"></a>-NonInteractive

No presenta un aviso interactivo al usuario.

### <a name="-noprofile"></a>-NoProfile

No carga el perfil de PowerShell.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}

Determina cómo se formatea la salida de PowerShell. Los valores válidos son "Text" (cadenas de texto) o "XML" (formato CLIXML serializado).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Carga el archivo de consola de PowerShell especificado. Escriba la ruta de acceso y el nombre del archivo de consola. Para crear un archivo de consola, use el cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) de PowerShell.

### <a name="-sta"></a>-Sta

Inicia PowerShell con un contenedor uniproceso. En PowerShell 3.0, el valor predeterminado es el contenedor uniproceso (STA). En PowerShell 2.0, el valor predeterminado es el contenedor multiproceso (MTA).

### <a name="-version-powershell-version"></a>-Version <PowerShell Version>

Inicia la versión especificada de PowerShell. La versión que especifique debe estar instalada en el sistema. Si PowerShell 3.0 está instalado en el equipo, los valores válidos son "2.0" y "3.0". El valor predeterminado es "3.0".

Si PowerShell 3.0 no está instalado, el único valor válido es "2.0". Otros valores se omiten.

Para obtener más información, consulte [Instalar Windows PowerShell](../../setup/installing-windows-powershell.md).

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

Establece el estilo de ventana de la sesión. Los valores válidos son Normal, Minimizada, Maximizada y Oculta.

### <a name="-command"></a>-Command

Ejecuta los comandos especificados (con todos los parámetros) como si se hubiesen escrito en el símbolo del sistema de PowerShell.
Después de la ejecución, PowerShell se cierra, a menos que el **NoExit** se especifica el parámetro.
Cualquier texto después de `-Command` se envía como una sola línea de comandos a PowerShell.
Esto es diferente de cómo `-File` controla los parámetros enviados a un script.

El valor de `-Command` puede ser "-", una cadena o un bloque de script.
Los resultados del comando se devuelven al shell principal como objetos XML deserializados, los objetos no activos.

Si el valor de `-Command` es "-", el texto de comando se lee de la entrada estándar.

Cuando el valor de `-Command` es una cadena, **comando** _debe_ ser el último parámetro especificado porque los caracteres escritos después del comando se interpretan como argumentos del comando.

El **comando** parámetro solo acepta un bloque de script para la ejecución puede reconocer el valor pasado a `-Command` como un tipo de bloque de script.
Se trata de _sólo_ posible cuando ejecute PowerShell.exe desde otro host de PowerShell.
Hospedar el bloque de script tipo puede estar incluido en una variable, devuelto por una expresión o analizada por PowerShell existentes como un bloque de script literal entre llaves `{}`, antes de que se pasan a PowerShell.exe.

En cmd.exe, no hay nada como un bloque de script (o el tipo de bloque de script), por lo que el valor pasado a **comando** le _siempre_ sea una cadena.
Puede escribir un bloque de script dentro de una cadena, pero en lugar de que se está ejecutando, se comporta exactamente como si lo hubiera escrito en un símbolo del sistema de PowerShell típico, imprimir el contenido de la secuencia de comandos Bloquear nuevo para usted.

Una cadena pasada a `-Command` todavía se ejecutará como PowerShell, por lo que las llaves de cierre del bloque de script a menudo no son necesarias en primer lugar cuando se ejecuta desde cmd.exe.
Para ejecutar un bloque de scripts alineado definido dentro de una cadena, el [operador de llamada](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` se puede usar:

```console
"& {<command>}"
```

### <a name="-help---"></a>-Help, -?, /?

Muestra la sintaxis de powershell.exe. Si está escribiendo un comando de PowerShell.exe en PowerShell, anteponga a los parámetros del comando un guion (-), no una barra diagonal (/). Puede usar un guion o una barra diagonal en Cmd.exe.

> [!NOTE]
> Nota de solución de problemas: En PowerShell 2.0, al iniciar algunos programas en la consola de Windows PowerShell, se produce un error LastExitCode 0xc0000142.

## <a name="examples"></a>EJEMPLOS

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
