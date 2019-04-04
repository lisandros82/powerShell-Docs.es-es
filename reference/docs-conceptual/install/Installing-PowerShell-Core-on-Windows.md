---
title: Instalación de PowerShell Core en Windows
description: Información sobre cómo instalar PowerShell Core en Windows
ms.date: 08/06/2018
ms.openlocfilehash: 450a38a1ef2e2890059094774fcc3f2ad4fcda6e
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2019
ms.locfileid: "58748949"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="2afa6-103">Instalación de PowerShell Core en Windows</span><span class="sxs-lookup"><span data-stu-id="2afa6-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="2afa6-104">MSI</span><span class="sxs-lookup"><span data-stu-id="2afa6-104">MSI</span></span>

<span data-ttu-id="2afa6-105">Para instalar PowerShell en un cliente de Windows o Windows Server (funciona en Windows 7 SP1, Server 2008 R2 y versiones posteriores), descargue el paquete MSI desde nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="2afa6-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>  <span data-ttu-id="2afa6-106">Desplácese hacia abajo hasta la sección **Recursos** de la versión que quiere instalar.</span><span class="sxs-lookup"><span data-stu-id="2afa6-106">Scroll down to the **Assets** section of the Release you want to install.</span></span>  <span data-ttu-id="2afa6-107">Es posible que la sección Recursos esté contraída, por lo que tendría que hacer clic para expandirla.</span><span class="sxs-lookup"><span data-stu-id="2afa6-107">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="2afa6-108">El archivo MSI tiene este aspecto: `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="2afa6-108">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="2afa6-109">Una vez descargado, haga doble clic en el instalador y siga las indicaciones.</span><span class="sxs-lookup"><span data-stu-id="2afa6-109">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="2afa6-110">Tras la instalación, se coloca un acceso directo en el menú Inicio.</span><span class="sxs-lookup"><span data-stu-id="2afa6-110">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="2afa6-111">De forma predeterminada, el paquete se instala en `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="2afa6-111">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="2afa6-112">Puede iniciar PowerShell mediante el menú Inicio o `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="2afa6-112">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="2afa6-113">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="2afa6-113">Prerequisites</span></span>

<span data-ttu-id="2afa6-114">Para habilitar la comunicación remota de PowerShell a través de WSMan, deben cumplirse los siguientes requisitos previos:</span><span class="sxs-lookup"><span data-stu-id="2afa6-114">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="2afa6-115">Instale el [entorno de ejecución de C universal](https://www.microsoft.com/download/details.aspx?id=50410) en las versiones de Windows anteriores a Windows 10.</span><span class="sxs-lookup"><span data-stu-id="2afa6-115">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="2afa6-116">Está disponible mediante descarga directa o Windows Update.</span><span class="sxs-lookup"><span data-stu-id="2afa6-116">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="2afa6-117">Los sistemas admitidos a los que se hayan aplicado todas las revisiones (incluidos los paquetes opcionales) ya lo tienen instalado.</span><span class="sxs-lookup"><span data-stu-id="2afa6-117">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="2afa6-118">Instale Windows Management Framework (WMF) 4.0 o una versión más reciente en Windows 7 y Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="2afa6-118">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="2afa6-119">ZIP</span><span class="sxs-lookup"><span data-stu-id="2afa6-119">ZIP</span></span>

<span data-ttu-id="2afa6-120">Se proporcionan archivos binarios ZIP de PowerShell para permitir escenarios de implementación avanzada.</span><span class="sxs-lookup"><span data-stu-id="2afa6-120">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="2afa6-121">Tenga en cuenta que, cuando use el archivo ZIP, no aparecerá la comprobación de requisitos previos como en el caso del paquete MSI.</span><span class="sxs-lookup"><span data-stu-id="2afa6-121">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="2afa6-122">Por ello, para que la comunicación remota mediante WSMan funcione correctamente en versiones de Windows anteriores a Windows 10, debe asegurarse de que se cumplan los [requisitos previos](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="2afa6-122">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="2afa6-123">Implementación en Windows IoT</span><span class="sxs-lookup"><span data-stu-id="2afa6-123">Deploying on Windows IoT</span></span>

<span data-ttu-id="2afa6-124">Windows IoT ya incluye Windows PowerShell, que se usará para implementar PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="2afa6-124">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="2afa6-125">Cree `PSSession` en el dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="2afa6-125">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="2afa6-126">Copie el paquete ZIP en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2afa6-126">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="2afa6-127">Conéctese al dispositivo y expanda el archivo.</span><span class="sxs-lookup"><span data-stu-id="2afa6-127">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="2afa6-128">Configure el acceso remoto a PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="2afa6-128">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="2afa6-129">Conéctese al punto de conexión de PowerShell Core 6 en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2afa6-129">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="2afa6-130">Desarrollo en Nano Server</span><span class="sxs-lookup"><span data-stu-id="2afa6-130">Deploying on Nano Server</span></span>

<span data-ttu-id="2afa6-131">En estas instrucciones se da por supuesto que ya se ejecuta una versión de PowerShell en la imagen de Nano Server y que se ha generado mediante [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="2afa6-131">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="2afa6-132">Nano Server es un sistema operativo "sin periféricos".</span><span class="sxs-lookup"><span data-stu-id="2afa6-132">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="2afa6-133">Los archivos binarios principales se pueden implementar mediante dos métodos diferentes.</span><span class="sxs-lookup"><span data-stu-id="2afa6-133">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="2afa6-134">Sin conexión: monte el VHD de Nano Server y descomprima el contenido del archivo ZIP en la ubicación seleccionada de la imagen montada.</span><span class="sxs-lookup"><span data-stu-id="2afa6-134">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="2afa6-135">En línea: transfiera el archivo ZIP a través de una sesión de PowerShell y descomprímalo en la ubicación seleccionada.</span><span class="sxs-lookup"><span data-stu-id="2afa6-135">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="2afa6-136">En ambos casos, necesitará el paquete comercial ZIP de Windows 10 x64 y deberá ejecutar los comandos en una instancia de PowerShell de "Administrador".</span><span class="sxs-lookup"><span data-stu-id="2afa6-136">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="2afa6-137">Implementación sin conexión de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="2afa6-137">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="2afa6-138">Use su utilidad ZIP favorita para descomprimir el paquete en un directorio de la imagen montada de Nano Server.</span><span class="sxs-lookup"><span data-stu-id="2afa6-138">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="2afa6-139">Desmonte la imagen e iníciela.</span><span class="sxs-lookup"><span data-stu-id="2afa6-139">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="2afa6-140">Conéctese a la instancia de Bandeja de entrada de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2afa6-140">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="2afa6-141">Siga las instrucciones para crear un punto de conexión de comunicación remota mediante "[otra técnica de instancia"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="2afa6-141">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="2afa6-142">Implementación en línea de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="2afa6-142">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="2afa6-143">Los pasos siguientes le guían por la implementación de PowerShell Core en una instancia en ejecución de Nano Server y la configuración de su punto de conexión remoto.</span><span class="sxs-lookup"><span data-stu-id="2afa6-143">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="2afa6-144">Conéctese a la instancia de Bandeja de entrada de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2afa6-144">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="2afa6-145">Copie el archivo en la instancia de Nano Server.</span><span class="sxs-lookup"><span data-stu-id="2afa6-145">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="2afa6-146">Especifique la sesión.</span><span class="sxs-lookup"><span data-stu-id="2afa6-146">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="2afa6-147">Extraiga el archivo ZIP.</span><span class="sxs-lookup"><span data-stu-id="2afa6-147">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="2afa6-148">Si le interesa la comunicación remota basada en WSMan, siga las instrucciones para crear un punto de conexión de comunicación remota mediante ["otra técnica de instancia"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="2afa6-148">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="2afa6-149">Instrucciones para crear un punto de conexión de comunicación remota</span><span class="sxs-lookup"><span data-stu-id="2afa6-149">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="2afa6-150">PowerShell Core admite el Protocolo de comunicación remota de PowerShell (PSRP) a través de WSMan y SSH.</span><span class="sxs-lookup"><span data-stu-id="2afa6-150">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="2afa6-151">Para obtener más información, consulte:</span><span class="sxs-lookup"><span data-stu-id="2afa6-151">For more information, see:</span></span>

- <span data-ttu-id="2afa6-152">[Comunicación remota mediante SSH en PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="2afa6-152">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="2afa6-153">[Comunicación remota mediante WSMan en PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="2afa6-153">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="2afa6-154">Instrucciones de instalación de artefactos</span><span class="sxs-lookup"><span data-stu-id="2afa6-154">Artifact Installation Instructions</span></span>

<span data-ttu-id="2afa6-155">Publicamos un archivo con bits de CoreCLR en todas las compilaciones de CI con [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="2afa6-155">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="2afa6-156">Para instalar PowerShell Core desde el artefacto de CoreCLR:</span><span class="sxs-lookup"><span data-stu-id="2afa6-156">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="2afa6-157">Descargue el paquete ZIP desde la pestaña **artefactos** de la compilación determinada.</span><span class="sxs-lookup"><span data-stu-id="2afa6-157">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="2afa6-158">Desbloquee el archivo ZIP. Para ello, haga clic con el botón derecho en el Explorador de archivos -> Propiedades -> active la casilla "Desbloquear" -> Aplicar.</span><span class="sxs-lookup"><span data-stu-id="2afa6-158">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="2afa6-159">Extraiga el archivo ZIP en el directorio `bin`.</span><span class="sxs-lookup"><span data-stu-id="2afa6-159">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[Versiones]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
