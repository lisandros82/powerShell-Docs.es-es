---
title: Comunicación remota de WS-Management (WSMan) en PowerShell Core
description: Comunicación remota en PowerShell Core con WSMan
ms.date: 08/06/2018
ms.openlocfilehash: e5f00128bc8ebc1b432cc77a5896a9e09d684109
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "62058886"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a>Comunicación remota de WS-Management (WSMan) en PowerShell Core

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instrucciones para crear un punto de conexión de comunicación remota

El paquete de PowerShell Core para Windows incluye un complemento WinRM (`pwrshplugin.dll`) y un script de instalación (`Install-PowerShellRemoting.ps1`) en `$PSHome`.
Estos archivos permiten que PowerShell acepte conexiones remotas entrantes de PowerShell cuando se especifica su punto de conexión.

### <a name="motivation"></a>Motivaciones

Una instalación de PowerShell puede establecer sesiones de PowerShell en equipos remotos a través `New-PSSession` y `Enter-PSSession`.
Para permitirle aceptar conexiones remotas entrantes de PowerShell, el usuario debe crear un punto de conexión de comunicación remota de WinRM.
Se trata de un escenario de participación explícito, en el que el usuario ejecuta Install-PowerShellRemoting.ps1 para crear el punto de conexión de WinRM.
El script de instalación es una solución a corto plazo, hasta que agreguemos funcionalidad adicional a `Enable-PSRemoting` para realizar la misma acción.
Para más información, vea problema [#1193](https://github.com/PowerShell/PowerShell/issues/1193).

### <a name="script-actions"></a>Acciones de script

El script

1. Crea un directorio para el complemento en `$env:windir\System32\PowerShell`
1. Copia pwrshplugin.dll en esa ubicación.
1. Genera un archivo de configuración.
1. Registra el complemento con WinRM.

### <a name="registration"></a>Registro

El script debe ejecutarse en una sesión de PowerShell de nivel de administrador y se ejecuta en dos modos.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Ejecutado por la instancia de PowerShell que registrará

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Ejecutado por otra instancia de PowerShell en nombre de la instancia que registrará

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

Por ejemplo:

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

**NOTA**: El script de registro de comunicación remota reiniciará WinRM, por lo que todas las sesiones PSRP existentes se cerrarán inmediatamente tras ejecutar el script. Si se ejecuta durante una sesión remota, la conexión finalizará.

## <a name="how-to-connect-to-the-new-endpoint"></a>Cómo conectarse al nuevo punto de conexión

Cree una sesión de PowerShell en el nuevo punto de conexión de PowerShell. Para ello, especifique `-ConfigurationName "some endpoint name"`. Para conectarse a la instancia de PowerShell en el ejemplo anterior, use una de las opciones siguientes:

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

Tenga en cuenta que las invocaciones `New-PSSession` y `Enter-PSSession` que no especifiquen `-ConfigurationName` tendrán como destino el punto de conexión predeterminado de PowerShell, `microsoft.powershell`.