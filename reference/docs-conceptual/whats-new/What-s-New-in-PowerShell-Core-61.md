---
title: Novedades de PowerShell Core 6.1
description: Nuevas características y cambios publicados en PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: 531259217f2b71213776e7d394616c7790e9aca9
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995514"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="34a63-103">Novedades de PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="34a63-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="34a63-104">Esta es una selección de algunas de las principales características nuevas y los cambios que se han incorporado en PowerShell Core 6.1.</span><span class="sxs-lookup"><span data-stu-id="34a63-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="34a63-105">También hay **toneladas** de "cosas aburridas" que hacen que PowerShell sea más rápido y más estable (además de montones y montones de correcciones de errores).</span><span class="sxs-lookup"><span data-stu-id="34a63-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span> <span data-ttu-id="34a63-106">Si quiere ver una lista completa de los cambios, eche un vistazo a nuestro [registro de cambios en GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="34a63-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="34a63-107">Y aunque destacamos algunos nombres al final, queremos dar las gracias a [todos los colaboradores de la comunidad](https://github.com/PowerShell/PowerShell/graphs/contributors) que han hecho posible esta versión.</span><span class="sxs-lookup"><span data-stu-id="34a63-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="34a63-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="34a63-108">.NET Core 2.1</span></span>

<span data-ttu-id="34a63-109">PowerShell Core 6.1 cambió a .NET Core 2.1 después de su [lanzamiento en mayo](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), lo que dio lugar a muchas mejoras en PowerShell, incluidas:</span><span class="sxs-lookup"><span data-stu-id="34a63-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="34a63-110">mejoras de rendimiento (ver más [abajo](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="34a63-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="34a63-111">compatibilidad con Alpine Linux (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="34a63-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="34a63-112">[compatibilidad con la herramienta global .NET](/dotnet/core/tools/global-tools) (próximamente en PowerShell)</span><span class="sxs-lookup"><span data-stu-id="34a63-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="34a63-113">paquete de compatibilidad de Windows para .NET Core</span><span class="sxs-lookup"><span data-stu-id="34a63-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="34a63-114">En Windows, el equipo de .NET incluyó [paquete de compatibilidad de Windows para .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), un conjunto de ensamblados que agregan varias API que se quitaron a .NET Core en Windows.</span><span class="sxs-lookup"><span data-stu-id="34a63-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="34a63-115">Hemos agregado el paquete de compatibilidad de Windows a la versión PowerShell Core 6.1 para que los módulos o scripts que usen estas API puedan tener la seguridad de que estarán disponibles.</span><span class="sxs-lookup"><span data-stu-id="34a63-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="34a63-116">El paquete de compatibilidad de Windows permite que PowerShell Core use **más de 1900 cmdlets que se incluyen con la actualización de Windows 10 de octubre de 2018 y Windows Server 2019**.</span><span class="sxs-lookup"><span data-stu-id="34a63-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-whitelisting"></a><span data-ttu-id="34a63-117">Compatibilidad con la lista blanca de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="34a63-117">Support for Application Whitelisting</span></span>

<span data-ttu-id="34a63-118">PowerShell Core 6.1 incluye paridad con Windows PowerShell 5.1 al ser compatible con la lista blanca de aplicaciones [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) y [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control).</span><span class="sxs-lookup"><span data-stu-id="34a63-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application whitelisting.</span></span> <span data-ttu-id="34a63-119">La creación de listas blancas de aplicaciones permite un control granular de qué archivos binarios se pueden ejecutar mediante el [modo de lenguaje restringido](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34a63-119">Application whitelisting allows granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="34a63-120">Mejoras en el rendimiento</span><span class="sxs-lookup"><span data-stu-id="34a63-120">Performance improvements</span></span>

<span data-ttu-id="34a63-121">En PowerShell Core 6.0 se realizaron algunas mejoras de rendimiento significativas.</span><span class="sxs-lookup"><span data-stu-id="34a63-121">PowerShell Core 6.0 made some significant performance improvements.</span></span> <span data-ttu-id="34a63-122">PowerShell Core 6.1 sigue mejorando la velocidad de determinadas operaciones.</span><span class="sxs-lookup"><span data-stu-id="34a63-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="34a63-123">Por ejemplo, `Group-Object` se ha agilizado en un 66 %:</span><span class="sxs-lookup"><span data-stu-id="34a63-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="34a63-124">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="34a63-124">Windows PowerShell 5.1</span></span> | <span data-ttu-id="34a63-125">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="34a63-125">PowerShell Core 6.0</span></span> | <span data-ttu-id="34a63-126">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="34a63-126">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="34a63-127">Tiempo (s)</span><span class="sxs-lookup"><span data-stu-id="34a63-127">Time (sec)</span></span>   | <span data-ttu-id="34a63-128">25,178</span><span class="sxs-lookup"><span data-stu-id="34a63-128">25.178</span></span>                 | <span data-ttu-id="34a63-129">19,653</span><span class="sxs-lookup"><span data-stu-id="34a63-129">19.653</span></span>              | <span data-ttu-id="34a63-130">6,641</span><span class="sxs-lookup"><span data-stu-id="34a63-130">6.641</span></span>               |
| <span data-ttu-id="34a63-131">Aceleración (%)</span><span class="sxs-lookup"><span data-stu-id="34a63-131">Speed-up (%)</span></span> | <span data-ttu-id="34a63-132">N/D</span><span class="sxs-lookup"><span data-stu-id="34a63-132">N/A</span></span>                    | <span data-ttu-id="34a63-133">21,9 %</span><span class="sxs-lookup"><span data-stu-id="34a63-133">21.9%</span></span>               | <span data-ttu-id="34a63-134">66,2 %</span><span class="sxs-lookup"><span data-stu-id="34a63-134">66.2%</span></span>               |

<span data-ttu-id="34a63-135">De forma similar, escenarios de ordenación como este han mejorado en más del 15 %:</span><span class="sxs-lookup"><span data-stu-id="34a63-135">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="34a63-136">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="34a63-136">Windows PowerShell 5.1</span></span> | <span data-ttu-id="34a63-137">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="34a63-137">PowerShell Core 6.0</span></span> | <span data-ttu-id="34a63-138">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="34a63-138">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="34a63-139">Tiempo (s)</span><span class="sxs-lookup"><span data-stu-id="34a63-139">Time (sec)</span></span>   | <span data-ttu-id="34a63-140">12,170</span><span class="sxs-lookup"><span data-stu-id="34a63-140">12.170</span></span>                 | <span data-ttu-id="34a63-141">8,493</span><span class="sxs-lookup"><span data-stu-id="34a63-141">8.493</span></span>               | <span data-ttu-id="34a63-142">7,08</span><span class="sxs-lookup"><span data-stu-id="34a63-142">7.08</span></span>                |
| <span data-ttu-id="34a63-143">Aceleración (%)</span><span class="sxs-lookup"><span data-stu-id="34a63-143">Speed-up (%)</span></span> | <span data-ttu-id="34a63-144">N/D</span><span class="sxs-lookup"><span data-stu-id="34a63-144">N/A</span></span>                    | <span data-ttu-id="34a63-145">30,2 %</span><span class="sxs-lookup"><span data-stu-id="34a63-145">30.2%</span></span>               | <span data-ttu-id="34a63-146">16,6 %</span><span class="sxs-lookup"><span data-stu-id="34a63-146">16.6%</span></span>               |

<span data-ttu-id="34a63-147">`Import-Csv` también se han agilizado mucho después de una regresión desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34a63-147">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="34a63-148">En este ejemplo se usa un CSV de prueba con 26 616 filas y 6 columnas:</span><span class="sxs-lookup"><span data-stu-id="34a63-148">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="34a63-149">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="34a63-149">Windows PowerShell 5.1</span></span> | <span data-ttu-id="34a63-150">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="34a63-150">PowerShell Core 6.0</span></span> | <span data-ttu-id="34a63-151">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="34a63-151">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="34a63-152">Tiempo (s)</span><span class="sxs-lookup"><span data-stu-id="34a63-152">Time (sec)</span></span>   | <span data-ttu-id="34a63-153">0,441</span><span class="sxs-lookup"><span data-stu-id="34a63-153">0.441</span></span>                  | <span data-ttu-id="34a63-154">1,069</span><span class="sxs-lookup"><span data-stu-id="34a63-154">1.069</span></span>               | <span data-ttu-id="34a63-155">0,268</span><span class="sxs-lookup"><span data-stu-id="34a63-155">0.268</span></span>                  |
| <span data-ttu-id="34a63-156">Aceleración (%)</span><span class="sxs-lookup"><span data-stu-id="34a63-156">Speed-up (%)</span></span> | <span data-ttu-id="34a63-157">N/D</span><span class="sxs-lookup"><span data-stu-id="34a63-157">N/A</span></span>                    | <span data-ttu-id="34a63-158">-142,4 %</span><span class="sxs-lookup"><span data-stu-id="34a63-158">-142.4%</span></span>             | <span data-ttu-id="34a63-159">74,9 % (39,2 % desde WPS)</span><span class="sxs-lookup"><span data-stu-id="34a63-159">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="34a63-160">Por último, la conversión de JSON en `PSObject` se ha agilizado en más del 50 % desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34a63-160">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="34a63-161">El ejemplo siguiente usa un archivo JSON de prueba de unos 2 MB:</span><span class="sxs-lookup"><span data-stu-id="34a63-161">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="34a63-162">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="34a63-162">Windows PowerShell 5.1</span></span> | <span data-ttu-id="34a63-163">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="34a63-163">PowerShell Core 6.0</span></span> | <span data-ttu-id="34a63-164">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="34a63-164">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="34a63-165">Tiempo (s)</span><span class="sxs-lookup"><span data-stu-id="34a63-165">Time (sec)</span></span>   | <span data-ttu-id="34a63-166">0,259</span><span class="sxs-lookup"><span data-stu-id="34a63-166">0.259</span></span>                  | <span data-ttu-id="34a63-167">0,577</span><span class="sxs-lookup"><span data-stu-id="34a63-167">0.577</span></span>               | <span data-ttu-id="34a63-168">0,125</span><span class="sxs-lookup"><span data-stu-id="34a63-168">0.125</span></span>                  |
| <span data-ttu-id="34a63-169">Aceleración (%)</span><span class="sxs-lookup"><span data-stu-id="34a63-169">Speed-up (%)</span></span> | <span data-ttu-id="34a63-170">N/D</span><span class="sxs-lookup"><span data-stu-id="34a63-170">N/A</span></span>                    | <span data-ttu-id="34a63-171">-122,8%</span><span class="sxs-lookup"><span data-stu-id="34a63-171">-122.8%</span></span>             | <span data-ttu-id="34a63-172">78,3 % (51,7 % desde WPS)</span><span class="sxs-lookup"><span data-stu-id="34a63-172">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a><span data-ttu-id="34a63-173">Comprobar `system32` para los módulos integrados compatibles en Windows</span><span class="sxs-lookup"><span data-stu-id="34a63-173">Check `system32` for compatible in-box modules on Windows</span></span>

<span data-ttu-id="34a63-174">En la actualización de Windows 10 1809 y Windows Server 2019, actualizamos una serie de módulos de PowerShell integrados para marcarlos como compatibles con PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="34a63-174">In the Windows 10 1809 update and Windows Server 2019, we updated a number of in-box PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="34a63-175">Cuando se inicie PowerShell Core 6.1, incluirá automáticamente `$windir\System32` como parte de la variable de entorno `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="34a63-175">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span> <span data-ttu-id="34a63-176">Pero solo expone módulos a `Get-Module` y `Import-Module` si su `CompatiblePSEdition` está marcado como compatible con `Core`.</span><span class="sxs-lookup"><span data-stu-id="34a63-176">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="34a63-177">Puede que vea otros módulos disponibles, en función de qué roles y características estén instaladas.</span><span class="sxs-lookup"><span data-stu-id="34a63-177">You may see different available modules depending on what roles and features are installed.</span></span>

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

<span data-ttu-id="34a63-178">Puede invalidar este comportamiento para que se muestren todos los módulos mediante el parámetro de modificador `-SkipEditionCheck`.</span><span class="sxs-lookup"><span data-stu-id="34a63-178">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="34a63-179">También hemos agregado una propiedad `PSEdition` a la salida de la tabla.</span><span class="sxs-lookup"><span data-stu-id="34a63-179">We've also added a `PSEdition` property to the table output.</span></span>

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

<span data-ttu-id="34a63-180">Para más información sobre este comportamiento, eche un vistazo a [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span><span class="sxs-lookup"><span data-stu-id="34a63-180">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="34a63-181">Representación y cmdlets de Markdown</span><span class="sxs-lookup"><span data-stu-id="34a63-181">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="34a63-182">Markdown es un estándar para crear documentos de texto simple legible con el formato básico que se puede representar en HTML.</span><span class="sxs-lookup"><span data-stu-id="34a63-182">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="34a63-183">Hemos agregado algunos cmdlets en 6.1 que permiten convertir y representar documentos de Markdown en la consola, incluidos:</span><span class="sxs-lookup"><span data-stu-id="34a63-183">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="34a63-184">Por ejemplo, `Show-Markdown` representa un archivo de Markdown en la consola:</span><span class="sxs-lookup"><span data-stu-id="34a63-184">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Ejemplo donde se muestra Markdown](./images/markdown_example.png)

<span data-ttu-id="34a63-186">Para más información sobre cómo funcionan estos cmdlets, vea [este RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span><span class="sxs-lookup"><span data-stu-id="34a63-186">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="34a63-187">Marcas de características experimentales</span><span class="sxs-lookup"><span data-stu-id="34a63-187">Experimental feature flags</span></span>

<span data-ttu-id="34a63-188">Ya habíamos habilitado la compatibilidad con las [características experimentales][].</span><span class="sxs-lookup"><span data-stu-id="34a63-188">We enabled support for [Experimental Features][].</span></span> <span data-ttu-id="34a63-189">Esto permite a los desarrolladores de PowerShell ofrecer nuevas características y obtener comentarios antes de completar el diseño.</span><span class="sxs-lookup"><span data-stu-id="34a63-189">This allows PowerShell developers to deliver new features and get feedback before the design is complete.</span></span> <span data-ttu-id="34a63-190">De este modo, evitamos realizar cambios importantes a medida que evoluciona el diseño.</span><span class="sxs-lookup"><span data-stu-id="34a63-190">This way we avoid making breaking changes as the design evolves.</span></span>

<span data-ttu-id="34a63-191">Use `Get-ExperimentalFeature` para obtener una lista de las características experimentales disponibles.</span><span class="sxs-lookup"><span data-stu-id="34a63-191">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="34a63-192">Puede habilitar o deshabilitar estas características con `Enable-ExperimentalFeature` y `Disable-ExperimentalFeature`.</span><span class="sxs-lookup"><span data-stu-id="34a63-192">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

<span data-ttu-id="34a63-193">Puede saber más sobre esta característica en [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="34a63-193">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="34a63-194">Mejoras de cmdlets de web</span><span class="sxs-lookup"><span data-stu-id="34a63-194">Web cmdlet improvements</span></span>

<span data-ttu-id="34a63-195">Gracias a [@markekraus](https://github.com/markekraus), se ha realizado una gran cantidad de mejoras en nuestros cmdlets de web: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="34a63-195">Thanks to [@markekraus](https://github.com/markekraus), a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="34a63-196">y [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span><span class="sxs-lookup"><span data-stu-id="34a63-196">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="34a63-197">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - codificación predeterminada establecida en UTF-8 para respuestas `application-json` predeterminadas</span><span class="sxs-lookup"><span data-stu-id="34a63-197">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="34a63-198">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) -parámetro `-SkipHeaderValidation` para permitir encabezados `Content-Type` que no son compatibles con el estándar</span><span class="sxs-lookup"><span data-stu-id="34a63-198">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="34a63-199">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) -parámetro `Form` para admitir compatibilidad con `multipart/form-data` simplificada</span><span class="sxs-lookup"><span data-stu-id="34a63-199">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="34a63-200">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - control compatible que distingue entre mayúsculas y minúsculas de las claves de la relación</span><span class="sxs-lookup"><span data-stu-id="34a63-200">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="34a63-201">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - adición del parámetro `-Resume` para cmdlets de web</span><span class="sxs-lookup"><span data-stu-id="34a63-201">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="34a63-202">Mejoras de comunicación remota</span><span class="sxs-lookup"><span data-stu-id="34a63-202">Remoting improvements</span></span>

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a><span data-ttu-id="34a63-203">PowerShell Direct para contenedores intenta usar primero PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="34a63-203">PowerShell Direct for Containers tries to use PowerShell Core first</span></span>

<span data-ttu-id="34a63-204">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) es una característica de PowerShell e Hyper-V que permite conectarse a una máquina virtual de Hyper-V o un contenedor sin conectividad de red u otros servicios de administración remota.</span><span class="sxs-lookup"><span data-stu-id="34a63-204">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM or Container without network connectivity or other remote management services.</span></span>

<span data-ttu-id="34a63-205">Antes, PowerShell Direct se conectaba mediante la instancia de Windows PowerShell integrada en el contenedor.</span><span class="sxs-lookup"><span data-stu-id="34a63-205">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the Container.</span></span> <span data-ttu-id="34a63-206">Ahora, PowerShell Direct intenta primero conectarse usando cualquier `pwsh.exe` disponible en la variable de entorno `PATH`.</span><span class="sxs-lookup"><span data-stu-id="34a63-206">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span> <span data-ttu-id="34a63-207">Si `pwsh.exe` no está disponible, PowerShell Direct recurre a usar `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="34a63-207">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="34a63-208">`Enable-PSRemoting` ahora crea puntos de conexión de comunicación remota independientes para versiones preliminares</span><span class="sxs-lookup"><span data-stu-id="34a63-208">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="34a63-209">`Enable-PSRemoting` ahora crea dos configuraciones de sesión de comunicación remota:</span><span class="sxs-lookup"><span data-stu-id="34a63-209">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="34a63-210">Una para la versión principal de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34a63-210">One for the major version of PowerShell.</span></span> <span data-ttu-id="34a63-211">Por ejemplo, `PowerShell.6`.</span><span class="sxs-lookup"><span data-stu-id="34a63-211">For example, `PowerShell.6`.</span></span> <span data-ttu-id="34a63-212">Este punto de conexión en el que se puede confiar en todas las actualizaciones de versiones secundarias como la configuración de sesión de PowerShell 6 "para todo el sistema".</span><span class="sxs-lookup"><span data-stu-id="34a63-212">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="34a63-213">Una configuración de sesión específica de la versión, por ejemplo: `PowerShell.6.1.0`</span><span class="sxs-lookup"><span data-stu-id="34a63-213">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="34a63-214">Este comportamiento es útil si quiere tener varias versiones de PowerShell 6 instaladas y accesibles en la misma máquina.</span><span class="sxs-lookup"><span data-stu-id="34a63-214">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="34a63-215">Además, las versiones preliminares de PowerShell ahora obtienen sus propias configuraciones de sesión de comunicación remota después de ejecutar el cmdlet `Enable-PSRemoting`:</span><span class="sxs-lookup"><span data-stu-id="34a63-215">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="34a63-216">El resultado puede ser diferente si no ha configurado WinRM antes.</span><span class="sxs-lookup"><span data-stu-id="34a63-216">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="34a63-217">Después puede ver las configuraciones de sesión de PowerShell independientes para la versión preliminar y compilaciones estables de PowerShell 6, para cada versión específica.</span><span class="sxs-lookup"><span data-stu-id="34a63-217">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

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

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="34a63-218">Sintaxis `user@host:port` para SSH</span><span class="sxs-lookup"><span data-stu-id="34a63-218">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="34a63-219">Los clientes SSH suelen admitir una cadena de conexión en el formato `user@host:port`.</span><span class="sxs-lookup"><span data-stu-id="34a63-219">SSH clients typically support a connection string in the format `user@host:port`.</span></span> <span data-ttu-id="34a63-220">Al agregar SSH como protocolo para la comunicación remota de PowerShell, se ha agregado compatibilidad con este formato de cadena de conexión:</span><span class="sxs-lookup"><span data-stu-id="34a63-220">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="34a63-221">Opción de MSI para agregar el menú contextual del shell del Explorador en Windows</span><span class="sxs-lookup"><span data-stu-id="34a63-221">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="34a63-222">Gracias a [@bergmeister](https://github.com/bergmeister), ya puede habilitar un menú contextual en Windows.</span><span class="sxs-lookup"><span data-stu-id="34a63-222">Thanks to [@bergmeister](https://github.com/bergmeister), now you can enable a context menu on Windows.</span></span> <span data-ttu-id="34a63-223">Ahora puede abrir la instalación de todo el sistema de PowerShell 6.1 desde cualquier carpeta en el Explorador de Windows:</span><span class="sxs-lookup"><span data-stu-id="34a63-223">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![Menú contextual del shell para PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="34a63-225">Extras</span><span class="sxs-lookup"><span data-stu-id="34a63-225">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="34a63-226">"Ejecutar como administrador" en la lista de accesos directos de Windows</span><span class="sxs-lookup"><span data-stu-id="34a63-226">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="34a63-227">Gracias a [@bergmeister](https://github.com/bergmeister), la lista de accesos directos de PowerShell Core incluye ahora "Ejecutar como administrador":</span><span class="sxs-lookup"><span data-stu-id="34a63-227">Thanks to [@bergmeister](https://github.com/bergmeister), the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![Ejecutar como administrador en la lista de accesos directos de PowerShell 6](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="34a63-229">`cd -` vuelve al directorio anterior</span><span class="sxs-lookup"><span data-stu-id="34a63-229">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="34a63-230">O en Linux:</span><span class="sxs-lookup"><span data-stu-id="34a63-230">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="34a63-231">Además, `cd` y `cd --` cambian a `$HOME`.</span><span class="sxs-lookup"><span data-stu-id="34a63-231">Also, `cd` and `cd --` change to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="34a63-232">Gracias a [@iSazonov](https://github.com/iSazonov), el cmdlet [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) se ha trasladado a PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="34a63-232">Thanks to [@iSazonov](https://github.com/iSazonov), the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="34a63-233">`Update-Help` como no administrador</span><span class="sxs-lookup"><span data-stu-id="34a63-233">`Update-Help` as non-admin</span></span>

<span data-ttu-id="34a63-234">Por petición popular, `Update-Help` ya no debe ejecutarse como administrador.</span><span class="sxs-lookup"><span data-stu-id="34a63-234">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span> <span data-ttu-id="34a63-235">`Update-Help` ahora tiene como valor predeterminado guardar la Ayuda en una carpeta con ámbito de usuario.</span><span class="sxs-lookup"><span data-stu-id="34a63-235">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="34a63-236">Nuevos métodos y propiedades en `PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="34a63-236">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="34a63-237">Gracias a [@iSazonov](https://github.com/iSazonov), hemos agregado nuevos métodos y propiedades a `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="34a63-237">Thanks to [@iSazonov](https://github.com/iSazonov), we've added new methods and properties to `PSCustomObject`.</span></span> <span data-ttu-id="34a63-238">`PSCustomObject` ahora incluye una propiedad `Count`/`Length` como otros objetos.</span><span class="sxs-lookup"><span data-stu-id="34a63-238">`PSCustomObject` now includes a `Count`/`Length` property like other objects.</span></span>

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

<span data-ttu-id="34a63-239">Este trabajo también incluye los métodos `ForEach` y `Where` que permiten operar y filtrar en elementos `PSCustomObject`:</span><span class="sxs-lookup"><span data-stu-id="34a63-239">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

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

<span data-ttu-id="34a63-240">Gracias a @SimonWahlin, hemos agregado el parámetro `-Not` a `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="34a63-240">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span> <span data-ttu-id="34a63-241">Ahora puede filtrar un objeto en la canalización para la no existencia de una propiedad o un valor de propiedad nula o vacía.</span><span class="sxs-lookup"><span data-stu-id="34a63-241">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="34a63-242">Por ejemplo, este comando devuelve todos los servicios que no tienen los servicios dependientes definidos:</span><span class="sxs-lookup"><span data-stu-id="34a63-242">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="34a63-243">`New-ModuleManifest` crea un documento UTF-8 sin marca BOM</span><span class="sxs-lookup"><span data-stu-id="34a63-243">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="34a63-244">Debido a nuestro cambio a UTF-8 sin marca BOM en PowerShell 6.0, hemos actualizado el cmdlet `New-ModuleManifest` para crear un documento UTF-8 sin marca BOM en lugar de uno UTF-16.</span><span class="sxs-lookup"><span data-stu-id="34a63-244">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="34a63-245">Conversiones de PSMethod a delegado</span><span class="sxs-lookup"><span data-stu-id="34a63-245">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="34a63-246">Gracias a [@powercode](https://github.com/powercode), ahora se admite la conversión de un `PSMethod` a un delegado.</span><span class="sxs-lookup"><span data-stu-id="34a63-246">Thanks to [@powercode](https://github.com/powercode), we now support the conversion of a `PSMethod` into a delegate.</span></span> <span data-ttu-id="34a63-247">Esto permite hacer cosas como pasar `PSMethod` `[M]::DoubleStrLen` como un valor de delegado en `[M]::AggregateString`:</span><span class="sxs-lookup"><span data-stu-id="34a63-247">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

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

<span data-ttu-id="34a63-248">Para más información sobre este cambio, eche un vistazo a [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span><span class="sxs-lookup"><span data-stu-id="34a63-248">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="34a63-249">Desviación estándar en `Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="34a63-249">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="34a63-250">Gracias a [@CloudyDino](https://github.com/CloudyDino), hemos agregado una propiedad `StandardDeviation` a `Measure-Object`:</span><span class="sxs-lookup"><span data-stu-id="34a63-250">Thanks to [@CloudyDino](https://github.com/CloudyDino), we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

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

<span data-ttu-id="34a63-251">Gracias a [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` tiene ahora el parámetro `Password`, que toma `SecureString`.</span><span class="sxs-lookup"><span data-stu-id="34a63-251">Thanks to [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="34a63-252">Esto permite usarlo de forma no interactiva:</span><span class="sxs-lookup"><span data-stu-id="34a63-252">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="34a63-253">Eliminación de la función `more`</span><span class="sxs-lookup"><span data-stu-id="34a63-253">Removal of the `more` function</span></span>

<span data-ttu-id="34a63-254">Antes, PowerShell incluía una función en Windows llamada `more` que encapsulaba `more.com`.</span><span class="sxs-lookup"><span data-stu-id="34a63-254">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span> <span data-ttu-id="34a63-255">Se ha quitado esa función.</span><span class="sxs-lookup"><span data-stu-id="34a63-255">That function has now been removed.</span></span>

<span data-ttu-id="34a63-256">Además, se ha cambiado la función `help` para usar `more.com` en Windows o el elemento de paginación del sistema predeterminado especificado por `$env:PAGER` en plataformas que no sean Windows.</span><span class="sxs-lookup"><span data-stu-id="34a63-256">Also, the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="34a63-257">`cd DriveName:` ahora devuelve a los usuarios al directorio de trabajo actual en esa unidad</span><span class="sxs-lookup"><span data-stu-id="34a63-257">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="34a63-258">Antes, al usar `Set-Location` o `cd` para volver a un PSDrive enviaba a los usuarios a la ubicación predeterminada para esa unidad.</span><span class="sxs-lookup"><span data-stu-id="34a63-258">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="34a63-259">Gracias a [@mcbobke](https://github.com/mcbobke), ahora se envía a los usuarios al último directorio de trabajo actual conocido para esa sesión.</span><span class="sxs-lookup"><span data-stu-id="34a63-259">Thanks to [@mcbobke](https://github.com/mcbobke), users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="34a63-260">Aceleradores de tipo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="34a63-260">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="34a63-261">En Windows PowerShell, hemos incluido estos aceleradores de tipo para que sea más fácil trabajar con sus tipos respectivos:</span><span class="sxs-lookup"><span data-stu-id="34a63-261">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="34a63-262">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="34a63-262">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="34a63-263">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="34a63-263">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="34a63-264">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="34a63-264">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="34a63-265">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="34a63-265">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="34a63-266">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="34a63-266">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="34a63-267">Estos aceleradores de tipo no se incluían en PowerShell 6, pero se han agregado a PowerShell 6.1 que se ejecuta en Windows.</span><span class="sxs-lookup"><span data-stu-id="34a63-267">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="34a63-268">Estos tipos son útiles para crear fácilmente objetos de AD y WMI.</span><span class="sxs-lookup"><span data-stu-id="34a63-268">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="34a63-269">Por ejemplo, puede consultar mediante LDAP:</span><span class="sxs-lookup"><span data-stu-id="34a63-269">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="34a63-270">En este ejemplo se crea un objeto CIM de Win32_OperatingSystem:</span><span class="sxs-lookup"><span data-stu-id="34a63-270">Following example creates a Win32_OperatingSystem CIM object:</span></span>

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

<span data-ttu-id="34a63-271">En este ejemplo se devuelve un objeto ManagementClass para la clase Win32_OperatingSystem.</span><span class="sxs-lookup"><span data-stu-id="34a63-271">This example returns a ManagementClass object for Win32_OperatingSystem class.</span></span>

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="34a63-272">Alias `-lp` para todos los parámetros `-LiteralPath`</span><span class="sxs-lookup"><span data-stu-id="34a63-272">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="34a63-273">Gracias a [@kvprasoon](https://github.com/kvprasoon), ahora tenemos un alias de parámetro `-lp` para todos los cmdlets de PowerShell integrados que tienen un parámetro `-LiteralPath`.</span><span class="sxs-lookup"><span data-stu-id="34a63-273">Thanks to [@kvprasoon](https://github.com/kvprasoon), we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="34a63-274">Últimos cambios</span><span class="sxs-lookup"><span data-stu-id="34a63-274">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="34a63-275">Rutas de acceso de instalación basadas en MSI en Windows</span><span class="sxs-lookup"><span data-stu-id="34a63-275">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="34a63-276">En Windows, el paquete MSI ahora instala esta ruta de acceso:</span><span class="sxs-lookup"><span data-stu-id="34a63-276">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="34a63-277">`$env:ProgramFiles\PowerShell\6\` para la instalación estable de 6.x</span><span class="sxs-lookup"><span data-stu-id="34a63-277">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="34a63-278">`$env:ProgramFiles\PowerShell\6-preview\` para la instalación de versión preliminar de 6.x</span><span class="sxs-lookup"><span data-stu-id="34a63-278">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="34a63-279">Este cambio garantiza que PowerShell Core se pueda actualizar o mantener a través de Microsoft Update.</span><span class="sxs-lookup"><span data-stu-id="34a63-279">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="34a63-280">Para más información, vea [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span><span class="sxs-lookup"><span data-stu-id="34a63-280">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="34a63-281">Solo se puede deshabilitar la telemetría con una variable de entorno</span><span class="sxs-lookup"><span data-stu-id="34a63-281">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="34a63-282">PowerShell Core envía datos de telemetría básica a Microsoft cuando se inicia.</span><span class="sxs-lookup"><span data-stu-id="34a63-282">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="34a63-283">Los datos incluyen el nombre del sistema operativo, la versión del sistema operativo y la versión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34a63-283">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="34a63-284">Estos datos nos permiten comprender mejor los entornos donde se usa PowerShell y nos permite dar prioridad a nuevas características y correcciones.</span><span class="sxs-lookup"><span data-stu-id="34a63-284">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="34a63-285">Para dejar de participar en esta telemetría, establezca la variable de entorno `POWERSHELL_TELEMETRY_OPTOUT` en `true`, `yes` o `1`.</span><span class="sxs-lookup"><span data-stu-id="34a63-285">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="34a63-286">Ya no se admite la eliminación del archivo `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` para deshabilitar la telemetría.</span><span class="sxs-lookup"><span data-stu-id="34a63-286">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="34a63-287">No permite la autenticación básica a través de HTTP de comunicación remota de PowerShell en plataformas Unix</span><span class="sxs-lookup"><span data-stu-id="34a63-287">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="34a63-288">Para evitar el uso de tráfico sin cifrar, ahora es necesario usar NTLM/Negotiate o HTTPS para la comunicación remota de PowerShell en plataformas Unix.</span><span class="sxs-lookup"><span data-stu-id="34a63-288">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="34a63-289">Para obtener más información sobre estos cambios, consulte [PR #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span><span class="sxs-lookup"><span data-stu-id="34a63-289">For more information on these changes, check out [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="34a63-290">Se quitó `VisualBasic` como lenguaje compatible en Add-Type</span><span class="sxs-lookup"><span data-stu-id="34a63-290">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="34a63-291">Antes, se podía compilar código de Visual Basic mediante el cmdlet `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="34a63-291">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span> <span data-ttu-id="34a63-292">Visual Basic se usó rara vez con `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="34a63-292">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="34a63-293">Hemos quitado esta característica para reducir el tamaño de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34a63-293">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="34a63-294">Se limpiaron los usos de `CommandTypes.Workflow` y `WorkflowInfoCleaned`</span><span class="sxs-lookup"><span data-stu-id="34a63-294">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="34a63-295">Para más información sobre estos cambios, eche un vistazo a [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span><span class="sxs-lookup"><span data-stu-id="34a63-295">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>

### <a name="group-object-now-sorts-the-groups"></a><span data-ttu-id="34a63-296">Ahora, Group-Object ordena los grupos</span><span class="sxs-lookup"><span data-stu-id="34a63-296">Group-Object now sorts the groups</span></span>

<span data-ttu-id="34a63-297">Como parte de la mejora del rendimiento, `Group-Object` ahora devuelve una lista ordenada de los grupos.</span><span class="sxs-lookup"><span data-stu-id="34a63-297">As part of the performance improvement, `Group-Object` now returns a sorted listing of the groups.</span></span>
<span data-ttu-id="34a63-298">Aunque no debe confiar en el orden, podría verse interrumpida por este cambio si quisiera el primer grupo.</span><span class="sxs-lookup"><span data-stu-id="34a63-298">Although you should not rely on the order, you could be broken by this change if you wanted the first group.</span></span> <span data-ttu-id="34a63-299">Decidimos que esta mejora en el rendimiento valía la pena el cambio, ya que el impacto de depender del comportamiento previo es bajo.</span><span class="sxs-lookup"><span data-stu-id="34a63-299">We decided that this performance improvement was worth the change since the impact of being dependent on previous behavior is low.</span></span>

<span data-ttu-id="34a63-300">Para más información sobre este cambio, consulte el [problema #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span><span class="sxs-lookup"><span data-stu-id="34a63-300">For more information on this change, see [Issue #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span></span>

<!-- URL references -->
[Características experimentales]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
