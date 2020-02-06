---
ms.date: 02/03/2020
keywords: powershell,core
title: Cambios importantes en PowerShell Core 6.0
ms.openlocfilehash: 47ed14cceed86e4dd04a8e0079af00f6a98988ea
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995460"
---
# <a name="breaking-changes-for-powershell-6x"></a>Cambios importantes en PowerShell Core 6.x

## <a name="features-no-longer-available-in-powershell-core"></a>Características que ya no están disponibles en PowerShell Core

### <a name="modules-not-shipped-for-powershell-6x"></a>Módulos no distribuidos para PowerShell 6.x

Por diversas razones de compatibilidad, los siguientes módulos no se incluyen en PowerShell 6.

- ISE
- Microsoft.PowerShell.LocalAccounts
- Microsoft.PowerShell.ODataUtils
- Microsoft.PowerShell.Operation.Validation
- PSScheduledJob
- PSWorkflow
- PSWorkflowUtility

### <a name="powershell-workflow"></a>Flujo de trabajo de PowerShell

El [flujo de trabajo de PowerShell][workflow] es una característica de Windows PowerShell basada en [Windows Workflow Foundation (WF)][workflow-foundation] que permite la creación de runbooks sólidos para tareas de larga ejecución o paralelizadas.

Debido a la falta de compatibilidad con Windows Workflow Foundation en .NET Core, no seguiremos admitiendo el flujo de trabajo de PowerShell en PowerShell Core.

En el futuro, nos gustaría habilitar paralelismo nativo/simultaneidad en el lenguaje de PowerShell sin la necesidad del flujo de trabajo de PowerShell.

Si es necesario usar puntos de control para reanudar un script una vez reiniciado el sistema operativo, recomendamos usar Programador de tareas para ejecutar un script al iniciarse el sistema operativo, pero el script debería mantener su propio estado (como conservarlo en un archivo).

[workflow]: /powershell/scripting/components/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Complementos personalizados

Los [complementos de PowerShell][snapin] son un predecesor de los módulos de PowerShell cuya adopción en la comunidad de PowerShell no está generalizada.

Dada la complejidad de admitir complementos y su falta de uso en la comunidad, ya no admitimos complementos personalizados en PowerShell Core.

Actualmente, esto rompe los módulos `ActiveDirectory` y `DnsClient` en Windows y Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>Cmdlets WMI v1

Dada la complejidad de admitir dos conjuntos de módulos basados en WMI, quitamos los cmdlets WMI v1 de PowerShell Core:

- `Register-WmiEvent`
- `Set-WmiInstance`
- `Invoke-WmiMethod`
- `Get-WmiObject`
- `Remove-WmiObject`

En su lugar, recomendamos que use los cmdlets de CIM (también conocido como WMI v2), que proporcionan la misma funcionalidad con una nueva funcionalidad y una sintaxis rediseñada:

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

Debido al uso de API no admitidas, `Microsoft.PowerShell.LocalAccounts` se ha quitado de PowerShell Core hasta que se encuentre una solución mejor.

### <a name="new-webserviceproxy-cmdlet-removed"></a>Cmdlet `New-WebServiceProxy` quitado

.NET Core no es compatible con Windows Communication Framework, que proporciona servicios para usar el protocolo SOAP. Este cmdlet se quitó porque requiere SOAP.

### <a name="-transaction-cmdlets-removed"></a>`*-Transaction` cmdlets quitados

Estos cmdlets tenían un uso muy limitado. Se tomó la decisión de dejar de admitirlos.

- `Complete-Transaction`
- `Get-Transaction`
- `Start-Transaction`
- `Undo-Transaction`
- `Use-Transaction`

### <a name="security-cmdlets-not-available-on-non-windows-platforms"></a>Cmdlets de seguridad no disponibles en plataformas que no son de Windows

- `Get-Acl`
- `Set-Acl`
- `Get-AuthenticodeSignature`
- `Set-AuthenticodeSignature`
- `Get-CmsMessage`
- `Protect-CmsMessage`
- `Unprotect-CmsMessage`
- `New-FileCatalog`
- `Test-FileCatalog`

### <a name="-computerand-other-windows-specific-cmdlets"></a>`*-Computer`y otros cmdlets específicos de Windows

Debido al uso de API no admitidas, los cmdlets siguientes se han quitado de PowerShell Core hasta que se encuentre una solución mejor.

- `Get-Clipboard`
- `Set-Clipboard`
- `Add-Computer`
- `Checkpoint-Computer`
- `Remove-Computer`
- `Restore-Computer`
- `Reset-ComputerMachinePassword`
- `Disable-ComputerRestore`
- `Enable-ComputerRestore`
- `Get-ComputerRestorePoint`
- `Test-ComputerSecureChannel`
- `Get-ControlPanelItem`
- `Show-ControlPanelItem`
- `Get-HotFix`
- `Clear-RecycleBin`
- `Update-List`
- `Out-Printer`
- `ConvertFrom-String`
- `Convert-String`

### <a name="-counter-cmdlets"></a>Cmdlets de `*-Counter`

Debido al uso de API no admitidas, `*-Counter` se ha quitado de PowerShell Core hasta que se encuentre una solución mejor.

### <a name="-eventlog-cmdlets"></a>Cmdlets de `*-EventLog`

Debido al uso de API no admitidas, `*-EventLog` se ha quitado de PowerShell Core. hasta que se encuentra una solución mejor. `Get-WinEvent` y `Create-WinEvent` están disponibles para obtener y crear eventos en Windows.

### <a name="cmdlets-that-use-wpf-removed"></a>Cmdlets que usan WPF quitados

Windows Presentation Framework no se admite en CoreCLR. Los siguientes cmdlets se ven afectados:

- `Show-Command`
- `Out-GridView`
- Parámetro **showwindow** de `Get-Help`

### <a name="some-dsc-cmdlets-removed"></a>Algunos cmdlets de DSC quitados

- `Get-DscConfiguration`
- `Publish-DscConfiguration`
- `Restore-DscConfiguration`
- `Start-DscConfiguration`
- `Stop-DscConfiguration`
- `Test-DscConfiguration`
- `Update-DscConfiguration`
- `Remove-DscConfigurationDocument`
- `Get-DscConfigurationStatus`
- `Disable-DscDebug`
- `Enable-DscDebug`
- `Get-DscLocalConfigurationManager`
- `Set-DscLocalConfigurationManager`
- `Invoke-DscResource`

## <a name="enginelanguage-changes"></a>Cambios en el lenguaje/motor

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Cambio del nombre de `powershell.exe` a `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Para ofrecer a los usuarios una forma determinista de llamar a PowerShell Core en Windows (frente a Windows PowerShell), el archivo binario de PowerShell Core se cambió a `pwsh.exe` en Windows y `pwsh` en plataformas que no son de Windows.

El nombre abreviado también es coherente con la nomenclatura de los shells en las plataformas que no son de Windows.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>No insertar saltos de línea en la salida (salvo para las tablas) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Anteriormente, la salida se alineaba con el ancho de la consola y los saltos de línea se agregaban en el ancho final de la consola, lo que significaba que la salida no se volvía a formatear como se esperaba si se cambiaba el tamaño del terminal. Este cambio no se aplicaba a las tablas, ya que los saltos de línea eran necesarios para mantener las columnas alineadas.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Omitir la comprobación del elemento NULL de las colecciones con un tipo de elemento de tipo de valor [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

En el parámetro `Mandatory` y los atributos `ValidateNotNull` y `ValidateNotNullOrEmpty`, omita la comprobación del elemento NULL si el tipo de elemento de la colección es tipo de valor.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Cambiar `$OutputEncoding` para usar la codificación `UTF-8 NoBOM` en lugar de ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

La codificación anterior, ASCII (7 bits), daría lugar a una alteración incorrecta de la salida en algunos casos. Este cambio consiste en convertir `UTF-8 NoBOM` en valor predeterminado, que conserva la salida de Unicode con una codificación admitida por la mayoría de las herramientas y sistemas operativos.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Quitar `AllScope` de la mayoría de los alias predeterminados [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Para acelerar la creación de ámbito, `AllScope` se quitó de la mayoría de los alias predeterminados. `AllScope` se dejó para un alias no usado con frecuencia donde la búsqueda era más rápida.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` y `-Debug` ya no invalidan `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Anteriormente, si se especificaban `-Verbose` o `-Debug`, invalidaba el comportamiento de `$ErrorActionPreference`. Con este cambio, `-Verbose` y `-Debug` ya no influyen en el comportamiento de `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Cambios en el cmdlet

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Invoke-RestMethod no devuelve información útil cuando no se devuelven datos. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Cuando una API devuelve solo `null`, Invoke-RestMethod lo serializaba como la cadena `"null"` en lugar de `$null`. Este cambio corrige la lógica en `Invoke-RestMethod` para serializar correctamente un valor único válido JSON `null` literal como `$null`.

### <a name="remove--protocol-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Quitar `-Protocol` de los cmdlets `*-Computer`[#5277](https://github.com/PowerShell/PowerShell/issues/5277)

Debido a problemas con la comunicación remota RPC en CoreFX (especialmente en plataformas que no son de Windows) y la garantía de una experiencia de comunicación remota coherente en PowerShell, el parámetro `-Protocol` se quitó de los cmdlets `\*-Computer`. DCOM ya no se admite para la comunicación remota. Los cmdlets siguientes solo admiten la comunicación remota mediante WSMAN:

- Rename-Computer
- Restart-Computer
- Stop-Computer

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Quitar `-ComputerName` de los cmdlets `*-Service`[#5090](https://github.com/PowerShell/PowerShell/issues/5094)

Para fomentar el uso coherente de PSRP, el parámetro `-ComputerName` se quitó de los cmdlets `*-Service`.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Corregir `Get-Item -LiteralPath a*b` si `a*b` no existe realmente para devolver el error [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Anteriormente, `-LiteralPath` al que se le daba un carácter comodín lo trataría de la misma forma que `-Path` y, si el carácter comodín no encontraba ningún archivo, existiría en modo silencioso. El comportamiento correcto debería ser que `-LiteralPath` fuera literal de modo que, de no existir el archivo, debería producir un error. El cambio consiste en tratar los caracteres comodín usados con `-Literal` como literales.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` debe aplicar `PSTypeNames` durante la importación cuando la información de tipo esté presente en el CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Anteriormente, los objetos exportados mediante el uso de `Export-CSV` con `TypeInformation` importado con `ConvertFrom-Csv` no retenían la información de tipo. Este cambio agrega la información de tipo al miembro `PSTypeNames` si está disponible desde el archivo CSV.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` debería ser valor predeterminado en `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Este cambio se realizó para abordar los comentarios de los clientes sobre el comportamiento predeterminado de `Export-CSV` a fin de incluir la información de tipo.

Anteriormente, el cmdlet generaría un comentario como la primera línea que incluye el nombre de tipo del objeto. El cambio consiste en suprimir esto de forma predeterminada, pues la mayoría de las herramientas no lo comprenden. Use `-IncludeTypeInformation` para retener el comportamiento anterior.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Los cmdlets web deben advertir cada vez que `-Credential` se envía a través de conexiones descifradas [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

Al usar HTTP, el contenido y las contraseñas se envían como texto no cifrado. Este cambio consiste en no permitir esto de forma predeterminada y devolver un error si las credenciales se pasan con inseguridad. Los usuarios pueden omitir esto con el conmutador `-AllowUnencryptedAuthentication`.

## <a name="api-changes"></a>Cambios de API

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Quitar la clase `AddTypeCommandBase`[#5407](https://github.com/PowerShell/PowerShell/issues/5407)

La clase `AddTypeCommandBase` se quitó de `Add-Type` para mejorar el rendimiento. El cmdlet Add-Type es el único que usa esta clase, la cual no debe afectar a los usuarios.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Unificar los cmdlets con el parámetro `-Encoding` para que sea de tipo `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

El valor `-Encoding``Byte` se ha quitado de los cmdlets del proveedor del sistema de archivos. Un nuevo parámetro, `-AsByteStream`, se usa ahora para especificar que un flujo de bytes se necesita como entrada o que la salida es un flujo de bytes.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Agregar un mensaje de error mejor para el parámetro vacío y nulo `-UFormat`[#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Anteriormente, al pasar una cadena de formato vacía a `-UFormat`, aparecía un mensaje de error poco práctico. Se ha agregado un error más descriptivo.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Limpiar el código de consola [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Las siguientes características se quitaron al no admitirse en PowerShell Core y no se tienen planes de agregar compatibilidad puesto que existen por motivos de herencia: conmutador y código `-psconsolefile`, conmutador y código `-importsystemmodules` y código de cambio de fuente.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Compatibilidad con `RunspaceConfiguration` quitada [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

Anteriormente, al crear un espacio de ejecución de PowerShell mediante programación con la API, podía usar el elemento [`RunspaceConfiguration`][runspaceconfig] heredado o el más reciente [`InitialSessionState`][iss]. Este cambio quitó la compatibilidad con `RunspaceConfiguration` y solo admite `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` enlaza argumentos a `$input` en lugar de `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

Una posición incorrecta de un parámetro dio como resultado que los argumentos se pasaran como entrada en lugar de como argumentos.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Quitar el conmutador `-showwindow` no admitido de `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` confía en WPF, que no se admite en CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>Permitir el uso de * en la ruta de acceso del Registro para `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Anteriormente, `-LiteralPath` al que se le daba un carácter comodín lo trataría de la misma forma que `-Path` y, si el carácter comodín no encontraba ningún archivo, existiría en modo silencioso. El comportamiento correcto debería ser que `-LiteralPath` fuera literal de modo que, de no existir el archivo, debería producir un error. El cambio consiste en tratar los caracteres comodín usados con `-Literal` como literales.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Corregir la prueba con errores `Set-Service`[#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Anteriormente, si se usaba `New-Service -StartupType foo`, `foo` se omitía y el servicio se creaba con algún tipo de inicio predeterminado. Este cambio consiste en mostrar un error de forma explícita para un tipo de inicio no válido.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Cambio del nombre de `$IsOSX` a `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

La nomenclatura en PowerShell debe ser coherente con la nuestra y ajustarse al uso de macOS de Apple en lugar de OSX. Sin embargo, para legibilidad y coherencia, optamos por el uso de mayúsculas o minúsculas de Pascal.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Haga que el mensaje de error sea coherente cuando el script no válido se pase a -File; mejor error al superarse el argumento ambiguo [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Cambie los códigos de salida de `pwsh.exe` para su alineación con las convenciones de Unix.

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Eliminación de `LocalAccount` y cmdlets de los módulos `Diagnostics`. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Debido a las API no admitidas, el módulo `LocalAccounts` y los cmdlets `Counter` del módulo `Diagnostics` se quitaron hasta que se encuentre una solución mejor.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>La ejecución de un script de PowerShell con un parámetro bool no funciona [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Anteriormente, el uso de **powershell.exe** (ahora **pwsh.exe**) para ejecutar un script de PowerShell con `-File` no proporcionaba ninguna forma de pasar `$true`/`$false` como valores del parámetro. La compatibilidad con `$true`/`$false` como valores analizados de parámetros se agregó. Los valores de conmutador también se admiten, ya que la sintaxis documentada actualmente no funciona.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Quitar la propiedad `ClrVersion` de `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

La propiedad `ClrVersion` de `$PSVersionTable` no es útil con CoreCLR y los usuarios no deben usar ese valor para determinar la compatibilidad.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Cambiar parámetro posicional para `powershell.exe` de `-Command` a `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Permita el uso del par de caracteres shebang de PowerShell en plataformas que no son de Windows. Esto significa que, en los sistemas basados en Unix, puede hacer que un script pueda ejecutarse, lo que invocaría PowerShell automáticamente en lugar de invocar `pwsh` de forma explícita. También significa que ahora puede hacer cosas como `powershell foo.ps1` o `powershell fooScript` sin especificar `-File`. Aun así, este cambio requiere ahora que se especifique explícitamente `-c` o `-Command` al intentar hacer cosas como `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Implementar análisis de escape Unicode [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u####`` o `` `u{####}`` se convierte en el carácter Unicode correspondiente. Para generar un elemento `` `u`` literal, evite la tilde aguda: ``` ``u```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Cambie la codificación `New-ModuleManifest` a `UTF8NoBOM` en plataformas que no son de Windows [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Anteriormente, `New-ModuleManifest` creaba manifiestos psd1 en UTF-16 con BOM, dando lugar a un problema para las herramientas de Linux. Este cambio importante cambia la codificación de `New-ModuleManifest` para que sea UTF (sin BOM) en plataformas que no son de Windows.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Evite que `Get-ChildItem` recurra a symlinks (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Este cambio trae `Get-ChildItem`, más acorde con los comandos nativos `ls -r` de Unix y `dir /s` de Windows. Al igual que los comandos mencionados, el cmdlet muestra vínculos simbólicos a directorios encontrados durante la recursión, pero no recurre a ellos.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Corregir `Get-Content -Delimiter` para no incluir el delimitador en las líneas devueltas [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Anteriormente, la salida mientras se usaba `Get-Content -Delimiter` era incoherente e incómoda, ya que requería un mayor procesamiento de los datos para quitar el delimitador. Este cambio quita el delimitador en líneas devueltas.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Implementar Format-Hex en C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

El parámetro `-Raw` ahora es un "no-op" (ahí no hace nada). En adelante, toda la salida se mostrará con una auténtica representación de números que incluye todos los bytes de su tipo (lo que el parámetro `-Raw` hacía formalmente antes de este cambio).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>PowerShell como shell predeterminado no funciona con un comando de script [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

En Unix, es una convención para que los shells acepten `-i` para un shell interactivo y muchas herramientas esperan este comportamiento (`script` por ejemplo y al establecer PowerShell como el shell predeterminado) y llama al shell con el conmutador `-i`. Este cambio es importante en que `-i` podía usarse anteriormente como fórmula sencilla para coincidir con `-inputformat`, que ahora debe ser `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Corregir error de escritura en el nombre de la propiedad Get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` se escribió incorrectamente como `BiosSeralNumber` y se ha cambiado a la ortografía correcta.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Agregar los cmdlets `Get-StringHash` y `Get-FileHash`[#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Este cambio consiste en que algunos algoritmos hash no son compatibles con CoreFX, por lo que ya no están disponibles:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Agregar validación en los cmdlets `Get-*` donde al pasar $null se devuelven todos los objetos en lugar del error [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Ahora, al pasar `$null` a cualquiera de los siguientes elementos, se muestra un error:

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Agregar compatibilidad con formato de archivo de registro extendido W3C en `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Anteriormente, el cmdlet `Import-Csv` no se podía usar directamente para importar los archivos de registro en el formato de registro extendido W3C y se requerían medidas adicionales. Con este cambio, el formato de registro extendido W3C se admite.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Problema de enlace de parámetros con `ValueFromRemainingArguments` en funciones de PS [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` ahora devuelve los valores como una matriz en lugar de un solo valor que en sí mismo es una matriz.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion` se quita de `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Quite la propiedad `BuildVersion` de `$PSVersionTable`. Esta propiedad estaba ligada a la versión de compilación de Windows. En su lugar, se recomienda usar `GitCommitId` para recuperar la versión de compilación exacta de PowerShell Core.

### <a name="changes-to-web-cmdlets"></a>Cambios en los cmdlets web

La API de .NET subyacente de los cmdlets web se ha cambiado a `System.Net.Http.HttpClient`. Este cambio ofrece muchas ventajas. Sin embargo, este cambio y una falta de interoperabilidad con Internet Explorer han dado lugar a varios cambios importantes en `Invoke-WebRequest` y `Invoke-RestMethod`.

- `Invoke-WebRequest` ahora solo admite un análisis básico de HTML. `Invoke-WebRequest` siempre devuelve un objeto `BasicHtmlWebResponseObject`. Las propiedades `ParsedHtml` y `Forms` se han quitado.
- Los valores `BasicHtmlWebResponseObject.Headers` ahora son `String[]` en lugar de `String`.
- `BasicHtmlWebResponseObject.BaseResponse` ahora es un objeto `System.Net.Http.HttpResponseMessage`.
- La propiedad `Response` de excepciones de cmdlets web ahora es un objeto `System.Net.Http.HttpResponseMessage`.
- El análisis estricto del encabezado RFC ahora es el valor predeterminado de los parámetros `-Headers` y `-UserAgent`. Esto se puede omitir con `-SkipHeaderValidation`.
- Los esquemas de URI `file://` y `ftp://` ya no se admiten.
- La configuración `System.Net.ServicePointManager` ya no se admite.
- Actualmente no hay ninguna autenticación disponible en macOS basada en certificado.
- El uso de `-Credential` sobre un URI `http://` dará lugar a un error. Use un URI `https://` o proporcione el parámetro `-AllowUnencryptedAuthentication` para suprimir el error.
- `-MaximumRedirection` ahora genera un error de terminación cuando los intentos de redirección superan el límite proporcionado en lugar de devolver los resultados de la última redirección.
- En PowerShell 6.2, se ha realizado un cambio para usar de forma predeterminada la codificación UTF-8 en las respuestas JSON. Cuando no se proporciona un juego de caracteres para una respuesta JSON, la codificación predeterminada debe ser UTF-8 según la norma RFC 8259.
