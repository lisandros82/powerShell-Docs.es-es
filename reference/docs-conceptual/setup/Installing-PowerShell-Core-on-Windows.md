# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="07cdf-101">Instalación de PowerShell Core en Windows</span><span class="sxs-lookup"><span data-stu-id="07cdf-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="07cdf-102">MSI</span><span class="sxs-lookup"><span data-stu-id="07cdf-102">MSI</span></span>

<span data-ttu-id="07cdf-103">Para instalar PowerShell en un cliente de Windows o Windows Server (funciona en Windows 7 SP1, Server 2008 R2 y versiones posteriores), descargue el paquete MSI desde nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="07cdf-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="07cdf-104">El archivo MSI tiene este aspecto: `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="07cdf-104">The MSI file looks like this - `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="07cdf-105">Una vez descargado, haga doble clic en el instalador y siga las indicaciones.</span><span class="sxs-lookup"><span data-stu-id="07cdf-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="07cdf-106">Tras la instalación, se coloca un acceso directo en el menú Inicio.</span><span class="sxs-lookup"><span data-stu-id="07cdf-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="07cdf-107">De forma predeterminada, el paquete se instala en `$env:ProgramFiles\PowerShell\`</span><span class="sxs-lookup"><span data-stu-id="07cdf-107">By default the package is installed to `$env:ProgramFiles\PowerShell\`</span></span>
- <span data-ttu-id="07cdf-108">Puede iniciar PowerShell mediante el menú Inicio o `$env:ProgramFiles\PowerShell\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="07cdf-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="07cdf-109">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="07cdf-109">Prerequisites</span></span>

<span data-ttu-id="07cdf-110">Para habilitar la comunicación remota de PowerShell a través de WSMan, deben cumplirse los siguientes requisitos previos:</span><span class="sxs-lookup"><span data-stu-id="07cdf-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="07cdf-111">Instale el [entorno de ejecución de C universal](https://www.microsoft.com/download/details.aspx?id=50410) en las versiones de Windows anteriores a Windows 10.</span><span class="sxs-lookup"><span data-stu-id="07cdf-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="07cdf-112">Está disponible mediante descarga directa o Windows Update.</span><span class="sxs-lookup"><span data-stu-id="07cdf-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="07cdf-113">Los sistemas admitidos a los que se hayan aplicado todas las revisiones (incluidos los paquetes opcionales) ya lo tienen instalado.</span><span class="sxs-lookup"><span data-stu-id="07cdf-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="07cdf-114">Instale Windows Management Framework (WMF) 4.0 o una versión más reciente en Windows 7 y Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="07cdf-114">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="07cdf-115">ZIP</span><span class="sxs-lookup"><span data-stu-id="07cdf-115">ZIP</span></span>

<span data-ttu-id="07cdf-116">Se proporcionan archivos binarios ZIP de PowerShell para permitir escenarios de implementación avanzada.</span><span class="sxs-lookup"><span data-stu-id="07cdf-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="07cdf-117">Tenga en cuenta que, cuando use el archivo ZIP, no aparecerá la comprobación de requisitos previos como en el caso del paquete MSI.</span><span class="sxs-lookup"><span data-stu-id="07cdf-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="07cdf-118">Por ello, para que la comunicación remota mediante WSMan funcione correctamente en versiones de Windows anteriores a Windows 10, debe asegurarse de que se cumplan los [requisitos previos](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="07cdf-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="07cdf-119">Implementación en Windows IoT</span><span class="sxs-lookup"><span data-stu-id="07cdf-119">Deploying on Windows IoT</span></span>

<span data-ttu-id="07cdf-120">Windows IoT ya incluye Windows PowerShell, que se usará para implementar PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="07cdf-120">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="07cdf-121">Cree `PSSession` en el dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="07cdf-121">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="07cdf-122">Copie el paquete ZIP en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="07cdf-122">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.0.2-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="07cdf-123">Conéctese al dispositivo y expanda el archivo.</span><span class="sxs-lookup"><span data-stu-id="07cdf-123">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.0.2-win-arm32.zip
   ```

4. <span data-ttu-id="07cdf-124">Configure el acceso remoto a PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="07cdf-124">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   cd .\PowerShell-6.0.2-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="07cdf-125">Conéctese al punto de conexión de PowerShell Core 6 en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="07cdf-125">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.0.2
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="07cdf-126">Desarrollo en Nano Server</span><span class="sxs-lookup"><span data-stu-id="07cdf-126">Deploying on Nano Server</span></span>

<span data-ttu-id="07cdf-127">En estas instrucciones se da por supuesto que ya se ejecuta una versión de PowerShell en la imagen de Nano Server y que se ha generado mediante [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="07cdf-127">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="07cdf-128">Nano Server es un sistema operativo "sin periféricos".</span><span class="sxs-lookup"><span data-stu-id="07cdf-128">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="07cdf-129">Los archivos binarios principales se pueden implementar mediante dos métodos diferentes.</span><span class="sxs-lookup"><span data-stu-id="07cdf-129">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="07cdf-130">Sin conexión: monte el VHD de Nano Server y descomprima el contenido del archivo ZIP en la ubicación seleccionada de la imagen montada.</span><span class="sxs-lookup"><span data-stu-id="07cdf-130">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="07cdf-131">En línea: transfiera el archivo ZIP a través de una sesión de PowerShell y descomprímalo en la ubicación seleccionada.</span><span class="sxs-lookup"><span data-stu-id="07cdf-131">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="07cdf-132">En ambos casos, necesitará el paquete comercial ZIP de Windows 10 x64 y deberá ejecutar los comandos en una instancia de PowerShell de "Administrador".</span><span class="sxs-lookup"><span data-stu-id="07cdf-132">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="07cdf-133">Implementación sin conexión de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="07cdf-133">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="07cdf-134">Use su utilidad ZIP favorita para descomprimir el paquete en un directorio de la imagen montada de Nano Server.</span><span class="sxs-lookup"><span data-stu-id="07cdf-134">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="07cdf-135">Desmonte la imagen e iníciela.</span><span class="sxs-lookup"><span data-stu-id="07cdf-135">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="07cdf-136">Conéctese a la instancia de Bandeja de entrada de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07cdf-136">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="07cdf-137">Siga las instrucciones para crear un punto de conexión de comunicación remota mediante "[otra técnica de instancia"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="07cdf-137">Follow the instructions to create a remoting endpoint using the ["another instance technique"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="07cdf-138">Implementación en línea de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="07cdf-138">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="07cdf-139">Los pasos siguientes le guían por la implementación de PowerShell Core en una instancia en ejecución de Nano Server y la configuración de su punto de conexión remoto.</span><span class="sxs-lookup"><span data-stu-id="07cdf-139">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="07cdf-140">Conéctese a la instancia de Bandeja de entrada de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07cdf-140">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="07cdf-141">Copie el archivo en la instancia de Nano Server.</span><span class="sxs-lookup"><span data-stu-id="07cdf-141">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="07cdf-142">Especifique la sesión.</span><span class="sxs-lookup"><span data-stu-id="07cdf-142">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="07cdf-143">Extraiga el archivo ZIP.</span><span class="sxs-lookup"><span data-stu-id="07cdf-143">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="07cdf-144">Si le interesa la comunicación remota basada en WSMan, siga las instrucciones para crear un punto de conexión de comunicación remota mediante ["otra técnica de instancia"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="07cdf-144">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="07cdf-145">Instrucciones para crear un punto de conexión de comunicación remota</span><span class="sxs-lookup"><span data-stu-id="07cdf-145">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="07cdf-146">PowerShell Core admite el Protocolo de comunicación remota de PowerShell (PSRP) a través de WSMan y SSH.</span><span class="sxs-lookup"><span data-stu-id="07cdf-146">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="07cdf-147">Para obtener más información, consulte:</span><span class="sxs-lookup"><span data-stu-id="07cdf-147">For more information, see:</span></span>

- <span data-ttu-id="07cdf-148">[Comunicación remota mediante SSH en PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="07cdf-148">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="07cdf-149">[Comunicación remota mediante WSMan en PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="07cdf-149">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="07cdf-150">Instrucciones de instalación de artefactos</span><span class="sxs-lookup"><span data-stu-id="07cdf-150">Artifact Installation Instructions</span></span>

<span data-ttu-id="07cdf-151">Publicamos un archivo con bits de CoreCLR en todas las compilaciones de CI con [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="07cdf-151">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="07cdf-152">Para instalar PowerShell Core desde el artefacto de CoreCLR:</span><span class="sxs-lookup"><span data-stu-id="07cdf-152">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="07cdf-153">Descargue el paquete ZIP desde la pestaña **artefactos** de la compilación determinada.</span><span class="sxs-lookup"><span data-stu-id="07cdf-153">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="07cdf-154">Desbloquee el archivo ZIP. Para ello, haga clic con el botón derecho en el Explorador de archivos -> Propiedades -> active la casilla "Desbloquear" -> Aplicar.</span><span class="sxs-lookup"><span data-stu-id="07cdf-154">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="07cdf-155">Extraiga el archivo ZIP en el directorio `bin`.</span><span class="sxs-lookup"><span data-stu-id="07cdf-155">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[versiones]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell