---
title: Instalación de PowerShell Core en macOS
description: Información sobre cómo instalar PowerShell Core en macOS
ms.date: 11/02/2018
ms.openlocfilehash: 162e841bf71d708e9db84ea1bb2dbef13924783b
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998510"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="5e606-103">Instalación de PowerShell Core en macOS</span><span class="sxs-lookup"><span data-stu-id="5e606-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="5e606-104">PowerShell Core admite macOS 10.12 y superior.</span><span class="sxs-lookup"><span data-stu-id="5e606-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="5e606-105">Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="5e606-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="5e606-106">Una vez que se haya instalado el paquete, ejecute `pwsh` desde un terminal.</span><span class="sxs-lookup"><span data-stu-id="5e606-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="5e606-107">Acerca de Brew</span><span class="sxs-lookup"><span data-stu-id="5e606-107">About Brew</span></span>

<span data-ttu-id="5e606-108">[Homebrew][brew] es el administrador de paquetes preferido de macOS.</span><span class="sxs-lookup"><span data-stu-id="5e606-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="5e606-109">Si no se encuentra el comando `brew`, debe instalar Homebrew según [sus instrucciones][brew].</span><span class="sxs-lookup"><span data-stu-id="5e606-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="5e606-110">Instalación de la versión estable más reciente a través de Homebrew en macOS 10.12 o superior</span><span class="sxs-lookup"><span data-stu-id="5e606-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="5e606-111">Consulte [Acerca de Brew](#about-brew) para obtener información sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="5e606-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="5e606-112">Ahora puede instalar PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5e606-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="5e606-113">Por último, compruebe que la instalación funciona correctamente:</span><span class="sxs-lookup"><span data-stu-id="5e606-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="5e606-114">Cuando se publiquen nuevas versiones de PowerShell, bastará con actualizar las fórmulas de Homebrew y PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5e606-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="5e606-115">Los comandos anteriores pueden llamarse desde un host de PowerShell (pwsh), pero, acto seguido, el shell de PowerShell se debe cerrar y volver a iniciar para finalizar la actualización y actualizar los valores que aparecen en $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="5e606-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="5e606-116">Instalación de la versión preliminar más reciente a través de Homebrew en macOS 10.12 o superior</span><span class="sxs-lookup"><span data-stu-id="5e606-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="5e606-117">Consulte [Acerca de Brew](#about-brew) para obtener información sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="5e606-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="5e606-118">Una vez que haya instalado Homebrew, le resultará muy fácil instalar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e606-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="5e606-119">En primer lugar, instale [Cask-Versions][cask-versions] que le permite instalar versiones alternativas de los paquetes de cask:</span><span class="sxs-lookup"><span data-stu-id="5e606-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="5e606-120">Ahora puede instalar PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5e606-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="5e606-121">Por último, compruebe que la instalación funciona correctamente:</span><span class="sxs-lookup"><span data-stu-id="5e606-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="5e606-122">Cuando se publiquen nuevas versiones de PowerShell, bastará con actualizar las fórmulas de Homebrew y PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5e606-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="5e606-123">Los comandos anteriores pueden llamarse desde dentro de un host de PowerShell (pwsh), pero, en este caso, es necesario salir y reiniciar el shell de PowerShell para completar la actualización.</span><span class="sxs-lookup"><span data-stu-id="5e606-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="5e606-124">y actualizar los valores mostrados en $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="5e606-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="5e606-125">Instalación mediante descarga directa</span><span class="sxs-lookup"><span data-stu-id="5e606-125">Installation via Direct Download</span></span>

<span data-ttu-id="5e606-126">Descargue el paquete PKG `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="5e606-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="5e606-127">desde la página de [versiones][] en la máquina macOS.</span><span class="sxs-lookup"><span data-stu-id="5e606-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="5e606-128">Puede hacer doble clic en el archivo y seguir las indicaciones, o bien instalarlo desde el terminal:</span><span class="sxs-lookup"><span data-stu-id="5e606-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="5e606-129">Instale [OpenSSL](#install-openssl), ya que es necesario para operaciones de CIM y comunicaciones remotas de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e606-129">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="5e606-130">Archivos binarios</span><span class="sxs-lookup"><span data-stu-id="5e606-130">Binary Archives</span></span>

<span data-ttu-id="5e606-131">Se proporcionan archivos binarios `tar.gz` de PowerShell para la plataforma macOS, a fin de permitir escenarios de implementación avanzados.</span><span class="sxs-lookup"><span data-stu-id="5e606-131">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="5e606-132">Instalación de archivos binarios en macOS</span><span class="sxs-lookup"><span data-stu-id="5e606-132">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="5e606-133">Instale [OpenSSL](#install-openssl), ya que es necesario para las operaciones de CIM y las comunicaciones remotas de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e606-133">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="5e606-134">Instalación de dependencias</span><span class="sxs-lookup"><span data-stu-id="5e606-134">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="5e606-135">Instalación de las herramientas de la línea de comandos de XCode</span><span class="sxs-lookup"><span data-stu-id="5e606-135">Install XCode command line tools</span></span>

```shell
xcode-select -install
```

### <a name="install-openssl"></a><span data-ttu-id="5e606-136">Instalación de OpenSSL</span><span class="sxs-lookup"><span data-stu-id="5e606-136">Install OpenSSL</span></span>

<span data-ttu-id="5e606-137">OpenSSL se necesita para la comunicación remota de PowerShell y las operaciones de CIM.</span><span class="sxs-lookup"><span data-stu-id="5e606-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>  <span data-ttu-id="5e606-138">Puede realizar la instalación mediante MacPorts o Brew.</span><span class="sxs-lookup"><span data-stu-id="5e606-138">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="5e606-139">Instalación de OpenSSL mediante Brew</span><span class="sxs-lookup"><span data-stu-id="5e606-139">Install OpenSSL via Brew</span></span>

<span data-ttu-id="5e606-140">Consulte [Acerca de Brew](#about-brew) para obtener información sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="5e606-140">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="5e606-141">Ejecute `brew install openssl` para instalar OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="5e606-141">Run `brew install openssl` to install OpenSSL.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="5e606-142">Instalación de OpenSSL mediante MacPorts</span><span class="sxs-lookup"><span data-stu-id="5e606-142">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="5e606-143">Instalación de las [herramientas de la línea de comandos de XCode](#install-xcode-command-line-tools)</span><span class="sxs-lookup"><span data-stu-id="5e606-143">Instal the [XCode command line tools](#install-xcode-command-line-tools)</span></span>
1. <span data-ttu-id="5e606-144">Instale MacPorts.</span><span class="sxs-lookup"><span data-stu-id="5e606-144">Install MacPorts.</span></span>
   <span data-ttu-id="5e606-145">Consulte la [guía de instalación](https://guide.macports.org/chunked/installing.macports.html) si necesita instrucciones.</span><span class="sxs-lookup"><span data-stu-id="5e606-145">See the [installation guide](https://guide.macports.org/chunked/installing.macports.html) if you need instructions.</span></span>
1. <span data-ttu-id="5e606-146">Actualice MacPorts mediante la ejecución de `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="5e606-146">Update MacPorts by running `sudo port selfupdate`</span></span>
1. <span data-ttu-id="5e606-147">Actualice los paquetes de MacPorts mediante la ejecución de `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="5e606-147">Upgrade MacPorts packages by running `sudo port upgrade outdated`</span></span>
1. <span data-ttu-id="5e606-148">Instale OpenSSL mediante la ejecución de `sudo port instal openssl`.</span><span class="sxs-lookup"><span data-stu-id="5e606-148">Install OpenSSL by running by running `sudo port instal openssl`</span></span>
1. <span data-ttu-id="5e606-149">Vincule las bibliotecas para que PowerShell pueda usarlas.</span><span class="sxs-lookup"><span data-stu-id="5e606-149">Link the libraries so that PowerShell can use it.</span></span>

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="5e606-150">Desinstalación de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5e606-150">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="5e606-151">Si ha instalado PowerShell con Homebrew, la desinstalación es fácil:</span><span class="sxs-lookup"><span data-stu-id="5e606-151">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="5e606-152">Si ha instalado PowerShell mediante descarga directa, deberá quitar PowerShell manualmente:</span><span class="sxs-lookup"><span data-stu-id="5e606-152">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="5e606-153">Para quitar las rutas de acceso de PowerShell adicionales, consulte la sección [Rutas de acceso](#paths) de este documento y elimine las rutas de acceso deseadas mediante `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="5e606-153">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="5e606-154">Este paso no es necesario si ha realizado la instalación con Homebrew.</span><span class="sxs-lookup"><span data-stu-id="5e606-154">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="5e606-155">Rutas de acceso</span><span class="sxs-lookup"><span data-stu-id="5e606-155">Paths</span></span>

* <span data-ttu-id="5e606-156">`$PSHOME` es `/usr/local/microsoft/powershell/6.1.0/`.</span><span class="sxs-lookup"><span data-stu-id="5e606-156">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="5e606-157">Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="5e606-157">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="5e606-158">Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="5e606-158">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="5e606-159">Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="5e606-159">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="5e606-160">Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="5e606-160">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="5e606-161">Los módulos predeterminados se leerán de `$PSHOME/Modules`.</span><span class="sxs-lookup"><span data-stu-id="5e606-161">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="5e606-162">El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.</span><span class="sxs-lookup"><span data-stu-id="5e606-162">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="5e606-163">Los perfiles respetan la configuración por host de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e606-163">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="5e606-164">Así que los perfiles predeterminados específicos del host están en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="5e606-164">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="5e606-165">PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en macOS.</span><span class="sxs-lookup"><span data-stu-id="5e606-165">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="5e606-166">Dado que macOS es una derivación de BSD, se usa el prefijo `/usr/local` en lugar de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="5e606-166">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="5e606-167">Por lo tanto, `$PSHOME` es `/usr/local/microsoft/powershell/6.1.0/`, y el vínculo simbólico se coloca en `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="5e606-167">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="5e606-168">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="5e606-168">Additional Resources</span></span>

* <span data-ttu-id="5e606-169">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="5e606-169">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="5e606-170">[Repositorio GitHub de Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="5e606-170">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="5e606-171">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="5e606-171">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
