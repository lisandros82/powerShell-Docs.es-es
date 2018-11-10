---
title: Comunicación remota de PowerShell a través de SSH
description: Comunicación remota en PowerShell Core con SSH
ms.date: 08/14/2018
ms.openlocfilehash: 842e67e96661bca8be54aab33cbc11aa23dbd1c0
ms.sourcegitcommit: 47becf2823ece251a7264db2387bb503cf3abaa9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2018
ms.locfileid: "49451072"
---
# <a name="powershell-remoting-over-ssh"></a>Comunicación remota de PowerShell a través de SSH

## <a name="overview"></a>Introducción

La comunicación remota de PowerShell suele usar WinRM para la negociación de la conexión y el transporte de datos. SSH está ahora disponible para plataformas Linux y Windows y permite una verdadera comunicación remota multiplataforma en PowerShell.

WinRM proporciona un modelo de hospedaje sólido para las sesiones remotas de PowerShell. La comunicación remota basada en SSH no admite actualmente la configuración remota de puntos de conexión y de JEA (Just Enough Administration).

La comunicación remota mediante SSH permite una comunicación remota de sesión de PowerShell básica entre los equipos Windows y Linux. La comunicación remota mediante SSH crea un proceso de host de PowerShell en la máquina de destino como un subsistema SSH.
Finalmente, implementaremos un modelo general de hospedaje, similar a WinRM, para admitir la configuración de puntos de conexión y JEA.

Los cmdlets `New-PSSession`, `Enter-PSSession` y `Invoke-Command` ahora tienen un nuevo conjunto de parámetros que permite esta nueva conexión de comunicación remota.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Para crear una sesión remota, especifique la máquina de destino con el parámetro `HostName` y proporcione el nombre de usuario con `UserName`. Al ejecutar los cmdlets de forma interactiva, se le pedirá una contraseña. También, puede utilizar la autenticación de clave SSH con un archivo de clave privada con el parámetro `KeyFilePath`.

## <a name="general-setup-information"></a>Información de configuración general

Es necesario instalar SSH en todas las máquinas. Instale tanto el cliente (`ssh.exe`) y el servidor (`sshd.exe`) SSH para que pueda comunicarse de forma remota hacia y desde las máquinas. Para Windows, instale [Win32 OpenSSH desde GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
Para Linux, instale SSH (incluido el servidor sshd) en función de la plataforma. También necesita instalar PowerShell Core de GitHub para obtener la característica de comunicación remota mediante SSH. El servidor SSH debe estar configurado para crear un subsistema SSH para hospedar un proceso PowerShell en la máquina remota. También debe configurar la habilitación de la contraseña o la autenticación basada en claves.

## <a name="set-up-on-windows-machine"></a>Configuración en una máquina Windows

1. Instalación de la versión más reciente de [PowerShell Core para Windows](../setup/installing-powershell-core-on-windows.md#msi)

   - Para saber si tiene compatibilidad con la comunicación remota mediante SSH, examine los conjuntos de parámetros de `New-PSSession`.

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. Instale la compilación más reciente de [Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases) de GitHub según las instrucciones de [instalación](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH).
3. Edite el archivo sshd_config ubicado en `%ProgramData%\ssh`.

   - Asegúrese de que la autenticación de contraseña esté habilitada.

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > Hay un error en OpenSSH para Windows que impide que los espacios funcionen en rutas de acceso ejecutables del subsistema. Para más información, consulte [este problema de GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     Una solución consiste en crear un vínculo simbólico al directorio de instalación de Powershell que no tenga espacios:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     Después, escríbalo en el subsistema:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - Opcionalmente, habilite la autenticación de clave.

     ```
     PubkeyAuthentication yes
     ```

4. Reinicie el servicio sshd.

   ```powershell
   Restart-Service sshd
   ```

5. Agregue la ruta de acceso donde está instalado OpenSSH a la variable de entorno Path. Por ejemplo, `C:\Program Files\OpenSSH\`. Esta entrada permite encontrar el archivo ssh.exe.

## <a name="set-up-on-linux-ubuntu-1404-machine"></a>Configuración en una máquina Linux (Ubuntu 14.04)

1. Instale la compilación más reciente de [PowerShell Core para Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404) de GitHub.
2. Instale [SSH de Ubuntu](https://help.ubuntu.com/lts/serverguide/openssh-server.html) según sea necesario.

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. Edite el archivo sshd_config en la ubicación /etc/ssh.

   - Asegúrese de que la autenticación de contraseña esté habilitada.

   ```
   PasswordAuthentication yes
   ```

   - Agregue una entrada de subsistema de PowerShell.

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - Opcionalmente, habilite la autenticación de clave.

   ```
   PubkeyAuthentication yes
   ```

4. Reinicie el servicio sshd.

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a>Configuración en una máquina MacOS

1. Instale la compilación más reciente de [PowerShell Core para MacOS](../setup/installing-powershell-core-on-macos.md).

   - Asegúrese de que la comunicación remota mediante SSH está habilitada. Para ello, siga estos pasos:
     - Abra `System Preferences`.
     - Haga clic en `Sharing`.
     - Compruebe que `Remote Login` indique `Remote Login: On`.
     - Permita el acceso a los usuarios adecuados.

2. Edite el archivo `sshd_config` en ubicación `/private/etc/ssh/sshd_config`.

   - Use su editor favorito.

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - Asegúrese de que la autenticación de contraseña esté habilitada.

     ```
     PasswordAuthentication yes
     ```

   - Agregue una entrada de subsistema de PowerShell.

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - Opcionalmente, habilite la autenticación de clave.

     ```
     PubkeyAuthentication yes
     ```

3. Reinicie el servicio sshd.

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Autenticación

La comunicación remota de PowerShell a través de SSH se basa en el intercambio de autenticación entre el cliente de SSH y el servicio SSH, y no implementa los esquemas de autenticación.
Esto significa que los esquemas de autenticación configurados, incluida la autenticación multifactor, se controlan mediante SSH y son independientes de PowerShell.
Por ejemplo, puede configurar el servicio SSH para que solicite la autenticación con una clave pública y con una contraseña de un solo uso para una mayor seguridad.
La configuración de autenticación multifactor queda fuera del ámbito de este documento.
Consulte la documentación para SSH sobre cómo configurar la autenticación multifactor correctamente y validar su funcionamiento fuera de PowerShell antes de intentar usarlo con comunicación remota de PowerShell.

## <a name="powershell-remoting-example"></a>Ejemplo de comunicación remota de PowerShell

La manera más fácil de comprobar si la comunicación remota funciona es probarla en una única máquina. En este ejemplo, vamos a crear una sesión remota en la misma máquina Linux. Estamos usando cmdlets de PowerShell de manera interactiva para que aparezcan avisos de SSH que solicitan comprobar el equipo host y que piden una contraseña. Puede hacer lo mismo en una máquina de Windows para garantizar que la comunicación remota funcione. Después, establézcala entre máquinas mediante el cambio del nombre de host.

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```output
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

```output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```output
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

El comando sudo no funciona en una sesión remota con una máquina Linux.

## <a name="see-also"></a>Véase también

[PowerShell Core para Windows](../setup/installing-powershell-core-on-windows.md#msi)

[PowerShell Core para Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[PowerShell Core para MacOS](../setup/installing-powershell-core-on-macos.md)

[Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)

[SSH de Ubuntu](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
