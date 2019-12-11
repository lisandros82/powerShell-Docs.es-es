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
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="c07af-103">Comunicación remota de PowerShell a través de SSH</span><span class="sxs-lookup"><span data-stu-id="c07af-103">PowerShell remoting over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="c07af-104">Introducción</span><span class="sxs-lookup"><span data-stu-id="c07af-104">Overview</span></span>

<span data-ttu-id="c07af-105">La comunicación remota de PowerShell suele usar WinRM para la negociación de la conexión y el transporte de datos.</span><span class="sxs-lookup"><span data-stu-id="c07af-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="c07af-106">SSH está ahora disponible para plataformas Linux y Windows y permite una verdadera comunicación remota multiplataforma en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c07af-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="c07af-107">WinRM proporciona un modelo de hospedaje sólido para las sesiones remotas de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c07af-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="c07af-108">La comunicación remota basada en SSH no admite actualmente la configuración remota de puntos de conexión y de Just Enough Administration (JEA).</span><span class="sxs-lookup"><span data-stu-id="c07af-108">SSH-based remoting doesn't currently support remote endpoint configuration and Just Enough Administration (JEA).</span></span>

<span data-ttu-id="c07af-109">La comunicación remota mediante SSH permite una comunicación remota de sesión de PowerShell básica entre los equipos Windows y Linux.</span><span class="sxs-lookup"><span data-stu-id="c07af-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux computers.</span></span> <span data-ttu-id="c07af-110">La comunicación remota mediante SSH crea un proceso de host de PowerShell en el equipo de destino como un subsistema SSH.</span><span class="sxs-lookup"><span data-stu-id="c07af-110">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="c07af-111">Finalmente, implementaremos un modelo general de hospedaje, similar a WinRM, para admitir la configuración de puntos de conexión y JEA.</span><span class="sxs-lookup"><span data-stu-id="c07af-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="c07af-112">Los cmdlets `New-PSSession`, `Enter-PSSession` y `Invoke-Command` ahora tienen un nuevo conjunto de parámetros que permite esta nueva conexión de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="c07af-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="c07af-113">Para crear una sesión remota, especifique el equipo de destino con el parámetro `HostName` y proporcione el nombre de usuario con `UserName`.</span><span class="sxs-lookup"><span data-stu-id="c07af-113">To create a remote session, you specify the target computer with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="c07af-114">Al ejecutar los cmdlets de forma interactiva, se le pedirá una contraseña.</span><span class="sxs-lookup"><span data-stu-id="c07af-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="c07af-115">También, puede utilizar la autenticación de clave SSH con un archivo de clave privada con el parámetro `KeyFilePath`.</span><span class="sxs-lookup"><span data-stu-id="c07af-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="c07af-116">Información de configuración general</span><span class="sxs-lookup"><span data-stu-id="c07af-116">General setup information</span></span>

<span data-ttu-id="c07af-117">Deben estar instalados PowerShell 6 o versiones posteriores y SSH en todos los equipos.</span><span class="sxs-lookup"><span data-stu-id="c07af-117">PowerShell 6 or higher, and SSH must be installed on all computers.</span></span> <span data-ttu-id="c07af-118">Instale tanto el cliente (`ssh.exe`) y el servidor (`sshd.exe`) SSH para que pueda comunicarse de forma remota hacia y desde los equipos.</span><span class="sxs-lookup"><span data-stu-id="c07af-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the computers.</span></span> <span data-ttu-id="c07af-119">OpenSSH para Windows ahora está disponible en las compilación 1809 de Windows 10 y en Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="c07af-119">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="c07af-120">Para obtener más información, vea [Administrar Windows con OpenSSH](/windows-server/administration/openssh/openssh_overview).</span><span class="sxs-lookup"><span data-stu-id="c07af-120">For more information, see [Manage Windows with OpenSSH](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="c07af-121">Para Linux, instale SSH, incluido el servidor sshd, más adecuado para su plataforma.</span><span class="sxs-lookup"><span data-stu-id="c07af-121">For Linux, install SSH, including sshd server, that's appropriate for your platform.</span></span> <span data-ttu-id="c07af-122">También necesita instalar PowerShell de GitHub para obtener la característica de comunicación remota mediante SSH.</span><span class="sxs-lookup"><span data-stu-id="c07af-122">You also need to install PowerShell from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="c07af-123">El servidor SSH debe estar configurado para crear un subsistema SSH para hospedar un proceso PowerShell en el equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="c07af-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote computer.</span></span> <span data-ttu-id="c07af-124">Además, debe habilitar la **contraseña** o la autenticación **basada en claves**.</span><span class="sxs-lookup"><span data-stu-id="c07af-124">And, you must enable **password** or **key-based** authentication.</span></span>

## <a name="set-up-on-a-windows-computer"></a><span data-ttu-id="c07af-125">Configuración en un equipo Windows</span><span class="sxs-lookup"><span data-stu-id="c07af-125">Set up on a Windows computer</span></span>

1. <span data-ttu-id="c07af-126">Instale la versión más reciente de PowerShell, vea [Instalación de PowerShell Core en Windows](../../install/installing-powershell-core-on-windows.md#msi).</span><span class="sxs-lookup"><span data-stu-id="c07af-126">Install the latest version of PowerShell, see [Installing PowerShell Core on Windows](../../install/installing-powershell-core-on-windows.md#msi).</span></span>

   <span data-ttu-id="c07af-127">Para confirmar que PowerShell tiene compatibilidad con la comunicación remota SSH, enumere los conjuntos de parámetros `New-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="c07af-127">You can confirm that PowerShell has SSH remoting support by listing the `New-PSSession` parameter sets.</span></span> <span data-ttu-id="c07af-128">Observará que hay nombres de conjuntos de parámetros que comienzan por **SSH**.</span><span class="sxs-lookup"><span data-stu-id="c07af-128">You'll notice there are parameter set names that begin with **SSH**.</span></span> <span data-ttu-id="c07af-129">Esos conjuntos de parámetros incluyen parámetros **SSH**.</span><span class="sxs-lookup"><span data-stu-id="c07af-129">Those parameter sets include **SSH** parameters.</span></span>

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. <span data-ttu-id="c07af-130">Instale la versión más reciente de OpenSSH para Win32.</span><span class="sxs-lookup"><span data-stu-id="c07af-130">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="c07af-131">Para obtener instrucciones de instalación, vea [Introducción a OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span><span class="sxs-lookup"><span data-stu-id="c07af-131">For installation instructions, see [Getting started with OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>

   > [!NOTE]
   > <span data-ttu-id="c07af-132">Si quiere establecer PowerShell como el shell predeterminado para OpenSSH, vea [Configuración de Windows para OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span><span class="sxs-lookup"><span data-stu-id="c07af-132">If you want to set PowerShell as the default shell for OpenSSH, see [Configuring Windows for OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span></span>

1. <span data-ttu-id="c07af-133">Edite el archivo `sshd_config` ubicado en `$env:ProgramData\ssh`.</span><span class="sxs-lookup"><span data-stu-id="c07af-133">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   <span data-ttu-id="c07af-134">Asegúrese de que la autenticación de contraseña esté habilitada:</span><span class="sxs-lookup"><span data-stu-id="c07af-134">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="c07af-135">Cree el subsistema SSH que hospeda un proceso de PowerShell en el equipo remoto:</span><span class="sxs-lookup"><span data-stu-id="c07af-135">Create the SSH subsystem that hosts a PowerShell process on the remote computer:</span></span>

   ```
   Subsystem powershell c:/progra~1/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > <span data-ttu-id="c07af-136">Debe usar el nombre corto de 8.3 para las rutas de acceso de archivo que contengan espacios.</span><span class="sxs-lookup"><span data-stu-id="c07af-136">You must use the 8.3 short name for any file paths that contain spaces.</span></span> <span data-ttu-id="c07af-137">Hay un error en OpenSSH para Windows que impide que los espacios funcionen en rutas de acceso ejecutables del subsistema.</span><span class="sxs-lookup"><span data-stu-id="c07af-137">There's a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="c07af-138">Para obtener más información, vea [este problema de GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="c07af-138">For more information, see this [GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>
   >
   > <span data-ttu-id="c07af-139">Normalmente, el nombre corto de 8.3 de la carpeta `Program Files` en Windows es `Progra~1`.</span><span class="sxs-lookup"><span data-stu-id="c07af-139">The 8.3 short name for the `Program Files` folder in Windows is usually `Progra~1`.</span></span> <span data-ttu-id="c07af-140">No obstante, puede usar el comando siguiente para asegurarse:</span><span class="sxs-lookup"><span data-stu-id="c07af-140">However, you can use the following command to make sure:</span></span>
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

   <span data-ttu-id="c07af-141">Opcionalmente, habilite la autenticación de clave:</span><span class="sxs-lookup"><span data-stu-id="c07af-141">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

   <span data-ttu-id="c07af-142">Para obtener más información, vea [Administración de claves de OpenSSH](/windows-server/administration/openssh/openssh_keymanagement).</span><span class="sxs-lookup"><span data-stu-id="c07af-142">For more information, see [Managing OpenSSH Keys](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

1. <span data-ttu-id="c07af-143">Reinicie el servicio **sshd**.</span><span class="sxs-lookup"><span data-stu-id="c07af-143">Restart the **sshd** service.</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="c07af-144">Agregue la ruta de acceso donde está instalado OpenSSH a la variable de entorno Path.</span><span class="sxs-lookup"><span data-stu-id="c07af-144">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="c07af-145">Por ejemplo, `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="c07af-145">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="c07af-146">Esta entrada permite encontrar el archivo `ssh.exe`.</span><span class="sxs-lookup"><span data-stu-id="c07af-146">This entry allows for the `ssh.exe` to be found.</span></span>

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a><span data-ttu-id="c07af-147">Configuración en un equipo Linux Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c07af-147">Set up on an Ubuntu 16.04 Linux computer</span></span>

1. <span data-ttu-id="c07af-148">Instale la versión más reciente de PowerShell, vea [Instalación de PowerShell Core en Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span><span class="sxs-lookup"><span data-stu-id="c07af-148">Install the latest version of PowerShell, see [Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span></span>
1. <span data-ttu-id="c07af-149">Instale [Servidor OpenSSH en Ubuntu](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span><span class="sxs-lookup"><span data-stu-id="c07af-149">Install [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="c07af-150">Edite el archivo `sshd_config` en ubicación `/etc/ssh`.</span><span class="sxs-lookup"><span data-stu-id="c07af-150">Edit the `sshd_config` file at location `/etc/ssh`.</span></span>

   <span data-ttu-id="c07af-151">Asegúrese de que la autenticación de contraseña esté habilitada:</span><span class="sxs-lookup"><span data-stu-id="c07af-151">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="c07af-152">Agregue una entrada de subsistema de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c07af-152">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   <span data-ttu-id="c07af-153">Opcionalmente, habilite la autenticación de clave:</span><span class="sxs-lookup"><span data-stu-id="c07af-153">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="c07af-154">Reinicie el servicio **sshd**.</span><span class="sxs-lookup"><span data-stu-id="c07af-154">Restart the **sshd** service.</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-a-macos-computer"></a><span data-ttu-id="c07af-155">Configuración en un equipo macOS</span><span class="sxs-lookup"><span data-stu-id="c07af-155">Set up on a macOS computer</span></span>

1. <span data-ttu-id="c07af-156">Instale la versión más reciente de PowerShell, vea [Instalación de PowerShell Core en macOS](../../install/installing-powershell-core-on-macos.md).</span><span class="sxs-lookup"><span data-stu-id="c07af-156">Install the latest version of PowerShell, see [Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md).</span></span>

   <span data-ttu-id="c07af-157">Asegúrese de que la comunicación remota mediante SSH está habilitada. Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="c07af-157">Make sure SSH Remoting is enabled by following these steps:</span></span>

   1. <span data-ttu-id="c07af-158">Abra `System Preferences`.</span><span class="sxs-lookup"><span data-stu-id="c07af-158">Open `System Preferences`.</span></span>
   1. <span data-ttu-id="c07af-159">Haga clic en `Sharing`.</span><span class="sxs-lookup"><span data-stu-id="c07af-159">Click on `Sharing`.</span></span>
   1. <span data-ttu-id="c07af-160">Active `Remote Login` para establecer `Remote Login: On`.</span><span class="sxs-lookup"><span data-stu-id="c07af-160">Check `Remote Login` to set `Remote Login: On`.</span></span>
   1. <span data-ttu-id="c07af-161">Permita el acceso a los usuarios adecuados.</span><span class="sxs-lookup"><span data-stu-id="c07af-161">Allow access to the appropriate users.</span></span>

1. <span data-ttu-id="c07af-162">Edite el archivo `sshd_config` en ubicación `/private/etc/ssh/sshd_config`.</span><span class="sxs-lookup"><span data-stu-id="c07af-162">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`.</span></span>

   <span data-ttu-id="c07af-163">Use un editor de texto, como **nano**:</span><span class="sxs-lookup"><span data-stu-id="c07af-163">Use a text editor such as **nano**:</span></span>

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   <span data-ttu-id="c07af-164">Asegúrese de que la autenticación de contraseña esté habilitada:</span><span class="sxs-lookup"><span data-stu-id="c07af-164">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="c07af-165">Agregue una entrada de subsistema de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c07af-165">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   <span data-ttu-id="c07af-166">Opcionalmente, habilite la autenticación de clave:</span><span class="sxs-lookup"><span data-stu-id="c07af-166">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="c07af-167">Reinicie el servicio **sshd**.</span><span class="sxs-lookup"><span data-stu-id="c07af-167">Restart the **sshd** service.</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="c07af-168">Autenticación</span><span class="sxs-lookup"><span data-stu-id="c07af-168">Authentication</span></span>

<span data-ttu-id="c07af-169">La comunicación remota de PowerShell a través de SSH se basa en el intercambio de autenticación entre el cliente de SSH y el servicio SSH, y no implementa los esquemas de autenticación.</span><span class="sxs-lookup"><span data-stu-id="c07af-169">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and doesn't implement any authentication schemes itself.</span></span> <span data-ttu-id="c07af-170">El resultado es que los esquemas de autenticación configurados, incluida la autenticación multifactor, se controlan mediante SSH y son independientes de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c07af-170">The result is that any configured authentication schemes including multi-factor authentication are handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="c07af-171">Por ejemplo, puede configurar el servicio SSH para que solicite la autenticación con una clave pública y con una contraseña de un solo uso para una mayor seguridad.</span><span class="sxs-lookup"><span data-stu-id="c07af-171">For example, you can configure the SSH service to require public key authentication and a one-time password for added security.</span></span> <span data-ttu-id="c07af-172">La configuración de autenticación multifactor queda fuera del ámbito de este documento.</span><span class="sxs-lookup"><span data-stu-id="c07af-172">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="c07af-173">Consulte la documentación para SSH sobre cómo configurar la autenticación multifactor correctamente y validar su funcionamiento fuera de PowerShell antes de intentar usarlo con comunicación remota de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c07af-173">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="c07af-174">Ejemplo de comunicación remota de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c07af-174">PowerShell remoting example</span></span>

<span data-ttu-id="c07af-175">La manera más fácil de comprobar si la comunicación remota funciona es probarla en un único equipo.</span><span class="sxs-lookup"><span data-stu-id="c07af-175">The easiest way to test remoting is to try it on a single computer.</span></span> <span data-ttu-id="c07af-176">En este ejemplo, vamos a crear una sesión remota en el mismo equipo Linux.</span><span class="sxs-lookup"><span data-stu-id="c07af-176">In this example, we create a remote session back to the same Linux computer.</span></span> <span data-ttu-id="c07af-177">Estamos usando cmdlets de PowerShell de manera interactiva para que aparezcan avisos de SSH que solicitan comprobar el equipo host y que piden una contraseña.</span><span class="sxs-lookup"><span data-stu-id="c07af-177">We're using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="c07af-178">Puede hacer lo mismo en un equipo Windows para garantizar que la comunicación remota funcione.</span><span class="sxs-lookup"><span data-stu-id="c07af-178">You can do the same thing on a Windows computer to ensure remoting is working.</span></span> <span data-ttu-id="c07af-179">Después, establézcala entre equipos mediante el cambio del nombre de host.</span><span class="sxs-lookup"><span data-stu-id="c07af-179">Then, remote between computers by changing the host name.</span></span>

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

### <a name="known-issues"></a><span data-ttu-id="c07af-180">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="c07af-180">Known issues</span></span>

<span data-ttu-id="c07af-181">El comando **sudo** no funciona en una sesión remota con un equipo Linux.</span><span class="sxs-lookup"><span data-stu-id="c07af-181">The **sudo** command doesn't work in a remote session to a Linux computer.</span></span>

## <a name="see-also"></a><span data-ttu-id="c07af-182">Vea también</span><span class="sxs-lookup"><span data-stu-id="c07af-182">See also</span></span>

[<span data-ttu-id="c07af-183">Instalación de PowerShell Core en Linux</span><span class="sxs-lookup"><span data-stu-id="c07af-183">Installing PowerShell Core on Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[<span data-ttu-id="c07af-184">Instalación de PowerShell Core en macOS</span><span class="sxs-lookup"><span data-stu-id="c07af-184">Installing PowerShell Core on macOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="c07af-185">Instalación de PowerShell Core en Windows</span><span class="sxs-lookup"><span data-stu-id="c07af-185">Installing PowerShell Core on Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="c07af-186">Administración de Windows con OpenSSH</span><span class="sxs-lookup"><span data-stu-id="c07af-186">Manage Windows with OpenSSH</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="c07af-187">Administración de claves OpenSSH</span><span class="sxs-lookup"><span data-stu-id="c07af-187">Managing OpenSSH Keys</span></span>](/windows-server/administration/openssh/openssh_keymanagement)

[<span data-ttu-id="c07af-188">SSH de Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c07af-188">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
