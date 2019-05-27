---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Mejoras de la consola en WMF 5.1
ms.openlocfilehash: d0dd8e3c31dc0ddebab1bb899468b77a9292954d
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855510"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="8aaad-103">Mejoras de la consola en WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="8aaad-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="8aaad-104">Mejoras en la consola de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8aaad-104">PowerShell console improvements</span></span>

<span data-ttu-id="8aaad-105">En WMF 5.1, se han realizado los siguientes cambios en PowerShell.exe para mejorar la experiencia de la consola:</span><span class="sxs-lookup"><span data-stu-id="8aaad-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="8aaad-106">Compatibilidad con VT100</span><span class="sxs-lookup"><span data-stu-id="8aaad-106">VT100 support</span></span>

<span data-ttu-id="8aaad-107">Windows 10 agregó compatibilidad con [secuencias de escape de VT100](/windows/console/console-virtual-terminal-sequences).</span><span class="sxs-lookup"><span data-stu-id="8aaad-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="8aaad-108">PowerShell ignorará ciertas secuencias de escape con formato VT100 al calcular los anchos de tabla.</span><span class="sxs-lookup"><span data-stu-id="8aaad-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="8aaad-109">PowerShell también agregó una nueva API que puede utilizarse al dar formato al código para determinar si se admite VT100.</span><span class="sxs-lookup"><span data-stu-id="8aaad-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="8aaad-110">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8aaad-110">For example:</span></span>

```powershell
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```

<span data-ttu-id="8aaad-111">Esta es un [ejemplo](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) completo que se puede utilizar para resaltar las coincidencias de `Select-String`.</span><span class="sxs-lookup"><span data-stu-id="8aaad-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span> <span data-ttu-id="8aaad-112">Guarde el ejemplo en un archivo denominado `MatchInfo.format.ps1xml` y para usarlo, en su perfil o en cualquier otro lugar, ejecute `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="8aaad-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="8aaad-113">Tenga en cuenta que las secuencias de escape de VT100 solo se admiten a partir de la Actualización de aniversario de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="8aaad-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update.</span></span>
<span data-ttu-id="8aaad-114">No se admiten en sistemas anteriores.</span><span class="sxs-lookup"><span data-stu-id="8aaad-114">They are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="8aaad-115">Compatibilidad con el modo VI en PSReadline</span><span class="sxs-lookup"><span data-stu-id="8aaad-115">Vi mode support in PSReadline</span></span>

<span data-ttu-id="8aaad-116">[PSReadline](https://github.com/PowerShell/PSReadLine) agrega compatibilidad con el modo VI.</span><span class="sxs-lookup"><span data-stu-id="8aaad-116">[PSReadline](https://github.com/PowerShell/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="8aaad-117">Para utilizar el modo VI, ejecute `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="8aaad-117">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="8aaad-118">Stdin redirigido con entrada interactiva</span><span class="sxs-lookup"><span data-stu-id="8aaad-118">Redirected stdin with interactive input</span></span>

<span data-ttu-id="8aaad-119">En versiones anteriores, a partir de PowerShell con `powershell -File -` se requería cuando se redirigía stdin y deseaba especificar los comandos de forma interactiva.</span><span class="sxs-lookup"><span data-stu-id="8aaad-119">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="8aaad-120">Con WMF 5.1 ya no es necesaria esta opción, que es difícil de detectar.</span><span class="sxs-lookup"><span data-stu-id="8aaad-120">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="8aaad-121">Puede iniciar PowerShell sin ninguna opción.</span><span class="sxs-lookup"><span data-stu-id="8aaad-121">You can start PowerShell without any options.</span></span>

<span data-ttu-id="8aaad-122">Tenga en cuenta que PSReadline no admite stdin redirigido y la experiencia de edición de línea de comandos integrada con stdin redirigido es extremadamente limitada, por ejemplo, las teclas de dirección no funcionan.</span><span class="sxs-lookup"><span data-stu-id="8aaad-122">Note that PSReadline does not support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="8aaad-123">Una futura versión de PSReadline debería solucionar este problema.</span><span class="sxs-lookup"><span data-stu-id="8aaad-123">A future release of PSReadline should address this issue.</span></span>