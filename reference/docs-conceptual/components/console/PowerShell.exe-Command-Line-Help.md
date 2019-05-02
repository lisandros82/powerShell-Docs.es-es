---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Ayuda para la línea de comandos de PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058520"
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

Los parámetros que se pasan al script lo hacen como cadenas literales (una vez interpretados por el shell actual). Por ejemplo, si está en cmd.exe y desea pasar un valor de variable de entorno, usaría la sintaxis de cmd.exe: `powershell.exe -File .\test.ps1 -TestParam %windir%`

En cambio, al ejecutar `powershell.exe -File .\test.ps1 -TestParam $env:windir` en cmd.exe, el script recibe la cadena literal `$env:windir` porque no tiene un significado especial para el shell cmd.exe actual.
El estilo `$env:windir` de la referencia de la variable de entorno se _puede_ usar dentro de un parámetro `-Command`, ya que allí se interpretará como código de PowerShell.

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
Después de la ejecución, PowerShell se cierra, a menos que se especifique el parámetro **NoExit**.
Cualquier texto después de `-Command` se envía como una sola línea de comandos a PowerShell.
Esto es diferente de cómo `-File` controla los parámetros enviados a un script.

El valor de `-Command` puede ser "-", una cadena o un bloque de script.
Los resultados del comando se devuelven al shell principal como objetos XML deserializados, no como objetos activos.

Si el valor de `-Command` es "-", el texto del comando se lee de la entrada estándar.

Si el valor de `-Command` es una cadena, **Command** _debe_ ser el último parámetro del comando, porque los caracteres escritos después del comando se interpretan como argumentos del comando.

El parámetro **Command** solo acepta un bloque de script para su ejecución cuando puede reconocer el valor pasado a `-Command` como un tipo de ScriptBlock.
Esto _solo_ es posible cuando ejecuta PowerShell.exe desde otro host de PowerShell.
El tipo ScriptBlock puede contenerse en una variable existente, devolverse desde una expresión o analizarse por el host de PowerShell como un bloque de script literal incluido entre llaves `{}`, antes de pasarlo a PowerShell.exe.

En cmd.exe, no hay nada como un bloque de scripts (o tipo ScriptBlock), por lo que el valor pasado a **Command** será _siempre_ una cadena.
Puede escribir un bloque de script dentro de la cadena, pero en lugar de ejecutarse, se comportará exactamente como si lo hubiera escrito en una solicitud de PowerShell típica, devolviéndole los contenidos impresos del bloque de script.

Una cadena pasada a `-Command` se seguirá ejecutando como PowerShell, por lo que las llaves del bloque de script a menudo no son necesarias cuando se ejecutan en primer lugar desde cmd.exe.
Para ejecutar un bloque de script alineado definido dentro de una cadena, se puede usar el [operador de llamada](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&`:

```console
"& {<command>}"
```

### <a name="-help---"></a>-Help, -?, /?

Muestra la sintaxis de powershell.exe. Si está escribiendo un comando de PowerShell.exe en PowerShell, anteponga a los parámetros del comando un guion (-), no una barra diagonal (/). Puede usar un guion o una barra diagonal en Cmd.exe.

> [!NOTE]
> Nota para la solución de problemas: En PowerShell 2.0, al iniciar algunos programas en la consola de Windows PowerShell, se produce un error LastExitCode 0xc0000142.

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
