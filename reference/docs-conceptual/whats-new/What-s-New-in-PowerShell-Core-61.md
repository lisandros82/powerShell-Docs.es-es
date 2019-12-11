---
title: Novedades de PowerShell Core 6.1
description: Nuevas características y cambios publicados en PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: 3d836a24b494df9c7f6ebe994386e2a0297521fa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "62086133"
---
# <a name="whats-new-in-powershell-core-61"></a>Novedades de PowerShell Core 6.1

Esta es una selección de algunas de las principales características nuevas y los cambios que se han incorporado en PowerShell Core 6.1.

También hay **toneladas** de "cosas aburridas" que hacen que PowerShell sea más rápido y más estable (además de montones y montones de correcciones de errores).
Si quiere ver una lista completa de los cambios, eche un vistazo a nuestro [registro de cambios en GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

Y aunque destacamos algunos nombres al final, queremos dar las gracias a [todos los colaboradores de la comunidad](https://github.com/PowerShell/PowerShell/graphs/contributors) que han hecho posible esta versión.

## <a name="net-core-21"></a>.NET Core 2.1

PowerShell Core 6.1 cambió a .NET Core 2.1 después de su [lanzamiento en mayo](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), lo que dio lugar a muchas mejoras en PowerShell, incluidas:

- mejoras de rendimiento (ver más [abajo](#performance-improvements))
- compatibilidad con Alpine Linux (versión preliminar)
- [compatibilidad con la herramienta global .NET](/dotnet/core/tools/global-tools) (próximamente en PowerShell)
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a>paquete de compatibilidad de Windows para .NET Core

En Windows, el equipo de .NET incluyó [paquete de compatibilidad de Windows para .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), un conjunto de ensamblados que agregan varias API que se quitaron a .NET Core en Windows.

Hemos agregado el paquete de compatibilidad de Windows a la versión PowerShell Core 6.1 para que los módulos o scripts que usen estas API puedan tener la seguridad de que estarán disponibles.

El paquete de compatibilidad de Windows permite que PowerShell Core use **más de 1900 cmdlets que se incluyen con la actualización de Windows 10 de octubre de 2018 y Windows Server 2019**.

## <a name="support-for-application-whitelisting"></a>Compatibilidad con la lista blanca de aplicaciones

PowerShell Core 6.1 incluye paridad con Windows PowerShell 5.1 al ser compatible con la lista blanca de aplicaciones [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) y [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control).
La creación de listas blancas de aplicaciones permite un control granular de qué archivos binarios se pueden ejecutar mediante el [modo de lenguaje restringido](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/) de PowerShell.

## <a name="performance-improvements"></a>Mejoras en el rendimiento

En PowerShell Core 6.0 se realizaron algunas mejoras de rendimiento significativas.
PowerShell Core 6.1 sigue mejorando la velocidad de determinadas operaciones.

Por ejemplo, `Group-Object` se ha agilizado en un 66 %:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Tiempo (s)   | 25,178                 | 19,653              | 6,641               |
| Aceleración (%) | N/A                    | 21,9 %               | 66,2 %               |

De forma similar, escenarios de ordenación como este han mejorado en más del 15 %:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Tiempo (s)   | 12,170                 | 8,493               | 7,08                |
| Aceleración (%) | N/A                    | 30,2 %               | 16,6 %               |

`Import-Csv` también se han agilizado mucho después de una regresión desde Windows PowerShell.
En este ejemplo se usa un CSV de prueba con 26 616 filas y 6 columnas:

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Tiempo (s)   | 0,441                  | 1,069               | 0,268                  |
| Aceleración (%) | N/A                    | -142,4 %             | 74,9 % (39,2 % desde WPS) |

Por último, la conversión de JSON en `PSObject` se ha agilizado en más del 50 % desde Windows PowerShell.
El ejemplo siguiente usa un archivo JSON de prueba de unos 2 MB:

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Tiempo (s)   | 0,259                  | 0,577               | 0,125                  |
| Aceleración (%) | N/A                    | -122,8%             | 78,3 % (51,7 % desde WPS) |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a>Comprobar `system32` para los módulos integrados compatibles en Windows

En la actualización de Windows 10 1809 y Windows Server 2019, actualizamos una serie de módulos de PowerShell integrados para marcarlos como compatibles con PowerShell Core.

Cuando se inicie PowerShell Core 6.1, incluirá automáticamente `$windir\System32` como parte de la variable de entorno `PSModulePath`.
Pero solo expone módulos a `Get-Module` y `Import-Module` si su `CompatiblePSEdition` está marcado como compatible con `Core`.


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> Puede que vea otros módulos disponibles, en función de qué roles y características estén instaladas.

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

Puede invalidar este comportamiento para que se muestren todos los módulos mediante el parámetro de modificador `-SkipEditionCheck`.
También hemos agregado una propiedad `PSEdition` a la salida de la tabla.

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

Para más información sobre este comportamiento, eche un vistazo a [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).

## <a name="markdown-cmdlets-and-rendering"></a>Representación y cmdlets de Markdown

Markdown es un estándar para crear documentos de texto simple legible con el formato básico que se puede representar en HTML.

Hemos agregado algunos cmdlets en 6.1 que permiten convertir y representar documentos de Markdown en la consola, incluidos:

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

Por ejemplo, `Show-Markdown` representa un archivo de Markdown en la consola:

![Ejemplo donde se muestra Markdown](./images/markdown_example.png)

Para más información sobre cómo funcionan estos cmdlets, vea [este RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).

## <a name="experimental-feature-flags"></a>Marcas de características experimentales

Ya habíamos habilitado la compatibilidad con las [características experimentales][]. Esto permite a los desarrolladores de PowerShell ofrecer nuevas características y obtener comentarios antes de completar el diseño. De este modo, evitamos realizar cambios importantes a medida que evoluciona el diseño.

Use `Get-ExperimentalFeature` para obtener una lista de las características experimentales disponibles. Puede habilitar o deshabilitar estas características con `Enable-ExperimentalFeature` y `Disable-ExperimentalFeature`.

Puede saber más sobre esta característica en [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).

## <a name="web-cmdlet-improvements"></a>Mejoras de cmdlets de web

Gracias a [@markekraus](https://github.com/markekraus), se ha realizado una gran cantidad de mejoras en nuestros cmdlets de web: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
y [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).

- [PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - codificación predeterminada establecida en UTF-8 para respuestas `application-json` predeterminadas
- [PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - parámetro `-SkipHeaderValidation` para permitir encabezados `Content-Type` que no son compatibles con el estándar
- [PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - parámetro `Form` para admitir compatibilidad con `multipart/form-data` simplificada
- [PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - control compatible que distingue entre mayúsculas y minúsculas de las claves de la relación
- [PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - adición del parámetro `-Resume` para cmdlets de web

## <a name="remoting-improvements"></a>Mejoras de comunicación remota

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a>PowerShell Direct para contenedores intenta usar primero PowerShell Core

[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) es una característica de PowerShell e Hyper-V que permite conectarse a una máquina virtual de Hyper-V o un contenedor sin conectividad de red u otros servicios de administración remota.

Antes, PowerShell Direct se conectaba mediante la instancia de Windows PowerShell integrada en el contenedor.
Ahora, PowerShell Direct intenta primero conectarse usando cualquier `pwsh.exe` disponible en la variable de entorno `PATH`.
Si `pwsh.exe` no está disponible, PowerShell Direct recurre a usar `powershell.exe`.

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>`Enable-PSRemoting` ahora crea puntos de conexión de comunicación remota independientes para versiones preliminares

`Enable-PSRemoting` ahora crea dos configuraciones de sesión de comunicación remota:

- Una para la versión principal de PowerShell. Por ejemplo, `PowerShell.6`. Este punto de conexión en el que se puede confiar en todas las actualizaciones de versiones secundarias como la configuración de sesión de PowerShell 6 "para todo el sistema".
- Una configuración de sesión específica de la versión, por ejemplo: `PowerShell.6.1.0`

Este comportamiento es útil si quiere tener varias versiones de PowerShell 6 instaladas y accesibles en la misma máquina.

Además, las versiones preliminares de PowerShell ahora obtienen sus propias configuraciones de sesión de comunicación remota después de ejecutar el cmdlet `Enable-PSRemoting`:

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

El resultado puede ser diferente si no ha configurado WinRM antes.

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

Después puede ver las configuraciones de sesión de PowerShell independientes para la versión preliminar y compilaciones estables de PowerShell 6, para cada versión específica.

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a>Sintaxis `user@host:port` para SSH

Los clientes SSH suelen admitir una cadena de conexión en el formato `user@host:port`.
Al agregar SSH como protocolo para la comunicación remota de PowerShell, se ha agregado compatibilidad con este formato de cadena de conexión:

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>Opción de MSI para agregar el menú contextual del shell del Explorador en Windows

Gracias a [@bergmeister](https://github.com/bergmeister), ya puede habilitar un menú contextual en Windows. Ahora puede abrir la instalación de todo el sistema de PowerShell 6.1 desde cualquier carpeta en el Explorador de Windows:

![Menú contextual del shell para PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a>Extras

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>"Ejecutar como administrador" en la lista de accesos directos de Windows

Gracias a [@bergmeister](https://github.com/bergmeister), la lista de accesos directos de PowerShell Core incluye ahora "Ejecutar como administrador":

![Ejecutar como administrador en la lista de accesos directos de PowerShell 6](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>`cd -` vuelve al directorio anterior

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

O en Linux:

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

Además, `cd` y `cd --` cambian a `$HOME`.

### `Test-Connection`

Gracias a [@iSazonov](https://github.com/iSazonov), el cmdlet [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) se ha trasladado a PowerShell Core.

### <a name="update-help-as-non-admin"></a>`Update-Help` como no administrador

Por petición popular, `Update-Help` ya no debe ejecutarse como administrador.
`Update-Help` ahora tiene como valor predeterminado guardar la Ayuda en una carpeta con ámbito de usuario.

### <a name="new-methodsproperties-on-pscustomobject"></a>Nuevos métodos y propiedades en `PSCustomObject`

Gracias a [@iSazonov](https://github.com/iSazonov), hemos agregado nuevos métodos y propiedades a `PSCustomObject`.
`PSCustomObject` ahora incluye una propiedad `Count`/`Length` como otros objetos.

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

Este trabajo también incluye los métodos `ForEach` y `Where` que permiten operar y filtrar en elementos `PSCustomObject`:

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

Gracias a @SimonWahlin, hemos agregado el parámetro `-Not` a `Where-Object`.
Ahora puede filtrar un objeto en la canalización para la no existencia de una propiedad o un valor de propiedad nula o vacía.

Por ejemplo, este comando devuelve todos los servicios que no tienen los servicios dependientes definidos:

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>`New-ModuleManifest` crea un documento UTF-8 sin marca BOM

Debido a nuestro cambio a UTF-8 sin marca BOM en PowerShell 6.0, hemos actualizado el cmdlet `New-ModuleManifest` para crear un documento UTF-8 sin marca BOM en lugar de uno UTF-16.

### <a name="conversions-from-psmethod-to-delegate"></a>Conversiones de PSMethod a delegado

Gracias a [@powercode](https://github.com/powercode), ahora se admite la conversión de un `PSMethod` a un delegado.
Esto permite hacer cosas como pasar `PSMethod` `[M]::DoubleStrLen` como un valor de delegado en `[M]::AggregateString`:

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

Para más información sobre este cambio, eche un vistazo a [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).

### <a name="standard-deviation-in-measure-object"></a>Desviación estándar en `Measure-Object`

Gracias a [@CloudyDino](https://github.com/CloudyDino), hemos agregado una propiedad `StandardDeviation` a `Measure-Object`:

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

Gracias a [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` tiene ahora el parámetro `Password`, que toma `SecureString`. Esto permite usarlo de forma no interactiva:

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>Eliminación de la función `more`

Antes, PowerShell incluía una función en Windows llamada `more` que encapsulaba `more.com`.
Se ha quitado esa función.

Además, se ha cambiado la función `help` para usar `more.com` en Windows o el elemento de paginación del sistema predeterminado especificado por `$env:PAGER` en plataformas que no sean Windows.

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>`cd DriveName:` ahora devuelve a los usuarios al directorio de trabajo actual en esa unidad

Antes, al usar `Set-Location` o `cd` para volver a un PSDrive enviaba a los usuarios a la ubicación predeterminada para esa unidad.

Gracias a [@mcbobke](https://github.com/mcbobke), ahora se envía a los usuarios al último directorio de trabajo actual conocido para esa sesión.

### <a name="windows-powershell-type-accelerators"></a>Aceleradores de tipo de Windows PowerShell

En Windows PowerShell, hemos incluido estos aceleradores de tipo para que sea más fácil trabajar con sus tipos respectivos:

- `[adsi]`: `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`
- `[wmi]`: `System.Management.ManagementObject`
- `[wmiclass]`: `System.Management.ManagementClass`
- `[wmisearcher]`: `System.Management.ManagementObjectSearcher`

Estos aceleradores de tipo no se incluían en PowerShell 6, pero se han agregado a PowerShell 6.1 que se ejecuta en Windows.

Estos tipos son útiles para crear fácilmente objetos de AD y WMI.

Por ejemplo, puede consultar mediante LDAP:

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

En este ejemplo se crea un objeto CIM de Win32_OperatingSystem:

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

En este ejemplo se devuelve un objeto ManagementClass para la clase Win32_OperatingSystem.

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>Alias `-lp` para todos los parámetros `-LiteralPath`

Gracias a [@kvprasoon](https://github.com/kvprasoon), ahora tenemos un alias de parámetro `-lp` para todos los cmdlets de PowerShell integrados que tienen un parámetro `-LiteralPath`.

## <a name="breaking-changes"></a>Cambios importantes

### <a name="msi-based-installation-paths-on-windows"></a>Rutas de acceso de instalación basadas en MSI en Windows

En Windows, el paquete MSI ahora instala esta ruta de acceso:

- `$env:ProgramFiles\PowerShell\6\` para la instalación estable de 6.x
- `$env:ProgramFiles\PowerShell\6-preview\` para la instalación de versión preliminar de 6.x

Este cambio garantiza que PowerShell Core se pueda actualizar o mantener a través de Microsoft Update.

Para más información, vea [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>Solo se puede deshabilitar la telemetría con una variable de entorno

PowerShell Core envía datos de telemetría básica a Microsoft cuando se inicia. Los datos incluyen el nombre del sistema operativo, la versión del sistema operativo y la versión de PowerShell. Estos datos nos permiten comprender mejor los entornos donde se usa PowerShell y nos permite dar prioridad a nuevas características y correcciones.

Para dejar de participar en esta telemetría, establezca la variable de entorno `POWERSHELL_TELEMETRY_OPTOUT` en `true`, `yes` o `1`. Ya no se admite la eliminación del archivo `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` para deshabilitar la telemetría.

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>No permite la autenticación básica a través de HTTP de comunicación remota de PowerShell en plataformas Unix

Para evitar el uso de tráfico sin cifrar, ahora es necesario usar NTLM/Negotiate o HTTPS para la comunicación remota de PowerShell en plataformas Unix.

Para obtener más información sobre estos cambios, consulte [PR #6779](https://github.com/PowerShell/PowerShell/issues/6779).

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>Se quitó `VisualBasic` como lenguaje compatible en Add-Type

Antes, se podía compilar código de Visual Basic mediante el cmdlet `Add-Type`.
Visual Basic se usó rara vez con `Add-Type`. Hemos quitado esta característica para reducir el tamaño de PowerShell.

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>Se limpiaron los usos de `CommandTypes.Workflow` y `WorkflowInfoCleaned`

Para más información sobre estos cambios, eche un vistazo a [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).

### <a name="group-object-now-sorts-the-groups"></a>Ahora, Group-Object ordena los grupos

Como parte de la mejora del rendimiento, `Group-Object` ahora devuelve una lista ordenada de los grupos.
Aunque no debe confiar en el orden, podría verse interrumpida por este cambio si quisiera el primer grupo. Decidimos que esta mejora en el rendimiento valía la pena el cambio, ya que el impacto de depender del comportamiento previo es bajo.

Para más información sobre este cambio, consulte el [problema #7409](https://github.com/PowerShell/PowerShell/issues/7409).

<!-- URL references -->
[Características experimentales]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
