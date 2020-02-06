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
# <a name="breaking-changes-for-powershell-6x"></a><span data-ttu-id="7f1fb-103">Cambios importantes en PowerShell Core 6.x</span><span class="sxs-lookup"><span data-stu-id="7f1fb-103">Breaking Changes for PowerShell 6.x</span></span>

## <a name="features-no-longer-available-in-powershell-core"></a><span data-ttu-id="7f1fb-104">Características que ya no están disponibles en PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="7f1fb-104">Features no longer available in PowerShell Core</span></span>

### <a name="modules-not-shipped-for-powershell-6x"></a><span data-ttu-id="7f1fb-105">Módulos no distribuidos para PowerShell 6.x</span><span class="sxs-lookup"><span data-stu-id="7f1fb-105">Modules not shipped for PowerShell 6.x</span></span>

<span data-ttu-id="7f1fb-106">Por diversas razones de compatibilidad, los siguientes módulos no se incluyen en PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-106">For various compatibility reasons, the following modules are not included in PowerShell 6.</span></span>

- <span data-ttu-id="7f1fb-107">ISE</span><span class="sxs-lookup"><span data-stu-id="7f1fb-107">ISE</span></span>
- <span data-ttu-id="7f1fb-108">Microsoft.PowerShell.LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="7f1fb-108">Microsoft.PowerShell.LocalAccounts</span></span>
- <span data-ttu-id="7f1fb-109">Microsoft.PowerShell.ODataUtils</span><span class="sxs-lookup"><span data-stu-id="7f1fb-109">Microsoft.PowerShell.ODataUtils</span></span>
- <span data-ttu-id="7f1fb-110">Microsoft.PowerShell.Operation.Validation</span><span class="sxs-lookup"><span data-stu-id="7f1fb-110">Microsoft.PowerShell.Operation.Validation</span></span>
- <span data-ttu-id="7f1fb-111">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="7f1fb-111">PSScheduledJob</span></span>
- <span data-ttu-id="7f1fb-112">PSWorkflow</span><span class="sxs-lookup"><span data-stu-id="7f1fb-112">PSWorkflow</span></span>
- <span data-ttu-id="7f1fb-113">PSWorkflowUtility</span><span class="sxs-lookup"><span data-stu-id="7f1fb-113">PSWorkflowUtility</span></span>

### <a name="powershell-workflow"></a><span data-ttu-id="7f1fb-114">Flujo de trabajo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f1fb-114">PowerShell Workflow</span></span>

<span data-ttu-id="7f1fb-115">El [flujo de trabajo de PowerShell][workflow] es una característica de Windows PowerShell basada en [Windows Workflow Foundation (WF)][workflow-foundation] que permite la creación de runbooks sólidos para tareas de larga ejecución o paralelizadas.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-115">[PowerShell Workflow][workflow] is a feature in Windows PowerShell that builds on top of [Windows Workflow Foundation (WF)][workflow-foundation] that enables the creation of robust runbooks for long-running or parallelized tasks.</span></span>

<span data-ttu-id="7f1fb-116">Debido a la falta de compatibilidad con Windows Workflow Foundation en .NET Core, no seguiremos admitiendo el flujo de trabajo de PowerShell en PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-116">Due to the lack of support for Windows Workflow Foundation in .NET Core, we are not supporting PowerShell Workflow in PowerShell Core.</span></span>

<span data-ttu-id="7f1fb-117">En el futuro, nos gustaría habilitar paralelismo nativo/simultaneidad en el lenguaje de PowerShell sin la necesidad del flujo de trabajo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-117">In the future, we would like to enable native parallelism/concurrency in the PowerShell language without the need for PowerShell Workflow.</span></span>

<span data-ttu-id="7f1fb-118">Si es necesario usar puntos de control para reanudar un script una vez reiniciado el sistema operativo, recomendamos usar Programador de tareas para ejecutar un script al iniciarse el sistema operativo, pero el script debería mantener su propio estado (como conservarlo en un archivo).</span><span class="sxs-lookup"><span data-stu-id="7f1fb-118">If there is a need to use checkpoints to resume a script after the OS restarts, we recommend using Task Scheduler to run a script on OS startup, but the script would need to maintain its own state (like persisting it to a file).</span></span>

[workflow]: /powershell/scripting/components/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a><span data-ttu-id="7f1fb-119">Complementos personalizados</span><span class="sxs-lookup"><span data-stu-id="7f1fb-119">Custom snap-ins</span></span>

<span data-ttu-id="7f1fb-120">Los [complementos de PowerShell][snapin] son un predecesor de los módulos de PowerShell cuya adopción en la comunidad de PowerShell no está generalizada.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-120">[PowerShell snap-ins][snapin] are a predecessor to PowerShell modules that do not have widespread adoption in the PowerShell community.</span></span>

<span data-ttu-id="7f1fb-121">Dada la complejidad de admitir complementos y su falta de uso en la comunidad, ya no admitimos complementos personalizados en PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-121">Due to the complexity of supporting snap-ins and their lack of usage in the community, we no longer support custom snap-ins in PowerShell Core.</span></span>

<span data-ttu-id="7f1fb-122">Actualmente, esto rompe los módulos `ActiveDirectory` y `DnsClient` en Windows y Windows Server.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-122">Today, this breaks the `ActiveDirectory` and `DnsClient` modules in Windows and Windows Server.</span></span>

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a><span data-ttu-id="7f1fb-123">Cmdlets WMI v1</span><span class="sxs-lookup"><span data-stu-id="7f1fb-123">WMI v1 cmdlets</span></span>

<span data-ttu-id="7f1fb-124">Dada la complejidad de admitir dos conjuntos de módulos basados en WMI, quitamos los cmdlets WMI v1 de PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="7f1fb-124">Due to the complexity of supporting two sets of WMI-based modules, we removed the WMI v1 cmdlets from PowerShell Core:</span></span>

- `Register-WmiEvent`
- `Set-WmiInstance`
- `Invoke-WmiMethod`
- `Get-WmiObject`
- `Remove-WmiObject`

<span data-ttu-id="7f1fb-125">En su lugar, recomendamos que use los cmdlets de CIM (también conocido como WMI v2), que proporcionan la misma funcionalidad con una nueva funcionalidad y una sintaxis rediseñada:</span><span class="sxs-lookup"><span data-stu-id="7f1fb-125">Instead, we recommend that you the use the CIM (aka WMI v2) cmdlets which provide the same functionality with new functionality and a redesigned syntax:</span></span>

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

### <a name="microsoftpowershelllocalaccounts"></a><span data-ttu-id="7f1fb-126">Microsoft.PowerShell.LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="7f1fb-126">Microsoft.PowerShell.LocalAccounts</span></span>

<span data-ttu-id="7f1fb-127">Debido al uso de API no admitidas, `Microsoft.PowerShell.LocalAccounts` se ha quitado de PowerShell Core hasta que se encuentre una solución mejor.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-127">Due to the use of unsupported APIs, `Microsoft.PowerShell.LocalAccounts` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="new-webserviceproxy-cmdlet-removed"></a><span data-ttu-id="7f1fb-128">Cmdlet `New-WebServiceProxy` quitado</span><span class="sxs-lookup"><span data-stu-id="7f1fb-128">`New-WebServiceProxy` cmdlet removed</span></span>

<span data-ttu-id="7f1fb-129">.NET Core no es compatible con Windows Communication Framework, que proporciona servicios para usar el protocolo SOAP.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-129">.NET Core does not support the Windows Communication Framework, which provide services for using the SOAP protocol.</span></span> <span data-ttu-id="7f1fb-130">Este cmdlet se quitó porque requiere SOAP.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-130">This cmdlet was removed because it requires SOAP.</span></span>

### <a name="-transaction-cmdlets-removed"></a><span data-ttu-id="7f1fb-131">`*-Transaction` cmdlets quitados</span><span class="sxs-lookup"><span data-stu-id="7f1fb-131">`*-Transaction` cmdlets removed</span></span>

<span data-ttu-id="7f1fb-132">Estos cmdlets tenían un uso muy limitado.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-132">These cmdlets had very limited usage.</span></span> <span data-ttu-id="7f1fb-133">Se tomó la decisión de dejar de admitirlos.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-133">The decision was made to discontinue support for them.</span></span>

- `Complete-Transaction`
- `Get-Transaction`
- `Start-Transaction`
- `Undo-Transaction`
- `Use-Transaction`

### <a name="security-cmdlets-not-available-on-non-windows-platforms"></a><span data-ttu-id="7f1fb-134">Cmdlets de seguridad no disponibles en plataformas que no son de Windows</span><span class="sxs-lookup"><span data-stu-id="7f1fb-134">Security cmdlets not available on non-Windows platforms</span></span>

- `Get-Acl`
- `Set-Acl`
- `Get-AuthenticodeSignature`
- `Set-AuthenticodeSignature`
- `Get-CmsMessage`
- `Protect-CmsMessage`
- `Unprotect-CmsMessage`
- `New-FileCatalog`
- `Test-FileCatalog`

### <a name="-computerand-other-windows-specific-cmdlets"></a><span data-ttu-id="7f1fb-135">`*-Computer`y otros cmdlets específicos de Windows</span><span class="sxs-lookup"><span data-stu-id="7f1fb-135">`*-Computer`and other Windows-specific cmdlets</span></span>

<span data-ttu-id="7f1fb-136">Debido al uso de API no admitidas, los cmdlets siguientes se han quitado de PowerShell Core hasta que se encuentre una solución mejor.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-136">Due to the use of unsupported APIs, the following cmdlets have been removed from PowerShell Core until a better solution is found.</span></span>

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

### <a name="-counter-cmdlets"></a><span data-ttu-id="7f1fb-137">Cmdlets de `*-Counter`</span><span class="sxs-lookup"><span data-stu-id="7f1fb-137">`*-Counter` cmdlets</span></span>

<span data-ttu-id="7f1fb-138">Debido al uso de API no admitidas, `*-Counter` se ha quitado de PowerShell Core hasta que se encuentre una solución mejor.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-138">Due to the use of unsupported APIs, the `*-Counter` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="-eventlog-cmdlets"></a><span data-ttu-id="7f1fb-139">Cmdlets de `*-EventLog`</span><span class="sxs-lookup"><span data-stu-id="7f1fb-139">`*-EventLog` cmdlets</span></span>

<span data-ttu-id="7f1fb-140">Debido al uso de API no admitidas, `*-EventLog` se ha quitado de PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-140">Due to the use of unsupported APIs, the `*-EventLog` has been removed from PowerShell Core.</span></span> <span data-ttu-id="7f1fb-141">hasta que se encuentra una solución mejor.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-141">until a better solution is found.</span></span> <span data-ttu-id="7f1fb-142">`Get-WinEvent` y `Create-WinEvent` están disponibles para obtener y crear eventos en Windows.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-142">`Get-WinEvent` and `Create-WinEvent` are available to get and create events on Windows.</span></span>

### <a name="cmdlets-that-use-wpf-removed"></a><span data-ttu-id="7f1fb-143">Cmdlets que usan WPF quitados</span><span class="sxs-lookup"><span data-stu-id="7f1fb-143">Cmdlets that use WPF removed</span></span>

<span data-ttu-id="7f1fb-144">Windows Presentation Framework no se admite en CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-144">The Windows Presentation Framework is not supported on CoreCLR.</span></span> <span data-ttu-id="7f1fb-145">Los siguientes cmdlets se ven afectados:</span><span class="sxs-lookup"><span data-stu-id="7f1fb-145">The following cmdlets are affected:</span></span>

- `Show-Command`
- `Out-GridView`
- <span data-ttu-id="7f1fb-146">Parámetro **showwindow** de `Get-Help`</span><span class="sxs-lookup"><span data-stu-id="7f1fb-146">The **showwindow** parameter of `Get-Help`</span></span>

### <a name="some-dsc-cmdlets-removed"></a><span data-ttu-id="7f1fb-147">Algunos cmdlets de DSC quitados</span><span class="sxs-lookup"><span data-stu-id="7f1fb-147">Some DSC cmdlets removed</span></span>

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

## <a name="enginelanguage-changes"></a><span data-ttu-id="7f1fb-148">Cambios en el lenguaje/motor</span><span class="sxs-lookup"><span data-stu-id="7f1fb-148">Engine/language changes</span></span>

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a><span data-ttu-id="7f1fb-149">Cambio del nombre de `powershell.exe` a `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-149">Rename `powershell.exe` to `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span></span>

<span data-ttu-id="7f1fb-150">Para ofrecer a los usuarios una forma determinista de llamar a PowerShell Core en Windows (frente a Windows PowerShell), el archivo binario de PowerShell Core se cambió a `pwsh.exe` en Windows y `pwsh` en plataformas que no son de Windows.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-150">In order to give users a deterministic way to call PowerShell Core on Windows (as opposed to Windows PowerShell), the PowerShell Core binary was changed to `pwsh.exe` on Windows and `pwsh` on non-Windows platforms.</span></span>

<span data-ttu-id="7f1fb-151">El nombre abreviado también es coherente con la nomenclatura de los shells en las plataformas que no son de Windows.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-151">The shortened name is also consistent with naming of shells on non-Windows platforms.</span></span>

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a><span data-ttu-id="7f1fb-152">No insertar saltos de línea en la salida (salvo para las tablas) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-152">Don't insert line breaks to output (except for tables) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span></span>

<span data-ttu-id="7f1fb-153">Anteriormente, la salida se alineaba con el ancho de la consola y los saltos de línea se agregaban en el ancho final de la consola, lo que significaba que la salida no se volvía a formatear como se esperaba si se cambiaba el tamaño del terminal.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-153">Previously, output was aligned to the width of the console and line breaks were added at the end width of the console, meaning the output didn't get reformatted as expected if the terminal was resized.</span></span> <span data-ttu-id="7f1fb-154">Este cambio no se aplicaba a las tablas, ya que los saltos de línea eran necesarios para mantener las columnas alineadas.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-154">This change was not applied to tables, as the line breaks are necessary to keep the columns aligned.</span></span>

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a><span data-ttu-id="7f1fb-155">Omitir la comprobación del elemento NULL de las colecciones con un tipo de elemento de tipo de valor [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-155">Skip null-element check for collections with a value-type element type [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span></span>

<span data-ttu-id="7f1fb-156">En el parámetro `Mandatory` y los atributos `ValidateNotNull` y `ValidateNotNullOrEmpty`, omita la comprobación del elemento NULL si el tipo de elemento de la colección es tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-156">For the `Mandatory` parameter and `ValidateNotNull` and `ValidateNotNullOrEmpty` attributes, skip the null-element check if the collection's element type is value type.</span></span>

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a><span data-ttu-id="7f1fb-157">Cambiar `$OutputEncoding` para usar la codificación `UTF-8 NoBOM` en lugar de ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-157">Change `$OutputEncoding` to use `UTF-8 NoBOM` encoding rather than ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span></span>

<span data-ttu-id="7f1fb-158">La codificación anterior, ASCII (7 bits), daría lugar a una alteración incorrecta de la salida en algunos casos.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-158">The previous encoding, ASCII (7-bit), would result in incorrect alteration of the output in some cases.</span></span> <span data-ttu-id="7f1fb-159">Este cambio consiste en convertir `UTF-8 NoBOM` en valor predeterminado, que conserva la salida de Unicode con una codificación admitida por la mayoría de las herramientas y sistemas operativos.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-159">This change is to make `UTF-8 NoBOM` default, which preserves Unicode output with an encoding supported by most tools and operating systems.</span></span>

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a><span data-ttu-id="7f1fb-160">Quitar `AllScope` de la mayoría de los alias predeterminados [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-160">Remove `AllScope` from most default aliases [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span></span>

<span data-ttu-id="7f1fb-161">Para acelerar la creación de ámbito, `AllScope` se quitó de la mayoría de los alias predeterminados.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-161">To speed up scope creation, `AllScope` was removed from most default aliases.</span></span> <span data-ttu-id="7f1fb-162">`AllScope` se dejó para un alias no usado con frecuencia donde la búsqueda era más rápida.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-162">`AllScope` was left for a few frequently used aliases where the lookup was faster.</span></span>

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a><span data-ttu-id="7f1fb-163">`-Verbose` y `-Debug` ya no invalidan `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-163">`-Verbose` and `-Debug` no longer overrides `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span></span>

<span data-ttu-id="7f1fb-164">Anteriormente, si se especificaban `-Verbose` o `-Debug`, invalidaba el comportamiento de `$ErrorActionPreference`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-164">Previously, if `-Verbose` or `-Debug` were specified, it overrode the behavior of `$ErrorActionPreference`.</span></span> <span data-ttu-id="7f1fb-165">Con este cambio, `-Verbose` y `-Debug` ya no influyen en el comportamiento de `$ErrorActionPreference`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-165">With this change, `-Verbose` and `-Debug` no longer affect the behavior of `$ErrorActionPreference`.</span></span>

## <a name="cmdlet-changes"></a><span data-ttu-id="7f1fb-166">Cambios en el cmdlet</span><span class="sxs-lookup"><span data-stu-id="7f1fb-166">Cmdlet changes</span></span>

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a><span data-ttu-id="7f1fb-167">Invoke-RestMethod no devuelve información útil cuando no se devuelven datos.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-167">Invoke-RestMethod doesn't return useful info when no data is returned.</span></span> [<span data-ttu-id="7f1fb-168">#5320</span><span class="sxs-lookup"><span data-stu-id="7f1fb-168">#5320</span></span>](https://github.com/PowerShell/PowerShell/issues/5320)

<span data-ttu-id="7f1fb-169">Cuando una API devuelve solo `null`, Invoke-RestMethod lo serializaba como la cadena `"null"` en lugar de `$null`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-169">When an API returns just `null`, Invoke-RestMethod was serializing this as the string `"null"` instead of `$null`.</span></span> <span data-ttu-id="7f1fb-170">Este cambio corrige la lógica en `Invoke-RestMethod` para serializar correctamente un valor único válido JSON `null` literal como `$null`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-170">This change fixes the logic in `Invoke-RestMethod` to properly serialize a valid single value JSON `null` literal as `$null`.</span></span>

### <a name="remove--protocol-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a><span data-ttu-id="7f1fb-171">Quitar `-Protocol` de los cmdlets `*-Computer`[#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-171">Remove `-Protocol` from `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span></span>

<span data-ttu-id="7f1fb-172">Debido a problemas con la comunicación remota RPC en CoreFX (especialmente en plataformas que no son de Windows) y la garantía de una experiencia de comunicación remota coherente en PowerShell, el parámetro `-Protocol` se quitó de los cmdlets `\*-Computer`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-172">Due to issues with RPC remoting in CoreFX (particularly on non-Windows platforms) and ensuring a consistent remoting experience in PowerShell, the `-Protocol` parameter was removed from the `\*-Computer` cmdlets.</span></span> <span data-ttu-id="7f1fb-173">DCOM ya no se admite para la comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-173">DCOM is no longer supported for remoting.</span></span> <span data-ttu-id="7f1fb-174">Los cmdlets siguientes solo admiten la comunicación remota mediante WSMAN:</span><span class="sxs-lookup"><span data-stu-id="7f1fb-174">The following cmdlets only support WSMAN remoting:</span></span>

- <span data-ttu-id="7f1fb-175">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="7f1fb-175">Rename-Computer</span></span>
- <span data-ttu-id="7f1fb-176">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="7f1fb-176">Restart-Computer</span></span>
- <span data-ttu-id="7f1fb-177">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="7f1fb-177">Stop-Computer</span></span>

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a><span data-ttu-id="7f1fb-178">Quitar `-ComputerName` de los cmdlets `*-Service`[#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-178">Remove `-ComputerName` from `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span></span>

<span data-ttu-id="7f1fb-179">Para fomentar el uso coherente de PSRP, el parámetro `-ComputerName` se quitó de los cmdlets `*-Service`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-179">In order to encourage the consistent use of PSRP, the `-ComputerName` parameter was removed from `*-Service` cmdlets.</span></span>

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a><span data-ttu-id="7f1fb-180">Corregir `Get-Item -LiteralPath a*b` si `a*b` no existe realmente para devolver el error [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-180">Fix `Get-Item -LiteralPath a*b` if `a*b` doesn't actually exist to return error [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span></span>

<span data-ttu-id="7f1fb-181">Anteriormente, `-LiteralPath` al que se le daba un carácter comodín lo trataría de la misma forma que `-Path` y, si el carácter comodín no encontraba ningún archivo, existiría en modo silencioso.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-181">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="7f1fb-182">El comportamiento correcto debería ser que `-LiteralPath` fuera literal de modo que, de no existir el archivo, debería producir un error.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-182">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="7f1fb-183">El cambio consiste en tratar los caracteres comodín usados con `-Literal` como literales.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-183">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a><span data-ttu-id="7f1fb-184">`Import-Csv` debe aplicar `PSTypeNames` durante la importación cuando la información de tipo esté presente en el CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-184">`Import-Csv` should apply `PSTypeNames` upon import when type information is present in the CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span></span>

<span data-ttu-id="7f1fb-185">Anteriormente, los objetos exportados mediante el uso de `Export-CSV` con `TypeInformation` importado con `ConvertFrom-Csv` no retenían la información de tipo.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-185">Previously, objects exported using `Export-CSV` with `TypeInformation` imported with `ConvertFrom-Csv` were not retaining the type information.</span></span> <span data-ttu-id="7f1fb-186">Este cambio agrega la información de tipo al miembro `PSTypeNames` si está disponible desde el archivo CSV.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-186">This change adds the type information to `PSTypeNames` member if available from the CSV file.</span></span>

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a><span data-ttu-id="7f1fb-187">`-NoTypeInformation` debería ser valor predeterminado en `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-187">`-NoTypeInformation` should be default on `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span></span>

<span data-ttu-id="7f1fb-188">Este cambio se realizó para abordar los comentarios de los clientes sobre el comportamiento predeterminado de `Export-CSV` a fin de incluir la información de tipo.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-188">This change was made to address customer feedback on the default behavior of `Export-CSV` to include type information.</span></span>

<span data-ttu-id="7f1fb-189">Anteriormente, el cmdlet generaría un comentario como la primera línea que incluye el nombre de tipo del objeto.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-189">Previously, the cmdlet would output a comment as the first line containing the type name of the object.</span></span> <span data-ttu-id="7f1fb-190">El cambio consiste en suprimir esto de forma predeterminada, pues la mayoría de las herramientas no lo comprenden.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-190">The change is to suppress this by default as it's not understood by most tools.</span></span> <span data-ttu-id="7f1fb-191">Use `-IncludeTypeInformation` para retener el comportamiento anterior.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-191">Use `-IncludeTypeInformation` to retain the previous behavior.</span></span>

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a><span data-ttu-id="7f1fb-192">Los cmdlets web deben advertir cada vez que `-Credential` se envía a través de conexiones descifradas [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-192">Web Cmdlets should warn when `-Credential` is sent over unencrypted connections [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span></span>

<span data-ttu-id="7f1fb-193">Al usar HTTP, el contenido y las contraseñas se envían como texto no cifrado.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-193">When using HTTP, content including passwords are sent as clear-text.</span></span> <span data-ttu-id="7f1fb-194">Este cambio consiste en no permitir esto de forma predeterminada y devolver un error si las credenciales se pasan con inseguridad.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-194">This change is to not allow this by default and return an error if credentials are being passed in an insecure manner.</span></span> <span data-ttu-id="7f1fb-195">Los usuarios pueden omitir esto con el conmutador `-AllowUnencryptedAuthentication`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-195">Users can bypass this by using the `-AllowUnencryptedAuthentication` switch.</span></span>

## <a name="api-changes"></a><span data-ttu-id="7f1fb-196">Cambios de API</span><span class="sxs-lookup"><span data-stu-id="7f1fb-196">API changes</span></span>

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a><span data-ttu-id="7f1fb-197">Quitar la clase `AddTypeCommandBase`[#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-197">Remove `AddTypeCommandBase` class [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span></span>

<span data-ttu-id="7f1fb-198">La clase `AddTypeCommandBase` se quitó de `Add-Type` para mejorar el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-198">The `AddTypeCommandBase` class was removed from `Add-Type` to improve performance.</span></span> <span data-ttu-id="7f1fb-199">El cmdlet Add-Type es el único que usa esta clase, la cual no debe afectar a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-199">This class is only used by the Add-Type cmdlet and should not impact users.</span></span>

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a><span data-ttu-id="7f1fb-200">Unificar los cmdlets con el parámetro `-Encoding` para que sea de tipo `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-200">Unify cmdlets with parameter `-Encoding` to be of type `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span></span>

<span data-ttu-id="7f1fb-201">El valor `-Encoding``Byte` se ha quitado de los cmdlets del proveedor del sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-201">The `-Encoding` value `Byte` has been removed from the filesystem provider cmdlets.</span></span> <span data-ttu-id="7f1fb-202">Un nuevo parámetro, `-AsByteStream`, se usa ahora para especificar que un flujo de bytes se necesita como entrada o que la salida es un flujo de bytes.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-202">A new parameter, `-AsByteStream`, is now used to specify that a byte stream is required as input or that the output is a stream of bytes.</span></span>

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a><span data-ttu-id="7f1fb-203">Agregar un mensaje de error mejor para el parámetro vacío y nulo `-UFormat`[#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-203">Add better error message for empty and null `-UFormat` parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span></span>

<span data-ttu-id="7f1fb-204">Anteriormente, al pasar una cadena de formato vacía a `-UFormat`, aparecía un mensaje de error poco práctico.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-204">Previously, when passing an empty format string to `-UFormat`, an unhelpful error message would appear.</span></span> <span data-ttu-id="7f1fb-205">Se ha agregado un error más descriptivo.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-205">A more descriptive error has been added.</span></span>

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a><span data-ttu-id="7f1fb-206">Limpiar el código de consola [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-206">Clean up console code [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span></span>

<span data-ttu-id="7f1fb-207">Las siguientes características se quitaron al no admitirse en PowerShell Core y no se tienen planes de agregar compatibilidad puesto que existen por motivos de herencia: conmutador y código `-psconsolefile`, conmutador y código `-importsystemmodules` y código de cambio de fuente.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-207">The following features were removed as they are not supported in PowerShell Core, and there are no plans to add support as they exist for legacy reasons for Windows PowerShell: `-psconsolefile` switch and code, `-importsystemmodules` switch and code, and font changing code.</span></span>

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a><span data-ttu-id="7f1fb-208">Compatibilidad con `RunspaceConfiguration` quitada [#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-208">Removed `RunspaceConfiguration` support [#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span></span>

<span data-ttu-id="7f1fb-209">Anteriormente, al crear un espacio de ejecución de PowerShell mediante programación con la API, podía usar el elemento [`RunspaceConfiguration`][runspaceconfig] heredado o el más reciente [`InitialSessionState`][iss].</span><span class="sxs-lookup"><span data-stu-id="7f1fb-209">Previously, when creating a PowerShell runspace programmatically using the API you could use the legacy [`RunspaceConfiguration`][runspaceconfig] or the newer [`InitialSessionState`][iss].</span></span> <span data-ttu-id="7f1fb-210">Este cambio quitó la compatibilidad con `RunspaceConfiguration` y solo admite `InitialSessionState`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-210">This change removed support for `RunspaceConfiguration` and only supports `InitialSessionState`.</span></span>

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a><span data-ttu-id="7f1fb-211">`CommandInvocationIntrinsics.InvokeScript` enlaza argumentos a `$input` en lugar de `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-211">`CommandInvocationIntrinsics.InvokeScript` bind arguments to `$input` instead of `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span></span>

<span data-ttu-id="7f1fb-212">Una posición incorrecta de un parámetro dio como resultado que los argumentos se pasaran como entrada en lugar de como argumentos.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-212">An incorrect position of a parameter resulted in the args passed as input instead of as args.</span></span>

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a><span data-ttu-id="7f1fb-213">Quitar el conmutador `-showwindow` no admitido de `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-213">Remove unsupported `-showwindow` switch from `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span></span>

<span data-ttu-id="7f1fb-214">`-showwindow` confía en WPF, que no se admite en CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-214">`-showwindow` relies on WPF, which is not supported on CoreCLR.</span></span>

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a><span data-ttu-id="7f1fb-215">Permitir el uso de \* en la ruta de acceso del Registro para `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-215">Allow \* to be used in registry path for `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span></span>

<span data-ttu-id="7f1fb-216">Anteriormente, `-LiteralPath` al que se le daba un carácter comodín lo trataría de la misma forma que `-Path` y, si el carácter comodín no encontraba ningún archivo, existiría en modo silencioso.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-216">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="7f1fb-217">El comportamiento correcto debería ser que `-LiteralPath` fuera literal de modo que, de no existir el archivo, debería producir un error.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-217">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="7f1fb-218">El cambio consiste en tratar los caracteres comodín usados con `-Literal` como literales.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-218">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a><span data-ttu-id="7f1fb-219">Corregir la prueba con errores `Set-Service`[#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-219">Fix `Set-Service` failing test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span></span>

<span data-ttu-id="7f1fb-220">Anteriormente, si se usaba `New-Service -StartupType foo`, `foo` se omitía y el servicio se creaba con algún tipo de inicio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-220">Previously, if `New-Service -StartupType foo` was used, `foo` was ignored and the service was created with some default startup type.</span></span> <span data-ttu-id="7f1fb-221">Este cambio consiste en mostrar un error de forma explícita para un tipo de inicio no válido.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-221">This change is to explicitly throw an error for an invalid startup type.</span></span>

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a><span data-ttu-id="7f1fb-222">Cambio del nombre de `$IsOSX` a `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-222">Rename `$IsOSX` to `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span></span>

<span data-ttu-id="7f1fb-223">La nomenclatura en PowerShell debe ser coherente con la nuestra y ajustarse al uso de macOS de Apple en lugar de OSX.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-223">The naming in PowerShell should be consistent with our naming and conform to Apple's use of macOS instead of OSX.</span></span> <span data-ttu-id="7f1fb-224">Sin embargo, para legibilidad y coherencia, optamos por el uso de mayúsculas o minúsculas de Pascal.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-224">However, for readability and consistently we are staying with Pascal casing.</span></span>

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a><span data-ttu-id="7f1fb-225">Haga que el mensaje de error sea coherente cuando el script no válido se pase a -File; mejor error al superarse el argumento ambiguo [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-225">Make error message consistent when invalid script is passed to -File, better error when passed ambiguous argument [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span></span>

<span data-ttu-id="7f1fb-226">Cambie los códigos de salida de `pwsh.exe` para su alineación con las convenciones de Unix.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-226">Change the exit codes of `pwsh.exe` to align with Unix conventions</span></span>

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a><span data-ttu-id="7f1fb-227">Eliminación de `LocalAccount` y cmdlets de los módulos `Diagnostics`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-227">Removal of `LocalAccount` and cmdlets from  `Diagnostics` modules.</span></span> <span data-ttu-id="7f1fb-228">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-228">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span></span>

<span data-ttu-id="7f1fb-229">Debido a las API no admitidas, el módulo `LocalAccounts` y los cmdlets `Counter` del módulo `Diagnostics` se quitaron hasta que se encuentre una solución mejor.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-229">Due to unsupported APIs, the `LocalAccounts` module and the `Counter` cmdlets in the `Diagnostics` module were removed until a better solution is found.</span></span>

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a><span data-ttu-id="7f1fb-230">La ejecución de un script de PowerShell con un parámetro bool no funciona [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-230">Executing PowerShell script with bool parameter does not work [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span></span>

<span data-ttu-id="7f1fb-231">Anteriormente, el uso de **powershell.exe** (ahora **pwsh.exe**) para ejecutar un script de PowerShell con `-File` no proporcionaba ninguna forma de pasar `$true`/`$false` como valores del parámetro.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-231">Previously, using **powershell.exe** (now **pwsh.exe**) to execute a PowerShell script using `-File` provided no way to pass `$true`/`$false` as parameter values.</span></span> <span data-ttu-id="7f1fb-232">La compatibilidad con `$true`/`$false` como valores analizados de parámetros se agregó.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-232">Support for `$true`/`$false` as parsed values to parameters was added.</span></span> <span data-ttu-id="7f1fb-233">Los valores de conmutador también se admiten, ya que la sintaxis documentada actualmente no funciona.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-233">Switch values are also supported as currently documented syntax doesn't work.</span></span>

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a><span data-ttu-id="7f1fb-234">Quitar la propiedad `ClrVersion` de `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-234">Remove `ClrVersion` property from `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span></span>

<span data-ttu-id="7f1fb-235">La propiedad `ClrVersion` de `$PSVersionTable` no es útil con CoreCLR y los usuarios no deben usar ese valor para determinar la compatibilidad.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-235">The `ClrVersion` property of `$PSVersionTable` is not useful with CoreCLR, end users should not be using that value to determine compatibility.</span></span>

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a><span data-ttu-id="7f1fb-236">Cambiar parámetro posicional para `powershell.exe` de `-Command` a `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-236">Change positional parameter for `powershell.exe` from `-Command` to `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span></span>

<span data-ttu-id="7f1fb-237">Permita el uso del par de caracteres shebang de PowerShell en plataformas que no son de Windows.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-237">Enable shebang use of PowerShell on non-Windows platforms.</span></span> <span data-ttu-id="7f1fb-238">Esto significa que, en los sistemas basados en Unix, puede hacer que un script pueda ejecutarse, lo que invocaría PowerShell automáticamente en lugar de invocar `pwsh` de forma explícita.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-238">This means on Unix based systems, you can make a script executable that would invoke PowerShell automatically rather than explicitly invoking `pwsh`.</span></span> <span data-ttu-id="7f1fb-239">También significa que ahora puede hacer cosas como `powershell foo.ps1` o `powershell fooScript` sin especificar `-File`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-239">This also means that you can now do things like `powershell foo.ps1` or `powershell fooScript` without specifying `-File`.</span></span> <span data-ttu-id="7f1fb-240">Aun así, este cambio requiere ahora que se especifique explícitamente `-c` o `-Command` al intentar hacer cosas como `powershell.exe Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-240">However, this change now requires that you explicitly specify `-c` or `-Command` when trying to do things like `powershell.exe Get-Command`.</span></span>

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a><span data-ttu-id="7f1fb-241">Implementar análisis de escape Unicode [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-241">Implement Unicode escape parsing [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span></span>

<span data-ttu-id="7f1fb-242">`` `u####`` o `` `u{####}`` se convierte en el carácter Unicode correspondiente.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-242">`` `u####`` or `` `u{####}`` is converted to the corresponding Unicode character.</span></span> <span data-ttu-id="7f1fb-243">Para generar un elemento `` `u`` literal, evite la tilde aguda: ``` ``u```.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-243">To output a literal `` `u``, escape the backtick: ``` ``u```.</span></span>

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a><span data-ttu-id="7f1fb-244">Cambie la codificación `New-ModuleManifest` a `UTF8NoBOM` en plataformas que no son de Windows [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-244">Change `New-ModuleManifest` encoding to `UTF8NoBOM` on non-Windows platforms [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span></span>

<span data-ttu-id="7f1fb-245">Anteriormente, `New-ModuleManifest` creaba manifiestos psd1 en UTF-16 con BOM, dando lugar a un problema para las herramientas de Linux.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-245">Previously, `New-ModuleManifest` creates psd1 manifests in UTF-16 with BOM, creating a problem for Linux tools.</span></span> <span data-ttu-id="7f1fb-246">Este cambio importante cambia la codificación de `New-ModuleManifest` para que sea UTF (sin BOM) en plataformas que no son de Windows.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-246">This breaking change changes the encoding of `New-ModuleManifest` to be UTF (no BOM) in non-Windows platforms.</span></span>

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a><span data-ttu-id="7f1fb-247">Evite que `Get-ChildItem` recurra a symlinks (#1875).</span><span class="sxs-lookup"><span data-stu-id="7f1fb-247">Prevent `Get-ChildItem` from recursing into symlinks (#1875).</span></span> [<span data-ttu-id="7f1fb-248">#3780</span><span class="sxs-lookup"><span data-stu-id="7f1fb-248">#3780</span></span>](https://github.com/PowerShell/PowerShell/issues/3780)

<span data-ttu-id="7f1fb-249">Este cambio trae `Get-ChildItem`, más acorde con los comandos nativos `ls -r` de Unix y `dir /s` de Windows.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-249">This change brings `Get-ChildItem` more in line with the Unix `ls -r` and the Windows `dir /s` native commands.</span></span> <span data-ttu-id="7f1fb-250">Al igual que los comandos mencionados, el cmdlet muestra vínculos simbólicos a directorios encontrados durante la recursión, pero no recurre a ellos.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-250">Like the mentioned commands, the cmdlet displays symbolic links to directories found during recursion, but does not recurse into them.</span></span>

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a><span data-ttu-id="7f1fb-251">Corregir `Get-Content -Delimiter` para no incluir el delimitador en las líneas devueltas [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-251">Fix `Get-Content -Delimiter` to not include the delimiter in the returned lines [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span></span>

<span data-ttu-id="7f1fb-252">Anteriormente, la salida mientras se usaba `Get-Content -Delimiter` era incoherente e incómoda, ya que requería un mayor procesamiento de los datos para quitar el delimitador.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-252">Previously, the output while using `Get-Content -Delimiter` was inconsistent and inconvenient as it required further processing of the data to remove the delimiter.</span></span> <span data-ttu-id="7f1fb-253">Este cambio quita el delimitador en líneas devueltas.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-253">This change removes the delimiter in returned lines.</span></span>

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a><span data-ttu-id="7f1fb-254">Implementar Format-Hex en C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-254">Implement Format-Hex in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span></span>

<span data-ttu-id="7f1fb-255">El parámetro `-Raw` ahora es un "no-op" (ahí no hace nada).</span><span class="sxs-lookup"><span data-stu-id="7f1fb-255">The `-Raw` parameter is now a "no-op" (in that it does nothing).</span></span> <span data-ttu-id="7f1fb-256">En adelante, toda la salida se mostrará con una auténtica representación de números que incluye todos los bytes de su tipo (lo que el parámetro `-Raw` hacía formalmente antes de este cambio).</span><span class="sxs-lookup"><span data-stu-id="7f1fb-256">Going forward all of the output will be displayed with a true representation of numbers that includes all of the bytes for its type (what the `-Raw` parameter was formally doing prior to this change).</span></span>

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a><span data-ttu-id="7f1fb-257">PowerShell como shell predeterminado no funciona con un comando de script [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-257">PowerShell as a default shell doesn't work with script command [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span></span>

<span data-ttu-id="7f1fb-258">En Unix, es una convención para que los shells acepten `-i` para un shell interactivo y muchas herramientas esperan este comportamiento (`script` por ejemplo y al establecer PowerShell como el shell predeterminado) y llama al shell con el conmutador `-i`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-258">On Unix, it is a convention for shells to accept `-i` for an interactive shell and many tools expect this behavior (`script` for example, and when setting PowerShell as the default shell) and calls the shell with the `-i` switch.</span></span> <span data-ttu-id="7f1fb-259">Este cambio es importante en que `-i` podía usarse anteriormente como fórmula sencilla para coincidir con `-inputformat`, que ahora debe ser `-in`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-259">This change is breaking in that `-i` previously could be used as short hand to match `-inputformat`, which now needs to be `-in`.</span></span>

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a><span data-ttu-id="7f1fb-260">Corregir error de escritura en el nombre de la propiedad Get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-260">Typo fix in Get-ComputerInfo property name [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span></span>

<span data-ttu-id="7f1fb-261">`BiosSerialNumber` se escribió incorrectamente como `BiosSeralNumber` y se ha cambiado a la ortografía correcta.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-261">`BiosSerialNumber` was misspelled as `BiosSeralNumber` and has been changed to the correct spelling.</span></span>

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a><span data-ttu-id="7f1fb-262">Agregar los cmdlets `Get-StringHash` y `Get-FileHash`[#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-262">Add `Get-StringHash` and `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span></span>

<span data-ttu-id="7f1fb-263">Este cambio consiste en que algunos algoritmos hash no son compatibles con CoreFX, por lo que ya no están disponibles:</span><span class="sxs-lookup"><span data-stu-id="7f1fb-263">This change is that some hash algorithms are not supported by CoreFX, therefore they are no longer available:</span></span>

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a><span data-ttu-id="7f1fb-264">Agregar validación en los cmdlets `Get-*` donde al pasar $null se devuelven todos los objetos en lugar del error [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-264">Add validation on `Get-*` cmdlets where passing $null returns all objects instead of error [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span></span>

<span data-ttu-id="7f1fb-265">Ahora, al pasar `$null` a cualquiera de los siguientes elementos, se muestra un error:</span><span class="sxs-lookup"><span data-stu-id="7f1fb-265">Passing `$null` to any of the following now throws an error:</span></span>

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

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a><span data-ttu-id="7f1fb-266">Agregar compatibilidad con formato de archivo de registro extendido W3C en `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-266">Add support W3C Extended Log File Format in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span></span>

<span data-ttu-id="7f1fb-267">Anteriormente, el cmdlet `Import-Csv` no se podía usar directamente para importar los archivos de registro en el formato de registro extendido W3C y se requerían medidas adicionales.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-267">Previously, the `Import-Csv` cmdlet cannot be used to directly import the log files in W3C extended log format and additional action would be required.</span></span> <span data-ttu-id="7f1fb-268">Con este cambio, el formato de registro extendido W3C se admite.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-268">With this change, W3C extended log format is supported.</span></span>

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a><span data-ttu-id="7f1fb-269">Problema de enlace de parámetros con `ValueFromRemainingArguments` en funciones de PS [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-269">Parameter binding problem with `ValueFromRemainingArguments` in PS functions [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span></span>

<span data-ttu-id="7f1fb-270">`ValueFromRemainingArguments` ahora devuelve los valores como una matriz en lugar de un solo valor que en sí mismo es una matriz.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-270">`ValueFromRemainingArguments` now returns the values as an array instead of a single value which itself is an array.</span></span>

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a><span data-ttu-id="7f1fb-271">`BuildVersion` se quita de `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span><span class="sxs-lookup"><span data-stu-id="7f1fb-271">`BuildVersion` is removed from `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span></span>

<span data-ttu-id="7f1fb-272">Quite la propiedad `BuildVersion` de `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-272">Remove the `BuildVersion` property from `$PSVersionTable`.</span></span> <span data-ttu-id="7f1fb-273">Esta propiedad estaba ligada a la versión de compilación de Windows.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-273">This property was tied to the Windows build version.</span></span> <span data-ttu-id="7f1fb-274">En su lugar, se recomienda usar `GitCommitId` para recuperar la versión de compilación exacta de PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-274">Instead, we recommend that you use `GitCommitId` to retrieve the exact build version of PowerShell Core.</span></span>

### <a name="changes-to-web-cmdlets"></a><span data-ttu-id="7f1fb-275">Cambios en los cmdlets web</span><span class="sxs-lookup"><span data-stu-id="7f1fb-275">Changes to Web Cmdlets</span></span>

<span data-ttu-id="7f1fb-276">La API de .NET subyacente de los cmdlets web se ha cambiado a `System.Net.Http.HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-276">The underlying .NET API of the Web Cmdlets has been changed to `System.Net.Http.HttpClient`.</span></span> <span data-ttu-id="7f1fb-277">Este cambio ofrece muchas ventajas.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-277">This change provides many benefits.</span></span> <span data-ttu-id="7f1fb-278">Sin embargo, este cambio y una falta de interoperabilidad con Internet Explorer han dado lugar a varios cambios importantes en `Invoke-WebRequest` y `Invoke-RestMethod`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-278">However, this change along with a lack of interoperability with Internet Explorer have resulted in several breaking changes within `Invoke-WebRequest` and `Invoke-RestMethod`.</span></span>

- <span data-ttu-id="7f1fb-279">`Invoke-WebRequest` ahora solo admite un análisis básico de HTML.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-279">`Invoke-WebRequest` now supports basic HTML Parsing only.</span></span> <span data-ttu-id="7f1fb-280">`Invoke-WebRequest` siempre devuelve un objeto `BasicHtmlWebResponseObject`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-280">`Invoke-WebRequest` always returns a `BasicHtmlWebResponseObject` object.</span></span> <span data-ttu-id="7f1fb-281">Las propiedades `ParsedHtml` y `Forms` se han quitado.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-281">The `ParsedHtml` and `Forms` properties have been removed.</span></span>
- <span data-ttu-id="7f1fb-282">Los valores `BasicHtmlWebResponseObject.Headers` ahora son `String[]` en lugar de `String`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-282">`BasicHtmlWebResponseObject.Headers` values are now `String[]` instead of `String`.</span></span>
- <span data-ttu-id="7f1fb-283">`BasicHtmlWebResponseObject.BaseResponse` ahora es un objeto `System.Net.Http.HttpResponseMessage`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-283">`BasicHtmlWebResponseObject.BaseResponse` is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="7f1fb-284">La propiedad `Response` de excepciones de cmdlets web ahora es un objeto `System.Net.Http.HttpResponseMessage`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-284">The `Response` property on Web Cmdlet exceptions is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="7f1fb-285">El análisis estricto del encabezado RFC ahora es el valor predeterminado de los parámetros `-Headers` y `-UserAgent`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-285">Strict RFC header parsing is now default for the `-Headers` and `-UserAgent` parameter.</span></span> <span data-ttu-id="7f1fb-286">Esto se puede omitir con `-SkipHeaderValidation`.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-286">This can be bypassed with `-SkipHeaderValidation`.</span></span>
- <span data-ttu-id="7f1fb-287">Los esquemas de URI `file://` y `ftp://` ya no se admiten.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-287">`file://` and `ftp://` URI schemes are no longer supported.</span></span>
- <span data-ttu-id="7f1fb-288">La configuración `System.Net.ServicePointManager` ya no se admite.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-288">`System.Net.ServicePointManager` settings are no longer honored.</span></span>
- <span data-ttu-id="7f1fb-289">Actualmente no hay ninguna autenticación disponible en macOS basada en certificado.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-289">There is currently no certificate based authentication available on macOS.</span></span>
- <span data-ttu-id="7f1fb-290">El uso de `-Credential` sobre un URI `http://` dará lugar a un error.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-290">Use of `-Credential` over an `http://` URI will result in an error.</span></span> <span data-ttu-id="7f1fb-291">Use un URI `https://` o proporcione el parámetro `-AllowUnencryptedAuthentication` para suprimir el error.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-291">Use an `https://` URI or supply the `-AllowUnencryptedAuthentication` parameter to suppress the error.</span></span>
- <span data-ttu-id="7f1fb-292">`-MaximumRedirection` ahora genera un error de terminación cuando los intentos de redirección superan el límite proporcionado en lugar de devolver los resultados de la última redirección.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-292">`-MaximumRedirection` now produces a terminating error when redirection attempts exceed the provided limit instead of returning the results of the last redirection.</span></span>
- <span data-ttu-id="7f1fb-293">En PowerShell 6.2, se ha realizado un cambio para usar de forma predeterminada la codificación UTF-8 en las respuestas JSON.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-293">In PowerShell 6.2, a change was made to default to UTF-8 encoding for JSON responses.</span></span> <span data-ttu-id="7f1fb-294">Cuando no se proporciona un juego de caracteres para una respuesta JSON, la codificación predeterminada debe ser UTF-8 según la norma RFC 8259.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-294">When a charset is not supplied for a JSON response, the default encoding should be UTF-8 per RFC 8259.</span></span>
