---
title: Novedades de PowerShell Core 6.2
description: Nuevas características y cambios publicados en PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750060"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="ef32c-103">Novedades de PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="ef32c-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="ef32c-104">Esta es una selección de algunas de las principales características nuevas y los cambios que se han incorporado en PowerShell Core 6.2.</span><span class="sxs-lookup"><span data-stu-id="ef32c-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.2.</span></span>

<span data-ttu-id="ef32c-105">También hay **toneladas** de "cosas aburridas" que hacen que PowerShell sea más rápido y más estable (además de montones y montones de correcciones de errores).</span><span class="sxs-lookup"><span data-stu-id="ef32c-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="ef32c-106">Si quiere ver una lista completa de los cambios, eche un vistazo a nuestro [registro de cambios en GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="ef32c-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="ef32c-107">Y aunque destacamos algunos nombres al final, queremos dar las gracias a [todos los colaboradores de la comunidad](https://github.com/PowerShell/PowerShell/graphs/contributors) que han hecho posible esta versión.</span><span class="sxs-lookup"><span data-stu-id="ef32c-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="engine-updates-and-fixes"></a><span data-ttu-id="ef32c-108">Actualizaciones y correcciones del motor</span><span class="sxs-lookup"><span data-stu-id="ef32c-108">Engine Updates and Fixes</span></span>

- <span data-ttu-id="ef32c-109">Incorporación de mensajes de advertencia de cmdlet de habilitación o deshabilitación remota de PowerShell ([#9203][])</span><span class="sxs-lookup"><span data-stu-id="ef32c-109">Add PowerShell remoting enable/disable cmdlet warning messages ([#9203][])</span></span>
- <span data-ttu-id="ef32c-110">Corrección de la regresión de deserialización remota `FormatTable` ([#9116][])</span><span class="sxs-lookup"><span data-stu-id="ef32c-110">Fix for `FormatTable` remote deserialization regression ([#9116][])</span></span>
- <span data-ttu-id="ef32c-111">Actualización de las API `async` basadas en tareas agregadas a PowerShell para devolver directamente un objeto de tarea ([#9079][])</span><span class="sxs-lookup"><span data-stu-id="ef32c-111">Update the task-based `async` APIs added to PowerShell to return a Task object directly ([#9079][])</span></span>
- <span data-ttu-id="ef32c-112">Incorporación de 5 cargas de trabajo `InvokeAsync` y `StopAsync` al tipo `PowerShell` ([#8056][]) (Muchas gracias, @KirkMunro)</span><span class="sxs-lookup"><span data-stu-id="ef32c-112">Add 5 `InvokeAsync` overloads and `StopAsync` to the `PowerShell` type ([#8056][]) (Thanks @KirkMunro!)</span></span>

## <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="ef32c-113">Actualizaciones y correcciones generales de cmdlet</span><span class="sxs-lookup"><span data-stu-id="ef32c-113">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="ef32c-114">Habilitación de cmdlets `SecureString` para entornos que no son de Windows mediante el almacenamiento del texto sin formato ([#9199][])</span><span class="sxs-lookup"><span data-stu-id="ef32c-114">Enable `SecureString` cmdlets for non-Windows by storing the plain text ([#9199][])</span></span>
- <span data-ttu-id="ef32c-115">Incorporación de mensaje obsoleto en `Send-MailMessage` ([#9178][])</span><span class="sxs-lookup"><span data-stu-id="ef32c-115">Add Obsolete message to `Send-MailMessage` ([#9178][])</span></span>
- <span data-ttu-id="ef32c-116">Corrección de `Restart-Computer` para trabajar en `localhost` cuando WinRM no está presente ([#9160][])</span><span class="sxs-lookup"><span data-stu-id="ef32c-116">Fix `Restart-Computer` to work on `localhost` when WinRM is not present ([#9160][])</span></span>
- <span data-ttu-id="ef32c-117">Generación de error de terminación `Start-Job` cuando se hospeda PowerShell ([#9128][])</span><span class="sxs-lookup"><span data-stu-id="ef32c-117">Make `Start-Job` throw terminating error when PowerShell is being hosted ([#9128][])</span></span>
- <span data-ttu-id="ef32c-118">Actualización de la versión para `PowerShell.Native` y pruebas de hospedaje ([#8983][])</span><span class="sxs-lookup"><span data-stu-id="ef32c-118">Update version for `PowerShell.Native` and hosting tests ([#8983][])</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="ef32c-119">Cambios importantes</span><span class="sxs-lookup"><span data-stu-id="ef32c-119">Breaking Changes</span></span>

<span data-ttu-id="ef32c-120">Corrección del comportamiento -NoEnumerate en Write-Output para coherencia con Windows PowerShell ([#9069][]) (Muchas gracias, @vexx32)</span><span class="sxs-lookup"><span data-stu-id="ef32c-120">Fix -NoEnumerate behavior in Write-Output to be consistent with Windows PowerShell ([#9069][]) (Thanks @vexx32!)</span></span>

<!-- Link references -->
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
