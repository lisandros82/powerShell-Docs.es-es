---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9ead27fd5d4f146e9062488c1c8cc22a073b922e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="improvements-in-powershell-script-debugging"></a>Mejoras en la depuración de scripts de PowerShell

PowerShell 5.0 incluye varias mejoras para ofrecer una experiencia de depuración superior:

## <a name="break-all"></a>Interrumpir todos

La consola de PowerShell y Windows PowerShell ISE permite ahora el acceso al depurador para ejecutar scripts. Está opción está disponible para sesiones locales y remotas.

En la consola, presione **Ctrl+Interrumpir**.

En el ISE, presione **Ctrl+B** o use el comando de menú **Depurar -> Interrumpir todos**.

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a>Depuración remota y edición remota de archivos en Windows PowerShell ISE

Windows PowerShell ISE permite ahora abrir y editar archivos en una sesión remota mediante la ejecución del comando PSEdit.
Por ejemplo, puede abrir un archivo para editarlo desde la línea de comandos en una sesión remota de la siguiente manera:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Además, ahora puede editarlo y guardar los cambios en un archivo remoto que se abrirá automáticamente en Windows PowerShell ISE cuando se alcance un punto de interrupción.
Ahora, puede depurar un archivo de script que se ejecute en un equipo remoto, editar el archivo para corregir un error y, después, volver a ejecutar el script modificado.

## <a name="advanced-script-debugging"></a>Depuración de scripts avanzada

Existen nuevas características de depuración avanzadas que permiten conectarse a cualquier proceso del equipo local que tenga Windows PowerShell cargado, así como depurar espacios de ejecución arbitrarios en ese proceso.

### <a name="runspace-debugging"></a>Depuración del espacio de ejecución

Los nuevos cmdlets agregados permiten enumerar los espacios de ejecución actuales en un proceso y conectar la consola de Windows PowerShell o el depurador de ISE a ese espacio de ejecución para la depuración de scripts:

-   Get-Runspace
-   Debug-Runspace
-   Enable-RunspaceDebug
-   Disable-RunspaceDebug
-   Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Conectarse al proceso que hospeda PowerShell

Ahora puede establecer la conexión con cualquier proceso del equipo que tenga Windows PowerShell cargado. Para ello, inicie una sesión interactiva con el proceso, como lo haría con una sesión remota interactiva ejecutando el cmdlet Enter-PSSession:

-   Enter-PSHostProcess
-   Exit-PSHostProcess
