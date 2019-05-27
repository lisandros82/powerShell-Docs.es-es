---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Mejoras en la depuración de scripts de PowerShell
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855450"
---
# <a name="improvements-in-powershell-script-debugging"></a>Mejoras en la depuración de scripts de PowerShell

PowerShell 5.0 incluye varias mejoras que perfeccionan la experiencia de depuración.

## <a name="break-all"></a>Interrumpir todos

La consola de PowerShell y PowerShell ISE permiten ahora el acceso al depurador para ejecutar scripts. Está opción está disponible para sesiones locales y remotas.

En la consola, presione <kbd>Ctrl</kbd>+<kbd>Interrumpir</kbd>.

En el ISE, presione <kbd>Ctrl</kbd>+<kbd>B</kbd> o use el comando de menú **Depurar -> Interrumpir todos**.

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a>Depuración remota y edición remota de archivos en PowerShell ISE

PowerShell ISE permite ahora abrir y editar archivos en una sesión remota mediante la ejecución del comando PSEdit.
Por ejemplo, puede abrir un archivo para editarlo desde la línea de comandos en una sesión remota de la siguiente manera:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Además, ahora puede editarlo y guardar los cambios en un archivo remoto que se abrirá automáticamente en PowerShell ISE cuando se alcance un punto de interrupción. Ahora, puede depurar un archivo de script que se ejecute en un equipo remoto, editar el archivo para corregir un error y, después, volver a ejecutar el script modificado.

## <a name="advanced-script-debugging"></a>Depuración de scripts avanzada

Existen nuevas características de depuración avanzadas que permiten conectarse a cualquier proceso del equipo local que tenga PowerShell cargado, así como depurar espacios de ejecución arbitrarios en ese proceso.

### <a name="runspace-debugging"></a>Depuración del espacio de ejecución

Los nuevos cmdlets agregados permiten enumerar los espacios de ejecución actuales en un proceso y conectar la consola de PowerShell o el depurador de PowerShell ISE a ese espacio de ejecución para la depuración de scripts:

- Get-Runspace
- Debug-Runspace
- Enable-RunspaceDebug
- Disable-RunspaceDebug
- Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Conectarse al proceso que hospeda PowerShell

Ahora puede establecer la conexión con cualquier proceso del equipo que tenga PowerShell cargado. Para ello, ingrese en una sesión interactiva con el proceso de host. Para obtener más información, consulte:

- [Enter-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [Exit-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
