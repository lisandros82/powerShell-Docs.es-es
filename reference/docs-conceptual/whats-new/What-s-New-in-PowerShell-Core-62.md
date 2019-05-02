---
title: Novedades de PowerShell Core 6.2
description: Nuevas características y cambios publicados en PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 6a0da8a410e602ae3963e0bc7bace745317d7d4b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058104"
---
# <a name="whats-new-in-powershell-core-62"></a>Novedades de PowerShell Core 6.2

La versión PowerShell Core 6.2 se centró en mejoras de rendimiento, correcciones de errores y otras actualizaciones más pequeñas relativas a los cmdlet y el lenguaje en favor de la calidad. Para ver una lista completa de las mejoras, consulte nuestros [registros de cambios](https://github.com/PowerShell/PowerShell/releases) detallados en GitHub.

## <a name="experimental-features"></a>Características experimentales

Ya habíamos habilitado con anterioridad la compatibilidad con las [características experimentales][]. En la versión 6.2, tenemos cuatro características experimentales para probar. Háganos llegar sus comentarios para que podamos realizar mejoras y decidir si vale la pena promocionar la función al estado general.

Use `Get-ExperimentalFeature` para obtener una lista de las características experimentales disponibles. Puede habilitar o deshabilitar estas características con `Enable-ExperimentalFeature` y `Disable-ExperimentalFeature`.

### <a name="command-not-found-suggestions"></a>Sugerencias para comandos no encontrados

Esta característica utiliza la coincidencia aproximada para buscar sugerencias para aquellos comandos o cmdlets que puede haber escrito de manera incorrecta.

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a>Ejemplo

En este ejemplo, el nombre del cmdlet mal escrito coincide de manera aproximada con varias sugerencias que se ordenan de la más probable a la menos probable.

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a>Procesamiento por lotes de comunicación remota implícita

Cuando se usa la [comunicación remota implícita](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) en una canalización, PowerShell trata cada comando en la canalización de forma independiente. Los objetos se serializan repetidamente y `de-serialized` entre el cliente y el sistema remoto a través de la ejecución de la canalización.

Con esta característica, PowerShell analiza la canalización para determinar si es seguro ejecutar el comando y existe en el sistema de destino. Cuando es true, PowerShell ejecuta toda la canalización de forma remota y solo serializa y `de-serializes` los resultados al cliente.

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

Una prueba real de `Get-Process | Sort-Object` sobre localhost disminuye de 10-15 segundos a 20-30 **milisegundos**. Solo debe habilitarse la característica en el cliente. No es preciso realizar cambios en el servidor.

### <a name="temp-drive"></a>Unidad temporal

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

Si usa PowerShell Core en diferentes sistemas operativos, verá que la variable de entorno para buscar el directorio temporal es diferente en Windows, macOS y Linux. Con esta característica, obtendrá un [PSDrive][] denominado `Temp:` que se asigna automáticamente a la carpeta temporal para el sistema operativo que está usando.

#### <a name="example"></a>Ejemplo

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> `Get-Content` Temp:/hello.txt
Hello World!
```

Tenga en cuenta que los comandos de archivo nativos (como `ls` en Linux) no son compatibles con PSDrive y no verán esta unidad `Temp:`.

### <a name="abbreviation-expansion"></a>Expansión de abreviatura

Se espera que los cmdlets de PowerShell tengan nombres descriptivos. Esto da como resultado nombres largos que son más difíciles de escribir. Esta característica permite simplemente escribir los caracteres en mayúsculas del cmdlet y usar la finalización con tabulación para encontrar una coincidencia.

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a>Ejemplo

```powershell
PS> i-arsavsf
```

Si presiona el tabulador y tiene instalado el módulo [Az](https://www.powershellgallery.com/packages/Az) de Azure PowerShell, se completará automáticamente a lo siguiente:

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> Esta característica está pensada para usarse interactivamente. No se pueden ejecutar las formas abreviadas de los cmdlets.
> Esta característica no sirve para reemplazar los alias.

## <a name="breaking-changes"></a>Cambios importantes

- Se ha corregido el comportamiento de `-NoEnumerate` en `Write-Output` para que sea coherente con Windows PowerShell. (#9069)
- Se ha hecho que el resultado de `Join-String -InputObject 1,2,3` sea igual al resultado de `1,2,3 | Join-String` (#8611) (Gracias, @sethvs)
- Se ha agregado `-Stable` a `Sort-Object` y las pruebas relacionadas (#7862) (Gracias, @KirkMunro)
- Se ha mejorado el cmdlet `Start-Sleep` para que acepte las fracciones de segundo (#8537) (Gracias, @Prototyyppi)
- Se ha cambiado la tabla hash para que utilice OrdinalIgnoreCase para que sea `case-insensitive` en todas las referencias culturales (#8566)
- Se ha corregido **LiteralPath** en `Import-Csv` para que se enlace con la salida `Get-ChildItem` (#8277) (Gracias, @iSazonov)
- Ya no se omite una columna sin nombre si se usa el delimitador de comillas dobles en `Import-Csv` (#7899) (Gracias, @Topping)
- `Get-ExperimentalFeature` ya no tiene el conmutador `-ListAvailable` (#8318)
- El parámetro de depuración ahora establece `$DebugPreference` en **Continue** en lugar de en **Inquire** (#8195) (Gracias, @KirkMunro)
- Se respeta `-OutputFormat` si se especifica en un comando no interactivo, redirigido, codificado que se usa con pwsh (#8115)
- Se carga el ensamblado desde la ruta de acceso base del módulo antes de intentar cargar desde la GAC (#8073)
- Se ha quitado la tilde de los paquetes en versión preliminar de Linux (#8244)
- Se ha movido el procesamiento de `-WorkingDirectory` antes del procesamiento de perfiles (#8079)
- No se agrega la variable de entorno `PATHEXT` en Unix (#7697) (Gracias, @iSazonov)

## <a name="known-issues"></a>Problemas conocidos

- La comunicación remota en plataformas ARM de Windows IOT presenta un problema al cargar los módulos. Consulte (#8053)

## <a name="general-updates-and-fixes"></a>Actualizaciones y correcciones generales

- Se ha habilitado la finalización con tabulación que no distingue mayúsculas y minúsculas para los archivos y carpetas del sistema de archivos que distingue mayúsculas y minúsculas (#8128)
- Se ha hecho público PSVersionInfo.PSVersion y PSVersionInfo.PSEdition (#8054) (Gracias, @KirkMunro)
- Se ha agregado la inferencia de tipos para `$_` / `$PSItem` en bloques `catch{ }` (#8020) (Gracias, @vexx32)
- Se ha corregido la inferencia de tipo de invocación del método estático (#8018) (Gracias, @SeeminglyScience)
- Se han creado tipos deducidos para `Select-Object`, `Group-Object`, **PSObject** y **Hashtable** (#7231) (Gracias, @powercode)
- Se ha añadido compatibilidad para el método de llamada con parámetros de tipo `ByRef-like` (#7721)
- Se ha controlado el caso en que la ruta de acceso del módulo de Windows PowerShell ya está en el PSModulePath del entorno (#7727)
- Se han habilitado los cmdlets `SecureString` para entornos que no son de Windows mediante el almacenamiento del texto sin formato (#9199)
- Se ha mejorado el mensaje de error en sistemas que no son Windows al importar clixml con SecureString (#7997)
- Se ha agregado el parámetro ReplyTo a `Send-MailMessage` (#8727) (Gracias, @replicaJunction)
- Se ha agregado el mensaje Obsolete a `Send-MailMessage` (#9178)
- Se ha corregido `Restart-Computer` para que funcione en `localhost` cuando WinRM no está presente (#9160)
- Se ha generado error de terminación `Start-Job` cuando se hospeda PowerShell (#9128)
- Se han agregado aceleradores y sufijos de tipo de estilo C# para los literales ushort, uint, ulong y short (# 7813) (Gracias, @vexx32)
- Se han agregado nueva sufijos para literales numéricos - consulte [about_Numeric_Literals][] (Acerca de literales numéricos) (#7901) (Gracias, @vexx32)
- Se notifica el nivel de impacto correctamente cuando SupportsShouldProcess no está establecido en "true" (#8209) (Gracias, @vexx32)
- Se han solucionado los problemas del juego de caracteres de Request en los cmdlets web (#8742) (Gracias, @markekraus)
- Se ha solucionado el problema `100-continue` de Expect con los cmdlets web (#8679) (Gracias, @markekraus)
- Se ha solucionado el problema de bloqueo de archivos con los cmdlets web (#7676) (Gracias, @Claustn)
- Se ha corregido el problema de análisis de la página de códigos en `Invoke-RestMethod` (#8694) (Gracias, @markekraus)
- Se ha refactorizado `ConvertTo-Json` para exponer JsonObject.ConvertToJson como una API pública (#8682)
- Se ha agregado la profundidad máxima configurable en `ConvertFrom-Json` con -Depth (#8199) (Gracias, @louistio)
- Se ha agregado el parámetro EscapeHandling en el cmdlet `ConvertTo-Json` (#7775) (Gracias, @iSazonov)
- Se ha agregado `-CustomPipeName` a pwsh y `Enter-PSHostProcess` (#8889)
- Se ha habilitado la creación de vínculos simbólicos relativos en Windows con `New-Item` (#8783)
- Se permite a los usuarios de Windows en modo de desarrollador la creación de vínculos simbólicos sin elevación (#8534)
- Se ha habilitado `Write-Information` para aceptar `$null` (#8774)
- Se ha corregido `Get-Help` para las funciones avanzadas con el contenido de ayuda de Azure MAML (#8353)
- Se ha corregido el problema de PSTypeName `Get-Help` con -Parameter cuando se declara un solo parámetro (#8754) (Gracias, @pougetat)
- Se ha corregido el cálculo de token para `Get-Help` ejecutando en ScriptBlock para la ayuda de comentarios. (#8238) (Gracias, @hubuk)
- Se ha cambiado el parámetro -Parameter del cmdlet `Get-Help` para que acepte matrices de cadena (#8454) (Gracias, @sethvs)
- Se ha resuelto PAGER si su ruta de acceso contiene espacios (#8571) (Gracias, @pougetat)
- Se ha agregado símbolo del sistema para el uso de `less` en la función "help" para indicar al usuario cómo cerrar (#7998)
- Se ha agregado la compatibilidad con tipos enum y char en el cmdlet `Format-Hex` (#8191) (Gracias, @iSazonov)
- Se ha quitado ShouldProcess de `Format-Hex` (#8178)
- Se han agregado nuevos parámetros de Offset y Count a `Format-Hex` y se ha refactorizado el cmdlet (#7877) (Gracias, @iSazonov)
- Se permite "name" como clave de alias para "label" en `ConvertTo-Html`, se permite que la entrada "width" sea un número entero (#8426) (Gracias, @mklement0)
- Se ha conseguido que las propiedades calculadas basadas en el scriptblock vuelvan a funcionar en `ConvertTo-Html` (#8427) (Gracias, @mklement0)
- Se ha agregado un cmdlet `Join-String` para crear texto a partir de la canalización de entrada (#7660) (Gracias, @powercode)
- Se ha corregido la lógica del parámetro FormatString del cmdlet `Join-String` (#8449) (Gracias, @sethvs)
- Se ha vuelto a cambiar `Clear-Host` para que use `$RAWUI` y se ha desactivado para que funcione en la comunicación remota (#8609)
- Se ha cambiado `Clear-Host` para que llame simplemente a `[console]::clear` y se ha quitado el alias de Unix (#8603)
- Se ha corregido LiteralPath en `Import-Csv` para que se enlace con la salida `Get-ChildItem` (#8277) (Gracias, @iSazonov)
- La función de ayuda no debe usar el elemento de paginación para AliasHelpInfo (#8552)
- Se ha agregado `-UseMinimalHeader` a `Start-Transcript` para minimizar el encabezado de transcripción (#8402) (Gracias, @lukexjeremy)
- Se han agregado los cmdlets `Enable-ExperimentalFeature` y `Disable-ExperimentalFeature` (#8318)
- Se han expuesto todos los cmdlets de **PSDiagnostics** si logman.exe está disponible (#8366)
- Se ha quitado el parámetro **Persist** de `New-PSDrive` en la plataforma `non-Windows` (#8291) (Gracias, @lukexjeremy)
- Se ha agregado compatibilidad para `cd +` (#7206) (Gracias, @bergmeister)
- Se ha permitido que `Set-Location -LiteralPath` funcione con carpetas denominadas - y + (#8089)
- `Test-Path` devuelve `$false` cuando se especifica un valor vacío o de ruta de acceso `$null` (#8080) (Gracias, @vexx32)
- Se permite que un parámetro dinámico se devuelva incluso si la ruta de acceso no coincide con ningún proveedor (#7957)
- Se ha agregado compatibilidad con `Get-PSHostProcessInfo` y `Enter-PSHostProcess` en plataformas Unix (#8232)
- Se han reducido las asignaciones en el cmdlet `Get-Content` (#8103) (Gracias, @iSazonov)
- Se ha habilitado `Add-Content` para compartir el acceso de lectura con otras herramientas al escribir contenido (#8091)
- `Get/Add-Content` produce el error mejorado cuando el destino es un contenedor (#7823) (Gracias, @kvprasoon)
- Agregue los parámetros `-Name`, `-NoUserOverrides` y `-ListAvailable` al cmdlet `Get-Culture` (#7702) (Gracias, @iSazonov)
- Se ha agregado un atributo unificado para la finalización del parámetro **Encoding**. (#7732) (Gracias, @ThreeFive-O)
- Se permiten identificadores numéricos y el nombre de páginas de códigos registradas en los parámetros **Encoding** (#7636) (Gracias, @iSazonov)
- Se ha corregido `Rename-Item -Path` con el carácter comodín (#7398) (Gracias, @kwkam)
- Cuando se usa `Start-Transcript` y el archivo existe, se vacía el archivo en lugar de eliminarlo (#8131) (Gracias, @paalbra)
- Los archivos de código fuente `Add-Type` se han hecho tales explícitamente con **FileAccess.Read** y **FileShare.Read** (#7915) (Gracias, @IISResetMe)
- Se ha corregido `Enter-PSSession -ContainerId` para el Windows más reciente (#7883)
- Se ha asegurado que la propiedad **NestedModules** se rellene por `Test-ModuleManifest` (#7859)
- Se ha agregado el caso `%F` a `Get-Date` -UFormat (#7630) (Gracias, @britishben)
- Se ha corregido `Set-Service -Status Stopped` para que detenga los servicios con dependencias (#5525) (Gracias, @zhenggu)

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals (Acerca de literales numéricos)
[Características experimentales]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
