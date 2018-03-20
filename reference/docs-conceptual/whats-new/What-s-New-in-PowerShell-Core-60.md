# <a name="whats-new-in-powershell-core-60"></a>Novedades de PowerShell Core 6.0

[PowerShell Core 6.0][github] es una nueva edición de PowerShell multiplataforma (Windows, macOS y Linux), de código abierto y diseñada para entornos heterogéneos y la nube híbrida.

## <a name="moved-from-net-framework-to-net-core"></a>Cambio de .NET Framework a .NET Core

PowerShell Core usa [.NET Core 2.0][] como entorno de ejecución.
.NET Core 2.0 permite que PowerShell Core funcione en varias plataformas (Windows, macOS y Linux).
PowerShell Core también expone el conjunto de API que ofrece .NET Core 2.0 para su uso en scripts y cmdlets de PowerShell.

Windows PowerShell usaba el entorno de ejecución de .NET Framework para hospedar el motor de PowerShell.
Esto significa que Windows PowerShell expone el conjunto de API que ofrece .NET Framework.

Las API que se comparten entre .NET Core y .NET Framework se definen como parte de [.NET Standard][].

Para más información sobre cómo afecta esto a la compatibilidad de módulo/script entre PowerShell Core y Windows PowerShell, vea [Compatibilidad con versiones anteriores de Windows PowerShell](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>Compatibilidad con macOS y Linux

PowerShell ahora admite oficialmente macOS y Linux, incluido:

- Windows 7, 8.1 y 10
- Windows Server 2008 R2, 2012 R2 y 2016
- [Canal semianual de Windows Server][semi-annual]
- Ubuntu 14.04, 16.04 y 17.04
- Debian 8.7+ y 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25 y 26
- macOS 10.12+

Nuestra comunidad también ha aportado paquetes para las plataformas siguientes, pero no se admiten oficialmente:

- Arch Linux
- Kali Linux
- AppImage (funciona en varias plataformas Linux)

También tenemos versiones experimentales (no compatibles) para las plataformas siguientes:

- Windows en ARM32/ARM64
- Raspbian (Stretch)

Se ha realizado una serie de cambios en PowerShell Core 6.0 para que funcione mejor en sistemas distintos de Windows.
Algunos son cambios radicales que también afectan a Windows.
Otros solo están presentes o son aplicables en instalaciones que no son Windows de PowerShell Core.

- Se ha agregado compatibilidad con el uso global de comandos nativos en plataformas Unix.
- La funcionalidad `more` respeta el valor `$PAGER` de Linux y tiene como valor predeterminado `less`.
  Esto significa que ahora puede usar caracteres comodín con comandos o binarios nativos (por ejemplo, `ls *.txt`). (#3463)
- Se agrega automáticamente un carácter de escape a la barra diagonal inversa final cuando se trabaja con argumentos de comandos nativos. (#4965)
- Omita el modificador `-ExecutionPolicy` cuando ejecute PowerShell en plataformas que no sean Windows, ya que la firma de scripts no se admite actualmente. (#3481)
- Se ha corregido ConsoleHost para usar `NoEcho` en plataformas Unix. (#3801)
- Se ha corregido `Get-Help` para admitir la coincidencia de patrones que no distinguen mayúsculas de minúsculas en plataformas Unix. (#3852)
- Se ha agregado la página man `powershell` al paquete.

### <a name="logging"></a>Registro

En macOS, PowerShell usa las API `os_log` nativas para registrar información en el [sistema de registro unificado][os_log] de Apple.
En Linux, PowerShell usa [Syslog][], una solución de registro ubicua.

### <a name="filesystem"></a>Sistema de archivos

Se ha realizado una serie de cambios en macOS y Linux para admitir caracteres en los nombres de archivo que no se suelen admitir en Windows:

- Las rutas de acceso que se asignan a los cmdlets ahora son independientes de la barra diagonal (tanto / como \ funcionan como separador de directorio).
- Ahora se respeta la especificación de directorio base de XDG y se usa de forma predeterminada:
  - La ruta de acceso al perfil de Linux/macOS se encuentra en `~/.config/powershell/profile.ps1`.
  - La ruta de acceso de almacenamiento del historial se encuentra en `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`.
  - La ruta de acceso del módulo de usuario se encuentra en `~/.local/share/powershell/Modules`.
- Compatibilidad con nombres de archivo y carpeta que contienen el carácter de dos puntos en Unix. (#4959)
- Compatibilidad con nombres de script o rutas de acceso completas que tienen comas. (#4136) (Gracias, @TimCurwick).
- Se detecta cuándo se usa `-LiteralPath` para suprimir la expansión de caracteres comodín para los cmdlets de navegación. (#5038)
- Se ha actualizado `Get-ChildItem` para que su funcionamiento se parezca más a `ls -R` de *nix y los comandos nativos `DIR /S` de Windows.
  `Get-ChildItem` ahora devuelve los vínculos simbólicos que se encuentran durante una búsqueda recursiva y no busca en los directorios que esos vínculos tienen como destino. (#3780)

### <a name="case-sensitivity"></a>Distinción entre mayúsculas y minúsculas

Linux y macOS tienden a distinguir entre mayúsculas y minúsculas, mientras que Windows no distingue entre mayúsculas y minúsculas pero las conserva.
En general, PowerShell no distingue entre mayúsculas y minúsculas.

Por ejemplo, las variables de entorno distinguen entre mayúsculas y minúsculas en macOS y Linux, por lo que el uso de mayúsculas de la variable de entorno `PSModulePath` se ha estandarizado. (#3255) `Import-Module` no distingue entre mayúsculas y minúsculas cuando usa una ruta de archivo para determinar el nombre del módulo. (#5097)

## <a name="support-for-side-by-side-installations"></a>Compatibilidad con instalaciones en paralelo

PowerShell Core se instala, se configura y se ejecuta con independencia de Windows PowerShell.
PowerShell Core tiene un paquete ZIP "portátil".
Mediante el paquete ZIP, puede instalar cualquier número de versiones en cualquier lugar del disco, incluso de manera local en una aplicación que toma PowerShell como dependencia.
La instalación en paralelo hace que sea más fácil probar nuevas versiones de PowerShell y migrar scripts existentes con el paso del tiempo.
Además, la instalación en paralelo permite la compatibilidad con versiones anteriores, ya que los scripts se pueden anclar a las versiones específicas que requieren.

> [!NOTE]
> De forma predeterminada, el instalador basado en MSI de Windows hace una instalación de actualizaciones en contexto.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>Cambio de nombre de `powershell(.exe)` a `pwsh(.exe)`

El nombre del binario de PowerShell Core se ha cambiado de `powershell(.exe)` a `pwsh(.exe)`.
Este cambio proporciona una forma determinista de ejecutar PowerShell Core en equipos para admitir instalaciones en paralelo de Windows PowerShell y PowerShell Core.
`pwsh` es además mucho más corto y fácil de escribir.

Cambios adicionales en `pwsh(.exe)` con respecto a `powershell.exe`:

- Se ha cambiado el primer parámetro posicional de `-Command` a `-File`.
  Este cambio corrige el uso de `#!` (también conocido como par de caracteres shebang) en los scripts de PowerShell que se ejecutan desde shells que no son de PowerShell en plataformas distintas de Windows.
  También implica que se pueden ejecutar comandos como `pwsh foo.ps1` o `pwsh fooScript` sin especificar `-File`.
  Aun así, este cambio requiere que se especifique explícitamente `-c` o `-Command` al intentar ejecutar comandos como `pwsh.exe -Command Get-Command`. (#4019)
- PowerShell Core acepta el modificador `-i` (o `-Interactive`) para indicar un shell interactivo. (#3558) Esto permite usar PowerShell como shell predeterminado en plataformas Unix.
- Se han quitado los parámetros `-importsystemmodules` y `-psconsoleFile` de `pwsh.exe`. (#4995)
- Se ha cambiado `pwsh -version` y se ha integrado ayuda para `pwsh.exe` para que sea acorde con otras herramientas nativas. (#4958 y #4931) (Gracias, @iSazonov).
- Mensajes de error de argumento no válido para `-File` y `-Command` y códigos de salida coherentes con los estándares de Unix (#4573).
- Se ha agregado el parámetro `-WindowStyle` en Windows. (#4573) De forma similar, las actualizaciones de instalaciones basadas en paquete en plataformas distintas de Windows son actualizaciones en contexto.

## <a name="backwards-compatibility-with-windows-powershell"></a>Compatibilidad con versiones anteriores de Windows PowerShell

El objetivo de PowerShell Core es mantener el máximo de compatibilidad con Windows PowerShell.
PowerShell Core usa [.NET Standard][] 2.0 para proporcionar compatibilidad binaria con los ensamblados de .NET existentes.
Muchos de los módulos de PowerShell dependen de estos ensamblados (con frecuencia, DLL), y .NET Standard permite que sigan funcionando con .NET Core.
PowerShell Core también incluye una heurística para buscar en carpetas conocidas, como en la que suele residir en disco la caché global de ensamblados, para localizar dependencias de DLL de .NET Framework.

Puede obtener más información sobre .NET Standard en el [blog de .NET][], en este vídeo de [YouTube][] y en estas [preguntas más frecuentes][] de GitHub.

Se han realizado esfuerzos para asegurarse de que los módulos "integrados" y de lenguaje de PowerShell (como `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`, etc.) funcionen igual que en Windows PowerShell.
En muchos casos, con la ayuda de la comunidad, hemos agregado nuevas características y correcciones de errores para estos cmdlets.
En ocasiones, debido a la falta de una dependencia en niveles subyacentes de .NET, la funcionalidad se ha quitado o no está disponible.

La mayoría de los módulos que se incluyen como parte de Windows (por ejemplo, `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`, etc.) y otros productos de Microsoft como Azure y Office todavía no se han portado *explícitamente* a .NET Core.
El equipo de PowerShell está trabajando con estos grupos y equipos de productos para validar y portar sus módulos existentes a PowerShell Core.
Con .NET Standard y [CDXML][], muchos de estos módulos tradicionales de Windows PowerShell parecen funcionar en PowerShell Core, pero todavía no se han validado ni se admiten formalmente.

Si instala el módulo [`WindowsPSModulePath`][windowspsmodulepath], puede usar módulos de Windows PowerShell. Para ello, agregue `PSModulePath` de Windows PowerShell a `PSModulePath` de PowerShell Core.

En primer lugar, instale el módulo `WindowsPSModulePath` desde la Galería de PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin 
Install-Module WindowsPSModulePath -Force
```

Después de instalar este módulo, ejecute el cmdlet `Add-WindowsPSModulePath` para agregar `PSModulePath` de Windows PowerShell a PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Compatibilidad con Docker

PowerShell Core agrega compatibilidad con contenedores de Docker para todas las plataformas principales que admitimos (incluidas varias distribuciones de Linux, Windows Server Core y Nano Server).

Para obtener una lista completa, consulte las etiquetas en [`microsoft/powershell` en Docker Hub][docker-hub].
Para más información sobre Docker y PowerShell Core, vea [Docker][] en GitHub.

## <a name="ssh-based-powershell-remoting"></a>Comunicación remota de PowerShell basada en SSH

El Protocolo de comunicación remota de PowerShell (PSRP) ahora funciona con el protocolo Secure Shell (SSH), además de PSRP tradicional basado en WinRM.

Esto significa que puede usar cmdlets como `Enter-PSSession` y `New-PSSession` y autenticarse a través de SSH.
Lo único que debe hacer es registrar PowerShell como un subsistema con un servidor SSH basado en OpenSSH. Puede usar sus mecanismos de autenticación basados en SSH existentes (como contraseñas o claves privadas) con la semántica `PSSession` tradicional.

Para más información sobre cómo configurar y usar la comunicación remota basada en SSH, vea [PowerShell Remoting over SSH][ssh-remoting] (Comunicación remota de PowerShell a través de SSH).

## <a name="default-encoding-is-utf-8-without-a-bom"></a>La codificación predeterminada es UTF-8 sin una marca BOM

Anteriormente, los cmdlets de Windows PowerShell como `Get-Content` y `Set-Content` usaban codificaciones diferentes, como ASCII y UTF-16.
La discrepancia en los valores predeterminados de codificación causaba problemas cuando se mezclaban cmdlets sin especificar una codificación.

Las plataformas distintas de Windows usan tradicionalmente UTF-8 sin una marca BOM como codificación predeterminada para los archivos de texto.
Cada vez más aplicaciones y herramientas de Windows abandonan UTF-16 y pasan a la codificación UTF-8 sin una marca BOM.
PowerShell Core ha cambiado la codificación predeterminada para adaptarse a ecosistemas más amplios.

Esto significa que todos los cmdlets integrados que usan el parámetro `-Encoding` usan el valor `UTF8NoBOM` de forma predeterminada.
Los siguientes cmdlets se ven afectados por este cambio:

- Add-Content
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- New-ModuleManifest
- Out-File
- Select-String
- Send-MailMessage
- Set-Content

Estos cmdlets también se han actualizado para que el parámetro `-Encoding` acepte universalmente `System.Text.Encoding`.

El valor predeterminado de `$OutputEncoding` también se ha cambiado a UTF-8.

Se recomienda que establezca explícitamente codificaciones en scripts mediante el parámetro `-Encoding` para generar un comportamiento determinista entre las plataformas.

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Compatibilidad con la colocación en segundo plano de canalizaciones con Y comercial (`&`) (#3360)

Cuando se incluye `&` al final de una canalización, esta se ejecuta como un trabajo de PowerShell.
Cuando una canalización se pasa a segundo plano, se devuelve un objeto de trabajo.
Una vez que la canalización se ejecuta como un trabajo, se pueden usar todos los cmdlets `*-Job` estándar para administrar el trabajo.
Las variables (se omiten las específicas del proceso) que se usan en la canalización se copian automáticamente en el trabajo para que funcione `Copy-Item $foo $bar &`.
El trabajo también se ejecuta en el directorio actual, en lugar del directorio principal del usuario.
Para más información sobre los trabajos de PowerShell, vea [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).

## <a name="semantic-versioning"></a>Versionamiento Semántico

- `SemanticVersion` ahora es compatible con `SemVer 2.0`. (#5037) (Gracias, @iSazonov).
- Se ha cambiado el valor predeterminado de `ModuleVersion` en `New-ModuleManifest` a `0.0.1` para adaptarse a SemVer. (#4842) (Gracias, @LDSpits).
- Se ha agregado `semver` como acelerador de tipo para `System.Management.Automation.SemanticVersion`. (#4142) (Gracias, @oising).
- Se ha habilitado la comparación entre una instancia de `SemanticVersion` y una instancia de `Version` que se construye únicamente con valores de versión `Major` y `Minor`.

## <a name="language-updates"></a>Actualizaciones del lenguaje

- Implemente el análisis de escape Unicode para que los usuarios puedan emplear caracteres Unicode como argumentos, cadenas o nombres de variable. (#3958) (Gracias, @rkeithhill).
- Se ha agregado un nuevo carácter de escape para ESC: `` `e``.
- Se ha agregado compatibilidad con la conversión de enumeraciones en cadenas. (#4318) (Gracias, @KirkMunro).
- Se ha corregido la conversión de una matriz de elemento único en una colección genérica. (#3170)
- Se ha agregado la sobrecarga de intervalo de caracteres al operador `..`, por lo que `'a'..'z'` devuelve caracteres de la "a" a la "z". (#5026) (Gracias, @IISResetMe).
- Se ha corregido la asignación de variables de modo que no sobrescriba variables de solo lectura.
- Inserte variables locales de variables automáticas en "DottedScopes" al usar el operador punto en cmdlets de script. (#4709)
- Habilite el uso de la opción "Singleline, Multiline" en el operador de división. (#4721) (Gracias, @iSazonov).

## <a name="engine-updates"></a>Actualizaciones del motor

- `$PSVersionTable` tiene cuatro propiedades nuevas:
  - `PSEdition`: se establece en `Core` en PowerShell Core y en `Desktop` en Windows PowerShell.
  - `GitCommitId`: es el identificador de confirmación de Git de la rama o la etiqueta de Git donde se ha compilado PowerShell.
    En las compilaciones publicadas, probablemente será igual que `PSVersion`.
  - `OS`: se trata de una cadena de versión de sistema operativo devuelta por `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`.
  - `Platform`: la devuelve `[System.Environment]::OSVersion.Platform`. Se establece en `Win32NT` en Windows, en `MacOSX` en macOS y en `Unix` en Linux.
- Se ha quitado la propiedad `BuildVersion` de `$PSVersionTable`.
  Esta propiedad estaba estrechamente ligada a la versión de compilación de Windows.
  En su lugar, se recomienda usar `GitCommitId` para recuperar la versión de compilación exacta de PowerShell Core. (#3877) (Gracias, @iSazonov).
- Quite la propiedad `ClrVersion` de `$PSVersionTable`.
  Esta propiedad no es pertinente para .NET Core y solo se ha conservado en .NET Core con fines heredados específicos que son no aplicables a PowerShell.
- Se han agregado tres nuevas variables automáticas para determinar si PowerShell se está ejecutando en un sistema operativo determinado: `$IsWindows`, `$IsMacOs` y `$IsLinux`.
- Agregue `GitCommitId` al titular de PowerShell Core.
  Ahora ya no tiene que ejecutar `$PSVersionTable` al iniciar PowerShell para obtener la versión. (#3916) (Gracias, @iSazonov).
- Agregue un archivo de configuración JSON denominado `powershell.config.json` en `$PSHome` para almacenar algunos valores de configuración necesarios antes del momento del inicio (por ejemplo, `ExecutionPolicy`).
- No bloquee la canalización al ejecutar archivos ejecutables de Windows.
- Se ha habilitado la enumeración de colecciones COM. (#4553)

## <a name="cmdlet-updates"></a>Actualizaciones de cmdlets

### <a name="new-cmdlets"></a>Nuevos cmdlets

- Agregue `Get-Uptime` a `Microsoft.PowerShell.Utility`.
- Agregue el comando `Remove-Alias`. (#5143) (Gracias, @PowershellNinja).
- Agregue `Remove-Service` al módulo de administración. (#4858) (Gracias, @joandrsn).

### <a name="web-cmdlets"></a>Cmdlets web

- Agregue compatibilidad con la autenticación de certificados para cmdlets web. (#4646) (Gracias, @markekraus).
- Agregue compatibilidad con encabezados de contenido a los cmdlets de web. (#4494 y #4640) (Gracias, @markekraus).
- Agregue compatibilidad con varios encabezados de vínculo a los cmdlets web. (#5265) (Gracias, @markekraus).
- Compatibilidad con la paginación de encabezado de vínculo en los cmdlets web. (&#3828;)
  - Para `Invoke-WebRequest`, cuando la respuesta incluye un encabezado de vínculo, creamos una propiedad RelationLink, como un diccionario, que representa las direcciones URL y los atributos `rel`. Asegúrese de que las direcciones URL son absolutas para que al desarrollador le sea más fácil usarlas.
  - Para `Invoke-RestMethod`, cuando la respuesta incluye un encabezado de vínculo, exponemos un modificador `-FollowRelLink` que sigue automáticamente vínculos `next` `rel` hasta que ya no existan o se alcance el valor de parámetro opcional `-MaximumFollowRelLink`.
- Agregue el parámetro `-CustomMethod` a cmdlets web para permitir los verbos de método no estándar. (#3142) (Gracias, @Lee303).
- Agregue compatibilidad con `SslProtocol` a cmdlets web. (#5329) (Gracias, @markekraus).
- Agregue compatibilidad con varias partes a cmdlets web. (#4782) (Gracias, @markekraus).
- Agregue `-NoProxy` a los cmdlets web para que omitan la configuración de proxy de todo el sistema. (#3447) (Gracias, @TheFlyingCorpse).
- El agente de usuario de los cmdlets web ahora informa sobre la plataforma del sistema operativo. (#4937) (Gracias, @LDSpits).
- Agregue el modificador `-SkipHeaderValidation` a los cmdlets web para admitir la adición de encabezados sin validar el valor del encabezado. (#4085)
- Permita que los cmdlets web no validen el certificado HTTPS del servidor si es necesario.
- Agregue parámetros de autenticación a los cmdlets web. (#5052) (Gracias, @markekraus).
  - Agregue `-Authentication`, que proporciona tres opciones: Basic, OAuth y Bearer.
  - Agregue `-Token` para obtener el token de portador para las opciones OAuth y Bearer.
  - Agregue `-AllowUnencryptedAuthentication` para omitir la autenticación que se proporciona para todos los esquemas de transporte que no sean HTTPS.
- Agregue `-ResponseHeadersVariable` a `Invoke-RestMethod` para habilitar la captura de encabezados de respuesta. (#4888) (Gracias, @markekraus).
- Corrija los cmdlets web para incluir la respuesta HTTP en la excepción cuando el código de estado de respuesta no es correcto. (#3201)
- Cambie los cmdlets web `UserAgent` de `WindowsPowerShell` a `PowerShell`. (#4914) (Gracias, @markekraus).
- Agregue la detección explícita de `ContentType` a `Invoke-RestMethod`. (#4692)
- Corrija los cmdlets web `-SkipHeaderValidation` para que funcionen con encabezados de agente de usuario no estándares. (#4479 y #4512) (Gracias, @markekraus).

### <a name="json-cmdlets"></a>Cmdlets JSON

- Agregue `-AsHashtable` a `ConvertFrom-Json` para devolver `Hashtable` en su lugar. (#5043) (Gracias, @bergmeister).
- Use un formateador más descriptivo con la salida `ConvertTo-Json`. (#2787) (Gracias, @kittholland).
- Agregue compatibilidad con la serialización de `Jobject` a `ConvertTo-Json`. (#5141)
- Corrija `ConvertFrom-Json` para deserializar una matriz de cadenas de la canalización que construyan juntas una cadena JSON completa.
  Esto corrige algunos casos en los que las líneas nuevas interrumpirían el análisis de JSON. (#3823)
- Quite el valor `AliasProperty "Count"` definido para `System.Array`.
  Esto quita la propiedad superflua `Count` de alguna salida `ConvertFrom-Json`. (#3231) (Gracias, @PetSerAl).

### <a name="csv-cmdlets"></a>Cmdlets CSV

- Agregue compatibilidad con `PSTypeName` para `Import-Csv` y `ConvertFrom-Csv`. (#5389) (Gracias, @markekraus).
- Haga que `Import-Csv` admita `CR`, `LF` y `CRLF` como delimitadores de línea. (#5363) (Gracias, @iSazonov).
- Convierta `-NoTypeInformation` en el valor predeterminado en `Export-Csv` y `ConvertTo-Csv`. (#5164) (Gracias, @markekraus).

### <a name="service-cmdlets"></a>Cmdlets de servicio

- Agregue las propiedades `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName` y `StartupType` a los objetos `ServiceController` devueltos por `Get-Service`. (#4907) (Gracias, @joandrsn).
- Agregue funcionalidad para establecer credenciales en el comando `Set-Service`. (#4844) (Gracias, @joandrsn).

### <a name="other-cmdlets"></a>Otros cmdlets

- Agregue un parámetro a `Get-ChildItem` denominado `-FollowSymlink` que atraviese vínculos simbólicos a petición, con comprobaciones para los bucles de vínculo. (#4020)
- Actualice `Add-Type` para que admita `CSharpVersion7`. (#3933) (Gracias, @iSazonov).
- Quite el módulo `Microsoft.PowerShell.LocalAccounts` debido al uso de API no admitidas hasta que se encuentre una solución mejor. (#4302)
- Quite los cmdlets `*-Counter` de `Microsoft.PowerShell.Diagnostics` debido al uso de API no admitidas hasta que se encuentre una solución mejor. (#4303)
- Agregue compatibilidad con `Invoke-Item -Path <folder>`. (#4262)
- Agregue los modificadores `-Extension` y `-LeafBase` a `Split-Path` para poder dividir las rutas de acceso entre la extensión de nombre de archivo y el resto del nombre de archivo. (#2721) (Gracias, @powercode).
- Agregue parámetros `-Top` y `-Bottom` a `Sort-Object` para la ordenación N superior o inferior.
- Exponga el proceso primario de un proceso mediante la adición de `CodeProperty "Parent"` a `System.Diagnostics.Process`. (#2850) (Gracias, @powercode).
- Use MB en lugar de KB para las columnas de memoria de `Get-Process`.
- Agregue el modificador `-NoNewLine` para `Out-String`. (#5056) (Gracias, @raghav710).
- El cmdlet `Move-Item` usa los parámetros `-Include`, `-Exclude` y `-Filter`. (#3878)
- Permita el uso de `*` en la ruta de acceso del Registro para `Remove-Item`. (#4866)
- Agregue `-Title` a `Get-Credential` y unifique la experiencia del símbolo del sistema en las distintas plataformas.
- Agregue el parámetro `-TimeOut` a `Test-Connection`. (#2492)
- Los cmdlets `Get-AuthenticodeSignature` ahora pueden obtener la marca de tiempo de la firma del archivo. (#4061)
- Quite de `Get-Help` el modificador no admitido `-ShowWindow`. (#4903)
- Corrija `Get-Content -Delimiter` para que no incluya el delimitador en los elementos de matriz devueltos. (#3706) (Gracias, @mklement0).
- Agregue los parámetros `Meta`, `Charset` y `Transitional` a `ConvertTo-HTML`. (#4184) (Gracias, @ergo3114).
- Agregue las propiedades `WindowsUBR` y `WindowsVersion` al resultado `Get-ComputerInfo`.
- Agregue el parámetro `-Group` a `Get-Verb`.
- Agregue compatibilidad con `ShouldProcess` a `New-FileCatalog` y `Test-FileCatalog` (corrige `-WhatIf` y `-Confirm`). (#3074) (Gracias, @iSazonov).
- Agregue el modificador `-WhatIf` al cmdlet `Start-Process`. (#4735) (Gracias, @sarithsutha).
- Agregue `ValidateNotNullOrEmpty` a muchos parámetros existentes.

## <a name="tab-completion"></a>Finalización con tabulación

- Se ha mejorado la inferencia de tipos en la finalización con tabulación en función de los valores de las variables del entorno de ejecución. (#2744) (Gracias, @powercode). Esto permite la finalización con tabulación en situaciones como:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Agregue la finalización con tabulación de tabla hash para `-Property` de `Select-Object`. (#3625) (Gracias, @powercode).
- Habilite la finalización automática de argumentos para `-ExcludeProperty` y `-ExpandProperty` de `Select-Object`. (#3443) (Gracias, @iSazonov).
- Corrija un error en la finalización con tabulación para realizar una llamada a `native.exe --<tab>` en el completador nativo. (#3633) (Gracias, @powercode).

## <a name="breaking-changes"></a>Cambios importantes

Hemos introducido una serie de cambios importantes en PowerShell Core 6.0.
Para más información sobre ellos, vea [Breaking Changes in PowerShell Core 6.0][breaking-changes] (Cambios importantes en PowerShell Core 6.0).

## <a name="debugging"></a>Depuración

- Compatibilidad con la depuración paso a paso remota para `Invoke-Command -ComputerName`. (#3015)
- Habilite el registro de depuración del enlazador en PowerShell Core.

## <a name="filesystem-updates"></a>Actualizaciones del sistema de archivos

- Habilite el uso del proveedor del sistema de archivos desde una ruta de acceso UNC. ($4998)
- `Split-Path` ahora funciona con raíces UNC.
- `cd` sin argumentos ahora se comporta como `cd ~`.
- Se ha corregido PowerShell Core para que permita el uso de rutas de acceso con una longitud superior a 260 caracteres. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Correcciones de errores y mejoras en el rendimiento

Hemos realizado *numerosas* mejoras en el rendimiento de PowerShell, incluidos el tiempo de inicio, varios cmdlets integrados y la interacción con binarios nativos.

También se ha corregido una serie de errores de PowerShell Core.
Para obtener una lista completa de correcciones y cambios, visite nuestro [registro de cambios][] en GitHub.

## <a name="telemetry"></a>Telemetría

- PowerShell Core 6.0 ha agregado telemetría al host de consola para informar sobre dos valores (#3620):
  - La plataforma de sistema operativo (`$PSVersionTable.OSDescription`).
  - La versión exacta de PowerShell (`$PSVersionTable.GitCommitId`).

Si desea dejar de participar en esta telemetría, basta con eliminar `$PSHome\DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` o crear la variable de entorno `POWERSHELL_TELEMETRY_OPTOUT` con uno de los valores siguientes: `true`, `1` o `yes`.
Al eliminar este archivo o crear la variable se omite toda la telemetría, incluida la anterior a la primera ejecución de PowerShell.
También tenemos previsto exponer estos datos de telemetría y la información que se obtenga a partir de la telemetría en el [panel de comunidad][community-dashboard].
Encontrará más información sobre la forma en que usamos estos datos en esta [entrada de blog][telemetry-blog].

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/en-us/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: https://github.com/PowerShell/PowerShell/tree/master/docs/BREAKINGCHANGES.md
[registro de cambios]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[blog de .NET]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[preguntas más frecuentes]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[Docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
