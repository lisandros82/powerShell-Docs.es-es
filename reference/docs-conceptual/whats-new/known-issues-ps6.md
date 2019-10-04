---
ms.date: 05/17/2018
keywords: powershell,core
title: Problemas conocidos de PowerShell 6.0
ms.openlocfilehash: e84dd2f7deefcc64aea09585e7ce24dc1e8515fc
ms.sourcegitcommit: a35450f420dc10a02379f6e6f08a28ad11fe5a6d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2019
ms.locfileid: "71692220"
---
# <a name="known-issues-for-powershell-60"></a>Problemas conocidos de PowerShell 6.0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Problemas conocidos de PowerShell en plataformas que no son de Windows

Las versiones alfa de PowerShell en Linux y macOS son mayoritariamente funcionales, pero presentan algunas limitaciones significativas y problemas de facilidad de uso. Las versiones beta de PowerShell en Linux y macOS son más funcionales y estables que las versiones alfa, pero aún puede que carezcan de algún conjunto de características y pueden contener errores. En algunos casos, estos problemas son solo errores que no se han corregido todavía. En otros casos (como con los alias predeterminados de ls, cp, etc.), buscamos comentarios de la comunidad relativos a las elecciones que hacemos.

Nota: Debido a las similitudes de muchos sistemas subyacentes, PowerShell en Linux y macOS suelen compartir el mismo nivel de madurez en ambas características y errores. Excepto lo indicado a continuación, los problemas de esta sección se aplicarán a ambos sistemas operativos.

### <a name="case-sensitivity-in-powershell"></a>Distinción de mayúsculas y minúsculas en PowerShell

Históricamente, PowerShell ha distinguido entre mayúsculas y minúsculas de manera uniforme, con algunas excepciones. En los sistemas operativos similares a UNIX, el sistema de archivos distingue mayúsculas de minúsculas fundamentalmente y PowerShell se ajusta al estándar del sistema de archivos; este se expone de varias formas, obvias y no obvias.

#### <a name="directly"></a>Directamente

- Al especificar un archivo en PowerShell, deben usarse las mayúsculas y minúsculas correctas.

#### <a name="indirectly"></a>Indirectamente

- Si un script intenta cargar un módulo y el nombre del módulo no utiliza las mayúsculas y minúsculas correctamente, no se cargará el módulo. Esto puede provocar un problema con los scripts existentes si el nombre por el que se hace referencia al módulo no coincide con el nombre de archivo real.
- La finalización con tabulación no se completará automáticamente si las mayúsculas y minúsculas del nombre de archivo son incorrectas. El fragmento que se va a completar debe utilizar las mayúsculas y minúsculas correctamente (la finalización no distingue mayúsculas de minúsculas en el caso de las finalizaciones del miembro de tipo y el nombre de tipo).

### <a name="ps1-file-extensions"></a>Extensiones de archivo .PS1

Los scripts de PowerShell deben terminar en `.ps1` para que el intérprete sepa cómo cargarlos y ejecutarlos en el proceso actual. La ejecución de los scripts en el proceso actual es el comportamiento habitual esperado de PowerShell. El número mágico `#!` se puede agregar a un script que no tiene una extensión `.ps1`, pero esto hará que el script se ejecute en una nueva instancia de PowerShell que impedirá el correcto funcionamiento del script al intercambiar objetos (Nota: Este puede ser el comportamiento deseable al ejecutar un script de PowerShell desde `bash` u otro shell).

### <a name="missing-command-aliases"></a>Alias de comandos que faltan

En Linux/macOS, los "alias cómodos" de los comandos básicos `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount` y `ps` se han quitado. En Windows, PowerShell proporciona un conjunto de alias que se asignan a nombres de comandos de Linux para la comodidad del usuario. Estos alias se han quitado del PowerShell predeterminado en distribuciones de Linux/macOS, lo que permite al archivo ejecutable nativo ejecutarse sin especificar una ruta de acceso.

Hacer esto tiene pros y contras. La retirada de los alias expone la experiencia de comando nativo al usuario de PowerShell, pero reduce la funcionalidad en el shell porque los comandos nativos devuelven cadenas en lugar de objetos.

> [!NOTE]
> Esta es un área en la que el equipo de PowerShell busca comentarios.
> ¿Cuál es la solución preferida? ¿Debemos dejarla tal cual o volver a agregar los alias cómodos? Consulte [Issue #929](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Compatibilidad con caracteres comodín (uso global) que falta

Actualmente, PowerShell solo realiza la expansión de caracteres comodín (uso global) para cmdlets integrados en Windows y para comandos o archivos binarios, así como cmdlets en Linux. Esto significa que un comando como `ls
*.txt` producirá un error porque el asterisco no se expandirá para coincidir con los nombres de archivo. Puede solucionar esto haciendo `ls (gci *.txt | % name)` o, de forma más sencilla, `gci *.txt` con el equivalente integrado de PowerShell a `ls`.

Consulte [#954](https://github.com/PowerShell/PowerShell/issues/954) para proporcionarnos comentarios sobre cómo mejorar la experiencia de uso global en Linux/macOS.

### <a name="net-framework-vs-net-core-framework"></a>.NET Framework frente a .NET Core Framework

PowerShell en Linux/macOS usa .NET Core, que es un subconjunto de la instancia completa de .NET Framework en Microsoft Windows. Esto es significativo porque PowerShell proporciona acceso directo a los tipos de marco subyacentes, métodos, etc. Como resultado, los scripts que se ejecutan en Windows pueden no ejecutarse en plataformas que no son de Windows por las diferencias en los marcos. Para obtener más información sobre .NET Core Framework, vea [dotnetfoundation.org](https://dotnetfoundation.org/).

Con la llegada de [.NET Standard2.0](https://devblogs.microsoft.com/dotnet/introducing-net-standard/), .NET Core 2.0 volverá a traer muchos de los tipos y métodos tradicionales presentes en la instancia completa de .NET Framework. Esto significa que PowerShell Core podrá cargar muchos módulos de Windows PowerShell tradicionales sin modificación. Puede seguir nuestro trabajo relacionado con .NET Standard 2.0 [aquí](https://github.com/PowerShell/PowerShell/projects/4).

### <a name="redirection-issues"></a>Problemas de redireccionamiento

El redireccionamiento de entrada no se admite en PowerShell en ninguna plataforma.
[Issue #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Use `Get-Content` para escribir el contenido de un archivo en la canalización.

La salida redirigida incluirá la marca de orden de bytes (BOM) Unicode al usarse la codificación UTF-8 predeterminada. La BOM provocará problemas al trabajar con utilidades que no la esperan o al anexar a un archivo. Use `-Encoding Ascii` para escribir texto ASCII (que, al no ser Unicode, no tendrá una BOM)

> [!Note]
> consulte [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) para proporcionarnos comentarios sobre cómo mejorar la experiencia de codificación para PowerShell Core en todas las plataformas. Estamos trabajando para admitir UTF-8 sin una BOM y cambiando potencialmente los valores predeterminados de codificación para diversos cmdlets de las plataformas.

### <a name="job-control"></a>Control de trabajo

No hay ninguna funcionalidad de control de trabajo en PowerShell en Linux/macOS.
Los comandos `fg` y `bg` no están disponibles.

De momento, puede usar [trabajos de PowerShell](/powershell/module/microsoft.powershell.core/about/about_jobs) que funcionan en todas las plataformas.

### <a name="remoting-support"></a>Compatibilidad con la comunicación remota

Actualmente, PowerShell Core admite la Comunicación remota de PowerShell (PSRP) sobre WSMan con la autenticación básica en macOS y Linux, y con la autenticación basada en NTLM en Linux (no se admite la autenticación basada en Kerberos).

El trabajo para la comunicación remota basada en WSMan se realiza en el repositorio [psl-omi-provider](https://github.com/PowerShell/psl-omi-provider).

PowerShell Core también admite la Comunicación remota de PowerShell (PSRP) sobre SSH en todas las plataformas (Windows, macOS y Linux). Aunque no se admite actualmente en producción, puede obtener más información sobre cómo configurarla [aquí](../learn/remoting/SSH-Remoting-in-PowerShell-Core.md).

### <a name="just-enough-administration-jea-support"></a>Compatibilidad con Just Enough Administration (JEA)

La capacidad para crear puntos de conexión de comunicación remota de administración restringida (JEA) no está disponible actualmente en PowerShell en Linux/macOS. Esta característica no está actualmente en el ámbito de 6.0 y es algo que consideraremos posterior a 6.0, ya que necesita un trabajo de diseño significativo.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec` y PowerShell

Dado que PowerShell ejecuta la mayoría de los comandos en la memoria (como Python o Ruby), no puede usar sudo directamente con elementos integrados de PowerShell (puede, por supuesto, ejecutar `pwsh` desde sudo). Si es necesario ejecutar un cmdlet de PowerShell desde dentro de PowerShell con sudo, por ejemplo, `sudo Set-Date 8/18/2016`, haría `sudo pwsh Set-Date 8/18/2016`. Del mismo modo, no puede ejecutar un elemento integrado de PowerShell directamente. En su lugar, tendría que hacer `exec pwsh item_to_exec`.

Actualmente se realiza un seguimiento de este problema como parte de [#3232](https://github.com/PowerShell/PowerShell/issues/3232).

### <a name="missing-cmdlets"></a>Cmdlets que faltan

Un gran número de los comandos (cmdlets) normalmente disponibles en PowerShell no están disponibles en Linux/macOS. En muchos casos, estos comandos no tienen sentido en estas plataformas (p. ej., características específicas de Windows como el registro). Otros comandos como los comandos de control de servicios (Get/Start/Stop-Service) están presentes, pero no son funcionales. Las versiones futuras corregirán estos problemas, reparando los cmdlets rotos y agregando nuevos con el tiempo.

### <a name="command-availability"></a>Disponibilidad de los comandos

En la siguiente tabla se incluyen comandos conocidos por no funcionar en PowerShell en Linux/macOS.

|Comandos|Estado de funcionamiento|Notas|
|--------|-----------------|-----|
|`Get-Service`, `New-Service`, `Restart-Service`, `Resume-Service`, `Set-Service`, `Start-Service`, `Stop-Service`, `Suspend-Service`|No disponible.|Estos comandos no se reconocerán. Esto debe corregirse en una versión futura.|
|`Get-Acl`, `Set-Acl`|No está disponible.|Estos comandos no se reconocerán. Esto debe corregirse en una versión futura.|
|`Get-AuthenticodeSignature`, `Set-AuthenticodeSignature`|No está disponible.|Estos comandos no se reconocerán. Esto debe corregirse en una versión futura.|
|`Wait-Process`|Disponible, no funciona correctamente. |Por ejemplo `Start-Process gvim -PassThru | Wait-Process` no funciona; no se puede esperar el proceso.|
|`Register-PSSessionConfiguration`, `Unregister-PSSessionConfiguration`, `Get-PSSessionConfiguration`|Disponible pero no funciona.|Escribe un mensaje de error que indica que los comandos no funcionan. Esto debe corregirse en una versión futura.|
|`Get-Event`, `New-Event`, `Register-EngineEvent`, `Register-WmiEvent`, `Remove-Event`, `Unregister-Event`|Disponible pero no hay ningún origen del evento disponible.|Los comandos de eventos de PowerShell están presentes, pero la mayoría de los orígenes del evento usados con los comandos (como System.Timers.Timer) no están disponibles en Linux, lo que hace que los comandos no sirvan para nada en la versión alfa.|
|`Set-ExecutionPolicy`|Disponible pero no funciona.|Devuelve un mensaje informando que no se admite en esta plataforma. La directiva de ejecución es un "cinturón de seguridad" centrado en el usuario que ayuda a impedir que el usuario cometa errores caros. No es un límite de seguridad.|
|`New-PSSessionOption`, `New-PSTransportOption`|Disponible pero `New-PSSession` no funciona.|No se ha verificado que `New-PSSessionOption` y `New-PSTransportOption` funcionan ahora que `New-PSSession` funciona.|
