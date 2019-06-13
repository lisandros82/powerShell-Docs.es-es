---
title: Instalación de PowerShell Core en Windows
description: Información sobre cómo instalar PowerShell Core en Windows
ms.date: 08/06/2018
ms.openlocfilehash: 3f21761037311891162f1083234edb0aca80d28b
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830226"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="40a8a-103">Instalación de PowerShell Core en Windows</span><span class="sxs-lookup"><span data-stu-id="40a8a-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="40a8a-104">Hay varias formas de instalar PowerShell Core en Windows.</span><span class="sxs-lookup"><span data-stu-id="40a8a-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="40a8a-105">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="40a8a-105">Prerequisites</span></span>

<span data-ttu-id="40a8a-106">Para habilitar la comunicación remota de PowerShell a través de WSMan, deben cumplirse los siguientes requisitos previos:</span><span class="sxs-lookup"><span data-stu-id="40a8a-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="40a8a-107">Instale el [entorno de ejecución de C universal](https://www.microsoft.com/download/details.aspx?id=50410) en las versiones de Windows anteriores a Windows 10.</span><span class="sxs-lookup"><span data-stu-id="40a8a-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="40a8a-108">Está disponible mediante descarga directa o Windows Update.</span><span class="sxs-lookup"><span data-stu-id="40a8a-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="40a8a-109">Los sistemas admitidos a los que se hayan aplicado todas las revisiones (incluidos los paquetes opcionales) ya lo tienen instalado.</span><span class="sxs-lookup"><span data-stu-id="40a8a-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="40a8a-110">Instale Windows Management Framework (WMF) 4.0 o una versión más reciente en Windows 7 y Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="40a8a-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="40a8a-111">Para más información sobre WMF, consulte la [información general sobre WMF](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="40a8a-111">For more information about WMF, see [WMF Overview](/powershell/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="40a8a-112"><a id="msi" />Instalación del paquete MSI</span><span class="sxs-lookup"><span data-stu-id="40a8a-112"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="40a8a-113">Para instalar PowerShell en un cliente de Windows o Windows Server (funciona en Windows 7 SP1, Server 2008 R2 y versiones posteriores), descargue el paquete MSI desde nuestra página de [versiones][releases] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="40a8a-113">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="40a8a-114">Desplácese hacia abajo hasta la sección **Recursos** de la versión que quiere instalar.</span><span class="sxs-lookup"><span data-stu-id="40a8a-114">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="40a8a-115">Es posible que la sección Recursos esté contraída, por lo que tendría que hacer clic para expandirla.</span><span class="sxs-lookup"><span data-stu-id="40a8a-115">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="40a8a-116">El archivo MSI tiene este aspecto: `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="40a8a-116">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="40a8a-117">Una vez descargado, haga doble clic en el instalador y siga las indicaciones.</span><span class="sxs-lookup"><span data-stu-id="40a8a-117">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="40a8a-118">El instalador crea un acceso directo en el menú de inicio de Windows.</span><span class="sxs-lookup"><span data-stu-id="40a8a-118">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="40a8a-119">De forma predeterminada, el paquete se instala en `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="40a8a-119">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="40a8a-120">Puede iniciar PowerShell mediante el menú Inicio o `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="40a8a-120">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="40a8a-121">Instalación administrativa desde la línea de comandos</span><span class="sxs-lookup"><span data-stu-id="40a8a-121">Administrative install from the command line</span></span>

<span data-ttu-id="40a8a-122">Los paquetes MSI se pueden instalar desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="40a8a-122">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="40a8a-123">Esto permite a los administradores implementar los paquetes sin interacción del usuario.</span><span class="sxs-lookup"><span data-stu-id="40a8a-123">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="40a8a-124">El paquete MSI para PowerShell incluye las siguientes propiedades para controlar las opciones de instalación:</span><span class="sxs-lookup"><span data-stu-id="40a8a-124">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="40a8a-125">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL**: esta propiedad controla la opción para agregar el elemento **Open PowerShell** al menú contextual en el Explorador de Windows.</span><span class="sxs-lookup"><span data-stu-id="40a8a-125">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="40a8a-126">**ENABLE_PSREMOTING**: esta propiedad controla la opción para habilitar la comunicación remota de PowerShell durante la instalación.</span><span class="sxs-lookup"><span data-stu-id="40a8a-126">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="40a8a-127">**REGISTER_MANIFEST**: esta propiedad controla la opción para registrar el manifiesto de registro de eventos de Windows.</span><span class="sxs-lookup"><span data-stu-id="40a8a-127">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="40a8a-128">En los ejemplos siguientes se muestra cómo instalar PowerShell Core con todas las opciones de instalación habilitadas de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="40a8a-128">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="40a8a-129">Para obtener una lista completa de opciones de línea de comandos de Msiexec.exe, consulte [Opciones de línea de comandos](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="40a8a-129">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="40a8a-130"><a id="zip" />Instalación del paquete ZIP</span><span class="sxs-lookup"><span data-stu-id="40a8a-130"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="40a8a-131">Se proporcionan archivos binarios ZIP de PowerShell para permitir escenarios de implementación avanzada.</span><span class="sxs-lookup"><span data-stu-id="40a8a-131">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="40a8a-132">Tenga en cuenta que, cuando use el archivo ZIP, no aparecerá la comprobación de requisitos previos como en el caso del paquete MSI.</span><span class="sxs-lookup"><span data-stu-id="40a8a-132">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="40a8a-133">Para que la comunicación remota en WSMan funcione correctamente, asegúrese de que se han cumplido los [requisitos previos](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="40a8a-133">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="40a8a-134">Implementación en Windows IoT</span><span class="sxs-lookup"><span data-stu-id="40a8a-134">Deploying on Windows IoT</span></span>

<span data-ttu-id="40a8a-135">Windows IoT ya incluye Windows PowerShell, que se usará para implementar PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="40a8a-135">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="40a8a-136">Cree `PSSession` en el dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="40a8a-136">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="40a8a-137">Copie el paquete ZIP en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="40a8a-137">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="40a8a-138">Conéctese al dispositivo y expanda el archivo.</span><span class="sxs-lookup"><span data-stu-id="40a8a-138">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="40a8a-139">Configure el acceso remoto a PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="40a8a-139">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="40a8a-140">Conéctese al punto de conexión de PowerShell Core 6 en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="40a8a-140">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="40a8a-141">Desarrollo en Nano Server</span><span class="sxs-lookup"><span data-stu-id="40a8a-141">Deploying on Nano Server</span></span>

<span data-ttu-id="40a8a-142">En estas instrucciones se da por supuesto que ya se ejecuta una versión de PowerShell en la imagen de Nano Server y que se ha generado mediante [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="40a8a-142">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="40a8a-143">Nano Server es un sistema operativo "sin periféricos".</span><span class="sxs-lookup"><span data-stu-id="40a8a-143">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="40a8a-144">Los archivos binarios principales se pueden implementar mediante dos métodos diferentes.</span><span class="sxs-lookup"><span data-stu-id="40a8a-144">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="40a8a-145">Sin conexión: monte el VHD de Nano Server y descomprima el contenido del archivo ZIP en la ubicación seleccionada de la imagen montada.</span><span class="sxs-lookup"><span data-stu-id="40a8a-145">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="40a8a-146">En línea: transfiera el archivo ZIP a través de una sesión de PowerShell y descomprímalo en la ubicación seleccionada.</span><span class="sxs-lookup"><span data-stu-id="40a8a-146">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="40a8a-147">En ambos casos, necesitará el paquete comercial ZIP de Windows 10 x64 y deberá ejecutar los comandos en una instancia de PowerShell de "Administrador".</span><span class="sxs-lookup"><span data-stu-id="40a8a-147">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="40a8a-148">Implementación sin conexión de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="40a8a-148">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="40a8a-149">Use su utilidad ZIP favorita para descomprimir el paquete en un directorio de la imagen montada de Nano Server.</span><span class="sxs-lookup"><span data-stu-id="40a8a-149">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="40a8a-150">Desmonte la imagen e iníciela.</span><span class="sxs-lookup"><span data-stu-id="40a8a-150">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="40a8a-151">Conéctese a la instancia de Bandeja de entrada de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40a8a-151">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="40a8a-152">Siga las instrucciones para crear un punto de conexión de comunicación remota mediante "[otra técnica de instancia"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="40a8a-152">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="40a8a-153">Implementación en línea de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="40a8a-153">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="40a8a-154">Los pasos siguientes le guían por la implementación de PowerShell Core en una instancia en ejecución de Nano Server y la configuración de su punto de conexión remoto.</span><span class="sxs-lookup"><span data-stu-id="40a8a-154">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="40a8a-155">Conéctese a la instancia de Bandeja de entrada de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40a8a-155">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="40a8a-156">Copie el archivo en la instancia de Nano Server.</span><span class="sxs-lookup"><span data-stu-id="40a8a-156">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="40a8a-157">Especifique la sesión.</span><span class="sxs-lookup"><span data-stu-id="40a8a-157">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="40a8a-158">Extraiga el archivo ZIP.</span><span class="sxs-lookup"><span data-stu-id="40a8a-158">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="40a8a-159">Si le interesa la comunicación remota basada en WSMan, siga las instrucciones para crear un punto de conexión de comunicación remota mediante ["otra técnica de instancia"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="40a8a-159">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="40a8a-160">Procedimientos para crear un punto de conexión de comunicación remota</span><span class="sxs-lookup"><span data-stu-id="40a8a-160">How to create a remoting endpoint</span></span>

<span data-ttu-id="40a8a-161">PowerShell Core admite el Protocolo de comunicación remota de PowerShell (PSRP) a través de WSMan y SSH.</span><span class="sxs-lookup"><span data-stu-id="40a8a-161">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="40a8a-162">Para obtener más información, consulte:</span><span class="sxs-lookup"><span data-stu-id="40a8a-162">For more information, see:</span></span>

- <span data-ttu-id="40a8a-163">[Comunicación remota mediante SSH en PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="40a8a-163">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="40a8a-164">[Comunicación remota mediante WSMan en PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="40a8a-164">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
