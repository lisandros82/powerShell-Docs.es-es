---
title: Instalación de PowerShell Core en Windows
description: Información sobre cómo instalar PowerShell Core en Windows
ms.date: 08/06/2018
ms.openlocfilehash: 910ee5a653fc1703bfddaf6367225f3b654d600f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058036"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="5148c-103">Instalación de PowerShell Core en Windows</span><span class="sxs-lookup"><span data-stu-id="5148c-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="5148c-104">Hay varias formas de instalar PowerShell Core en Windows.</span><span class="sxs-lookup"><span data-stu-id="5148c-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5148c-105">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="5148c-105">Prerequisites</span></span>

<span data-ttu-id="5148c-106">Para habilitar la comunicación remota de PowerShell a través de WSMan, deben cumplirse los siguientes requisitos previos:</span><span class="sxs-lookup"><span data-stu-id="5148c-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="5148c-107">Instale el [entorno de ejecución de C universal](https://www.microsoft.com/download/details.aspx?id=50410) en las versiones de Windows anteriores a Windows 10.</span><span class="sxs-lookup"><span data-stu-id="5148c-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="5148c-108">Está disponible mediante descarga directa o Windows Update.</span><span class="sxs-lookup"><span data-stu-id="5148c-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="5148c-109">Los sistemas admitidos a los que se hayan aplicado todas las revisiones (incluidos los paquetes opcionales) ya lo tienen instalado.</span><span class="sxs-lookup"><span data-stu-id="5148c-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="5148c-110">Instale Windows Management Framework (WMF) 4.0 o una versión más reciente en Windows 7 y Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="5148c-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="5148c-111"><a id="msi" />Instalación del paquete MSI</span><span class="sxs-lookup"><span data-stu-id="5148c-111"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="5148c-112">Para instalar PowerShell en un cliente de Windows o Windows Server (funciona en Windows 7 SP1, Server 2008 R2 y versiones posteriores), descargue el paquete MSI desde nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="5148c-112">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span> <span data-ttu-id="5148c-113">Desplácese hacia abajo hasta la sección **Recursos** de la versión que quiere instalar.</span><span class="sxs-lookup"><span data-stu-id="5148c-113">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="5148c-114">Es posible que la sección Recursos esté contraída, por lo que tendría que hacer clic para expandirla.</span><span class="sxs-lookup"><span data-stu-id="5148c-114">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="5148c-115">El archivo MSI tiene este aspecto: `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="5148c-115">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="5148c-116">Una vez descargado, haga doble clic en el instalador y siga las indicaciones.</span><span class="sxs-lookup"><span data-stu-id="5148c-116">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="5148c-117">El instalador crea un acceso directo en el menú de inicio de Windows.</span><span class="sxs-lookup"><span data-stu-id="5148c-117">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="5148c-118">De forma predeterminada, el paquete se instala en `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="5148c-118">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="5148c-119">Puede iniciar PowerShell mediante el menú Inicio o `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="5148c-119">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="5148c-120">Instalación administrativa desde la línea de comandos</span><span class="sxs-lookup"><span data-stu-id="5148c-120">Administrative install from the command line</span></span>

<span data-ttu-id="5148c-121">Los paquetes MSI se pueden instalar desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="5148c-121">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="5148c-122">Esto permite a los administradores implementar los paquetes sin interacción del usuario.</span><span class="sxs-lookup"><span data-stu-id="5148c-122">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="5148c-123">El paquete MSI para PowerShell incluye las siguientes propiedades para controlar las opciones de instalación:</span><span class="sxs-lookup"><span data-stu-id="5148c-123">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="5148c-124">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL**: esta propiedad controla la opción para agregar el elemento **Open PowerShell** al menú contextual en el Explorador de Windows.</span><span class="sxs-lookup"><span data-stu-id="5148c-124">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="5148c-125">**ENABLE_PSREMOTING**: esta propiedad controla la opción para habilitar la comunicación remota de PowerShell durante la instalación.</span><span class="sxs-lookup"><span data-stu-id="5148c-125">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="5148c-126">**REGISTER_MANIFEST**: esta propiedad controla la opción para registrar el manifiesto de registro de eventos de Windows.</span><span class="sxs-lookup"><span data-stu-id="5148c-126">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="5148c-127">En los ejemplos siguientes se muestra cómo instalar PowerShell Core con todas las opciones de instalación habilitadas de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="5148c-127">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="5148c-128">Para obtener una lista completa de opciones de línea de comandos de Msiexec.exe, consulte [Opciones de línea de comandos](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="5148c-128">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="5148c-129"><a id="zip" />Instalación del paquete ZIP</span><span class="sxs-lookup"><span data-stu-id="5148c-129"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="5148c-130">Se proporcionan archivos binarios ZIP de PowerShell para permitir escenarios de implementación avanzada.</span><span class="sxs-lookup"><span data-stu-id="5148c-130">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="5148c-131">Tenga en cuenta que, cuando use el archivo ZIP, no aparecerá la comprobación de requisitos previos como en el caso del paquete MSI.</span><span class="sxs-lookup"><span data-stu-id="5148c-131">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="5148c-132">Para que la comunicación remota en WSMan funcione correctamente, asegúrese de que se han cumplido los [requisitos previos](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="5148c-132">For remoting over WSMan to work properly,, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="5148c-133">Implementación en Windows IoT</span><span class="sxs-lookup"><span data-stu-id="5148c-133">Deploying on Windows IoT</span></span>

<span data-ttu-id="5148c-134">Windows IoT ya incluye Windows PowerShell, que se usará para implementar PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="5148c-134">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="5148c-135">Cree `PSSession` en el dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="5148c-135">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="5148c-136">Copie el paquete ZIP en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5148c-136">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="5148c-137">Conéctese al dispositivo y expanda el archivo.</span><span class="sxs-lookup"><span data-stu-id="5148c-137">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="5148c-138">Configure el acceso remoto a PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="5148c-138">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="5148c-139">Conéctese al punto de conexión de PowerShell Core 6 en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5148c-139">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="5148c-140">Desarrollo en Nano Server</span><span class="sxs-lookup"><span data-stu-id="5148c-140">Deploying on Nano Server</span></span>

<span data-ttu-id="5148c-141">En estas instrucciones se da por supuesto que ya se ejecuta una versión de PowerShell en la imagen de Nano Server y que se ha generado mediante [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="5148c-141">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="5148c-142">Nano Server es un sistema operativo "sin periféricos".</span><span class="sxs-lookup"><span data-stu-id="5148c-142">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="5148c-143">Los archivos binarios principales se pueden implementar mediante dos métodos diferentes.</span><span class="sxs-lookup"><span data-stu-id="5148c-143">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="5148c-144">Sin conexión: monte el VHD de Nano Server y descomprima el contenido del archivo ZIP en la ubicación seleccionada de la imagen montada.</span><span class="sxs-lookup"><span data-stu-id="5148c-144">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="5148c-145">En línea: transfiera el archivo ZIP a través de una sesión de PowerShell y descomprímalo en la ubicación seleccionada.</span><span class="sxs-lookup"><span data-stu-id="5148c-145">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="5148c-146">En ambos casos, necesitará el paquete comercial ZIP de Windows 10 x64 y deberá ejecutar los comandos en una instancia de PowerShell de "Administrador".</span><span class="sxs-lookup"><span data-stu-id="5148c-146">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="5148c-147">Implementación sin conexión de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5148c-147">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="5148c-148">Use su utilidad ZIP favorita para descomprimir el paquete en un directorio de la imagen montada de Nano Server.</span><span class="sxs-lookup"><span data-stu-id="5148c-148">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="5148c-149">Desmonte la imagen e iníciela.</span><span class="sxs-lookup"><span data-stu-id="5148c-149">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="5148c-150">Conéctese a la instancia de Bandeja de entrada de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5148c-150">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="5148c-151">Siga las instrucciones para crear un punto de conexión de comunicación remota mediante "[otra técnica de instancia"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="5148c-151">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="5148c-152">Implementación en línea de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5148c-152">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="5148c-153">Los pasos siguientes le guían por la implementación de PowerShell Core en una instancia en ejecución de Nano Server y la configuración de su punto de conexión remoto.</span><span class="sxs-lookup"><span data-stu-id="5148c-153">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="5148c-154">Conéctese a la instancia de Bandeja de entrada de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5148c-154">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="5148c-155">Copie el archivo en la instancia de Nano Server.</span><span class="sxs-lookup"><span data-stu-id="5148c-155">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="5148c-156">Especifique la sesión.</span><span class="sxs-lookup"><span data-stu-id="5148c-156">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="5148c-157">Extraiga el archivo ZIP.</span><span class="sxs-lookup"><span data-stu-id="5148c-157">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="5148c-158">Si le interesa la comunicación remota basada en WSMan, siga las instrucciones para crear un punto de conexión de comunicación remota mediante ["otra técnica de instancia"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="5148c-158">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="5148c-159">Procedimientos para crear un punto de conexión de comunicación remota</span><span class="sxs-lookup"><span data-stu-id="5148c-159">How to create a remoting endpoint</span></span>

<span data-ttu-id="5148c-160">PowerShell Core admite el Protocolo de comunicación remota de PowerShell (PSRP) a través de WSMan y SSH.</span><span class="sxs-lookup"><span data-stu-id="5148c-160">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="5148c-161">Para obtener más información, consulte:</span><span class="sxs-lookup"><span data-stu-id="5148c-161">For more information, see:</span></span>

- <span data-ttu-id="5148c-162">[Comunicación remota mediante SSH en PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="5148c-162">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="5148c-163">[Comunicación remota mediante WSMan en PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="5148c-163">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->
[releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
