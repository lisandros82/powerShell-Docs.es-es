---
title: "Mejoras de la consola en WMF 5.1 (versión preliminar)"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 574fec8e1f4948021988d8489532d7325277fed6
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
# <a name="console-improvements-in-wmf-51-preview"></a><span data-ttu-id="f6c7b-103">Mejoras de la consola en WMF 5.1 (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="f6c7b-103">Console Improvements in WMF 5.1 (Preview)</span></span>#

## <a name="powershell-console-improvements"></a><span data-ttu-id="f6c7b-104">Mejoras en la consola de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6c7b-104">PowerShell console improvements</span></span>

<span data-ttu-id="f6c7b-105">En WMF 5.1, se han realizado los siguientes cambios en PowerShell.exe para mejorar la experiencia de la consola:</span><span class="sxs-lookup"><span data-stu-id="f6c7b-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

###<a name="vt100-support"></a><span data-ttu-id="f6c7b-106">Compatibilidad con VT100</span><span class="sxs-lookup"><span data-stu-id="f6c7b-106">VT100 support</span></span>

<span data-ttu-id="f6c7b-107">Windows 10 agregó compatibilidad con [secuencias de escape de VT100](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="f6c7b-107">Windows 10 added support for [VT100 escape sequences](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span></span>
<span data-ttu-id="f6c7b-108">PowerShell ignorará ciertas secuencias de escape con formato VT100 al calcular los anchos de tabla.</span><span class="sxs-lookup"><span data-stu-id="f6c7b-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="f6c7b-109">PowerShell también agregó una nueva API que puede utilizarse al dar formato al código para determinar si se admite VT100.</span><span class="sxs-lookup"><span data-stu-id="f6c7b-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="f6c7b-110">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="f6c7b-110">For example:</span></span>

```
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
<span data-ttu-id="f6c7b-111">Esta es un [ejemplo](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) completo que se puede utilizar para resaltar las coincidencias de Select-String.</span><span class="sxs-lookup"><span data-stu-id="f6c7b-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from Select-String.</span></span>
<span data-ttu-id="f6c7b-112">Guarde el ejemplo en un archivo denominado `MatchInfo.format.ps1xml` y para usarlo, en su perfil o en cualquier otro lugar, ejecute `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="f6c7b-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="f6c7b-113">Tenga en cuenta que las secuencias de escape VT100 solo se admiten a partir de la actualización de aniversario de Windows 10, no en los sistemas anteriores.</span><span class="sxs-lookup"><span data-stu-id="f6c7b-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>   

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="f6c7b-114">Compatibilidad con el modo VI en PSReadline</span><span class="sxs-lookup"><span data-stu-id="f6c7b-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="f6c7b-115">[PSReadline](https://github.com/lzybkr/PSReadLine) agrega compatibilidad con el modo VI.</span><span class="sxs-lookup"><span data-stu-id="f6c7b-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="f6c7b-116">Para utilizar el modo VI, ejecute `Set-PSReadline -EditMode vi`.</span><span class="sxs-lookup"><span data-stu-id="f6c7b-116">To use vi mode, run `Set-PSReadline -EditMode vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="f6c7b-117">Stdin redirigido con entrada interactiva</span><span class="sxs-lookup"><span data-stu-id="f6c7b-117">Redirected stdin with interactive input</span></span> 

<span data-ttu-id="f6c7b-118">En versiones anteriores, a partir de PowerShell con `powershell -File -` se requería cuando se redirigía stdin y deseaba especificar los comandos de forma interactiva.</span><span class="sxs-lookup"><span data-stu-id="f6c7b-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="f6c7b-119">Con WMF 5.1 ya no es necesaria esta opción, que es difícil de detectar.</span><span class="sxs-lookup"><span data-stu-id="f6c7b-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="f6c7b-120">Puede iniciar PowerShell sin opciones, por ejemplo, `powershell`.</span><span class="sxs-lookup"><span data-stu-id="f6c7b-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="f6c7b-121">Tenga en cuenta que PSReadline actualmente no admite stdin redirigido y la experiencia de edición de línea de comandos integrada con stdin redirigido es extremadamente limitada, por ejemplo, las teclas de dirección no funcionan.</span><span class="sxs-lookup"><span data-stu-id="f6c7b-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="f6c7b-122">Una futura versión de PSReadline debería solucionar este problema.</span><span class="sxs-lookup"><span data-stu-id="f6c7b-122">A future release of PSReadline should address this issue.</span></span>   
