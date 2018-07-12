
# <a name="powershell-remoting-over-ssh"></a>Comunicación remota de PowerShell a través de SSH

## <a name="overview"></a>Introducción

La comunicación remota de PowerShell suele usar WinRM para la negociación de la conexión y el transporte de datos.
Se ha elegido SSH para esta implementación de comunicación remota porque ya está disponible para plataformas Linux y Windows, y permite una comunicación remota de PowerShell verdaderamente multiplataforma.
Pero WinRM también proporciona un sólido modelo de hospedaje para sesiones remotas de PowerShell que esta implementación todavía no permite llevar a cabo.
Esto significa que la configuración de punto de conexión remota de PowerShell y JEA (Just Enough Administration) aún no se admite en esta implementación.

La comunicación remota mediante SSH en PowerShell permite una comunicación remota de sesión de PowerShell básica entre los equipos Windows y Linux.
Para ello, se crea un proceso de hospedaje de PowerShell en el equipo de destino como un subsistema SSH.
Con el tiempo, se cambiará a un modelo de hospedaje más general similar al funcionamiento de WinRM para admitir la configuración de puntos de conexión y JEA.

Los cmdlets `New-PSSession`, `Enter-PSSession` y `Invoke-Command` ahora tienen un nuevo conjunto de parámetros que facilita esta nueva conexión de comunicación remota.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Este nuevo conjunto de parámetros probablemente cambiará, pero por ahora permite crear PSSessions SSH con las que se puede interactuar desde la línea de comandos o en las que se pueden invocar comandos y scripts.
Debe especificar el equipo de destino con el parámetro HostName y proporcionar el nombre de usuario con UserName.
Al ejecutar los cmdlets de forma interactiva en la línea de comandos de PowerShell, se le pedirá una contraseña.
También tiene la opción de usar la autenticación de clave SSH y proporcionar una ruta de acceso de archivo de clave privada con el parámetro KeyFilePath.

## <a name="general-setup-information"></a>Información de configuración general

Es necesario instalar SSH en todos los equipos.
Debe instalar el cliente (`ssh.exe`) y el servidor (`sshd.exe`) para poder experimentar con la comunicación remota hacia y desde los equipos.
Para Windows debe instalar [Win32 OpenSSH desde GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
Para Linux debe instalar SSH (incluido el servidor sshd) en función de la plataforma.
También necesitará una compilación o paquete reciente de PowerShell de GitHub que disponga de la característica de comunicación remota mediante SSH.
El subsistema SSH se usa para establecer un proceso de PowerShell en el equipo remoto, y el servidor SSH deberá estar configurado para ello.
Además deberá habilitar la autenticación de contraseña y, opcionalmente, la autenticación basada en claves.

## <a name="setup-on-windows-machine"></a>Configuración en un equipo Windows

1. Instalación de la versión más reciente de [PowerShell Core para Windows]
   - Para saber si tiene compatibilidad con la comunicación remota mediante SSH, examine los conjuntos de parámetros de `New-PSSession`.

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. Instale la compilación más reciente de [Win32 OpenSSH] de GitHub según las instrucciones de [instalación].
3. Edite el archivo sshd_config en la ubicación en la que ha instalado Win32 OpenSSH.
   - Asegúrese de que la autenticación de contraseña esté habilitada.

   ```
   PasswordAuthentication yes
   ```

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    > [!NOTE]
    Hay un error en OpenSSH para Windows que impide que los espacios funcionen en rutas de acceso ejecutables del subsistema.
    Para obtener más información, vea [este problema en GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

    Una solución consiste en crear un vínculo simbólico al directorio de instalación de Powershell que no contenga espacios:

    ```powershell
    mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
    ```

    Después, escríbalo en el subsistema:

    ```
    Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
    ```

   ```
   Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   - Opcionalmente, habilite la autenticación de clave.

   ```
   PubkeyAuthentication yes
   ```

4. Reinicie el servicio sshd.

   ```powershell
   Restart-Service sshd
   ```

5. Agregue la ruta de acceso donde está instalado OpenSSH a la variable Path Env.
   - Debe ser algo similar a `C:\Program Files\OpenSSH\`.
   - Esto permite encontrar el archivo ssh.exe.

## <a name="setup-on-linux-ubuntu-1404-machine"></a>Configuración en un equipo Linux (Ubuntu 14.04)

1. Instale la compilación más reciente de [PowerShell Core para Linux] de GitHub.
2. Instale [SSH de Ubuntu] según sea necesario.

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

## <a name="setup-on-macos-machine"></a>Configuración en un equipo MacOS

1. Instale la compilación más reciente de [PowerShell Core para MacOS].
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

## <a name="powershell-remoting-example"></a>Ejemplo de comunicación remota de PowerShell

La manera más fácil de comprobar si la comunicación remota funciona es probarla en un único equipo.
A continuación crearé una sesión remota en el mismo equipo en un equipo Linux.
Observe que estoy usando cmdlets de PowerShell desde un símbolo del sistema para que aparezcan mensajes de SSH que solicitan comprobar el equipo host y que piden la contraseña.
Puede hacer lo mismo en un equipo Windows para asegurarse de que la comunicación remota funcione en él y, después, establecerla entre equipos mediante el cambio del nombre de host.

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
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available
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

- El comando sudo no funciona en una sesión remota con un equipo Linux.

## <a name="see-also"></a>Véase también

[PowerShell Core para Windows](../setup/installing-powershell-core-on-windows.md#msi)

[PowerShell Core para Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[PowerShell Core para MacOS](../setup/installing-powershell-core-on-macos.md)

[Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)

[Instalación](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[SSH de Ubuntu](https://help.ubuntu.com/lts/serverguide/openssh-server.html)