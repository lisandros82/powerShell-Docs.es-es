# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="e2b0b-101">Instalación de PowerShell Core en macOS</span><span class="sxs-lookup"><span data-stu-id="e2b0b-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="e2b0b-102">PowerShell Core admite macOS 10.12 y superior.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="e2b0b-103">Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="e2b0b-104">Una vez que se haya instalado el paquete, ejecute `pwsh` desde un terminal.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="e2b0b-105">Instalación mediante Homebrew en macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="e2b0b-105">Installation via Homebrew on macOS 10.12</span></span>

<span data-ttu-id="e2b0b-106">[Homebrew][brew] es el administrador de paquetes preferido de macOS.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="e2b0b-107">Si no se encuentra el comando `brew`, debe instalar Homebrew según [sus instrucciones][brew].</span><span class="sxs-lookup"><span data-stu-id="e2b0b-107">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="e2b0b-108">Una vez que haya instalado Homebrew, le resultará muy fácil instalar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-108">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="e2b0b-109">En primer lugar, instale [Homebrew-Cask][cask] para poder instalar más paquetes:</span><span class="sxs-lookup"><span data-stu-id="e2b0b-109">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="e2b0b-110">Ahora puede instalar PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e2b0b-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="e2b0b-111">Por último, compruebe que la instalación funciona correctamente:</span><span class="sxs-lookup"><span data-stu-id="e2b0b-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="e2b0b-112">Cuando se publiquen nuevas versiones de PowerShell, bastará con actualizar las fórmulas de Homebrew y PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e2b0b-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="e2b0b-113">Los comandos anteriores pueden llamarse desde dentro de un host de PowerShell (pwsh), pero, en este caso, es necesario salir y reiniciar el shell de PowerShell para completar la actualización.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="e2b0b-114">y actualizar los valores mostrados en $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-114">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download"></a><span data-ttu-id="e2b0b-115">Instalación mediante descarga directa</span><span class="sxs-lookup"><span data-stu-id="e2b0b-115">Installation via Direct Download</span></span>

<span data-ttu-id="e2b0b-116">Descargue el paquete PKG `powershell-6.0.2-osx.10.12-x64.pkg` de la página de [versiones][] en la máquina macOS.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-116">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="e2b0b-117">Puede hacer doble clic en el archivo y seguir las indicaciones, o bien instalarlo desde el terminal:</span><span class="sxs-lookup"><span data-stu-id="e2b0b-117">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="e2b0b-118">Archivos binarios</span><span class="sxs-lookup"><span data-stu-id="e2b0b-118">Binary Archives</span></span>

<span data-ttu-id="e2b0b-119">Se proporcionan archivos binarios `tar.gz` de PowerShell para que las plataformas macOS y Linux permitan escenarios de implementación avanzada.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-119">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="e2b0b-120">Instalación de archivos binarios en macOS</span><span class="sxs-lookup"><span data-stu-id="e2b0b-120">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="e2b0b-121">Desinstalación de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="e2b0b-121">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="e2b0b-122">Si ha instalado PowerShell con Homebrew, la desinstalación es fácil:</span><span class="sxs-lookup"><span data-stu-id="e2b0b-122">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="e2b0b-123">Si ha instalado PowerShell mediante descarga directa, deberá quitar PowerShell manualmente:</span><span class="sxs-lookup"><span data-stu-id="e2b0b-123">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="e2b0b-124">Para quitar las rutas de acceso de PowerShell adicionales, consulte la sección [Rutas de acceso][] de este documento y elimine las rutas de acceso deseadas mediante `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-124">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="e2b0b-125">Este paso no es necesario si ha realizado la instalación con Homebrew.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-125">This is not necessary if you installed with Homebrew.</span></span>

[Rutas de acceso]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="e2b0b-127">Rutas de acceso</span><span class="sxs-lookup"><span data-stu-id="e2b0b-127">Paths</span></span>

* <span data-ttu-id="e2b0b-128">`$PSHOME` es `/opt/microsoft/powershell/6.0.0/`.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-128">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="e2b0b-129">Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-129">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="e2b0b-130">Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-130">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="e2b0b-131">Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-131">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e2b0b-132">Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-132">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e2b0b-133">Los módulos predeterminados se leerán de `$PSHOME/Modules`.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-133">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="e2b0b-134">El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-134">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e2b0b-135">Los perfiles respetan la configuración por host de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-135">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="e2b0b-136">Así que los perfiles predeterminados específicos del host están en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-136">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e2b0b-137">PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en macOS.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-137">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="e2b0b-138">Dado que macOS es una derivación de BSD, se usa el prefijo `/usr/local` en lugar de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-138">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="e2b0b-139">Por lo tanto, `$PSHOME` es `/usr/local/microsoft/powershell/6.0.0/`, y el vínculo simbólico se coloca en `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="e2b0b-139">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
