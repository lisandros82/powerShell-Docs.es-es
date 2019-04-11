---
title: Instalación de PowerShell Core en macOS
description: Información sobre cómo instalar PowerShell Core en macOS
ms.date: 12/12/2018
ms.openlocfilehash: 7db8ca0cb6d13db8ce7f11b4a4b03b7d3f9b6feb
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293408"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="0ffc9-103">Instalación de PowerShell Core en macOS</span><span class="sxs-lookup"><span data-stu-id="0ffc9-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="0ffc9-104">PowerShell Core admite macOS 10.12 y superior.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="0ffc9-105">Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="0ffc9-106">Una vez instalado el paquete, ejecute `pwsh` desde un terminal.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="0ffc9-107">Acerca de Brew</span><span class="sxs-lookup"><span data-stu-id="0ffc9-107">About Brew</span></span>

<span data-ttu-id="0ffc9-108">[Homebrew][brew] es el administrador de paquetes preferido de macOS.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="0ffc9-109">Si no se encuentra el comando `brew`, debe instalar Homebrew según [sus instrucciones][brew].</span><span class="sxs-lookup"><span data-stu-id="0ffc9-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="0ffc9-110">Instalación de la versión estable más reciente a través de Homebrew en macOS 10.12 o superior</span><span class="sxs-lookup"><span data-stu-id="0ffc9-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="0ffc9-111">Consulte [Acerca de Brew](#about-brew) para obtener información sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="0ffc9-112">Ahora puede instalar PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0ffc9-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="0ffc9-113">Por último, compruebe que la instalación funciona correctamente:</span><span class="sxs-lookup"><span data-stu-id="0ffc9-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="0ffc9-114">Cuando se publiquen nuevas versiones de PowerShell, actualice PowerShell y las fórmulas de Homebrew:</span><span class="sxs-lookup"><span data-stu-id="0ffc9-114">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="0ffc9-115">Los comandos anteriores pueden llamarse desde un host de PowerShell (pwsh), pero, acto seguido, el shell de PowerShell se debe cerrar y volver a iniciar para finalizar la actualización y actualizar los valores que aparecen en `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="0ffc9-116">Instalación de la versión preliminar más reciente a través de Homebrew en macOS 10.12 o superior</span><span class="sxs-lookup"><span data-stu-id="0ffc9-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="0ffc9-117">Consulte [Acerca de Brew](#about-brew) para obtener información sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="0ffc9-118">Una vez instalado Homebrew, puede instalar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-118">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="0ffc9-119">En primer lugar, instale el paquete [Cask-Versions][cask-versions] que le permite instalar versiones alternativas de los paquetes de cask:</span><span class="sxs-lookup"><span data-stu-id="0ffc9-119">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="0ffc9-120">Ahora puede instalar PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0ffc9-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="0ffc9-121">Por último, compruebe que la instalación funciona correctamente:</span><span class="sxs-lookup"><span data-stu-id="0ffc9-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="0ffc9-122">Cuando se publiquen nuevas versiones de PowerShell, actualice PowerShell y las fórmulas de Homebrew:</span><span class="sxs-lookup"><span data-stu-id="0ffc9-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="0ffc9-123">Los comandos anteriores pueden llamarse desde dentro de un host de PowerShell (pwsh), pero, en este caso, es necesario salir y reiniciar el shell de PowerShell para completar la actualización.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="0ffc9-124">y actualice los valores mostrados en `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-124">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="0ffc9-125">Instalación mediante descarga directa</span><span class="sxs-lookup"><span data-stu-id="0ffc9-125">Installation via Direct Download</span></span>

<span data-ttu-id="0ffc9-126">Descargue el paquete PKG</span><span class="sxs-lookup"><span data-stu-id="0ffc9-126">Download the PKG package</span></span>
`powershell-6.2.0-osx-x64.pkg`
<span data-ttu-id="0ffc9-127">desde la página de [versiones][] en la máquina macOS.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="0ffc9-128">Puede hacer doble clic en el archivo y seguir las indicaciones, o bien instalarlo desde el terminal:</span><span class="sxs-lookup"><span data-stu-id="0ffc9-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="0ffc9-129">Instale [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="0ffc9-129">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="0ffc9-130">OpenSSL se necesita para la comunicación remota de PowerShell y las operaciones de CIM.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-130">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="0ffc9-131">Archivos binarios</span><span class="sxs-lookup"><span data-stu-id="0ffc9-131">Binary Archives</span></span>

<span data-ttu-id="0ffc9-132">Se proporcionan archivos binarios `tar.gz` de PowerShell para la plataforma macOS, a fin de permitir escenarios de implementación avanzados.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-132">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="0ffc9-133">Instalación de archivos binarios en macOS</span><span class="sxs-lookup"><span data-stu-id="0ffc9-133">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.2.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="0ffc9-134">Instale [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="0ffc9-134">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="0ffc9-135">OpenSSL se necesita para la comunicación remota de PowerShell y las operaciones de CIM.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-135">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="0ffc9-136">Instalación de dependencias</span><span class="sxs-lookup"><span data-stu-id="0ffc9-136">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="0ffc9-137">Instalación de las herramientas de línea de comandos de XCode</span><span class="sxs-lookup"><span data-stu-id="0ffc9-137">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="0ffc9-138">Instalación de OpenSSL</span><span class="sxs-lookup"><span data-stu-id="0ffc9-138">Install OpenSSL</span></span>

<span data-ttu-id="0ffc9-139">OpenSSL se necesita para la comunicación remota de PowerShell y las operaciones de CIM.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-139">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="0ffc9-140">Puede realizar la instalación mediante MacPorts o Brew.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-140">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="0ffc9-141">Instalación de OpenSSL mediante Brew</span><span class="sxs-lookup"><span data-stu-id="0ffc9-141">Install OpenSSL via Brew</span></span>

<span data-ttu-id="0ffc9-142">Consulte [Acerca de Brew](#about-brew) para obtener información sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-142">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="0ffc9-143">Para instalar OpenSSL, ejecute `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-143">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="0ffc9-144">Instalación de OpenSSL mediante MacPorts</span><span class="sxs-lookup"><span data-stu-id="0ffc9-144">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="0ffc9-145">Instale las [herramientas de la línea de comandos de XCode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="0ffc9-145">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="0ffc9-146">Instale MacPorts.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-146">Install MacPorts.</span></span>
   <span data-ttu-id="0ffc9-147">Si necesita instrucciones, consulte la [guía de instalación](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="0ffc9-147">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="0ffc9-148">Actualice MacPorts mediante la ejecución de `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-148">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="0ffc9-149">Actualice los paquetes de MacPorts mediante la ejecución de `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-149">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="0ffc9-150">Instale OpenSSL mediante la ejecución de `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-150">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="0ffc9-151">Vincule las bibliotecas para que estén a disposición de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0ffc9-151">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="0ffc9-152">Desinstalación de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="0ffc9-152">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="0ffc9-153">Si ha instalado PowerShell con Homebrew, use el siguiente comando para desinstalar:</span><span class="sxs-lookup"><span data-stu-id="0ffc9-153">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="0ffc9-154">Si ha instalado PowerShell mediante descarga directa, deberá quitar PowerShell manualmente:</span><span class="sxs-lookup"><span data-stu-id="0ffc9-154">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="0ffc9-155">Para quitar las rutas de acceso de PowerShell adicionales, consulte la sección de [rutas de acceso](#paths) de este documento y elimine las rutas de acceso deseadas mediante `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-155">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="0ffc9-156">Este paso no es necesario si ha realizado la instalación con Homebrew.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-156">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="0ffc9-157">Paths</span><span class="sxs-lookup"><span data-stu-id="0ffc9-157">Paths</span></span>

* `$PSHOME` <span data-ttu-id="0ffc9-158">estará</span><span class="sxs-lookup"><span data-stu-id="0ffc9-158">is</span></span> `/usr/local/microsoft/powershell/6.2.0/`
* <span data-ttu-id="0ffc9-159">Los perfiles de usuario se leerán de</span><span class="sxs-lookup"><span data-stu-id="0ffc9-159">User profiles will be read from</span></span> `~/.config/powershell/profile.ps1`
* <span data-ttu-id="0ffc9-160">Los perfiles predeterminados se leerán de</span><span class="sxs-lookup"><span data-stu-id="0ffc9-160">Default profiles will be read from</span></span> `$PSHOME/profile.ps1`
* <span data-ttu-id="0ffc9-161">Los módulos de usuario se leerán de</span><span class="sxs-lookup"><span data-stu-id="0ffc9-161">User modules will be read from</span></span> `~/.local/share/powershell/Modules`
* <span data-ttu-id="0ffc9-162">Los módulos compartidos se leerán de</span><span class="sxs-lookup"><span data-stu-id="0ffc9-162">Shared modules will be read from</span></span> `/usr/local/share/powershell/Modules`
* <span data-ttu-id="0ffc9-163">Los módulos predeterminados se leerán de</span><span class="sxs-lookup"><span data-stu-id="0ffc9-163">Default modules will be read from</span></span> `$PSHOME/Modules`
* <span data-ttu-id="0ffc9-164">El historial de PSReadline se grabará en</span><span class="sxs-lookup"><span data-stu-id="0ffc9-164">PSReadline history will be recorded to</span></span> `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

<span data-ttu-id="0ffc9-165">Los perfiles respetan la configuración por host de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-165">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="0ffc9-166">Así que el perfil predeterminado específico del host está en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-166">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="0ffc9-167">PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en macOS.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-167">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="0ffc9-168">Dado que macOS es una derivación de BSD, se usa el prefijo `/usr/local` en lugar de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-168">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="0ffc9-169">Por lo tanto, `$PSHOME` es `/usr/local/microsoft/powershell/6.2.0/`, y el vínculo simbólico se coloca en `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="0ffc9-169">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0ffc9-170">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="0ffc9-170">Additional Resources</span></span>

* <span data-ttu-id="0ffc9-171">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="0ffc9-171">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="0ffc9-172">[Repositorio GitHub de Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="0ffc9-172">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="0ffc9-173">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="0ffc9-173">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[<span data-ttu-id="0ffc9-174">versiones</span><span class="sxs-lookup"><span data-stu-id="0ffc9-174">releases</span></span>]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
