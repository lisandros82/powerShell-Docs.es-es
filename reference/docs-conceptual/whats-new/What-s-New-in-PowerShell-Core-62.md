---
title: Novedades de PowerShell Core 6.2
description: Nuevas características y cambios publicados en PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 2f5f5d11ba46d53966093c5e3ed6d0c7d47308d0
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737141"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="d5a33-103">Novedades de PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="d5a33-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="d5a33-104">La versión PowerShell Core 6.2 se centró en mejoras de rendimiento, correcciones de errores y otras actualizaciones más pequeñas relativas a los cmdlet y el lenguaje en favor de la calidad.</span><span class="sxs-lookup"><span data-stu-id="d5a33-104">The PowerShell Core 6.2 release focused on performance improvements, bug fixes, and smaller cmdlet and language enhancements that improve the quality.</span></span> <span data-ttu-id="d5a33-105">Para ver una lista completa de las mejoras, consulte nuestros [registros de cambios](https://github.com/PowerShell/PowerShell/releases) detallados en GitHub.</span><span class="sxs-lookup"><span data-stu-id="d5a33-105">To see a full list of improvements, check out our detailed [changelogs](https://github.com/PowerShell/PowerShell/releases) on GitHub.</span></span>

## <a name="experimental-features"></a><span data-ttu-id="d5a33-106">Características experimentales</span><span class="sxs-lookup"><span data-stu-id="d5a33-106">Experimental Features</span></span>

<span data-ttu-id="d5a33-107">Ya habíamos habilitado con anterioridad la compatibilidad con las [características experimentales][].</span><span class="sxs-lookup"><span data-stu-id="d5a33-107">Previously, we enabled support for [Experimental Features][].</span></span> <span data-ttu-id="d5a33-108">En la versión 6.2, tenemos cuatro características experimentales para probar. Háganos llegar sus comentarios para que podamos realizar mejoras y decidir si vale la pena promocionar la función al estado general.</span><span class="sxs-lookup"><span data-stu-id="d5a33-108">In the 6.2 release, we have four experimental features to try out. Please provide feedback so we can make improvements and to decide whether the feature is worth promoting to mainstream status.</span></span>

<span data-ttu-id="d5a33-109">Use `Get-ExperimentalFeature` para obtener una lista de las características experimentales disponibles.</span><span class="sxs-lookup"><span data-stu-id="d5a33-109">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="d5a33-110">Puede habilitar o deshabilitar estas características con `Enable-ExperimentalFeature` y `Disable-ExperimentalFeature`.</span><span class="sxs-lookup"><span data-stu-id="d5a33-110">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

### <a name="command-not-found-suggestions"></a><span data-ttu-id="d5a33-111">Sugerencias para comandos no encontrados</span><span class="sxs-lookup"><span data-stu-id="d5a33-111">Command Not Found Suggestions</span></span>

<span data-ttu-id="d5a33-112">Esta característica utiliza la coincidencia aproximada para buscar sugerencias para aquellos comandos o cmdlets que puede haber escrito de manera incorrecta.</span><span class="sxs-lookup"><span data-stu-id="d5a33-112">This feature uses fuzzy matching to find suggestions for commands or cmdlets you may have mistyped.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a><span data-ttu-id="d5a33-113">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d5a33-113">Example</span></span>

<span data-ttu-id="d5a33-114">En este ejemplo, el nombre del cmdlet mal escrito coincide de manera aproximada con varias sugerencias que se ordenan de la más probable a la menos probable.</span><span class="sxs-lookup"><span data-stu-id="d5a33-114">In this example, the misspelled cmdlet name is fuzzy matched to several suggestions from most likely to least likely.</span></span>

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

### <a name="implicit-remoting-batching"></a><span data-ttu-id="d5a33-115">Procesamiento por lotes de comunicación remota implícita</span><span class="sxs-lookup"><span data-stu-id="d5a33-115">Implicit Remoting Batching</span></span>

<span data-ttu-id="d5a33-116">Cuando se usa la [comunicación remota implícita](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) en una canalización, PowerShell trata cada comando en la canalización de forma independiente.</span><span class="sxs-lookup"><span data-stu-id="d5a33-116">When using [implicit remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in a pipeline, PowerShell treats each command in the pipeline independently.</span></span> <span data-ttu-id="d5a33-117">Los objetos se serializan repetidamente y `de-serialized` entre el cliente y el sistema remoto a través de la ejecución de la canalización.</span><span class="sxs-lookup"><span data-stu-id="d5a33-117">Objects are repeatedly serialized and `de-serialized` between the client and remote system over the execution of the pipeline.</span></span>

<span data-ttu-id="d5a33-118">Con esta característica, PowerShell analiza la canalización para determinar si es seguro ejecutar el comando y existe en el sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="d5a33-118">With this feature, PowerShell analyzes the pipeline to determine if the command is safe to run and it exists on the target system.</span></span> <span data-ttu-id="d5a33-119">Cuando es true, PowerShell ejecuta toda la canalización de forma remota y solo serializa y `de-serializes` los resultados al cliente.</span><span class="sxs-lookup"><span data-stu-id="d5a33-119">When true, PowerShell executes the entire pipeline remotely and only serializes and `de-serializes` the results back to the client.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

<span data-ttu-id="d5a33-120">Una prueba real de `Get-Process | Sort-Object` sobre localhost disminuye de 10-15 segundos a 20-30 **milisegundos**.</span><span class="sxs-lookup"><span data-stu-id="d5a33-120">A real-world test of `Get-Process | Sort-Object` over localhost decreases from 10-15 seconds to 20-30 **milliseconds**.</span></span> <span data-ttu-id="d5a33-121">Solo debe habilitarse la característica en el cliente.</span><span class="sxs-lookup"><span data-stu-id="d5a33-121">The feature only needs to be enabled on the client.</span></span> <span data-ttu-id="d5a33-122">No es preciso realizar cambios en el servidor.</span><span class="sxs-lookup"><span data-stu-id="d5a33-122">No changes are required on the server.</span></span>

### <a name="temp-drive"></a><span data-ttu-id="d5a33-123">Unidad temporal</span><span class="sxs-lookup"><span data-stu-id="d5a33-123">Temp Drive</span></span>

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

<span data-ttu-id="d5a33-124">Si usa PowerShell Core en diferentes sistemas operativos, verá que la variable de entorno para buscar el directorio temporal es diferente en Windows, macOS y Linux.</span><span class="sxs-lookup"><span data-stu-id="d5a33-124">If you're using PowerShell Core on different operating systems, you'll discover that the environment variable for finding the temporary directory is different on Windows, macOS, and Linux!</span></span> <span data-ttu-id="d5a33-125">Con esta característica, obtendrá un [PSDrive][] denominado `Temp:` que se asigna automáticamente a la carpeta temporal para el sistema operativo que está usando.</span><span class="sxs-lookup"><span data-stu-id="d5a33-125">With this feature, you get a [PSDrive][] called `Temp:` that is automatically mapped to the temporary folder for the operating system you are using.</span></span>

#### <a name="example"></a><span data-ttu-id="d5a33-126">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d5a33-126">Example</span></span>

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

<span data-ttu-id="d5a33-127">Tenga en cuenta que los comandos de archivo nativos (como `ls` en Linux) no son compatibles con PSDrive y no verán esta unidad `Temp:`.</span><span class="sxs-lookup"><span data-stu-id="d5a33-127">Be aware that native file commands (like `ls` on Linux) are not aware of PSDrives and won't see this `Temp:` drive.</span></span>

### <a name="abbreviation-expansion"></a><span data-ttu-id="d5a33-128">Expansión de abreviatura</span><span class="sxs-lookup"><span data-stu-id="d5a33-128">Abbreviation Expansion</span></span>

<span data-ttu-id="d5a33-129">Se espera que los cmdlets de PowerShell tengan nombres descriptivos.</span><span class="sxs-lookup"><span data-stu-id="d5a33-129">PowerShell cmdlets are expected to have descriptive nouns.</span></span> <span data-ttu-id="d5a33-130">Esto da como resultado nombres largos que son más difíciles de escribir.</span><span class="sxs-lookup"><span data-stu-id="d5a33-130">This results in long names that are more difficult to type.</span></span> <span data-ttu-id="d5a33-131">Esta característica permite simplemente escribir los caracteres en mayúsculas del cmdlet y usar la finalización con tabulación para encontrar una coincidencia.</span><span class="sxs-lookup"><span data-stu-id="d5a33-131">This feature allows you to just type the uppercase characters of the cmdlet and use tab-completion to find a match.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a><span data-ttu-id="d5a33-132">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d5a33-132">Example</span></span>

```powershell
PS> i-arsavsf
```

<span data-ttu-id="d5a33-133">Si presiona el tabulador y tiene instalado el módulo [Az](https://www.powershellgallery.com/packages/Az) de Azure PowerShell, se completará automáticamente a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d5a33-133">If you hit tab, and have the Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module installed, it will autocomplete to:</span></span>

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> <span data-ttu-id="d5a33-134">Esta característica está pensada para usarse interactivamente.</span><span class="sxs-lookup"><span data-stu-id="d5a33-134">This feature is intended to be used interactively.</span></span> <span data-ttu-id="d5a33-135">No se pueden ejecutar las formas abreviadas de los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d5a33-135">Abbreviated forms of cmdlets can't be executed.</span></span>
> <span data-ttu-id="d5a33-136">Esta característica no sirve para reemplazar los alias.</span><span class="sxs-lookup"><span data-stu-id="d5a33-136">This feature is not a replacement for aliases.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="d5a33-137">Últimos cambios</span><span class="sxs-lookup"><span data-stu-id="d5a33-137">Breaking Changes</span></span>

- <span data-ttu-id="d5a33-138">Se ha corregido el comportamiento de `-NoEnumerate` en `Write-Output` para que sea coherente con Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5a33-138">Fix `-NoEnumerate` behavior in `Write-Output` to be consistent with Windows PowerShell.</span></span> <span data-ttu-id="d5a33-139">(#9069)</span><span class="sxs-lookup"><span data-stu-id="d5a33-139">(#9069)</span></span>
- <span data-ttu-id="d5a33-140">Se ha hecho que el resultado de `Join-String -InputObject 1,2,3` sea igual al resultado de `1,2,3 | Join-String` (#8611) (Gracias, @sethvs)</span><span class="sxs-lookup"><span data-stu-id="d5a33-140">Make `Join-String -InputObject 1,2,3` result equal to `1,2,3 | Join-String` result (#8611) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="d5a33-141">Se ha agregado `-Stable` a `Sort-Object` y las pruebas relacionadas (#7862) (Gracias, @KirkMunro)</span><span class="sxs-lookup"><span data-stu-id="d5a33-141">Add `-Stable` to `Sort-Object` and related tests (#7862) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="d5a33-142">Se ha mejorado el cmdlet `Start-Sleep` para que acepte las fracciones de segundo (#8537) (Gracias, @Prototyyppi)</span><span class="sxs-lookup"><span data-stu-id="d5a33-142">Improve `Start-Sleep` cmdlet to accept fractional seconds (#8537) (Thanks @Prototyyppi!)</span></span>
- <span data-ttu-id="d5a33-143">Se ha cambiado la tabla hash para que utilice OrdinalIgnoreCase para que sea `case-insensitive` en todas las referencias culturales (#8566)</span><span class="sxs-lookup"><span data-stu-id="d5a33-143">Change hashtable to use OrdinalIgnoreCase to be `case-insensitive` in all Cultures (#8566)</span></span>
- <span data-ttu-id="d5a33-144">Se ha corregido **LiteralPath** en `Import-Csv` para que se enlace con la salida `Get-ChildItem` (#8277) (Gracias, @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="d5a33-144">Fix **LiteralPath** in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d5a33-145">Ya no se omite una columna sin nombre si se usa el delimitador de comillas dobles en `Import-Csv` (#7899) (Gracias, @Topping)</span><span class="sxs-lookup"><span data-stu-id="d5a33-145">No longer skips a column without name if double quote delimiter is used in `Import-Csv` (#7899) (Thanks @Topping!)</span></span>
- <span data-ttu-id="d5a33-146">`Get-ExperimentalFeature` ya no tiene el conmutador `-ListAvailable` (#8318)</span><span class="sxs-lookup"><span data-stu-id="d5a33-146">`Get-ExperimentalFeature` no longer has `-ListAvailable` switch (#8318)</span></span>
- <span data-ttu-id="d5a33-147">El parámetro de depuración ahora establece `$DebugPreference` en **Continue** en lugar de en **Inquire** (#8195) (Gracias, @KirkMunro)</span><span class="sxs-lookup"><span data-stu-id="d5a33-147">Debug parameter now sets `$DebugPreference` to **Continue** instead of **Inquire** (#8195) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="d5a33-148">Se respeta `-OutputFormat` si se especifica en un comando no interactivo, redirigido, codificado que se usa con pwsh (#8115)</span><span class="sxs-lookup"><span data-stu-id="d5a33-148">Honor `-OutputFormat` if specified in non-interactive, redirected, encoded command used with pwsh (#8115)</span></span>
- <span data-ttu-id="d5a33-149">Se carga el ensamblado desde la ruta de acceso base del módulo antes de intentar cargar desde la GAC (#8073)</span><span class="sxs-lookup"><span data-stu-id="d5a33-149">Load assembly from module base path before trying to load from the GAC (#8073)</span></span>
- <span data-ttu-id="d5a33-150">Se ha quitado la tilde de los paquetes en versión preliminar de Linux (#8244)</span><span class="sxs-lookup"><span data-stu-id="d5a33-150">Remove tilde from Linux preview packages (#8244)</span></span>
- <span data-ttu-id="d5a33-151">Se ha movido el procesamiento de `-WorkingDirectory` antes del procesamiento de perfiles (#8079)</span><span class="sxs-lookup"><span data-stu-id="d5a33-151">Move processing of `-WorkingDirectory` before processing of profiles (#8079)</span></span>
- <span data-ttu-id="d5a33-152">No se agrega la variable de entorno `PATHEXT` en Unix (#7697) (Gracias, @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="d5a33-152">Do not add `PATHEXT` environment variable on Unix (#7697) (Thanks @iSazonov!)</span></span>

## <a name="known-issues"></a><span data-ttu-id="d5a33-153">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="d5a33-153">Known Issues</span></span>

- <span data-ttu-id="d5a33-154">La comunicación remota en plataformas ARM de Windows IOT presenta un problema al cargar los módulos.</span><span class="sxs-lookup"><span data-stu-id="d5a33-154">Remoting on Windows IOT ARM platforms has an issue loading modules.</span></span> <span data-ttu-id="d5a33-155">Consulte (#8053)</span><span class="sxs-lookup"><span data-stu-id="d5a33-155">See (#8053)</span></span>

## <a name="general-updates-and-fixes"></a><span data-ttu-id="d5a33-156">Actualizaciones y correcciones generales</span><span class="sxs-lookup"><span data-stu-id="d5a33-156">General Updates and Fixes</span></span>

- <span data-ttu-id="d5a33-157">Se ha habilitado la finalización con tabulación que no distingue mayúsculas y minúsculas para los archivos y carpetas del sistema de archivos que distingue mayúsculas y minúsculas (#8128)</span><span class="sxs-lookup"><span data-stu-id="d5a33-157">Enable case-insensitive tab completion for files and folders on case-sensitive filesystem (#8128)</span></span>
- <span data-ttu-id="d5a33-158">Se ha hecho público PSVersionInfo.PSVersion y PSVersionInfo.PSEdition (#8054) (Gracias, @KirkMunro)</span><span class="sxs-lookup"><span data-stu-id="d5a33-158">Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="d5a33-159">Se ha agregado la inferencia de tipos para `$_` / `$PSItem` en bloques `catch{ }` (#8020) (Gracias, @vexx32)</span><span class="sxs-lookup"><span data-stu-id="d5a33-159">Add Type Inference for `$_` / `$PSItem` in `catch{ }` blocks (#8020) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="d5a33-160">Se ha corregido la inferencia de tipo de invocación del método estático (#8018) (Gracias, @SeeminglyScience)</span><span class="sxs-lookup"><span data-stu-id="d5a33-160">Fix static method invocation type inference (#8018) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="d5a33-161">Se han creado tipos deducidos para `Select-Object`, `Group-Object`, **PSObject** y **Hashtable** (#7231) (Gracias, @powercode)</span><span class="sxs-lookup"><span data-stu-id="d5a33-161">Create inferred types for `Select-Object`, `Group-Object`, **PSObject** and **Hashtable** (#7231) (Thanks @powercode!)</span></span>
- <span data-ttu-id="d5a33-162">Se ha añadido compatibilidad para el método de llamada con parámetros de tipo `ByRef-like` (#7721)</span><span class="sxs-lookup"><span data-stu-id="d5a33-162">Support calling method with `ByRef-like` type parameters (#7721)</span></span>
- <span data-ttu-id="d5a33-163">Se ha controlado el caso en que la ruta de acceso del módulo de Windows PowerShell ya está en el PSModulePath del entorno (#7727)</span><span class="sxs-lookup"><span data-stu-id="d5a33-163">Handle the case where the Windows PowerShell module path is already in the environment's PSModulePath (#7727)</span></span>
- <span data-ttu-id="d5a33-164">Se han habilitado los cmdlets `SecureString` para entornos que no son de Windows mediante el almacenamiento del texto sin formato (#9199)</span><span class="sxs-lookup"><span data-stu-id="d5a33-164">Enable `SecureString` cmdlets for non-Windows by storing the plain text (#9199)</span></span>
- <span data-ttu-id="d5a33-165">Se ha mejorado el mensaje de error en sistemas que no son Windows al importar clixml con SecureString (#7997)</span><span class="sxs-lookup"><span data-stu-id="d5a33-165">Improve error message on non-Windows when importing clixml with securestring (#7997)</span></span>
- <span data-ttu-id="d5a33-166">Se ha agregado el parámetro ReplyTo a `Send-MailMessage` (#8727) (Gracias, @replicaJunction)</span><span class="sxs-lookup"><span data-stu-id="d5a33-166">Adding parameter ReplyTo to `Send-MailMessage` (#8727) (Thanks @replicaJunction!)</span></span>
- <span data-ttu-id="d5a33-167">Se ha agregado el mensaje Obsolete a `Send-MailMessage` (#9178)</span><span class="sxs-lookup"><span data-stu-id="d5a33-167">Add Obsolete message to `Send-MailMessage` (#9178)</span></span>
- <span data-ttu-id="d5a33-168">Se ha corregido `Restart-Computer` para que funcione en `localhost` cuando WinRM no está presente (#9160)</span><span class="sxs-lookup"><span data-stu-id="d5a33-168">Fix `Restart-Computer` to work on `localhost` when WinRM is not present (#9160)</span></span>
- <span data-ttu-id="d5a33-169">Se ha generado error de terminación `Start-Job` cuando se hospeda PowerShell (#9128)</span><span class="sxs-lookup"><span data-stu-id="d5a33-169">Make `Start-Job` throw terminating error when PowerShell is being hosted (#9128)</span></span>
- <span data-ttu-id="d5a33-170">Se han agregado aceleradores y sufijos de tipo de estilo C# para los literales ushort, uint, ulong y short (# 7813) (Gracias, @vexx32)</span><span class="sxs-lookup"><span data-stu-id="d5a33-170">Add C# style type accelerators and suffixes for ushort, uint, ulong, and short literals (#7813) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="d5a33-171">Se han agregado nueva sufijos para literales numéricos - consulte [about_Numeric_Literals][] (Acerca de literales numéricos) (#7901) (Gracias, @vexx32)</span><span class="sxs-lookup"><span data-stu-id="d5a33-171">Added new suffixes for numeric literals - see [about_Numeric_Literals][] (#7901) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="d5a33-172">Se notifica el nivel de impacto correctamente cuando SupportsShouldProcess no está establecido en "true" (#8209) (Gracias, @vexx32)</span><span class="sxs-lookup"><span data-stu-id="d5a33-172">Correctly Report impact level when SupportsShouldProcess is not set to 'true' (#8209) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="d5a33-173">Se han solucionado los problemas del juego de caracteres de Request en los cmdlets web (#8742) (Gracias, @markekraus)</span><span class="sxs-lookup"><span data-stu-id="d5a33-173">Fix Request Charset Issues in Web Cmdlets (#8742) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="d5a33-174">Se ha solucionado el problema `100-continue` de Expect con los cmdlets web (#8679) (Gracias, @markekraus)</span><span class="sxs-lookup"><span data-stu-id="d5a33-174">Fix Expect `100-continue` issue with Web Cmdlets (#8679) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="d5a33-175">Se ha solucionado el problema de bloqueo de archivos con los cmdlets web (#7676) (Gracias, @Claustn)</span><span class="sxs-lookup"><span data-stu-id="d5a33-175">Fix file blocking issue with web cmdlets (#7676) (Thanks @Claustn!)</span></span>
- <span data-ttu-id="d5a33-176">Se ha corregido el problema de análisis de la página de códigos en `Invoke-RestMethod` (#8694) (Gracias, @markekraus)</span><span class="sxs-lookup"><span data-stu-id="d5a33-176">Fix code page parsing issue in `Invoke-RestMethod` (#8694) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="d5a33-177">Se ha refactorizado `ConvertTo-Json` para exponer JsonObject.ConvertToJson como una API pública (#8682)</span><span class="sxs-lookup"><span data-stu-id="d5a33-177">Refactor `ConvertTo-Json` to expose JsonObject.ConvertToJson as a public API (#8682)</span></span>
- <span data-ttu-id="d5a33-178">Se ha agregado la profundidad máxima configurable en `ConvertFrom-Json` con -Depth (#8199) (Gracias, @louistio)</span><span class="sxs-lookup"><span data-stu-id="d5a33-178">Add configurable maximum depth in `ConvertFrom-Json` with -Depth (#8199) (Thanks @louistio!)</span></span>
- <span data-ttu-id="d5a33-179">Se ha agregado el parámetro EscapeHandling en el cmdlet `ConvertTo-Json` (#7775) (Gracias, @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="d5a33-179">Add EscapeHandling parameter in `ConvertTo-Json` cmdlet (#7775) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d5a33-180">Se ha agregado `-CustomPipeName` a pwsh y `Enter-PSHostProcess` (#8889)</span><span class="sxs-lookup"><span data-stu-id="d5a33-180">Add `-CustomPipeName` to pwsh and `Enter-PSHostProcess` (#8889)</span></span>
- <span data-ttu-id="d5a33-181">Se ha habilitado la creación de vínculos simbólicos relativos en Windows con `New-Item` (#8783)</span><span class="sxs-lookup"><span data-stu-id="d5a33-181">Enable creating relative symbolic links on Windows with `New-Item` (#8783)</span></span>
- <span data-ttu-id="d5a33-182">Se permite a los usuarios de Windows en modo de desarrollador la creación de vínculos simbólicos sin elevación (#8534)</span><span class="sxs-lookup"><span data-stu-id="d5a33-182">Allow Windows users in developer mode to create symlinks without elevation (#8534)</span></span>
- <span data-ttu-id="d5a33-183">Se ha habilitado `Write-Information` para aceptar `$null` (#8774)</span><span class="sxs-lookup"><span data-stu-id="d5a33-183">Enable `Write-Information` to accept `$null` (#8774)</span></span>
- <span data-ttu-id="d5a33-184">Se ha corregido `Get-Help` para las funciones avanzadas con el contenido de ayuda de Azure MAML (#8353)</span><span class="sxs-lookup"><span data-stu-id="d5a33-184">Fix `Get-Help` for advanced functions with MAML help content (#8353)</span></span>
- <span data-ttu-id="d5a33-185">Se ha corregido el problema de PSTypeName `Get-Help` con -Parameter cuando se declara un solo parámetro (#8754) (Gracias, @pougetat)</span><span class="sxs-lookup"><span data-stu-id="d5a33-185">Fix `Get-Help` PSTypeName issue with -Parameter when only one parameter is declared (#8754) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="d5a33-186">Se ha corregido el cálculo de token para `Get-Help` ejecutando en ScriptBlock para la ayuda de comentarios.</span><span class="sxs-lookup"><span data-stu-id="d5a33-186">Token calculation fix for `Get-Help` executed on ScriptBlock for comment help.</span></span> <span data-ttu-id="d5a33-187">(#8238) (Gracias, @hubuk)</span><span class="sxs-lookup"><span data-stu-id="d5a33-187">(#8238) (Thanks @hubuk!)</span></span>
- <span data-ttu-id="d5a33-188">Se ha cambiado el parámetro -Parameter del cmdlet `Get-Help` para que acepte matrices de cadena (#8454) (Gracias, @sethvs)</span><span class="sxs-lookup"><span data-stu-id="d5a33-188">Change `Get-Help` cmdlet -Parameter parameter so it accepts string arrays (#8454) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="d5a33-189">Se ha resuelto PAGER si su ruta de acceso contiene espacios (#8571) (Gracias, @pougetat)</span><span class="sxs-lookup"><span data-stu-id="d5a33-189">Resolve PAGER if its path contains spaces (#8571) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="d5a33-190">Se ha agregado símbolo del sistema para el uso de `less` en la función "help" para indicar al usuario cómo cerrar (#7998)</span><span class="sxs-lookup"><span data-stu-id="d5a33-190">Add prompt to the use of `less` in the function 'help' to instruct user how to quit (#7998)</span></span>
- <span data-ttu-id="d5a33-191">Se ha agregado la compatibilidad con tipos enum y char en el cmdlet `Format-Hex` (#8191) (Gracias, @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="d5a33-191">Add support enum and char types in `Format-Hex` cmdlet (#8191) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d5a33-192">Se ha quitado ShouldProcess de `Format-Hex` (#8178)</span><span class="sxs-lookup"><span data-stu-id="d5a33-192">Remove ShouldProcess from `Format-Hex` (#8178)</span></span>
- <span data-ttu-id="d5a33-193">Se han agregado nuevos parámetros de Offset y Count a `Format-Hex` y se ha refactorizado el cmdlet (#7877) (Gracias, @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="d5a33-193">Add new Offset and Count parameters to `Format-Hex` and refactor the cmdlet (#7877) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d5a33-194">Se permite "name" como clave de alias para "label" en `ConvertTo-Html`, se permite que la entrada "width" sea un número entero (#8426) (Gracias, @mklement0)</span><span class="sxs-lookup"><span data-stu-id="d5a33-194">Allow 'name' as an alias key for 'label' in `ConvertTo-Html`, allow the 'width' entry to be an integer (#8426) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="d5a33-195">Se ha conseguido que las propiedades calculadas basadas en el scriptblock vuelvan a funcionar en `ConvertTo-Html` (#8427) (Gracias, @mklement0)</span><span class="sxs-lookup"><span data-stu-id="d5a33-195">Make scriptblock based calculated properties work again in `ConvertTo-Html` (#8427) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="d5a33-196">Se ha agregado un cmdlet `Join-String` para crear texto a partir de la canalización de entrada (#7660) (Gracias, @powercode)</span><span class="sxs-lookup"><span data-stu-id="d5a33-196">Add cmdlet `Join-String` for creating text from pipeline input (#7660) (Thanks @powercode!)</span></span>
- <span data-ttu-id="d5a33-197">Se ha corregido la lógica del parámetro FormatString del cmdlet `Join-String` (#8449) (Gracias, @sethvs)</span><span class="sxs-lookup"><span data-stu-id="d5a33-197">Fix `Join-String` cmdlet FormatString parameter logic (#8449) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="d5a33-198">Se ha vuelto a cambiar `Clear-Host` para que use `$RAWUI` y se ha desactivado para que funcione en la comunicación remota (#8609)</span><span class="sxs-lookup"><span data-stu-id="d5a33-198">Change `Clear-Host` back to using `$RAWUI` and clear to work over remoting (#8609)</span></span>
- <span data-ttu-id="d5a33-199">Se ha cambiado `Clear-Host` para que llame simplemente a `[console]::clear` y se ha quitado el alias de Unix (#8603)</span><span class="sxs-lookup"><span data-stu-id="d5a33-199">Change `Clear-Host` to simply called `[console]::clear` and remove clear alias from Unix (#8603)</span></span>
- <span data-ttu-id="d5a33-200">Se ha corregido LiteralPath en `Import-Csv` para que se enlace con la salida `Get-ChildItem` (#8277) (Gracias, @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="d5a33-200">Fix LiteralPath in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d5a33-201">La función de ayuda no debe usar el elemento de paginación para AliasHelpInfo (#8552)</span><span class="sxs-lookup"><span data-stu-id="d5a33-201">help function shouldn't use pager for AliasHelpInfo (#8552)</span></span>
- <span data-ttu-id="d5a33-202">Se ha agregado `-UseMinimalHeader` a `Start-Transcript` para minimizar el encabezado de transcripción (#8402) (Gracias, @lukexjeremy)</span><span class="sxs-lookup"><span data-stu-id="d5a33-202">Add `-UseMinimalHeader` to `Start-Transcript` to minimize transcript header (#8402) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="d5a33-203">Se han agregado los cmdlets `Enable-ExperimentalFeature` y `Disable-ExperimentalFeature` (#8318)</span><span class="sxs-lookup"><span data-stu-id="d5a33-203">Add `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature` cmdlets (#8318)</span></span>
- <span data-ttu-id="d5a33-204">Se han expuesto todos los cmdlets de **PSDiagnostics** si logman.exe está disponible (#8366)</span><span class="sxs-lookup"><span data-stu-id="d5a33-204">Expose all cmdlets from **PSDiagnostics** if logman.exe is available (#8366)</span></span>
- <span data-ttu-id="d5a33-205">Se ha quitado el parámetro **Persist** de `New-PSDrive` en la plataforma `non-Windows` (#8291) (Gracias, @lukexjeremy)</span><span class="sxs-lookup"><span data-stu-id="d5a33-205">Remove **Persist** parameter from `New-PSDrive` on `non-Windows` platform (#8291) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="d5a33-206">Se ha agregado compatibilidad para `cd +` (#7206) (Gracias, @bergmeister)</span><span class="sxs-lookup"><span data-stu-id="d5a33-206">Add support for `cd +` (#7206) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="d5a33-207">Se ha permitido que `Set-Location -LiteralPath` funcione con carpetas denominadas - y + (#8089)</span><span class="sxs-lookup"><span data-stu-id="d5a33-207">Enable `Set-Location -LiteralPath` to work with folders named - and + (#8089)</span></span>
- <span data-ttu-id="d5a33-208">`Test-Path` devuelve `$false` cuando se especifica un valor vacío o de ruta de acceso `$null` (#8080) (Gracias, @vexx32)</span><span class="sxs-lookup"><span data-stu-id="d5a33-208">`Test-Path` returns `$false` when given an empty or `$null` path value (#8080) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="d5a33-209">Se permite que un parámetro dinámico se devuelva incluso si la ruta de acceso no coincide con ningún proveedor (#7957)</span><span class="sxs-lookup"><span data-stu-id="d5a33-209">Allow dynamic parameter to be returned even if path does not match any provider (#7957)</span></span>
- <span data-ttu-id="d5a33-210">Se ha agregado compatibilidad con `Get-PSHostProcessInfo` y `Enter-PSHostProcess` en plataformas Unix (#8232)</span><span class="sxs-lookup"><span data-stu-id="d5a33-210">Support `Get-PSHostProcessInfo` and `Enter-PSHostProcess` on Unix platforms (#8232)</span></span>
- <span data-ttu-id="d5a33-211">Se han reducido las asignaciones en el cmdlet `Get-Content` (#8103) (Gracias, @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="d5a33-211">Reduce allocations in `Get-Content` cmdlet (#8103) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d5a33-212">Se ha habilitado `Add-Content` para compartir el acceso de lectura con otras herramientas al escribir contenido (#8091)</span><span class="sxs-lookup"><span data-stu-id="d5a33-212">Enable `Add-Content` to share read access with other tools while writing content (#8091)</span></span>
- <span data-ttu-id="d5a33-213">`Get/Add-Content` produce el error mejorado cuando el destino es un contenedor (#7823) (Gracias, @kvprasoon)</span><span class="sxs-lookup"><span data-stu-id="d5a33-213">`Get/Add-Content` throws improved error when targeting a container (#7823) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="d5a33-214">Agregue los parámetros `-Name`, `-NoUserOverrides` y `-ListAvailable` al cmdlet `Get-Culture` (#7702) (Gracias, @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="d5a33-214">Add `-Name`, `-NoUserOverrides` and `-ListAvailable` parameters to `Get-Culture` cmdlet (#7702) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d5a33-215">Se ha agregado un atributo unificado para la finalización del parámetro **Encoding**.</span><span class="sxs-lookup"><span data-stu-id="d5a33-215">Add unified attribute for completion for **Encoding** parameter.</span></span> <span data-ttu-id="d5a33-216">(#7732) (Gracias, @ThreeFive-O)</span><span class="sxs-lookup"><span data-stu-id="d5a33-216">(#7732) (Thanks @ThreeFive-O!)</span></span>
- <span data-ttu-id="d5a33-217">Se permiten identificadores numéricos y el nombre de páginas de códigos registradas en los parámetros **Encoding** (#7636) (Gracias, @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="d5a33-217">Allow numeric Ids and name of registered code pages in **Encoding** parameters (#7636) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d5a33-218">Se ha corregido `Rename-Item -Path` con el carácter comodín (#7398) (Gracias, @kwkam)</span><span class="sxs-lookup"><span data-stu-id="d5a33-218">Fix `Rename-Item -Path` with wildcard char (#7398) (Thanks @kwkam!)</span></span>
- <span data-ttu-id="d5a33-219">Cuando se usa `Start-Transcript` y el archivo existe, se vacía el archivo en lugar de eliminarlo (#8131) (Gracias, @paalbra)</span><span class="sxs-lookup"><span data-stu-id="d5a33-219">When using `Start-Transcript` and file exists, empty file rather than deleting (#8131) (Thanks @paalbra!)</span></span>
- <span data-ttu-id="d5a33-220">Los archivos de código fuente `Add-Type` se han hecho tales explícitamente con **FileAccess.Read** y **FileShare.Read** (#7915) (Gracias, @IISResetMe)</span><span class="sxs-lookup"><span data-stu-id="d5a33-220">Make `Add-Type` open source files with **FileAccess.Read** and **FileShare.Read** explicitly (#7915) (Thanks @IISResetMe!)</span></span>
- <span data-ttu-id="d5a33-221">Se ha corregido `Enter-PSSession -ContainerId` para el Windows más reciente (#7883)</span><span class="sxs-lookup"><span data-stu-id="d5a33-221">Fix `Enter-PSSession -ContainerId` for the latest Windows (#7883)</span></span>
- <span data-ttu-id="d5a33-222">Se ha asegurado que la propiedad **NestedModules** se rellene por `Test-ModuleManifest` (#7859)</span><span class="sxs-lookup"><span data-stu-id="d5a33-222">Ensure **NestedModules** property gets populated by `Test-ModuleManifest` (#7859)</span></span>
- <span data-ttu-id="d5a33-223">Se ha agregado el caso `%F` a `Get-Date` -UFormat (#7630) (Gracias, @britishben)</span><span class="sxs-lookup"><span data-stu-id="d5a33-223">Add `%F` case to `Get-Date` -UFormat (#7630) (Thanks @britishben!)</span></span>
- <span data-ttu-id="d5a33-224">Se ha corregido `Set-Service -Status Stopped` para que detenga los servicios con dependencias (#5525) (Gracias, @zhenggu)</span><span class="sxs-lookup"><span data-stu-id="d5a33-224">Fix `Set-Service -Status Stopped` to stop services with dependencies (#5525) (Thanks @zhenggu!)</span></span>

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals (Acerca de literales numéricos)
[Características experimentales]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
