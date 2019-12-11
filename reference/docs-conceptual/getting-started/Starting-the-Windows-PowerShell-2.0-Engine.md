---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Iniciar el motor de Windows PowerShell 2.0
ms.openlocfilehash: 824077008d2dcfd707e977d2112f0882d07a8aca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030429"
---
# <a name="starting-the-windows-powershell-20-engine"></a>Iniciar el motor de Windows PowerShell 2.0

En esta sección se explica cómo iniciar el motor de Windows PowerShell 2.0 en Windows 8.1, Windows Server 2012 R2, Windows 8 y Windows Server 2012, que incluyen el motor de Windows PowerShell 2.0, y en otros sistemas que tienen instalado Windows PowerShell 2.0, Windows PowerShell 3.0 y Windows PowerShell 4.0.

Windows PowerShell 4.0 y Windows PowerShell 3.0 están diseñados para ser compatibles con versiones anteriores de Windows PowerShell 2.0. Los cmdlets, proveedores, complementos, módulos y scripts escritos para Windows PowerShell 2.0 se ejecutan sin cambios en Windows PowerShell 4.0 y Windows PowerShell 3.0. Sin embargo, debido a un cambio en la directiva de activación de tiempo de ejecución en Microsoft .NET Framework 4, los programas host de Windows PowerShell escritos para Windows PowerShell 2.0 y compilados con Common Language Runtime (CLR) 2.0 no se pueden ejecutar sin modificaciones en Windows PowerShell 3.0 o Windows PowerShell 4.0, que están compilados con CLR 4.0. El motor de Windows PowerShell 2.0 está destinado a usarse solo cuando un programa host o un script existente no se puede ejecutar porque es incompatible con Windows PowerShell 4.0, Windows PowerShell 3.0 o Microsoft .NET Framework 4. Estos casos deben ser infrecuentes.

Muchos programas que requieren el motor de Windows PowerShell 2.0 lo inician automáticamente. Estas instrucciones se incluyen para las situaciones excepcionales en que necesite iniciar el motor de forma manual.

## <a name="installing-and-enabling-required-programs"></a>Instalar y habilitar los programas requeridos

Antes de iniciar el motor de Windows PowerShell 2.0, habilite el motor de Windows PowerShell 2.0 y Microsoft .NET Framework 3.5 con Service Pack 1. Para obtener instrucciones, consulte [instalar Windows PowerShell](../install/Installing-Windows-PowerShell.md).

Los sistemas con Windows Management Framework 4.0 o Windows Management Framework 3.0 instalado tienen todos los componentes necesarios. No es necesario realizar ninguna otra configuración. Para más información sobre cómo instalar [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) o Windows Management Framework 3.0, vea [Installing Windows PowerShell](../install/Installing-Windows-PowerShell.md) (Instalación de Windows PowerShell).

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Iniciar el motor de Windows PowerShell 2.0

Al iniciar Windows PowerShell, se inicia la versión más reciente de forma predeterminada. Para iniciar Windows PowerShell con el motor de Windows PowerShell 2.0, use el parámetro Version de PowerShell.exe. Puede ejecutar el comando en cualquier símbolo del sistema, incluidos Windows PowerShell y Cmd.exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Iniciar una sesión remota con el motor de Windows PowerShell 2.0

Para ejecutar el motor de Windows PowerShell 2.0 en una sesión remota, cree una configuración de sesión (también conocida como "punto de conexión") en el equipo remoto que carga el motor de Windows PowerShell 2.0. La configuración de sesión se guarda en el equipo remoto y puede usarla cualquier usuario autorizado para crear sesiones que usen el motor de Windows PowerShell 2.0.

Se trata de una tarea avanzada que suele realizarla un administrador del sistema.

El siguiente procedimiento usa el parámetro **PSVersion** del cmdlet [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) para crear una configuración de sesión que use el motor de Windows PowerShell 2.0. También puede usar el parámetro **PowerShellVersion** del cmdlet [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) para crear un archivo de configuración de sesión para una sesión que cargue el motor de Windows PowerShell 2.0 y el parámetro **PSVersion** del cmdlet [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) para cambiar una configuración de sesión para que use el motor de Windows PowerShell 2.0.

Para más información sobre los archivos de configuración de sesión, vea [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Para obtener información sobre las configuraciones de sesión, incluida la de configuración y seguridad,vea [about_Session_Configurations[v4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>Iniciar una sesión de Windows PowerShell 2.0

1. Para crear una configuración de sesión que requiera el motor de Windows PowerShell 2.0, use el parámetro **PSVersion** del cmdlet [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) con un valor de "2.0". Ejecute este comando en el equipo en el "lado servidor" o en el extremo receptor de la conexión.

   El siguiente comando de ejemplo crea la configuración de sesión PS2 en el equipo Server01. Para ejecutar este comando, inicie Windows PowerShell 4.0 o Windows PowerShell 3.0 con la opción **Ejecutar como administrador**.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. Para crear una sesión en el equipo Server01 que use la configuración de sesión PS2, use el parámetro **ConfigurationName** de los cmdlets que crean una sesión remota, como el cmdlet [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f).

   Cuando se inicia una sesión que usa la configuración de sesión, el motor de Windows PowerShell 2.0 se carga automáticamente en la sesión.

   El comando siguiente inicia una sesión en el equipo Server01 que usa la configuración de sesión PS2. El comando guarda la sesión en la variable $s.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Iniciar un trabajo en segundo plano con el motor de Windows PowerShell 2.0

Para iniciar un trabajo en segundo plano con el motor de Windows PowerShell 2.0, use el parámetro **PSVersion** del cmdlet [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442).

El comando siguiente inicia un trabajo en segundo plano con el motor de Windows PowerShell 2.0.

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Para obtener más información sobre los trabajos en segundo plano, vea [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).
