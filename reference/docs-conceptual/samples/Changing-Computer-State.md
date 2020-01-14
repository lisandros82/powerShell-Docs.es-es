---
ms.date: 12/23/2019
keywords: powershell, cmdlet
title: Cambiar el estado del equipo
ms.openlocfilehash: 9278df55ba027134a61c8ed4e89b5b839d460b29
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736920"
---
# <a name="changing-computer-state"></a>Cambiar el estado del equipo

Para restablecer un equipo en PowerShell, use una herramienta de línea de comandos estándar, WMI o una clase CIM.
Aunque use PowerShell solo para ejecutar la herramienta, aprender a cambiar el estado de energía de un equipo en PowerShell le mostrará algunos de los detalles importantes sobre el uso de herramientas externas en PowerShell.

## <a name="locking-a-computer"></a>Bloquear un equipo

La única manera de bloquear un equipo directamente con las herramientas estándar disponibles es llamar a la función **LockWorkstation()** en **user32.dll**:

```powershell
rundll32.exe user32.dll,LockWorkStation
```

Este comando bloquea inmediatamente la estación de trabajo. Usa **rundll32.exe**, que ejecuta archivos DLL de Windows (y guarda sus bibliotecas para usarlas repetidamente), para ejecutar `user32.dll`, una biblioteca de funciones de administración de Windows.

Si se bloquea una estación de trabajo mientras Cambio rápido de usuario está habilitado, como en Windows XP, el equipo muestra la pantalla de inicio de sesión de usuario, en lugar de iniciar el protector de pantalla del usuario actual.

Para cerrar sesiones determinadas en un servidor de Terminal Server, use la herramienta de línea de comandos **tsshutdn.exe**.

## <a name="logging-off-the-current-session"></a>Cerrar la sesión actual

Puede usar varias técnicas diferentes para cerrar una sesión en el sistema local. La manera más sencilla es usar la herramienta de línea de comandos **logoff.exe** de Escritorio remoto/Terminal Services (para obtener más información, en el símbolo del sistema de PowerShell, escriba `logoff /?`). Para cerrar la sesión activa actualmente, escriba `logoff` sin argumentos.

También puede usar la herramienta **shutdown.exe** con su opción de cierre de sesión:

```powershell
shutdown.exe -l
```

Otra opción es usar WMI. La clase **Win32_OperatingSystem** tiene un método **Shutdown**.
Al invocar el método con la marca 0 se inicia el cierre de sesión:

Para más información sobre el método **Shutdown**, consulte [Método Shutdown de la clase Win32_OperatingSystem](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem).

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a>Apagar o reiniciar un equipo

Apagar y reiniciar equipos suelen ser los mismos tipos de tarea. Las herramientas que apagan un equipo generalmente también lo reinician, y viceversa. Hay dos opciones sencillas para reiniciar un equipo desde PowerShell. Use **tsshutdn.exe** o **shutdown.exe** con los argumentos apropiados. Puede obtener información de uso detallada en `tsshutdn.exe /?` o `shutdown.exe /?`.

También puede realizar las operaciones de apagar y reiniciar directamente desde PowerShell.

Para apagar el equipo, use el comando Stop-Computer.

```powershell
Stop-Computer
```

Para reiniciar el sistema operativo, use el comando Restart-Computer.

```powershell
Restart-Computer
```

Para forzar un reinicio inmediato del equipo, use el parámetro -Force.

```powershell
Restart-Computer -Force
```
