---
title: Comunicación remota de PowerShell a través de SSH
description: Comunicación remota en PowerShell Core con SSH
ms.date: 08/14/2018
ms.openlocfilehash: 1de034d667aa9a377e5460e7eb474402c690cb42
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133146"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="5d97c-103">Comunicación remota de PowerShell a través de SSH</span><span class="sxs-lookup"><span data-stu-id="5d97c-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="5d97c-104">Introducción</span><span class="sxs-lookup"><span data-stu-id="5d97c-104">Overview</span></span>

<span data-ttu-id="5d97c-105">La comunicación remota de PowerShell suele usar WinRM para la negociación de la conexión y el transporte de datos.</span><span class="sxs-lookup"><span data-stu-id="5d97c-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="5d97c-106">SSH está ahora disponible para plataformas Linux y Windows y permite una verdadera comunicación remota multiplataforma en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d97c-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="5d97c-107">WinRM proporciona un modelo de hospedaje sólido para las sesiones remotas de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d97c-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="5d97c-108">Esta implementación de la comunicación remota basada en SSH no admite actualmente la configuración remota de puntos de conexión y de JEA (Just Enough Administration).</span><span class="sxs-lookup"><span data-stu-id="5d97c-108">which this implementation SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="5d97c-109">La comunicación remota mediante SSH permite una comunicación remota de sesión de PowerShell básica entre los equipos Windows y Linux.</span><span class="sxs-lookup"><span data-stu-id="5d97c-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="5d97c-110">La comunicación remota mediante SSH crea un proceso de host de PowerShell en la máquina de destino como un subsistema SSH.</span><span class="sxs-lookup"><span data-stu-id="5d97c-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="5d97c-111">Finalmente, implementaremos un modelo general de hospedaje, similar a WinRM, para admitir la configuración de puntos de conexión y JEA.</span><span class="sxs-lookup"><span data-stu-id="5d97c-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="5d97c-112">Los cmdlets `New-PSSession`, `Enter-PSSession` y `Invoke-Command` ahora tienen un nuevo conjunto de parámetros que permite esta nueva conexión de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="5d97c-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="5d97c-113">Para crear una sesión remota, especifique la máquina de destino con el parámetro `HostName` y proporcione el nombre de usuario con `UserName`.</span><span class="sxs-lookup"><span data-stu-id="5d97c-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="5d97c-114">Al ejecutar los cmdlets de forma interactiva, se le pedirá una contraseña.</span><span class="sxs-lookup"><span data-stu-id="5d97c-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="5d97c-115">También, puede utilizar la autenticación de clave SSH con un archivo de clave privada con el parámetro `KeyFilePath`.</span><span class="sxs-lookup"><span data-stu-id="5d97c-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="5d97c-116">Información de configuración general</span><span class="sxs-lookup"><span data-stu-id="5d97c-116">General setup information</span></span>

<span data-ttu-id="5d97c-117">Es necesario instalar SSH en todas las máquinas.</span><span class="sxs-lookup"><span data-stu-id="5d97c-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="5d97c-118">Instale tanto el cliente (`ssh.exe`) y el servidor (`sshd.exe`) SSH para que pueda comunicarse de forma remota hacia y desde las máquinas.</span><span class="sxs-lookup"><span data-stu-id="5d97c-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="5d97c-119">Para Windows, instale [Win32 OpenSSH desde GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="5d97c-119">For Windows, install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="5d97c-120">Para Linux, instale SSH (incluido el servidor sshd) en función de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="5d97c-120">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="5d97c-121">También necesita instalar PowerShell Core de GitHub para obtener la característica de comunicación remota mediante SSH.</span><span class="sxs-lookup"><span data-stu-id="5d97c-121">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="5d97c-122">El servidor SSH debe estar configurado para crear un subsistema SSH para hospedar un proceso PowerShell en la máquina remota.</span><span class="sxs-lookup"><span data-stu-id="5d97c-122">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="5d97c-123">También debe configurar la habilitación de la contraseña o la autenticación basada en claves.</span><span class="sxs-lookup"><span data-stu-id="5d97c-123">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="5d97c-124">Configuración en una máquina Windows</span><span class="sxs-lookup"><span data-stu-id="5d97c-124">Set up on Windows Machine</span></span>

1. <span data-ttu-id="5d97c-125">Instalación de la versión más reciente de [PowerShell Core para Windows]</span><span class="sxs-lookup"><span data-stu-id="5d97c-125">Install the latest version of [PowerShell Core for Windows]</span></span>

   - <span data-ttu-id="5d97c-126">Para saber si tiene compatibilidad con la comunicación remota mediante SSH, examine los conjuntos de parámetros de `New-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="5d97c-126">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="5d97c-127">Instale la compilación más reciente de [Win32 OpenSSH] de GitHub según las instrucciones de [instalación].</span><span class="sxs-lookup"><span data-stu-id="5d97c-127">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
3. <span data-ttu-id="5d97c-128">Edite el archivo sshd_config en la ubicación en la que ha instalado Win32 OpenSSH.</span><span class="sxs-lookup"><span data-stu-id="5d97c-128">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>

   - <span data-ttu-id="5d97c-129">Asegúrese de que la autenticación de contraseña esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="5d97c-129">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.4/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="5d97c-130">Hay un error en OpenSSH para Windows que impide que los espacios funcionen en rutas de acceso ejecutables del subsistema.</span><span class="sxs-lookup"><span data-stu-id="5d97c-130">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="5d97c-131">Para más información, consulte [este problema de GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="5d97c-131">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="5d97c-132">Una solución consiste en crear un vínculo simbólico al directorio de instalación de Powershell que no tenga espacios:</span><span class="sxs-lookup"><span data-stu-id="5d97c-132">One solution is to create a symlink to the Powershell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.4"
     ```

     <span data-ttu-id="5d97c-133">Después, escríbalo en el subsistema:</span><span class="sxs-lookup"><span data-stu-id="5d97c-133">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="5d97c-134">Opcionalmente, habilite la autenticación de clave.</span><span class="sxs-lookup"><span data-stu-id="5d97c-134">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="5d97c-135">Reinicie el servicio sshd.</span><span class="sxs-lookup"><span data-stu-id="5d97c-135">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="5d97c-136">Agregue la ruta de acceso donde está instalado OpenSSH a la variable de entorno Path.</span><span class="sxs-lookup"><span data-stu-id="5d97c-136">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="5d97c-137">Por ejemplo, `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="5d97c-137">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="5d97c-138">Esta entrada permite encontrar el archivo ssh.exe.</span><span class="sxs-lookup"><span data-stu-id="5d97c-138">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="5d97c-139">Configuración en una máquina Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="5d97c-139">Set up on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="5d97c-140">Instale la compilación más reciente de [PowerShell Core para Linux] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="5d97c-140">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
2. <span data-ttu-id="5d97c-141">Instale [SSH de Ubuntu] según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="5d97c-141">Install [Ubuntu SSH] as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="5d97c-142">Edite el archivo sshd_config en la ubicación /etc/ssh.</span><span class="sxs-lookup"><span data-stu-id="5d97c-142">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="5d97c-143">Asegúrese de que la autenticación de contraseña esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="5d97c-143">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="5d97c-144">Agregue una entrada de subsistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d97c-144">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="5d97c-145">Opcionalmente, habilite la autenticación de clave.</span><span class="sxs-lookup"><span data-stu-id="5d97c-145">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="5d97c-146">Reinicie el servicio sshd.</span><span class="sxs-lookup"><span data-stu-id="5d97c-146">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="5d97c-147">Configuración en una máquina MacOS</span><span class="sxs-lookup"><span data-stu-id="5d97c-147">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="5d97c-148">Instale la compilación más reciente de [PowerShell Core para MacOS].</span><span class="sxs-lookup"><span data-stu-id="5d97c-148">Install the latest [PowerShell Core for MacOS] build</span></span>

   - <span data-ttu-id="5d97c-149">Asegúrese de que la comunicación remota mediante SSH está habilitada. Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="5d97c-149">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="5d97c-150">Abra `System Preferences`.</span><span class="sxs-lookup"><span data-stu-id="5d97c-150">Open `System Preferences`</span></span>
     - <span data-ttu-id="5d97c-151">Haga clic en `Sharing`.</span><span class="sxs-lookup"><span data-stu-id="5d97c-151">Click on `Sharing`</span></span>
     - <span data-ttu-id="5d97c-152">Compruebe que `Remote Login` indique `Remote Login: On`.</span><span class="sxs-lookup"><span data-stu-id="5d97c-152">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="5d97c-153">Permita el acceso a los usuarios adecuados.</span><span class="sxs-lookup"><span data-stu-id="5d97c-153">Allow access to appropriate users</span></span>

2. <span data-ttu-id="5d97c-154">Edite el archivo `sshd_config` en ubicación `/private/etc/ssh/sshd_config`.</span><span class="sxs-lookup"><span data-stu-id="5d97c-154">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="5d97c-155">Use su editor favorito.</span><span class="sxs-lookup"><span data-stu-id="5d97c-155">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="5d97c-156">Asegúrese de que la autenticación de contraseña esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="5d97c-156">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="5d97c-157">Agregue una entrada de subsistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d97c-157">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="5d97c-158">Opcionalmente, habilite la autenticación de clave.</span><span class="sxs-lookup"><span data-stu-id="5d97c-158">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="5d97c-159">Reinicie el servicio sshd.</span><span class="sxs-lookup"><span data-stu-id="5d97c-159">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="5d97c-160">Ejemplo de comunicación remota de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d97c-160">PowerShell Remoting Example</span></span>

<span data-ttu-id="5d97c-161">La manera más fácil de comprobar si la comunicación remota funciona es probarla en una única máquina.</span><span class="sxs-lookup"><span data-stu-id="5d97c-161">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="5d97c-162">En este ejemplo, vamos a crear una sesión remota en la misma máquina Linux.</span><span class="sxs-lookup"><span data-stu-id="5d97c-162">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="5d97c-163">Estamos usando cmdlets de PowerShell de manera interactiva para que aparezcan avisos de SSH que solicitan comprobar el equipo host y que piden una contraseña.</span><span class="sxs-lookup"><span data-stu-id="5d97c-163">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="5d97c-164">Puede hacer lo mismo en una máquina de Windows para garantizar que la comunicación remota funcione.</span><span class="sxs-lookup"><span data-stu-id="5d97c-164">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="5d97c-165">Después, establézcala entre máquinas mediante el cambio del nombre de host.</span><span class="sxs-lookup"><span data-stu-id="5d97c-165">Then remote between machines by changing the host name.</span></span>

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

### <a name="known-issues"></a><span data-ttu-id="5d97c-166">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="5d97c-166">Known Issues</span></span>

<span data-ttu-id="5d97c-167">El comando sudo no funciona en una sesión remota con una máquina Linux.</span><span class="sxs-lookup"><span data-stu-id="5d97c-167">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d97c-168">Véase también</span><span class="sxs-lookup"><span data-stu-id="5d97c-168">See Also</span></span>

[<span data-ttu-id="5d97c-169">PowerShell Core para Windows</span><span class="sxs-lookup"><span data-stu-id="5d97c-169">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="5d97c-170">PowerShell Core para Linux</span><span class="sxs-lookup"><span data-stu-id="5d97c-170">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="5d97c-171">PowerShell Core para MacOS</span><span class="sxs-lookup"><span data-stu-id="5d97c-171">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="5d97c-172">Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="5d97c-172">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="5d97c-173">Instalación</span><span class="sxs-lookup"><span data-stu-id="5d97c-173">installation</span></span>](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[<span data-ttu-id="5d97c-174">SSH de Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5d97c-174">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
