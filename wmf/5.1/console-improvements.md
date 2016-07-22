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
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 221b8095c15a810c032bd93aafe8ec886af233d9

---

# Mejoras de la consola en WMF 5.1 (versión preliminar)#

## Mejoras en la consola de PowerShell

En WMF 5.1, se han realizado los siguientes cambios en PowerShell.exe para mejorar la experiencia de la consola:

###Compatibilidad con VT100

Windows 10 agregó compatibilidad con [secuencias de escape de VT100](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).
PowerShell ignorará ciertas secuencias de escape con formato VT100 al calcular los anchos de tabla.

PowerShell también agregó una nueva API que puede utilizarse al dar formato al código para determinar si se admite VT100. Por ejemplo:

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
Esta es un [ejemplo](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) completo que se puede utilizar para resaltar las coincidencias de Select-String.
Guarde el ejemplo en un archivo denominado `MatchInfo.format.ps1xml` y para usarlo, en su perfil o en cualquier otro lugar, ejecute `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Tenga en cuenta que las secuencias de escape VT100 solo se admiten a partir de la actualización de aniversario de Windows 10, no en los sistemas anteriores.   

### Compatibilidad con el modo VI en PSReadline

[PSReadline](https://github.com/lzybkr/PSReadLine) agrega compatibilidad con el modo VI. Para utilizar el modo VI, ejecute `Set-PSReadline -EditMode vi`.

### Stdin redirigido con entrada interactiva 

En versiones anteriores, a partir de PowerShell con `powershell -File -` se requería cuando se redirigía stdin y deseaba especificar los comandos de forma interactiva.

Con WMF 5.1, este opción, que es difícil de detectar, no es necesaria, y podrá iniciar PowerShell sin opciones, por ejemplo, `powershell`.

Tenga en cuenta que PSReadline no admite stdin redirigido y la experiencia de edición de línea de comandos integrada con stdin redirigido es extremadamente limitada, por ejemplo, las teclas de dirección no funcionan.  Una futura versión de PSReadline debería solucionar este problema.   



<!--HONumber=Jul16_HO3-->


