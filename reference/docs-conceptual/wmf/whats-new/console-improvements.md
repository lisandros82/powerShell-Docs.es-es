---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Mejoras de la consola en WMF 5.1
ms.openlocfilehash: d0dd8e3c31dc0ddebab1bb899468b77a9292954d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147635"
---
# <a name="console-improvements-in-wmf-51"></a>Mejoras de la consola en WMF 5.1

## <a name="powershell-console-improvements"></a>Mejoras en la consola de PowerShell

En WMF 5.1, se han realizado los siguientes cambios en PowerShell.exe para mejorar la experiencia de la consola:

### <a name="vt100-support"></a>Compatibilidad con VT100

Windows 10 agregó compatibilidad con [secuencias de escape de VT100](/windows/console/console-virtual-terminal-sequences).
PowerShell ignorará ciertas secuencias de escape con formato VT100 al calcular los anchos de tabla.

PowerShell también agregó una nueva API que puede utilizarse al dar formato al código para determinar si se admite VT100. Por ejemplo:

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

Esta es un [ejemplo](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) completo que se puede utilizar para resaltar las coincidencias de `Select-String`. Guarde el ejemplo en un archivo denominado `MatchInfo.format.ps1xml` y para usarlo, en su perfil o en cualquier otro lugar, ejecute `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Tenga en cuenta que las secuencias de escape de VT100 solo se admiten a partir de la Actualización de aniversario de Windows 10.
No se admiten en sistemas anteriores.

### <a name="vi-mode-support-in-psreadline"></a>Compatibilidad con el modo VI en PSReadline

[PSReadline](https://github.com/PowerShell/PSReadLine) agrega compatibilidad con el modo VI. Para utilizar el modo VI, ejecute `Set-PSReadlineOption -EditMode Vi`.

### <a name="redirected-stdin-with-interactive-input"></a>Stdin redirigido con entrada interactiva

En versiones anteriores, a partir de PowerShell con `powershell -File -` se requería cuando se redirigía stdin y deseaba especificar los comandos de forma interactiva.

Con WMF 5.1 ya no es necesaria esta opción, que es difícil de detectar. Puede iniciar PowerShell sin ninguna opción.

Tenga en cuenta que PSReadline no admite stdin redirigido y la experiencia de edición de línea de comandos integrada con stdin redirigido es extremadamente limitada, por ejemplo, las teclas de dirección no funcionan. Una futura versión de PSReadline debería solucionar este problema.