# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="c5409-101">Comunicación remota de PowerShell a través de SSH</span><span class="sxs-lookup"><span data-stu-id="c5409-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="c5409-102">Introducción</span><span class="sxs-lookup"><span data-stu-id="c5409-102">Overview</span></span>

<span data-ttu-id="c5409-103">La comunicación remota de PowerShell suele usar WinRM para la negociación de la conexión y el transporte de datos.</span><span class="sxs-lookup"><span data-stu-id="c5409-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="c5409-104">Se ha elegido SSH para esta implementación de comunicación remota porque ya está disponible para plataformas Linux y Windows, y permite una comunicación remota de PowerShell verdaderamente multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="c5409-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="c5409-105">Pero WinRM también proporciona un sólido modelo de hospedaje para sesiones remotas de PowerShell que esta implementación todavía no permite llevar a cabo.</span><span class="sxs-lookup"><span data-stu-id="c5409-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="c5409-106">Esto significa que la configuración de punto de conexión remota de PowerShell y JEA (Just Enough Administration) aún no se admite en esta implementación.</span><span class="sxs-lookup"><span data-stu-id="c5409-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="c5409-107">La comunicación remota mediante SSH en PowerShell permite una comunicación remota de sesión de PowerShell básica entre los equipos Windows y Linux.</span><span class="sxs-lookup"><span data-stu-id="c5409-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="c5409-108">Para ello, se crea un proceso de hospedaje de PowerShell en el equipo de destino como un subsistema SSH.</span><span class="sxs-lookup"><span data-stu-id="c5409-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="c5409-109">Con el tiempo, se cambiará a un modelo de hospedaje más general similar al funcionamiento de WinRM para admitir la configuración de puntos de conexión y JEA.</span><span class="sxs-lookup"><span data-stu-id="c5409-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="c5409-110">Los cmdlets New-PSSession, Enter-PSSession e Invoke-Command ahora tienen un nuevo conjunto de parámetros que facilita esta nueva conexión de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="c5409-110">The New-PSSession, Enter-PSSession and Invoke-Command cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="c5409-111">Este nuevo conjunto de parámetros probablemente cambiará, pero por ahora permite crear PSSessions SSH con las que se puede interactuar desde la línea de comandos o en las que se pueden invocar comandos y scripts.</span><span class="sxs-lookup"><span data-stu-id="c5409-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="c5409-112">Debe especificar el equipo de destino con el parámetro HostName y proporcionar el nombre de usuario con UserName.</span><span class="sxs-lookup"><span data-stu-id="c5409-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="c5409-113">Al ejecutar los cmdlets de forma interactiva en la línea de comandos de PowerShell, se le pedirá una contraseña.</span><span class="sxs-lookup"><span data-stu-id="c5409-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="c5409-114">También tiene la opción de usar la autenticación de clave SSH y proporcionar una ruta de acceso de archivo de clave privada con el parámetro KeyFilePath.</span><span class="sxs-lookup"><span data-stu-id="c5409-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="c5409-115">Información de configuración general</span><span class="sxs-lookup"><span data-stu-id="c5409-115">General setup information</span></span>

<span data-ttu-id="c5409-116">Es necesario instalar SSH en todos los equipos.</span><span class="sxs-lookup"><span data-stu-id="c5409-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="c5409-117">Debe instalar el cliente (ssh.exe) y el servidor (sshd.exe) para poder experimentar con la comunicación remota hacia y desde los equipos.</span><span class="sxs-lookup"><span data-stu-id="c5409-117">You should install both client (ssh.exe) and server (sshd.exe) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="c5409-118">Para Windows debe instalar [Win32 OpenSSH desde GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="c5409-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="c5409-119">Para Linux debe instalar SSH (incluido el servidor sshd) en función de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="c5409-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="c5409-120">También necesitará una compilación o paquete reciente de PowerShell de GitHub que disponga de la característica de comunicación remota mediante SSH.</span><span class="sxs-lookup"><span data-stu-id="c5409-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="c5409-121">El subsistema SSH se usa para establecer un proceso de PowerShell en el equipo remoto, y el servidor SSH deberá estar configurado para ello.</span><span class="sxs-lookup"><span data-stu-id="c5409-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="c5409-122">Además deberá habilitar la autenticación de contraseña y, opcionalmente, la autenticación basada en claves.</span><span class="sxs-lookup"><span data-stu-id="c5409-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="c5409-123">Configuración en un equipo Windows</span><span class="sxs-lookup"><span data-stu-id="c5409-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="c5409-124">Instalación de la versión más reciente de [PowerShell Core para Windows]</span><span class="sxs-lookup"><span data-stu-id="c5409-124">Install the latest version of [PowerShell Core for Windows]</span></span>
    - <span data-ttu-id="c5409-125">Para saber si tiene compatibilidad con la comunicación remota mediante SSH, examine los conjuntos de parámetros de New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="c5409-125">You can tell if it has the SSH remoting support by looking at the parameter sets for New-PSSession</span></span>

    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```

1. <span data-ttu-id="c5409-126">Instale la compilación más reciente de [Win32 OpenSSH] de GitHub según las instrucciones de [instalación].</span><span class="sxs-lookup"><span data-stu-id="c5409-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
1. <span data-ttu-id="c5409-127">Edite el archivo sshd_config en la ubicación en la que ha instalado Win32 OpenSSH.</span><span class="sxs-lookup"><span data-stu-id="c5409-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
    - <span data-ttu-id="c5409-128">Asegúrese de que la autenticación de contraseña esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="c5409-128">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="c5409-129">Agregue una entrada de subsistema de PowerShell y reemplace `c:/program files/powershell/6.0.0/pwsh.exe` por la ruta de acceso correcta de la versión que quiera usar.</span><span class="sxs-lookup"><span data-stu-id="c5409-129">Add a PowerShell subsystem entry, replace `c:/program files/powershell/6.0.0/pwsh.exe` with the correct path to the version you want to use</span></span>

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="c5409-130">Opcionalmente, habilite la autenticación de clave.</span><span class="sxs-lookup"><span data-stu-id="c5409-130">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="c5409-131">Reinicie el servicio sshd.</span><span class="sxs-lookup"><span data-stu-id="c5409-131">Restart the sshd service</span></span>

    ```powershell
    Restart-Service sshd
    ```

1. <span data-ttu-id="c5409-132">Agregue la ruta de acceso donde está instalado OpenSSH a la variable Path Env.</span><span class="sxs-lookup"><span data-stu-id="c5409-132">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
    - <span data-ttu-id="c5409-133">Debe ser algo similar a `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="c5409-133">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
    - <span data-ttu-id="c5409-134">Esto permite encontrar el archivo ssh.exe.</span><span class="sxs-lookup"><span data-stu-id="c5409-134">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="c5409-135">Configuración en un equipo Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="c5409-135">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="c5409-136">Instale la compilación más reciente de [PowerShell para Linux] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="c5409-136">Install the latest [PowerShell for Linux] build from GitHub</span></span>
1. <span data-ttu-id="c5409-137">Instale [SSH de Ubuntu] según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="c5409-137">Install [Ubuntu SSH] as needed</span></span>

    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```

1. <span data-ttu-id="c5409-138">Edite el archivo sshd_config en la ubicación /etc/ssh.</span><span class="sxs-lookup"><span data-stu-id="c5409-138">Edit the sshd_config file at location /etc/ssh</span></span>
    - <span data-ttu-id="c5409-139">Asegúrese de que la autenticación de contraseña esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="c5409-139">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="c5409-140">Agregue una entrada de subsistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c5409-140">Add a PowerShell subsystem entry</span></span>

    ```
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="c5409-141">Opcionalmente, habilite la autenticación de clave.</span><span class="sxs-lookup"><span data-stu-id="c5409-141">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="c5409-142">Reinicie el servicio sshd.</span><span class="sxs-lookup"><span data-stu-id="c5409-142">Restart the sshd service</span></span>

    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="c5409-143">Configuración en un equipo MacOS</span><span class="sxs-lookup"><span data-stu-id="c5409-143">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="c5409-144">Instale la compilación más reciente de [PowerShell para MacOS].</span><span class="sxs-lookup"><span data-stu-id="c5409-144">Install the latest [PowerShell for MacOS] build</span></span>
    - <span data-ttu-id="c5409-145">Asegúrese de que la comunicación remota mediante SSH está habilitada. Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="c5409-145">Make sure SSH Remoting is enabled by following these steps:</span></span>
      - <span data-ttu-id="c5409-146">Abra `System Preferences`.</span><span class="sxs-lookup"><span data-stu-id="c5409-146">Open `System Preferences`</span></span>
      - <span data-ttu-id="c5409-147">Haga clic en `Sharing`.</span><span class="sxs-lookup"><span data-stu-id="c5409-147">Click on `Sharing`</span></span>
      - <span data-ttu-id="c5409-148">Compruebe que `Remote Login` indique `Remote Login: On`.</span><span class="sxs-lookup"><span data-stu-id="c5409-148">Check `Remote Login` - Should say `Remote Login: On`</span></span>
      - <span data-ttu-id="c5409-149">Permita el acceso a los usuarios adecuados.</span><span class="sxs-lookup"><span data-stu-id="c5409-149">Allow access to appropriate users</span></span>
1. <span data-ttu-id="c5409-150">Edite el archivo `sshd_config` en ubicación `/private/etc/ssh/sshd_config`.</span><span class="sxs-lookup"><span data-stu-id="c5409-150">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
    - <span data-ttu-id="c5409-151">Use su editor favorito.</span><span class="sxs-lookup"><span data-stu-id="c5409-151">Use your favorite editor or</span></span>

    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```

    - <span data-ttu-id="c5409-152">Asegúrese de que la autenticación de contraseña esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="c5409-152">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="c5409-153">Agregue una entrada de subsistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c5409-153">Add a PowerShell subsystem entry</span></span>

    ```
    Subsystem powershell /usr/local/bin/powershell -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="c5409-154">Opcionalmente, habilite la autenticación de clave.</span><span class="sxs-lookup"><span data-stu-id="c5409-154">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="c5409-155">Reinicie el servicio sshd.</span><span class="sxs-lookup"><span data-stu-id="c5409-155">Restart the sshd service</span></span>

    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="c5409-156">Ejemplo de comunicación remota de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c5409-156">PowerShell Remoting Example</span></span>

<span data-ttu-id="c5409-157">La manera más fácil de comprobar si la comunicación remota funciona es probarla en un único equipo.</span><span class="sxs-lookup"><span data-stu-id="c5409-157">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="c5409-158">A continuación crearé una sesión remota en el mismo equipo en un equipo Linux.</span><span class="sxs-lookup"><span data-stu-id="c5409-158">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="c5409-159">Observe que estoy usando cmdlets de PowerShell desde un símbolo del sistema para que aparezcan mensajes de SSH que solicitan comprobar el equipo host y que piden la contraseña.</span><span class="sxs-lookup"><span data-stu-id="c5409-159">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="c5409-160">Puede hacer lo mismo en un equipo Windows para asegurarse de que la comunicación remota funcione en él y, después, establecerla entre equipos mediante el cambio del nombre de host.</span><span class="sxs-lookup"><span data-stu-id="c5409-160">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
PS /home/TestUser> $session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:

PS /home/TestUser> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available

PS /home/TestUser> Enter-PSSession $session

[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession

PS /home/TestUser> Invoke-Command $session -ScriptBlock { Get-Process powershell }

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1


#
# Linux to Windows
#
PS /home/TestUser> Enter-PSSession -HostName WinVM1 -UserName PTestName
PTestName@WinVM1s password:

[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver

Microsoft Windows [Version 10.0.10586]

[WinVM1]: PS C:\Users\PTestName\Documents>

#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.

PS C:\Users\PSUser\Documents> $session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
PS C:\Users\PSUser\Documents> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available


PS C:\Users\PSUser\Documents> Enter-PSSession -Session $session
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

### <a name="known-issues"></a><span data-ttu-id="c5409-161">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="c5409-161">Known Issues</span></span>

1. <span data-ttu-id="c5409-162">El comando sudo no funciona en una sesión remota con un equipo Linux.</span><span class="sxs-lookup"><span data-stu-id="c5409-162">sudo command does not work in remote session to Linux machine.</span></span>

[PowerShell Core para Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[PowerShell Core for Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH
[instalación]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[installation]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[PowerShell para Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[PowerShell for Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[SSH de Ubuntu]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
[PowerShell para MacOS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md#macos-1012
[PowerShell for MacOS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md#macos-1012