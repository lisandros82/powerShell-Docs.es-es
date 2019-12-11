---
title: Comunicación remota de PowerShell a través de SSH
description: Comunicación remota en PowerShell Core con SSH
ms.date: 09/30/2019
ms.openlocfilehash: 0f2fb13010d62dec5b19b373a24a199bff22665d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "73444374"
---
# <a name="powershell-remoting-over-ssh"></a>Comunicación remota de PowerShell a través de SSH

## <a name="overview"></a>Introducción

La comunicación remota de PowerShell suele usar WinRM para la negociación de la conexión y el transporte de datos. SSH está ahora disponible para plataformas Linux y Windows y permite una verdadera comunicación remota multiplataforma en PowerShell.

WinRM proporciona un modelo de hospedaje sólido para las sesiones remotas de PowerShell. La comunicación remota basada en SSH no admite actualmente la configuración remota de puntos de conexión y de Just Enough Administration (JEA).

La comunicación remota mediante SSH permite una comunicación remota de sesión de PowerShell básica entre los equipos Windows y Linux. La comunicación remota mediante SSH crea un proceso de host de PowerShell en el equipo de destino como un subsistema SSH. Finalmente, implementaremos un modelo general de hospedaje, similar a WinRM, para admitir la configuración de puntos de conexión y JEA.

Los cmdlets `New-PSSession`, `Enter-PSSession` y `Invoke-Command` ahora tienen un nuevo conjunto de parámetros que permite esta nueva conexión de comunicación remota.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Para crear una sesión remota, especifique el equipo de destino con el parámetro `HostName` y proporcione el nombre de usuario con `UserName`. Al ejecutar los cmdlets de forma interactiva, se le pedirá una contraseña. También, puede utilizar la autenticación de clave SSH con un archivo de clave privada con el parámetro `KeyFilePath`.

## <a name="general-setup-information"></a>Información de configuración general

Deben estar instalados PowerShell 6 o versiones posteriores y SSH en todos los equipos. Instale tanto el cliente (`ssh.exe`) y el servidor (`sshd.exe`) SSH para que pueda comunicarse de forma remota hacia y desde los equipos. OpenSSH para Windows ahora está disponible en las compilación 1809 de Windows 10 y en Windows Server 2019. Para obtener más información, vea [Administrar Windows con OpenSSH](/windows-server/administration/openssh/openssh_overview). Para Linux, instale SSH, incluido el servidor sshd, más adecuado para su plataforma. También necesita instalar PowerShell de GitHub para obtener la característica de comunicación remota mediante SSH. El servidor SSH debe estar configurado para crear un subsistema SSH para hospedar un proceso PowerShell en el equipo remoto. Además, debe habilitar la **contraseña** o la autenticación **basada en claves**.

## <a name="set-up-on-a-windows-computer"></a>Configuración en un equipo Windows

1. Instale la versión más reciente de PowerShell, vea [Instalación de PowerShell Core en Windows](../../install/installing-powershell-core-on-windows.md#msi).

   Para confirmar que PowerShell tiene compatibilidad con la comunicación remota SSH, enumere los conjuntos de parámetros `New-PSSession`. Observará que hay nombres de conjuntos de parámetros que comienzan por **SSH**. Esos conjuntos de parámetros incluyen parámetros **SSH**.

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. Instale la versión más reciente de OpenSSH para Win32. Para obtener instrucciones de instalación, vea [Introducción a OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).

   > [!NOTE]
   > Si quiere establecer PowerShell como el shell predeterminado para OpenSSH, vea [Configuración de Windows para OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).

1. Edite el archivo `sshd_config` ubicado en `$env:ProgramData\ssh`.

   Asegúrese de que la autenticación de contraseña esté habilitada:

   ```
   PasswordAuthentication yes
   ```

   Cree el subsistema SSH que hospeda un proceso de PowerShell en el equipo remoto:

   ```
   Subsystem powershell c:/progra~1/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > Debe usar el nombre corto de 8.3 para las rutas de acceso de archivo que contengan espacios. Hay un error en OpenSSH para Windows que impide que los espacios funcionen en rutas de acceso ejecutables del subsistema. Para obtener más información, vea [este problema de GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).
   >
   > Normalmente, el nombre corto de 8.3 de la carpeta `Program Files` en Windows es `Progra~1`. No obstante, puede usar el comando siguiente para asegurarse:
   >
   > ```powershell
   > Get-CimInstance Win32_Directory -Filter 'Name="C:\\Program Files"' |
   >   Select-Object EightDotThreeFileName
   > ```
   >
   > ```Output
   > EightDotThreeFileName
   > ---------------------
   > c:\progra~1
   > ```

   Opcionalmente, habilite la autenticación de clave:

   ```
   PubkeyAuthentication yes
   ```

   Para obtener más información, vea [Administración de claves de OpenSSH](/windows-server/administration/openssh/openssh_keymanagement).

1. Reinicie el servicio **sshd**.

   ```powershell
   Restart-Service sshd
   ```

1. Agregue la ruta de acceso donde está instalado OpenSSH a la variable de entorno Path. Por ejemplo, `C:\Program Files\OpenSSH\`. Esta entrada permite encontrar el archivo `ssh.exe`.

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a>Configuración en un equipo Linux Ubuntu 16.04

1. Instale la versión más reciente de PowerShell, vea [Instalación de PowerShell Core en Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).
1. Instale [Servidor OpenSSH en Ubuntu](https://help.ubuntu.com/lts/serverguide/openssh-server.html).

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. Edite el archivo `sshd_config` en ubicación `/etc/ssh`.

   Asegúrese de que la autenticación de contraseña esté habilitada:

   ```
   PasswordAuthentication yes
   ```

   Agregue una entrada de subsistema de PowerShell:

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   Opcionalmente, habilite la autenticación de clave:

   ```
   PubkeyAuthentication yes
   ```

1. Reinicie el servicio **sshd**.

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-a-macos-computer"></a>Configuración en un equipo macOS

1. Instale la versión más reciente de PowerShell, vea [Instalación de PowerShell Core en macOS](../../install/installing-powershell-core-on-macos.md).

   Asegúrese de que la comunicación remota mediante SSH está habilitada. Para ello, siga estos pasos:

   1. Abra `System Preferences`.
   1. Haga clic en `Sharing`.
   1. Active `Remote Login` para establecer `Remote Login: On`.
   1. Permita el acceso a los usuarios adecuados.

1. Edite el archivo `sshd_config` en ubicación `/private/etc/ssh/sshd_config`.

   Use un editor de texto, como **nano**:

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   Asegúrese de que la autenticación de contraseña esté habilitada:

   ```
   PasswordAuthentication yes
   ```

   Agregue una entrada de subsistema de PowerShell:

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   Opcionalmente, habilite la autenticación de clave:

   ```
   PubkeyAuthentication yes
   ```

1. Reinicie el servicio **sshd**.

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Autenticación

La comunicación remota de PowerShell a través de SSH se basa en el intercambio de autenticación entre el cliente de SSH y el servicio SSH, y no implementa los esquemas de autenticación. El resultado es que los esquemas de autenticación configurados, incluida la autenticación multifactor, se controlan mediante SSH y son independientes de PowerShell. Por ejemplo, puede configurar el servicio SSH para que solicite la autenticación con una clave pública y con una contraseña de un solo uso para una mayor seguridad. La configuración de autenticación multifactor queda fuera del ámbito de este documento. Consulte la documentación para SSH sobre cómo configurar la autenticación multifactor correctamente y validar su funcionamiento fuera de PowerShell antes de intentar usarlo con comunicación remota de PowerShell.

## <a name="powershell-remoting-example"></a>Ejemplo de comunicación remota de PowerShell

La manera más fácil de comprobar si la comunicación remota funciona es probarla en un único equipo. En este ejemplo, vamos a crear una sesión remota en el mismo equipo Linux. Estamos usando cmdlets de PowerShell de manera interactiva para que aparezcan avisos de SSH que solicitan comprobar el equipo host y que piden una contraseña. Puede hacer lo mismo en un equipo Windows para garantizar que la comunicación remota funcione. Después, establézcala entre equipos mediante el cambio del nombre de host.

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```Output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```Output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```Output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1
```

```powershell
#
# Linux to Windows
#
Enter-PSSession -HostName WinVM1 -UserName PTestName
```

```Output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```Output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```Output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```Output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```Output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```Output
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="known-issues"></a>Problemas conocidos

El comando **sudo** no funciona en una sesión remota con un equipo Linux.

## <a name="see-also"></a>Vea también

[Instalación de PowerShell Core en Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[Instalación de PowerShell Core en macOS](../../install/installing-powershell-core-on-macos.md)

[Instalación de PowerShell Core en Windows](../../install/installing-powershell-core-on-windows.md#msi)

[Administración de Windows con OpenSSH](/windows-server/administration/openssh/openssh_overview)

[Administración de claves OpenSSH](/windows-server/administration/openssh/openssh_keymanagement)

[SSH de Ubuntu](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
