---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Cambiar el estado del equipo
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: c659ad54325b0f7305f882e1cb9607062abad6a4
ms.sourcegitcommit: 2ffb9fa92129c2001379ca2c17646466721f7165
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251524"
---
# <a name="changing-computer-state"></a>Cambiar el estado del equipo

Para restablecer un equipo en Windows PowerShell, use una herramienta de línea de comandos estándar o una clase WMI. Aunque use Windows PowerShell solo para ejecutar la herramienta, aprender a cambiar el estado de energía de un equipo en Windows PowerShell le mostrará algunos de los detalles importantes sobre el uso de herramientas externas en Windows PowerShell.

### <a name="locking-a-computer"></a>Bloquear un equipo

La única manera de bloquear un equipo directamente con las herramientas estándar disponibles es llamar a la función **LockWorkstation()** en **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Este comando bloquea inmediatamente la estación de trabajo. Usa *rundll32.exe*, que ejecuta archivos DLL de Windows (y guarda sus bibliotecas para usarlas repetidamente), para ejecutar el archivo user32.dll, una biblioteca de funciones de administración de Windows.

Si se bloquea una estación de trabajo mientras Cambio rápido de usuario está habilitado, como en Windows XP, el equipo muestra la pantalla de inicio de sesión de usuario, en lugar de iniciar el protector de pantalla del usuario actual.

Para cerrar sesiones determinadas en un servidor de Terminal Server, use la herramienta de línea de comandos **tsshutdn.exe**.

### <a name="logging-off-the-current-session"></a>Cerrar la sesión actual

Puede usar varias técnicas diferentes para cerrar una sesión en el sistema local. La manera más sencilla es usar la herramienta de línea de comandos **logoff.exe** de Escritorio remoto/Terminal Services (para obtener más información, en el símbolo del sistema de Windows PowerShell, escriba **logoff /?**). Para cerrar la sesión activa actualmente, escriba **logoff** sin argumentos.

También puede usar la herramienta **shutdown.exe** con su opción de cierre de sesión:

```
shutdown.exe -l
```

Una tercera opción es usar WMI. La clase Win32_OperatingSystem tiene un método Win32Shutdown. Al invocar el método con la marca 0 se inicia el cierre de sesión:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Para obtener más información y otras características del método Win32Shutdown, vea "Win32Shutdown Method of the Win32_OperatingSystem Class" (Método Win32Shutdown de la clase Win32_OperatingSystem) en MSDN.

### <a name="shutting-down-or-restarting-a-computer"></a>Apagar o reiniciar un equipo

Apagar y reiniciar equipos suelen ser los mismos tipos de tarea. Las herramientas que apagan un equipo generalmente también lo reinician, y viceversa. Hay dos opciones sencillas para reiniciar un equipo desde Windows PowerShell. Use Tsshutdn.exe o Shutdown.exe con los argumentos apropiados. Puede obtener información de uso detallada en **tsshutdn.exe /?** o **shutdown.exe /?**.

También puede realizar las operaciones de apagar y reiniciar directamente desde Windows PowerShell.

Para apagar el equipo, use el comando Restart-Computer.

```powershell
stop-computer
```

Para reiniciar el sistema operativo, use el comando Restart-Computer.

```powershell
restart-computer
```
