
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="12ae8-101">Comunicación remota de PowerShell a través de SSH</span><span class="sxs-lookup"><span data-stu-id="12ae8-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="12ae8-102">Introducción</span><span class="sxs-lookup"><span data-stu-id="12ae8-102">Overview</span></span>

<span data-ttu-id="12ae8-103">La comunicación remota de PowerShell suele usar WinRM para la negociación de la conexión y el transporte de datos.</span><span class="sxs-lookup"><span data-stu-id="12ae8-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="12ae8-104">Se ha elegido SSH para esta implementación de comunicación remota porque ya está disponible para plataformas Linux y Windows, y permite una comunicación remota de PowerShell verdaderamente multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="12ae8-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="12ae8-105">Pero WinRM también proporciona un sólido modelo de hospedaje para sesiones remotas de PowerShell que esta implementación todavía no permite llevar a cabo.</span><span class="sxs-lookup"><span data-stu-id="12ae8-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="12ae8-106">Esto significa que la configuración de punto de conexión remota de PowerShell y JEA (Just Enough Administration) aún no se admite en esta implementación.</span><span class="sxs-lookup"><span data-stu-id="12ae8-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="12ae8-107">La comunicación remota mediante SSH en PowerShell permite una comunicación remota de sesión de PowerShell básica entre los equipos Windows y Linux.</span><span class="sxs-lookup"><span data-stu-id="12ae8-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="12ae8-108">Para ello, se crea un proceso de hospedaje de PowerShell en el equipo de destino como un subsistema SSH.</span><span class="sxs-lookup"><span data-stu-id="12ae8-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="12ae8-109">Con el tiempo, se cambiará a un modelo de hospedaje más general similar al funcionamiento de WinRM para admitir la configuración de puntos de conexión y JEA.</span><span class="sxs-lookup"><span data-stu-id="12ae8-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="12ae8-110">Los cmdlets `New-PSSession`, `Enter-PSSession` y `Invoke-Command` ahora tienen un nuevo conjunto de parámetros que facilita esta nueva conexión de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="12ae8-110">The `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="12ae8-111">Este nuevo conjunto de parámetros probablemente cambiará, pero por ahora permite crear PSSessions SSH con las que se puede interactuar desde la línea de comandos o en las que se pueden invocar comandos y scripts.</span><span class="sxs-lookup"><span data-stu-id="12ae8-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="12ae8-112">Debe especificar el equipo de destino con el parámetro HostName y proporcionar el nombre de usuario con UserName.</span><span class="sxs-lookup"><span data-stu-id="12ae8-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="12ae8-113">Al ejecutar los cmdlets de forma interactiva en la línea de comandos de PowerShell, se le pedirá una contraseña.</span><span class="sxs-lookup"><span data-stu-id="12ae8-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="12ae8-114">También tiene la opción de usar la autenticación de clave SSH y proporcionar una ruta de acceso de archivo de clave privada con el parámetro KeyFilePath.</span><span class="sxs-lookup"><span data-stu-id="12ae8-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="12ae8-115">Información de configuración general</span><span class="sxs-lookup"><span data-stu-id="12ae8-115">General setup information</span></span>

<span data-ttu-id="12ae8-116">Es necesario instalar SSH en todos los equipos.</span><span class="sxs-lookup"><span data-stu-id="12ae8-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="12ae8-117">Debe instalar el cliente (`ssh.exe`) y el servidor (`sshd.exe`) para poder experimentar con la comunicación remota hacia y desde los equipos.</span><span class="sxs-lookup"><span data-stu-id="12ae8-117">You should install both client (`ssh.exe`) and server (`sshd.exe`) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="12ae8-118">Para Windows debe instalar [Win32 OpenSSH desde GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="12ae8-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="12ae8-119">Para Linux debe instalar SSH (incluido el servidor sshd) en función de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="12ae8-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="12ae8-120">También necesitará una compilación o paquete reciente de PowerShell de GitHub que disponga de la característica de comunicación remota mediante SSH.</span><span class="sxs-lookup"><span data-stu-id="12ae8-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="12ae8-121">El subsistema SSH se usa para establecer un proceso de PowerShell en el equipo remoto, y el servidor SSH deberá estar configurado para ello.</span><span class="sxs-lookup"><span data-stu-id="12ae8-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="12ae8-122">Además deberá habilitar la autenticación de contraseña y, opcionalmente, la autenticación basada en claves.</span><span class="sxs-lookup"><span data-stu-id="12ae8-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="12ae8-123">Configuración en un equipo Windows</span><span class="sxs-lookup"><span data-stu-id="12ae8-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="12ae8-124">Instalación de la versión más reciente de [PowerShell Core para Windows]</span><span class="sxs-lookup"><span data-stu-id="12ae8-124">Install the latest version of [PowerShell Core for Windows]</span></span>
   - <span data-ttu-id="12ae8-125">Para saber si tiene compatibilidad con la comunicación remota mediante SSH, examine los conjuntos de parámetros de `New-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="12ae8-125">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

1. <span data-ttu-id="12ae8-126">Instale la compilación más reciente de [Win32 OpenSSH] de GitHub según las instrucciones de [instalación].</span><span class="sxs-lookup"><span data-stu-id="12ae8-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
1. <span data-ttu-id="12ae8-127">Edite el archivo sshd_config en la ubicación en la que ha instalado Win32 OpenSSH.</span><span class="sxs-lookup"><span data-stu-id="12ae8-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
   - <span data-ttu-id="12ae8-128">Asegúrese de que la autenticación de contraseña esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="12ae8-128">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    > [!NOTE]
    > <span data-ttu-id="12ae8-129">Hay un error en OpenSSH para Windows que impide que los espacios funcionen en rutas de acceso ejecutables del subsistema.</span><span class="sxs-lookup"><span data-stu-id="12ae8-129">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span>
    > <span data-ttu-id="12ae8-130">Para obtener más información, vea [este problema en GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="12ae8-130">See [this issue on GitHub for more information](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

    <span data-ttu-id="12ae8-131">Una solución consiste en crear un vínculo simbólico al directorio de instalación de Powershell que no contenga espacios:</span><span class="sxs-lookup"><span data-stu-id="12ae8-131">One solution is to create a symlink to the Powershell installation directory that does not contain spaces:</span></span>

    ```powershell
    mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
    ```

    <span data-ttu-id="12ae8-132">Después, escríbalo en el subsistema:</span><span class="sxs-lookup"><span data-stu-id="12ae8-132">and then enter it in the subsystem:</span></span>

    ```
    Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
    ```

   ```
   Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="12ae8-133">Opcionalmente, habilite la autenticación de clave.</span><span class="sxs-lookup"><span data-stu-id="12ae8-133">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="12ae8-134">Reinicie el servicio sshd.</span><span class="sxs-lookup"><span data-stu-id="12ae8-134">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="12ae8-135">Agregue la ruta de acceso donde está instalado OpenSSH a la variable Path Env.</span><span class="sxs-lookup"><span data-stu-id="12ae8-135">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
   - <span data-ttu-id="12ae8-136">Debe ser algo similar a `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="12ae8-136">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
   - <span data-ttu-id="12ae8-137">Esto permite encontrar el archivo ssh.exe.</span><span class="sxs-lookup"><span data-stu-id="12ae8-137">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="12ae8-138">Configuración en un equipo Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="12ae8-138">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="12ae8-139">Instale la compilación más reciente de [PowerShell Core para Linux] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="12ae8-139">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
1. <span data-ttu-id="12ae8-140">Instale [SSH de Ubuntu] según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="12ae8-140">Install [Ubuntu SSH] as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="12ae8-141">Edite el archivo sshd_config en la ubicación /etc/ssh.</span><span class="sxs-lookup"><span data-stu-id="12ae8-141">Edit the sshd_config file at location /etc/ssh</span></span>
   - <span data-ttu-id="12ae8-142">Asegúrese de que la autenticación de contraseña esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="12ae8-142">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="12ae8-143">Agregue una entrada de subsistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12ae8-143">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="12ae8-144">Opcionalmente, habilite la autenticación de clave.</span><span class="sxs-lookup"><span data-stu-id="12ae8-144">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="12ae8-145">Reinicie el servicio sshd.</span><span class="sxs-lookup"><span data-stu-id="12ae8-145">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="12ae8-146">Configuración en un equipo MacOS</span><span class="sxs-lookup"><span data-stu-id="12ae8-146">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="12ae8-147">Instale la compilación más reciente de [PowerShell Core para MacOS].</span><span class="sxs-lookup"><span data-stu-id="12ae8-147">Install the latest [PowerShell Core for MacOS] build</span></span>
   - <span data-ttu-id="12ae8-148">Asegúrese de que la comunicación remota mediante SSH está habilitada. Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="12ae8-148">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="12ae8-149">Abra `System Preferences`.</span><span class="sxs-lookup"><span data-stu-id="12ae8-149">Open `System Preferences`</span></span>
     - <span data-ttu-id="12ae8-150">Haga clic en `Sharing`.</span><span class="sxs-lookup"><span data-stu-id="12ae8-150">Click on `Sharing`</span></span>
     - <span data-ttu-id="12ae8-151">Compruebe que `Remote Login` indique `Remote Login: On`.</span><span class="sxs-lookup"><span data-stu-id="12ae8-151">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="12ae8-152">Permita el acceso a los usuarios adecuados.</span><span class="sxs-lookup"><span data-stu-id="12ae8-152">Allow access to appropriate users</span></span>
1. <span data-ttu-id="12ae8-153">Edite el archivo `sshd_config` en ubicación `/private/etc/ssh/sshd_config`.</span><span class="sxs-lookup"><span data-stu-id="12ae8-153">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
   - <span data-ttu-id="12ae8-154">Use su editor favorito.</span><span class="sxs-lookup"><span data-stu-id="12ae8-154">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="12ae8-155">Asegúrese de que la autenticación de contraseña esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="12ae8-155">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="12ae8-156">Agregue una entrada de subsistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12ae8-156">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="12ae8-157">Opcionalmente, habilite la autenticación de clave.</span><span class="sxs-lookup"><span data-stu-id="12ae8-157">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

1. <span data-ttu-id="12ae8-158">Reinicie el servicio sshd.</span><span class="sxs-lookup"><span data-stu-id="12ae8-158">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="12ae8-159">Ejemplo de comunicación remota de PowerShell</span><span class="sxs-lookup"><span data-stu-id="12ae8-159">PowerShell Remoting Example</span></span>

<span data-ttu-id="12ae8-160">La manera más fácil de comprobar si la comunicación remota funciona es probarla en un único equipo.</span><span class="sxs-lookup"><span data-stu-id="12ae8-160">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="12ae8-161">A continuación crearé una sesión remota en el mismo equipo en un equipo Linux.</span><span class="sxs-lookup"><span data-stu-id="12ae8-161">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="12ae8-162">Observe que estoy usando cmdlets de PowerShell desde un símbolo del sistema para que aparezcan mensajes de SSH que solicitan comprobar el equipo host y que piden la contraseña.</span><span class="sxs-lookup"><span data-stu-id="12ae8-162">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="12ae8-163">Puede hacer lo mismo en un equipo Windows para asegurarse de que la comunicación remota funcione en él y, después, establecerla entre equipos mediante el cambio del nombre de host.</span><span class="sxs-lookup"><span data-stu-id="12ae8-163">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

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

### <a name="known-issues"></a><span data-ttu-id="12ae8-164">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="12ae8-164">Known Issues</span></span>

- <span data-ttu-id="12ae8-165">El comando sudo no funciona en una sesión remota con un equipo Linux.</span><span class="sxs-lookup"><span data-stu-id="12ae8-165">sudo command does not work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="12ae8-166">Véase también</span><span class="sxs-lookup"><span data-stu-id="12ae8-166">See Also</span></span>

[<span data-ttu-id="12ae8-167">PowerShell Core para Windows</span><span class="sxs-lookup"><span data-stu-id="12ae8-167">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="12ae8-168">PowerShell Core para Linux</span><span class="sxs-lookup"><span data-stu-id="12ae8-168">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="12ae8-169">PowerShell Core para MacOS</span><span class="sxs-lookup"><span data-stu-id="12ae8-169">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="12ae8-170">Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="12ae8-170">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="12ae8-171">Instalación</span><span class="sxs-lookup"><span data-stu-id="12ae8-171">installation</span></span>](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[<span data-ttu-id="12ae8-172">SSH de Ubuntu</span><span class="sxs-lookup"><span data-stu-id="12ae8-172">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)